---
title: monolog & mongodb的强强联手
date: 2017-03-22 22:55:29
tags: [monolog,mongodb]
---
monolog和mongodb的强强联手
网站日志管理中将这两把利剑同时使用，效果如何，之后续......
因为这个日志管理还没做完，我边搜集资料边完成项目，文章会从“这是什么”，“为什么要用它”，“如何用”这三个方面展开。

<!--more-->

首先介绍一下这两位superstar:
`monolog`
==================

!['monolog'](https://raw.githubusercontent.com/AllenGu93/imageForHexo/master/monolog-1.gif)

>Monolog是php下比较全又容易扩展的记录日志类库。目前有包括Symfony 、Laravel、 CakePHP等诸多
>知名php框架都内置了Monolog。Monolog可以把你的日志发送到文件，sockets，收件箱，数据库。
>Monolog遵循PSR3的接口规范，可以很轻易的替换成其他遵循同一规范的日志类库。Monolog具有良好的
>扩展性，通过Handler、Formatter和Processor这几个接口，可以对Monolog类库进行各种扩展和自定
>义。

mongodb
=================
!['mongodb'](https://raw.githubusercontent.com/AllenGu93/imageForHexo/master/mongo.png)

>MongoDB is not a key/value store, it’s quite a bit more. It’s definitely not 
>a RDBMS either. It seems to be very performant and either has.
>I think Mongo might be **the closest thing to a RDBMS** replacement that I’ve 
>seen so far.It won’t work for all data sets 
>and access patterns, but it’s built for your typical CRUD stuff. Storing what 
>is essentially a huge hash, and being able to select on any of those keys, is 
>what most people use a relational database for. If your DB is 3NF and you 
>don’t do any joins (you’re just selecting a bunch of tables and putting all 
>the objects together, AKA what most people do in a web app), MongoDB would 
>probably kick ass for you.


如何让他们强强联合？
==================

最重要的地方来了，既然mongodb和monolog是这么牛，拓展性一定不差，对！ 我们去monolog里看看，有没有能连接到mongodb的接口啥的......
五分钟后......
```php
class MongoDBHandler extends AbstractProcessingHandler
{
    protected $mongoCollection;

    public function __construct($mongo, $database, $collection, $level = Logger::DEBUG, $bubble = true)
    {
        if (!($mongo instanceof \MongoClient || $mongo instanceof \Mongo || $mongo instanceof \MongoDB\Client)) {
            throw new \InvalidArgumentException('MongoClient, Mongo or MongoDB\Client instance required');
        }

        $this->mongoCollection = $mongo->selectCollection($database, $collection);

        parent::__construct($level, $bubble);
    }
```


