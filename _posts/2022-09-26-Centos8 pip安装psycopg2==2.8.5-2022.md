
---
layout:     post
title:      Centos8 pip3 安装psycopg2==2.8.5报错解决
subtitle:    "\"直接上代码\""
date:       2022-09-26
author:     Mr Du
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - centos8
---

> “🙉🙉🙉 ”


## 前言
在Centos8系统python3.8.5环境中pip安装odoo14的依赖包报错了！！！
错误的信息如下：

Collecting psycopg2==2.8.5
  Downloading http://mirrors.tencentyun.com/pypi/packages/a8/8f/1c5690eebf148d1d                                                                                                             1554fc00ccf9101e134636553dbb75bdfef4f85d7647/psycopg2-2.8.5.tar.gz (380 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 380.9/380.9 kB 878.0 kB/s eta 0:00:00
  Preparing metadata (setup.py) ... error
  error: subprocess-exited-with-error

  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [23 lines of output]
      running egg_info
      creating /tmp/pip-pip-egg-info-zz6ek4ba/psycopg2.egg-info
      writing /tmp/pip-pip-egg-info-zz6ek4ba/psycopg2.egg-info/PKG-INFO
      writing dependency_links to /tmp/pip-pip-egg-info-zz6ek4ba/psycopg2.egg-in                                                                                                             fo/dependency_links.txt
      writing top-level names to /tmp/pip-pip-egg-info-zz6ek4ba/psycopg2.egg-inf                                                                                                             o/top_level.txt
      writing manifest file '/tmp/pip-pip-egg-info-zz6ek4ba/psycopg2.egg-info/SO                                                                                                             URCES.txt'

      Error: pg_config executable not found.

      pg_config is required to build psycopg2 from source.  Please add the direc                                                                                                             tory
      containing pg_config to the $PATH or specify the full executable path with                                                                                                              the
      option:

          python setup.py build_ext --pg-config /path/to/pg_config build ...

      or with the pg_config option in 'setup.cfg'.

      If you prefer to avoid building psycopg2 from source, please install the P                                                                                                             yPI
      'psycopg2-binary' package instead.

      For further information please check the 'doc/src/install.rst' file (also                                                                                                              at
      <https://www.psycopg.org/docs/install.html>).

      [end of output]

  note: This error originates from a subprocess, and is likely not a problem wit                                                                                                             h pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
╰─> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.
[root@VM-4-4-centos ~]# pip3 install psycopg2==2.8.5
Looking in indexes: http://mirrors.tencentyun.com/pypi/simple
Collecting psycopg2==2.8.5
  Using cached http://mirrors.tencentyun.com/pypi/packages/a8/8f/1c5690eebf148d1                                                                                                             d1554fc00ccf9101e134636553dbb75bdfef4f85d7647/psycopg2-2.8.5.tar.gz (380 kB)
  Preparing metadata (setup.py) ... error
  error: subprocess-exited-with-error

  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [23 lines of output]
      running egg_info
      creating /tmp/pip-pip-egg-info-tbn29qtz/psycopg2.egg-info
      writing /tmp/pip-pip-egg-info-tbn29qtz/psycopg2.egg-info/PKG-INFO
      writing dependency_links to /tmp/pip-pip-egg-info-tbn29qtz/psycopg2.egg-in                                                                                                             fo/dependency_links.txt
      writing top-level names to /tmp/pip-pip-egg-info-tbn29qtz/psycopg2.egg-inf                                                                                                             o/top_level.txt
      writing manifest file '/tmp/pip-pip-egg-info-tbn29qtz/psycopg2.egg-info/SO                                                                                                             URCES.txt'

      Error: pg_config executable not found.

      pg_config is required to build psycopg2 from source.  Please add the direc                                                                                                             tory
      containing pg_config to the $PATH or specify the full executable path with                                                                                                              the
      option:

          python setup.py build_ext --pg-config /path/to/pg_config build ...

      or with the pg_config option in 'setup.cfg'.

      If you prefer to avoid building psycopg2 from source, please install the P                                                                                                             yPI
      'psycopg2-binary' package instead.

      For further information please check the 'doc/src/install.rst' file (also                                                                                                              at
      <https://www.psycopg.org/docs/install.html>).

      [end of output]

  note: This error originates from a subprocess, and is likely not a problem wit                                                                                                             h pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
╰─> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.

## 解决办法
1.网上搜了一把，postgres数据库的环境变量没有配置
2.有没有简单一点的呢，sudo dnf install libpq-devel，通过查看官方资料得到原来是缺少了libpq-devel这个库，安装这个库就编译通过了！
