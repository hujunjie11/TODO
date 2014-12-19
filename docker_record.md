docker awesome --- make deploying your app easy
==================================================
## 1. how to remove nemo(dangling images) docker images?
use command:
~~~shell
sudo docker rmi 'sudo docker images --filter 'dangling=true' -q --no-trunc'
~~~
### extension - how to remove all containers which are not running:
use command:
~~~shell
docker rm 'docker ps -aq --no-trunc --filter "status=exited"'
~~~
