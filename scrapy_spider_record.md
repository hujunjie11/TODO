scrapy details
====================
## The basic knowledge about scrapy ?
  * request & response ?
  * how selector works ? (xpath )
  * how to store items into redis & how to handle pipelines ?
  * scrapy queue (the perfermance of scrapy && RabbitMQ ) ?

## 测验 (性能检测)
* 单进程(settings 并发) 
* 多进程
* scrapyd
* redis中心模式(单机)
* redis分布式(celery)

## Tips:
 1. 开启gzip
 2. 多线程
 3. 对于定向采集可以用正则取代xpath
 4. 用pycurl代替urlib
 5. 换个带宽高的环境

## scrapy瓶颈
 * network 
 * disk
 * cpu
 * memory
 
## scrapy crawl test record 
 * COOKIE_ENABLE = False  default
 * HTTPCACHE_ENABLE = 
 * DNSCACHE = 
 * LOG_ENABLED = FALSE 
 * CONCURRENT_REQUESTS_PER_IP = 

## record
 * 实验时,跑一个spider比较稳定，存在多个spider时,spider容易崩溃,最终只存在一个spider
## some tips on StackOverflow:
 * [Speed up web scraper](http://stackoverflow.com/questions/17029752/speed-up-web-scraper)
 * 
## scrapyd
 1. 运scrapyd: 在终端中执行scrapyd 启动scrapy服务器
 2. scrapy.cfg 修改配置参考[用scrapyd来提供crawler服务](http://tchen.me/posts/2013-06-10-use-scrapyd-to-serve-scrapy-projects.html)
 3. 将爬虫部署到scrapyd中,运行命令scrapy deploy default -p [爬虫名]
 4. 打开浏览器,输入http://localhost:6800/可看见已经部署的爬虫
 5. 运行爬虫 curl http://localhost:6800/schedule.json -d project=default -d spider=[爬虫名]
