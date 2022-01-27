# hoocron-plugin-redis

Redis support for [Hoocron](https://github.com/yaroslaff/hoocron). Hoocron is cron with hooks.

## Installation
~~~
pip3 install hoocron-plugin-redis
~~~

## Example simple usage
Start hoocron with redis plugin, configure `--redis`:
~~~
$ hoocron.py --redis TICK

Loading hoocron_plugin.cron
Loading hoocron_plugin.http
Loading hoocron_plugin.redis
connect to redis over network: localhost:6379
started redis thread, watch list 'hook'
~~~

Now send hook name to list 'hook' (we will use redis-cli for this):
~~~
127.0.0.1:6379> LPUSH hook TICK
(integer) 1
~~~

hoocron will run job `TICK` in less then 1 second (default sleep period)

## Other options
~~~
  --redis JOB [JOB ...]
                        Jobs to bind with redis hook
  --redis-url REDIS_URL Path to redis def: redis://localhost:6379/0
  --redis-list KEY      name of redis key to trigger jobs. def: hook
~~~

`--redis-url` could be set from environment variable `REDIS_URL`