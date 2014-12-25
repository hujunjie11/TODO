# scrapy deploy test report
## 1 scrapy bench 
Scrapy提供了一个简单的性能测试工具。其创建了一个本地HTTP服务器，并以最大可能的速度进行爬取。 
该测试性能工具目的是测试Scrapy在您的硬件上的效率，来获得一个基本的底线用于对比。 其使用了一
个简单的spider，仅跟进链接，不做任何处理。
106.187.49.52输出如下：
![bench1](http://7sbqj0.com1.z0.glb.clouddn.com/bench.png)
![bench2](http://7sbqj0.com1.z0.glb.clouddn.com/bench1.png)
从图中可以看出在无其他压力（理想）情况下，日本服务器上爬虫理想爬取速度为**3360page/min**

## 2 scrapy crawl spider
在执行scrapy crawl spider 命令下

## 3 scrapyd 部署爬虫
使用scrapyd部署爬虫,在爬虫settings.py中DOWNLOAD_DELAY设置**较小**的时候(如0.6)的情况下,部署多个爬虫,爬虫之间或许由于存在竞争关系,导致最终只能存在一个爬虫运行. 若将DOWNLOAD_DELAY设置**较大**(如60),爬虫可以共存. 
通过网页访问job执行情况：

![scrapy job](http://7sbqj0.com1.z0.glb.clouddn.com/scrapy_job.png)

## 4 scrapy redis部署爬虫 -- 主从式部署
采用redis库管理爬虫队列, 并以主从模式部署redis.测试了两种情况:
* 日本服务器作为master,阿里云服务器作为slave;
* 阿里云服务器作为master,日本服务器作为slave.
两种情况下,爬虫抓取速度相比单机爬虫抓取速度(scrapy crawl方式)变慢了很多. *具体原因还未知* .

## 5 scrapy redis部署爬虫 -- 单机式部署
同样采用redis数据库方式部署爬虫,不采用任何模式,运行爬虫,爬虫抓取速度和采用redis数据库并以主从式部署爬虫的情况速度一样.

## 6 scrapy redis部署爬虫 -- 中心式部署
**还未测试**

