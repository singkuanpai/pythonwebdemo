# pythonwebdemo

## uwsgi + flask  demo

### 操作步骤

#### 安装
```
pip install uwsgi
```

#### 创建软连接
```
ln -s /usr/local/python3/bin/uwsgi /usr/local/bin/uwsgi
```

#### 配置文件
```
"""
# start: uwsgi --ini uwsgi.ini
# stop: uwsgi --stop uwsgi.pid
"""

[uwsgi]
# 直接做web服务器使用，项目所在服务器地址
http=0.0.0.0:5000
# 使用nginx连接时使用，项目所在服务器地址
socket=0.0.0.0:8001
# 项目目录
chdir=/home/project/uwsgi_test
# 项目中启动文件
wsgi-file=view.py
callable=app
# 进程数
processes=4
# 线程数
threads=2
# uwsgi服务器的角色
master = True
# 存放进程编号的文件
# pidfile = uwsgi.pid
# 日志文件，uwsgi可以脱离终端在后台运行，日志看不见。
daemonize = uwsgi.log
# 指定依赖的虚拟环境
# virtualenv= /home/python/.virtualenvs/test_py3

```

#### 启动服务
```
uwsgi config.ini
```
