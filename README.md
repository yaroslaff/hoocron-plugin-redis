# hoocron-plugin-redis

Redis support for [Hoocron](https://github.com/yaroslaff/hoocron). Hoocron is cron with hooks.

## Installation
~~~
pip3 install hoocron-plugin-redis
~~~

## Example usage
Start hoocron with redis plugin:
~~~
$ hoocron.py -j J /bin/touch /tmp/touch --redis J

Loading hoocron_plugin.cron
Loading hoocron_plugin.http
Loading hoocron_plugin.redis
connect to redis over network: localhost:6379
started redis thread, watch list 'hook'
~~~

Now send hook name to list 'hook' (we will use redis-cli for this):
~~~
127.0.0.1:6379> LPUSH hook T
(integer) 1
~~~

hoocron will 