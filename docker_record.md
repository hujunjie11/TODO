docker awesome --- make deploying your app easy
==================================================
## 1. how to remove neom docker images?
use command:
~~~shell
sudo docker images --filter 'dangling=true' -q --no-trunc
~~~
