# py-ulord-api

[![](https://img.shields.io/badge/py--ulord--api-incomplete-red.svg)](https://github.com/UlordChain/py-ulord-api#todo-list)
[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)
[![](https://img.shields.io/badge/cli-completed-green.svg)](https://github.com/UlordChain/py-ulord-api#cli)

[English](https://github.com/UlordChain/py-ulord-api)

Ulordƽ̨HTTP�ӿڿͻ���

����[�ĵ�](http://py-ulord-api.readthedocs.io/en/latest/)�鿴����API�ĵ��Լ����ʹ�á�

*��Ҫ*: ��ǰpy-ulord-api��Ŀֻ���ulordƽ̨��0.1�汾������python2.7���ݲ�֧��python3��

*ע��*: Ϊ�˱�����ulordƽ̨�㱣��ͬ��״̬����ǰ��Ŀ���ܻ���µıȽ�Ƶ����Ŀǰֻ���ƽ̨��0.1�汾�����˲��ԡ�����ǰ���������汾��ulordƽ̨����ʱ���ܻ���ּ������⡣

## Ŀ¼

- [��װ](#��װ)
- [ʹ��](#ʹ��)
- [�ĵ�](#�ĵ�)
- [����](#����)
- [��������](#��������)
- [����](#����)
  - [©������](#©������)
  - [��ȡ����](#��ȡ����)
- [��Ȩ](#��Ȩ)

## ��װ
> *��Ҫ*: ��δ��ɣ�

��װpip:

```sh
pip install ulordapi
```

����ʹ�������Ŀ���а�װ
```sh
git clone https://github.com/UlordChain/py-ulord-api.git
cd py-ulord-api
python setup.py install
```

## ʹ��
��ǰ��Ŀ�����ַ�ʽ�����������У�python�ӿ��Լ�web�ӿڡ�

### ������
�����ʹ�������д�ӡ������������һЩ����:

```sh
usage: ulordapi [options|sub-command] [-h]

ulordapi ---- SDK for the Ulord APIs

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit

ulordapi sub-command:
  ulordapi sub-command,reading API documents

  {daemon,UP,udfs,DB,config}
                        using basic config - E:\ulord\ulord-blog-demo\venv\lib\site-packages\ulordapi-0.0.1-py2.7.egg\ulordapi\config
    daemon              Daemon process,including web server and udfs daemon.
    UP                  main functions
    udfs                transfer resources to the platform
    DB                  Manage database
    config              Manage configuration

Use 'ulordapi <command> --help' to learn more about each command.

EXIT STATUS

The CLI will exit with one of the following values:

0   Successful execution.
1   Failed executions.
```
### python�ӿ�:

������...

```sh
In [1]: from ulordapi import Junior

In [2]: junior = Junior(appkey="5d42b27e581c11e88b12f48e3889c8ab",secret="5d42b27f581c11e8bf63f48e3889c8ab")

In [3]: junior.config_show()
Out[3]:
{'baseconfig': {'config_file': 'E:\\ulord\\py-ulord-api\\ulordapi\\config',
  'version': '0.0.1'},
 'dbconfig': {'Debug': True,
  'IsCreated': False,
  'JSON_AS_ASCII': False,
  'SECRET_KEY': 'ulord platform is good',
  'SQLALCHEMY_COMMIT_ON_TEARDOWN': True,
  'SQLALCHEMY_COMMIT_TEARDOWN': True,
  'SQLALCHEMY_DATABASE_URI': 'sqlite:///sqlite.db',
  'SQLALCHEMY_TRACK_MODIFICATIONS': True},
 'logconfig': {'format': '[%(asctime)s] %(levelname)-8s %(name)s %(message)s',
  'level': 'INFO',
  'log_file_path': 'E:\\ulord\\py-ulord-api\\ulordapi\\upapi.log'},
 'udfsconfig': {'udfs_host': '127.0.0.1', 'udfs_port': 5001},
 'ulordconfig': {'ulord_appkey': '5d42b27e581c11e88b12f48e3889c8ab',
  'ulord_billings': '/transactions/publish/account',
  'ulord_billings_detail': '/transactions/account/inout',
  'ulord_checkbought': '/transactions/check',
  'ulord_createwallet': '/transactions/createwallet',
  'ulord_curtime': 1526433796,
  'ulord_head': {'U-AppKey': '5d42b27e581c11e88b12f48e3889c8ab',
   'U-CurTime': '1526433796',
   'U-Sign': '65E98D476619939606D3438B535A07F0'},
  'ulord_in': '/transactions/account/in',
  'ulord_out': '/transactions/account/out',
  'ulord_paytouser': '/transactions/paytouser',
  'ulord_publish': '/transactions/publish',
  'ulord_publish_data': {'author': 'test3',
   'content_type': '.txt',
   'description': '\xe8\xbf\x99\xe6\x98\xaf\xe7\xac\xac\xe4\xb8\x80\xe7\xaf\x87UDFS\xe6\xb5\x8b\xe8\xaf\x95\xe6\x96\x87\xe4\xbb\xb6',
   'pay_password': '123',
   'price': 0.1,
   'tag': ['test', 'udfs'],
   'tags': ['test', 'udfs'],
   'title': '\xe7\xac\xac\xe4\xb8\x80\xe7\xaf\x87\xe6\x8a\x80\xe6\x9c\xaf\xe5\x8d\x9a\xe5\xae\xa2',
   'udfs_hash': 'QmQGSgwfMtLH291KmyVouvu1mCwNYvZ2FGmStfvRwLQEgV'},
  'ulord_publish_num': '/transactions/publish/count',
  'ulord_querybalance': '/transactions/balance',
  'ulord_queryblog': '/content/list',
  'ulord_secret': '5d42b27f581c11e8bf63f48e3889c8ab',
  'ulord_transaction': '/transactions/consume',
  'ulord_url': 'http://192.168.14.67:5000/v1',
  'ulord_userbought': '/content/consume/list',
  'ulord_userpublished': '/content/publish/list',
  'ulord_view': '/content/view'},
 'webconfig': {'activity': True,
  'amount': 10,
  'host': '0.0.0.0',
  'port': 5000,
  'privkeypath': 'E:\\ulord\\py-ulord-api\\utils\\private.pem',
  'pubkeypath': 'E:\\ulord\\py-ulord-api\\utils\\public.pem',
  'start': True,
  'token_expired': 86400}}
```

### web�ӿ�:

������...

## �ĵ�

API�ĵ�:[����](https://github.com/UlordChain/py-ulord-api/blob/master/docs/API.md)

[����](http://py-ulord-api.readthedocs.io/en/latest/)

�������ĵ�:[����](https://github.com/UlordChain/py-ulord-api/blob/master/docs/cli_help.md)

web�ӿ��ĵ�:[����](https://github.com/UlordChain/py-ulord-api/blob/master/docs/web-server.md)

## Featured Projects

 ������...

## ��������
- [x] ��Ӵ�������
- [ ] һЩ�ĵ�
- [ ] ֧�� python3
- [ ] �����Ƶı��ֽӿ�
- [ ] ��Ӷ��߳�����
- [ ] ��ӵ�Ԫ����
- [ ] docker ����

## ����

### ©������

�����ʹ��[GitHub issue tracker](https://github.com/UlordChain/py-ulord-api/issues)���ύ���ֵ�©��.

### ��ȡ����

�ǳ���ӭ��ȡ������ȡ֮ǰ, ��Щ��׼��ʱ��δ���...

### ���õ��Ķ�����Ŀ?

һЩ�㿪ʼ�ĵط��� (WIP)

�������������ļ�: [ulordapi/user.py](https://github.com/UlordChain/py-ulord-api/blob/master/ulordapi/user.py#L174) <br>
�м����������ļ�: [ulordapi/user.py](https://github.com/UlordChain/py-ulord-api/blob/master/ulordapi/user.py#L191) <br>
������: [ulordapi/daemonCLI.py](https://github.com/UlordChain/py-ulord-api/blob/master/ulordapi/daemonCLI.py) <br>
web�ӿ�: [ulordapi/webServer.py](https://github.com/UlordChain/py-ulord-api/blob/master/ulordapi/webServer.py) <br>

## ��Ȩ

����Ŀ������ѭ [MIT Э��](https://opensource.org/licenses/MIT)�����������Ŀ�е�[LICENSE](LICENSE)�ĵ���