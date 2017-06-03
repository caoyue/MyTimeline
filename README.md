timeline.me
==========================

### About
- ```timeline.me``` is a project let you backup your timeline, such as twitter, weibo, and rss feeds ...
- a [demo](https://i.caoyue.me)

### features
- sync your timeline
- update status, support twitter, weibo and "your own tweets" ([moments](https://i.caoyue.me/moments))
- this day in history posts ([past](https://i.caoyue.me/past))
- simple charts about your timeline ([chart](https://i.caoyue.me/chart))

### How to
1. install requirments

    ```shell
    pip install -r deploy/requirements.txt
    ```

2. mysql
    * create database

        ```shell
        mysql -u USERNAME -p < deploy/init.sql
        ```
    * emoji support
        + MySQL server v5.5.3+
        + set ```CHARSET``` to ```utf8mb4```

3. set config
    * rename ```config.example.py``` to ```config.py``` and set your configs
    * rename ```oauth2py.example.json``` to ```oauth2py.json``` and set your oauth keys

4. nginx
    * nginx config example is available in ```/deploy/timeline.conf```

5. start server
    - command

        ```shell
        python timeline.py --port=8888
        ```
    - supervisor
        * supervisor config example is available in ```/deploy/supervisor.conf```

6. sign in
    - http://your-domain/signin
    - sign in with your twitter/weibo/...
    - bind other accounts (your-domain/admin/accounts)

7. sync your timeline
    - use cron
        * cron example is available in ```/deploy/cron```
    - web
        * your-domain/admin

### docker
- build

    ```bash
    docker build -t timeline .
    ```
- run

    `${MYSQL_SERVER}` is your mysql container

    ```bash
    docker run --name timeline_server -p 8000:80 --link ${MYSQL_SERVER}:mysql_host -d timeline
    ```
