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
 * 实验时,跑一个spider比较稳定，存在多个spider时,spider容易崩溃,最终只存在一个spider;
 * 但个spider cpu占用率有时能达到90%多;
 


## some tips on StackOverflow:
 * [Speed up web scraper](http://stackoverflow.com/questions/17029752/speed-up-web-scraper)
 * [Scrapy Crawling Speed is Slow](http://stackoverflow.com/questions/13505194/scrapy-crawling-speed-is-slow-60-pages-min#comment18491083_13505194)
 

## scrapyd
 1. 运scrapyd: 在终端中执行scrapyd 启动scrapy服务器
 2. scrapy.cfg 修改配置参考[用scrapyd来提供crawler服务](http://tchen.me/posts/2013-06-10-use-scrapyd-to-serve-scrapy-projects.html)
 3. 将爬虫部署到scrapyd中,运行命令scrapy deploy default -p [爬虫名]
 4. 打开浏览器,输入http://localhost:6800/可看见已经部署的爬虫
 5. 运行爬虫 curl http://localhost:6800/schedule.json -d project=default -d spider=[爬虫名]

## scrapy 在单机上的性能测试
  *  运行scrapy bench。 Scrapy提供了一个简单的性能测试工具。其创建了一个本地HTTP服务器，并以最大可能的速度进行爬取。 该测试性能工具目的是测试Scrapy在您的硬件上的效率，来获得一个基本的底线用于对比。 其使用了一个简单的spider，仅跟进链接，不做任何处理。注意，这是一个非常简单，仅跟进链接的spider。 任何您所编写的spider会做更多处理，从而减慢爬取的速度。 减慢的程度取决于spider做的处理以及其是如何被编写的。
## scrapy 暂停、恢复 job
 * Scrapy通过如下工具支持这个功能:
      1. 一个把调度请求保存在磁盘的调度器
      2. 一个把访问请求保存在磁盘的副本过滤器[duplicates filter]
      3. 一个能持续保持爬虫状态(键/值对)的扩展
 * Job 路径 要启用持久化支持，你只需要通过 JOBDIR 设置 job directory 选项。这个路径将会存储 所有的请求数据来保持一个单独任务的状态(例如：一次spider爬取(a spider run))。必须要注意的是，这个目录不允许被不同的spider 共享，甚至是同一个spider的不同jobs/runs也不行。也就是说，这个目录就是存储一个 单独 job的状态信息。命令:scrapy crawl somespider -s JOBDIR=crawls/somespider-1
