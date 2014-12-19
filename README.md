TODO
====
## zinnia 博客系统界面定制
1. 模板系统
	*. 前端模板系统基础知识(类似jinja2包括页面的继承、引用、python变量的使用)
	*. 模板系统的框架(博客系统的构成要素)
2. jquery
	*. 前端行为  
		*. web页面的事件、行为
		*. 与后台交互
3. bootstrap
	*. 博客页面框架的构成(Header、container、footer、sidebar...)
4). 特效
	*. three.js 三维效果
	*. about可使用impress.js 


## scrapy爬虫系统

### 抓取一个网站的步骤：
	*. 新建项目(Project),新建一个爬虫项目
	*. 制定抓取目标(Items),明确抓取的目标
	*. 编写爬虫(Spider),编写抓取网页的爬虫
	*. 存储内容(Pipelien),设计管道存储爬取的数据

1. 爬虫基本结构
	*. spider 抓取行为
	*. pipeline 存储方式
	*. Item 存储结构
	*. Selector选择器
2. 爬虫优化
	*. 分布式
		*. Celery
		*. RabbitMQ
	*. 攻防策略
		*. Cookie
		*. Delay
		*. User Agent
		*. Proxy Pool

## docker 运用程序部署
	1. docker安装部署
		*. 更新docker源
		*. 安装docker
	2. docker基础使用
		*. 官网pull docker images (ubuntu、redis、nginx...)
		*. docker中运行简单web程序
		*. 定制属于自己的Dockerfile
		*. 发布Docker到官网
