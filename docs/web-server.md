# py-ulord-api web API document

This is a document of blog web's API.It services for front-end.

## Table of Contents Ŀ¼
- [Introudction ˵��](#introudction-˵��)
- [Get Publickey ��ȡ��Կ](#get-publickey-��ȡ��Կ)
- [test encrypt ���Լ���](#test-encrypt-���Լ���)
- [Register ע��](#Register-ע��)
- [Pay To User �Żݻ������ע����û���10��ulord](#pay-to-user-�Żݻ����ע����û���10��ulord)
- [Login ��¼](#login----��¼)
- [Install Go](#logout----�ǳ�)
- [Publish ��������](#publish--��������)
- [List All Blog ��ȡ����](#list-all-blog--��ȡ����)
- [check isbought ��鲩���Ƿ񸶷�](#check-isbought--��鲩���Ƿ񸶷�)
- [Pay blogs ֧������](#pay-blogs-֧������)
- [Pay ADs ֧�����](#pay-ads-֧�����)
- [List Personal Info �г�������Ϣ](#list-personal-info-�г�������Ϣ)
- [List Personal Balance �г��������](#list-personal-balance-�г��������)
- [List Personal Published �г����˷���������Դ](#list-personal-published-�г����˷���������Դ)
- [List Personal Published num �г����˷���������Դ����](#list-personal-published-num-�г����˷���������Դ����)
- [~~List Personal Bought �г����˹��������Դ~~](#list-personal-bought-�г����˹��������Դ)
- [List Billings detail �г������˵���ϸ��Ϣ(�����֧���ӿ��ܺ�)](#list-billings-detail-�г������˵���ϸ��Ϣ�����֧���ӿ��ܺ�)
- [List Billings �г������˵�](#list-billings-�г������˵�)
- [List User's Outgos �г�����֧��](#list-users-outgos-�г�����֧��)
- [List User's Incomes �г����������˵�](#list-users-incomes-�г����������˵�)
- [Add Blog View ���Ӳ��ͷ�����](#add-blog-view-���Ӳ��ͷ�����)
- [Modify Personal Info �޸ĸ�����Ϣ](#modify-personal-info-�޸ĸ�����Ϣ)
- [~~Modify Blog Info �޸�������Ϣ~~](#modify-blog-info-�޸�������Ϣ)
- [~~Record Blog ��Ӳ��ͷ���~~](#record-blog-��Ӳ��ͷ���)
- [��¼A:��������ձ�](#��¼a��������ձ�)

## Introudction ˵��

��ƪAPI�ĵ���ulord������ʾϵͳ��̨����python2.7��ɡ�����API��Ҫ��ͷ�����token�ſɵ��ã���������Ϊjson��ʽ���ɹ�����0�����󷵻ش����롣�����ʽ���£�

�ɹ�
```python
{
    "errcode": 0,#״̬��
    "reason": "success",#�ɹ�
    "result": ""#���ؽ��������һЩ����Ҫ�ķ���ֵ
}
```

ʧ��
```python
{
    "errcode": 400~60301,# �����룬�����¼A
    "reason": "some reason"# ����ԭ�������¼A
}
```
���ܲ��ֲ��÷ǶԳƼ��ܣ�ǰ������Կ�ӿڻ�ù�Կ�������ݷ��͵���ˣ���˽��н��ܡ�

ǰ�˼��ܲ��ִ����꿴[����](https://github.com/UlordChain/ulord-blog-demo/blob/master/js/ulord-blog/views/login.html#L54),��̨���ܴ����꿴[����](https://github.com/UlordChain/ulord-blog-demo/blob/master/python/server.py#L76)��RSA�����������ɿ�[����](http://tool.chacuo.net/cryptrsapubkey)

## Get Publickey ��ȡ��Կ

GET http://127.0.0.1:5000/user/password

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "pubkey": "..."
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:~# curl http://127.0.0.1:5000/user/password
{
  "errcode": 0,
  "reason": "success",
  "result": {
    "pubkey": "-----BEGIN PUBLIC KEY-----\nMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCL/kiPydajd864uwuRABZ2dPRd\n2Cnl095IIHdHh0hljrWcwWxk7FNd896I6P/Z/wnHVBsPklkOEw0/9p6AVnTDI1fa\nEUPYgKaGAQWrf6A+3YGBxucaOqdttN4c5/vIUEY0L1MDRsJEADTfji/KgS4FaGkf\nJKhqQf+r5TkLC/IzsQIDAQAB\n-----END PUBLIC KEY-----"
  }
}
```
## test encrypt ���Լ���

POST http://127.0.0.1:5000/user/password

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|password | ������Ϣ |��|

```python
{
	"password":"���ܺ������"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "password": "����ԭ��"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:/home/ubuntu# curl --header "Content-Type:application/json" --request POST --data '{"password":"dsBRr665H+O50qAyjf627O3fAsK+XEq0RoGn9x+WNedIRK1Yn8wolrOfHR72I7F5NPgz4aXQsVy+HR/xensubvJzTuhhinfRhHUX9t2DtLpAB0Y/Dh7cUDTB96CXP7IQuM0TIYuqXGxd/6eL8mWMnJGPGOuwGHHcImXdytdEqTg="}' http://127.0.0.1:5000/user/password
{
  "errcode": 0,
  "reason": "success",
  "result": {
    "password": "111111"
  }
}

```
## Register ע��

POST http://127.0.0.1:5000/user/regist

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|username | �û��� |��|
|password | ���� |��|
|cellphone | �ֻ��� |��|
|email | ���� |��|

```python
{
	"username":"test",
	"password":"123",
	"cellphone":"15278559846",
	"email":"15574859643@163.com"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "token": "adc23e30-42cc-11e8-a365-f48e388c65be"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:/home/ubuntu# curl --header "Content-Type:application/json" --request POST --data '{"username":"iLlNQVJEl1UXfvPGXi0QqZrw1CVRriQ7K+idYLjLnTNND+/GN4eId0qqDOSlI3vwAiiOu2uIfCAr4K/JMbrl5RJkbLHw7Puvp7/2a5jWM3/vmptoqQPIvsMh5pP3UAcwivPyXqUnLxu/K4zvbiAvX0ezM5D19QP7NqZhohmZCJU=","password":"dsBRr665H+O50qAyjf627O3fAsK+XEq0RoGn9x+WNedIRK1Yn8wolrOfHR72I7F5NPgz4aXQsVy+HR/xensubvJzTuhhinfRhHUX9t2DtLpAB0Y/Dh7cUDTB96CXP7IQuM0TIYuqXGxd/6eL8mWMnJGPGOuwGHHcImXdytdEqTg="}' http://127.0.0.1:5000/user/regist
{
  "errcode": 0,
  "reason": "success",
  "result": {
    "token": "48cbfb56-51f4-11e8-82da-fa163e1b6459"
  }
}
```
## Pay To User �Żݻ������ע����û���10��ulord

GET http://127.0.0.1:5000/user/activity

head:token

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "amount": "���Ǯ��"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:/home/ubuntu# curl --header "token:48cbfb56-51f4-11e8-82da-fa163e1b6459" http://127.0.0.1:5000/user/activity
{
  "errcode": 20206,
  "reason": "֧��ʧ��.",
  "result": {
    "wallet_reason": "(-32603, 'Server error:   File \"/home/ubuntu/ht/env/ulord/lib/python2.7/site-packages/muwallet-1.1.2-py2.7.egg/uwallet/network.py\", line 785, in synchronous_get | BaseException: Failed to get response from server within timeout of 30')"
  }
}
```
## Login    ��¼

POST http://127.0.0.1:5000/user/login

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|username | �û��� |��|
|password | ���� |��|

```python
{
	"username":"test",
	"password":"123"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "token": "adc23e30-42cc-11e8-a365-f48e388c65be"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:/home/ubuntu# curl --header "Content-Type:application/json" --request POST --data '{"username":"iLlNQVJEl1UXfvPGXi0QqZrw1CVRriQ7K+idYLjLnTNND+/GN4eId0qqDOSlI3vwAiiOu2uIfCAr4K/JMbrl5RJkbLHw7Puvp7/2a5jWM3/vmptoqQPIvsMh5pP3UAcwivPyXqUnLxu/K4zvbiAvX0ezM5D19QP7NqZhohmZCJU=","password":"dsBRr665H+O50qAyjf627O3fAsK+XEq0RoGn9x+WNedIRK1Yn8wolrOfHR72I7F5NPgz4aXQsVy+HR/xensubvJzTuhhinfRhHUX9t2DtLpAB0Y/Dh7cUDTB96CXP7IQuM0TIYuqXGxd/6eL8mWMnJGPGOuwGHHcImXdytdEqTg="}' http://127.0.0.1:5000/user/login
{
  "errcode": 0,
  "reason": "success",
  "result": {
    "token": "37b28362-51f9-11e8-82da-fa163e1b6459"
  }
}

```
## Logout    �ǳ�

POST/GET http://127.0.0.1:5000/user/logout

head:token

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": "success"
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash
root@ubuntu:/home/ubuntu# curl --header "token:37b28362-51f9-11e8-82da-fa163e1b6459" http://127.0.0.1:5000/user/logout
{
  "errcode": 0,
  "reason": "success",
  "result": "success"
}
root@ubuntu:/home/ubuntu# curl --header "token:37b28362-51f9-11e8-82da-fa163e1b6459" --request POST http://127.0.0.1:5000/user/logout
{
  "errcode": 60104,
  "reason": "��Ч��token"
}
root@ubuntu:/home/ubuntu# curl --header "Content-Type:application/json" --request POST --data '{"username":"iLlNQVJEl1UXfvPGXi0QqZrw1CVRriQ7K+idYLjLnTNND+/GN4eId0qqDOSlI3vwAiiOu2uIfCAr4K/JMbrl5RJkbLHw7Puvp7/2a5jWM3/vmptoqQPIvsMh5pP3UAcwivPyXqUnLxu/K4zvbiAvX0ezM5D19QP7NqZhohmZCJU=","password":"dsBRr665H+O50qAyjf627O3fAsK+XEq0RoGn9x+WNedIRK1Yn8wolrOfHR72I7F5NPgz4aXQsVy+HR/xensubvJzTuhhinfRhHUX9t2DtLpAB0Y/Dh7cUDTB96CXP7IQuM0TIYuqXGxd/6eL8mWMnJGPGOuwGHHcImXdytdEqTg="}' http://127.0.0.1:5000/user/login
{
  "errcode": 0,
  "reason": "success",
  "result": {
    "token": "9193b982-51f9-11e8-82da-fa163e1b6459"
  }
}
root@ubuntu:/home/ubuntu# curl --header "token:9193b982-51f9-11e8-82da-fa163e1b6459" --request POST http://127.0.0.1:5000/user/logout
{
  "errcode": 0,
  "reason": "success",
  "result": "success"
}

```
## Publish  ��������

POST http://127.0.0.1:5000/blog/publish

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|title | ���� |��|
|body | �������� |��|
|amount | ���� |��|
|tag | ��ǩ |��|
|description|����|��|

```python
{
	"title":"the first blog",
	"body":"This is a first blog.And it's just a test.",
	"amount":0.02,
	"tag":["test","first"],
	"description":"This is a test blog."
}
```

return:

�ɹ���
```python
{
    "errcode": 0,
    "reason": "success",
    "result":{
        "id":���ݿ�id,
        "claim_id":��Դ�����ϵ�id,
    }
}
```

ʧ�ܣ�
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List All Blog  ��ȡ����

POST http://127.0.0.1:5000/blog/all/list

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|

```python
{
	"page":1,
	"num":10
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        total:������,
        pages:��ҳ��,
        data:
        [
            {
                "author": "justin",
                "claim_id": "45cdb43d78bd12ee3acfa9be7c56ae02d6c88d3e",
                "content_type": ".txt",
                "create_timed": "2018-04-12T15:47:34.446858+00:00",
                "currency": "ULD",
                "des": "����ʹ��UDFS�����������ɵĵ�2ƪ���͵�������Ϣ",
                "id": 5,
                "price": 1.3,
                "status": 1,
                "tags": [
                    "C++",
                    "java",
                    "javascript",
                ],
                "title": "��2ƪ��������",
                "update_timed": null
            }
        ]
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## check isbought  ��鲩���Ƿ񸶷�

POST http://127.0.0.1:5000/blog/isbought

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|claim_ids|���͵�id�б�|��|

```python
{
	"claim_ids":[
        	"ec3c93680884d8b1aee25242f64f79f8bd847c57",
        	"a5b899fe01d633b6f0b809c4af2312524c081576",
        	"25e48b12694b4704aeff32ba0a568c21ad8dd5d6",
        	"e1b98bcc018950ac4684c663d0ea4fa9fc19543d",
        	"e1b98bcc018950ac4684c663d0ea4fa9fc19543f",
        	"2d4bbaf369464feeb90ac957af72a641f9a1bc9c"
    	]
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "25e48b12694b4704aeff32ba0a568c21ad8dd5d6": "QmUH2NbKrURA6hAmJnhfP4VTDtkjUs3fVCN2L7DoE3JLmm",
        "2d4bbaf369464feeb90ac957af72a641f9a1bc9c": false,  # δ����
        "a5b899fe01d633b6f0b809c4af2312524c081576": "QmUH2NbKrURA6hAmJnhfP4VTDtkjUs3fVCN2L7DoE3JLmm",
        "e1b98bcc018950ac4684c663d0ea4fa9fc19543d": null,  # û�д˼�¼
        "e1b98bcc018950ac4684c663d0ea4fa9fc19543f": false,
        "ec3c93680884d8b1aee25242f64f79f8bd847c57": "QmUH2NbKrURA6hAmJnhfP4VTDtkjUs3fVCN2L7DoE3JLmm"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## Pay blogs ֧������

POST http://127.0.0.1:5000/pay/blogs

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|password | ���� |��|
|claim_id | ����id |��|

```python
{
	"password":"123",
	"claim_id":"ec3c93680884d8b1aee25242f64f79f8bd847c57"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result":{
        "udfs_hash":udfs_hash,
    }
}

# ֧���ɹ������ļ���hashֵ��ͨ��UDFS�ӿڻ�ȡ����
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## Pay ADs ֧�����

POST http://127.0.0.1:5000/pay/ads

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|author | ���������� |��|
|claim_id | ����id |��|

```python
{
	"author":"justin",
	"claim_id":"ec3c93680884d8b1aee25242f64f79f8bd847c57"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result":{
        "udfs_hash":udfs_hash,
    }
}

# ֧���ɹ������ļ���hashֵ��ͨ��UDFS�ӿڻ�ȡ����
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Personal Info �г�������Ϣ

GET http://127.0.0.1:5000/user/info

head:token

return:

�ɹ�
```python
{
	'errcode':0,
        'reason':'success',
        'result':{
    	    "username": "test",
            "cellphone":"15278559846",
			"email":"15574859643@163.com"
            }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Personal Balance �г��������

GET http://127.0.0.1:5000/user/balance

head:token

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result":{
        "total":�����,
        "confirmed":��ȷ�����,
        "unconfirmed":δȷ�����,
        "unmatured":δ��������(�ڿ�����,100����ų���),
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Personal Published �г����˷���������Դ

POST http://127.0.0.1:5000/user/published

head:token

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|
|category|��ѯ����|��

```python
{
    "page":1,
    "num":1,
    "category":0
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ����ѯ����Ϊ0-����֧����1-������룬����-����

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "data": [
            {
                "claim_id": ��Դ��claim_id,
                "create_timed": �������ѵ�ʱ��,
                "customer": ������,
                "enabled": ��Դ�Ƿ�ɾ��,
                "id": ��Դ��DB�е�id,
                "price": 0.6,  # �۸�Ϊ��, �Ƿ����ߵ�����
                "title": ��Դ����,
                "txid": �������ѵ�txid
            }
        ],
        "pages": 1,
        "total": 4
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Personal Published num �г����˷���������Դ����

GET http://127.0.0.1:5000/user/published/num

head:token

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "count": 0
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## ~~List Personal Bought �г����˹��������Դ~~

~~POST http://127.0.0.1:5000/user/bought~~

~~head:token~~

~~args:json~~

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|
|category|��ѯ����|��

```python
{
    "page":1,
    "num":1,
    "category":0
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ����ѯ����Ϊ0-����֧����1-������룬����-����

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "pages": 1,
        "records": [
            {
                "author": ��Դ������,
                "claim_id": ��Դ�����ϵ�claim_id,
                "create_timed": ����ʱ��,
                "enabled": ��Դ�Ƿ�ɾ��,
                "id": ��Դ��DB��id,
                "price": 0.5, # �۸�Ϊ��ʱ, �������ߵ�֧��
                "title": ��Դ����,
                "txid": �������ѵ�txid
            }
        ],
        "total": 7
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Billings detail �г������˵���ϸ��Ϣ(�����֧���ӿ��ܺ�)

POST http://127.0.0.1:5000/user/billings/details

head:token

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|

```python
{
    "page":1,
    "num":6
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "pages": 1,
        "records": [
            {  # ��Ϊ������, price��Ϊ��Դ����
                "author": "uuu",
                "claim_id": "1eaeee8108d2ddeefebd5dc811c3722857e32165",
                "create_timed": "2018-04-21T08:40:07.045958+00:00",
                "customer": "935827234",
                "price": 0.65255,
                "title": "����1111111",
                "txid": "346bb03f63287b8c19ff0deee42ffe561d266beaeea80cff58f8098c4a4f42ab"
            },
            {  # ��Ϊ������, price��Ϊ���֧��
                "author": "ttt",
                "claim_id": "ca067e452618915fab2d33cdb6cecca83ae95659",
                "create_timed": "2018-04-20T16:10:25.831104+00:00",
                "customer": "uuu",
                "price": -0.5,
                "title": "df",
                "txid": "d70c00b042b0fabd9279290f72af233d7e50f3092a0c341b05b3a7fc5cd784be"
            },
            {  #��Ϊ������, price��Ϊ��Դ֧��
                "author": "tttttttttttt",
                "claim_id": "010d23be8ce1e23da9dad94c61618d1e0b484c77",
                "create_timed": "2018-04-20T16:09:38.522716+00:00",
                "customer": "uuu",
                "price": 0.02,
                "title": "the first blog",
                "txid": "1b05ff6234eb95f5836afe6e8caf2617206d1f0d540c3798d8a2004f1ac0e299"
            },
            {  # ��Ϊ������, price��Ϊ�������
                "author": "yyy",
                "claim_id": "798aedf4fab2fa77a77b56528abe6e50afce37e6",
                "create_timed": "2018-04-20T15:55:16.285238+00:00",
                "customer": "uuu",
                "price": -0.6,
                "title": "666",
                "txid": "851ecf55bd841322683a18a427fa69e6c6c49af8009c89ced6f0c1c12a620455"
            }
        ],
        "total": 6
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## List Billings �г������˵�

GET http://127.0.0.1:5000/user/billings/

head:token

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "customer_expenditure": {  # ����֧��
            "count": 2,  # ��¼����
            "sum": 1.17755  # ��֧��
        },
        "customer_income": {  # ��������
            "count": 0,
            "sum": null
        },
        "publisher_expenditure": {  # ����֧��
            "count": 0,
            "sum": null
        },
        "publisher_income": {  # ��������
            "count": 0,
            "sum": null
        }
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## ~~List Customer's Billings �г���Ϊ�����߸����˵�~~

## List User's Outgos �г�����֧��

~~POST http://127.0.0.1:5000/user/billings/customer~~

POST http://127.0.0.1:5000/user/billings/outgo

head:token

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|
|category|����|��|

```python
{
	"page":1,
	"num":2,
	"category":2
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ������Ϊ2

> ����0-Ϊ��Դ��1-Ϊ��棬2-Ϊ����

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "pages": 1,
        "records": [
            {  # �û���Ϊ������ ֧������
                "author": "719355782",  # ������
                "claim_id": "870c3a35a8b82f1d4f8e89b89b5c7d3b80d6bc5b",
                "create_timed": "2018-04-21T08:39:25.883777+00:00",
                "customer": "935827234",  # ������
                "price": 0.525,  # ���׽��
                "title": "123123123123",
                "txid": "31af05db89decfcd561ba79fbd130aacb8f02de4b75e55f4548626c1d9732c51"
            },
            {  # �û���Ϊ������, ֧����Դ����
                "author": "tttttttttttt",
                "claim_id": "010d23be8ce1e23da9dad94c61618d1e0b484c77",
                "create_timed": "2018-04-21T11:55:43.680047+00:00",
                "customer": "719355782",
                "price": 0.02,
                "title": "the first blog",
                "txid": "f672a32a11c1eb82a7a1b17e93bc823132c7bc75c3ed990fd1e797c8a11fbe50"
            }
        ],
        "total": 2
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## ~~List Author's Billings �г���Ϊ�����߸����˵�~~

## List User's Incomes �г����������˵�

~~POST http://127.0.0.1:5000/user/billings/author~~

POST http://127.0.0.1:5000/user/billings/income

head:token

args:json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|page|ҳ��|��|
|num|ÿҳ��ʾ��|��|
|category|����|��|

```python
{
	"page":1,
	"num":2,
	"category":2
}
```
> Ĭ��Ϊÿҳ10�����ݣ����ص�һҳ������Ϊ2

> ����0-Ϊ��Դ��1-Ϊ��棬2-Ϊ����

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "pages": 1,
        "records": [
            {  # �û���Ϊ������, ����������
                "author": "yyy",
                "claim_id": "798aedf4fab2fa77a77b56528abe6e50afce37e6",
                "create_timed": "2018-04-21T13:37:41.983595+00:00",
                "customer": "719355782",
                "price": 0.6,
                "title": "666",
                "txid": "d162db3c4185720d287b7fabbe560546c9bce06f0812fadeb9d78c8d0fe2a2aa"
            },
            {  # �û���Ϊ������, ������Դ����
                "author": "719355782",
                "claim_id": "870c3a35a8b82f1d4f8e89b89b5c7d3b80d6bc5b",
                "create_timed": "2018-04-21T09:47:05.902228+00:00",
                "customer": "zyding",
                "price": 0.525,
                "title": "123123123123",
                "txid": "b781f7c12aa7b7a43c22a5bea2ac56d6d15a1dbde7eeea9e2774f7e5f168df56"
            }
        ],
        "total": 2
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## Add Blog View ���Ӳ��ͷ�����

POST http://127.0.0.1:5000/blog/views

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|id | ���ݿ�ID(����claimID) |��|

```python
{
    'id':��Դid
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result": {
        "num": �޸�Ӱ������
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## Modify Personal Info �޸ĸ�����Ϣ
POST http://127.0.0.1:5000/user/modify

head:token

args��json

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|username | �û��� |��|
|password | ԭʼ���� |��|
|cellphone | �ֻ��� |��|
|email | ���� |��|
|new_password | ������ |��|

```python
{
	"username":"test1",
	"password":"123",
	"cellphone":"15574257777",
	"email":"7778547888@163.com",
	"new_password":"111"
}
```

return:

�ɹ�
```python
{
    "errcode": 0,
    "reason": "success",
    "result":{
        "userid":5,
        "username":"test1",
        "email":"7778547888@163.com",
        "cellphone":"15574257777"
    }
}
```

ʧ��
```python
{
    "errcode": ������,
    "reason": "����ԭ��"
}
```
example ʾ��
```bash

```
## ~~Modify Blog Info �޸�������Ϣ~~

~~POST http://127.0.0.1:5000/blog/modify~~

~~head:token~~

~~args��json~~

| arg      | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|~~title~~ | ~~���� ~~ |~~��~~|
|~~body~~ | ~~�������� ~~ |~~��~~|
|~~amount~~ | ~~���� ~~ |~~��~~|
|~~tag~~ | ~~��ǩ ~~ |~~��~~|
|~~description~~|~~����~~|~~��~~|

~~return:~~
```python
{
	"result": 1/0,
	"msg": "None/exception"
}
```

## ~~Record Blog ��Ӳ��ͷ���~~

~~POST http://127.0.0.1:5000/blog/record~~

~~head:token~~

~~args��json~~

| arg     | comment   |  �Ƿ����  |
| ----  | :-----:  |  :----:  |
|~~blog_ID~~ | ~~���͵�ID~~ |~~��~~|

~~return:~~
```python
{
	"result": 1/0,
	"msg": "None/exception"
}
```

## ��¼A:��������ձ�

```python
{
    # ����
    0:{'errcode':0,'reason':'success'},  # ������дreason��result����

    # HTTPЭ�������
    400:{'errcode':400,'reason':'���������.'},
    403:{'errcode':403,'reason':'��û��Ȩ�޽��д˲���.'},
    404:{'errcode':404,'reason':'Api������.'},
    405:{'errcode':405,'reason':'http���󷽷�������.'},
    500:{'errcode':500,'reason':'Api������, ����url�Լ�����.'},

    # ϵͳ��������
    10001:{'errcode':10001,'reason':'���������KEY.'},
    10002:{'errcode':10002,'reason':'��KEY������Ȩ��.'},
    10003:{'errcode':10003,'reason':'KEY����.'},
    10004:{'errcode':10004,'reason':'����ֹ��IP.'},
    10005:{'errcode':10005,'reason':'����ֹ��KEY.'},
    10006:{'errcode':10006,'reason':'��ǰIP���󳬹�����.'},
    10007:{'errcode':10007,'reason':'���󳬹���������.'},
    10008:{'errcode':10008,'reason':'ϵͳ�ڲ��쳣.'},
    10009:{'errcode':10009,'reason':'�ӿ�ά��.'},
    10010:{'errcode':10010,'reason':'�ӿ�ͣ��.'},
    10011:{'errcode':10011,'reason':'��ǰû�е�¼�û�,���¼.'},
    10012:{'errcode':10012,'reason':'ȱ��Ӧ��KEYֵ.'},
    10013:{'errcode':10013,'reason':'��Ȩ�޽��д˲���.'},

    # ���񼶴�����
    # 1. DB��ѯ��֤
    20000:{'errcode':20000,'reason':'�û��Ѵ���.'},
    20001:{'errcode':20001,'reason':'�����Ѵ���.'},
    20002:{'errcode':20002,'reason':'Ӧ�����Ѵ���.'},
    20003:{'errcode':20003,'reason':'�û�������.'},
    20004:{'errcode':20004,'reason':'�������.'},
    20005:{'errcode':20005,'reason':'���ݲ�����.'},
    20006:{'errcode':20006,'reason':'�û�������.'},
    20007:{'errcode':20007,'reason':'��Դ������.'},
    20008:{'errcode':20008,'reason':'��Դ�踶��.'},

    # 2. ���������֤���
    20100:{'errcode':20100,'reason':'ȱ�ٲ���.'},
    20101:{'errcode':20101,'reason':'�������Ȳ���.'},
    20102:{'errcode':20102,'reason':'��������Ϊjson��ʽ.'},
    # 3. Ǯ����ؽӿڵ���
    20200:{'errcode':20200,'reason':'����Ǯ���ӿ�ʧ��.'},
    20201:{'errcode':20201,'reason':'��Դ����ʧ��.'},
    20202:{'errcode':20202,'reason':'��Դ����ʧ��.'},
    20203:{'errcode':20203,'reason':'��ѯ���ʧ��.'},
    20204:{'errcode':20204,'reason':'����Ǯ��ʧ��.'},

    #Ǯ������
    https://github.com/UlordChain/Ulord-platform/blob/master/Uwallet/uwallet/errors.py#L28
    '51000': 'command not found',
    '51001': 'password error',
    '51002': 'password cannot be empty',
    '51003': 'user not exists',
    '51004': 'user already exists',
    '51005': 'invalid claim_id',
    '51006': "claim not find",
    '51007': "the bid must > 0",
    '51008': "the tx_fee must >= 0",
    '51009': "val sand metadata can't both empty",
    '51010': 'It cannot be converted to int'

    '50000': "Unknown Error",
    '52001': 'payment Failed',
    '52002': "can't find fee in the claim.",  #  �Ż�
    '52003': 'permission denied',
    '52004': 'Not enough funds',
    '52005': 'broadcast transaction fail',
    '52006': 'signature transaction fail',
    '52007': 'nout is None',
    '52008': 'operation is too frequent: it is necessary to wait for the transaction confirmation',
    '52009': 'get UTXO fail',
    '52010': 'No extra funds paid fee',
    '52011': 'Dont know which claim to update, because the same name claim > 1',
    '52012': 'cannot save field',
    '52013': 'Temporary dissupport',

    '53000': 'Decode claim value error',
    '53001': 'invalid claim address',

    # Ӧ�÷��񼶴�����
    # 1��DB��ѯ��֤
    60000:{'errcode':60000,'reason':'�û��Ѵ���.'},
    60001:{'errcode':60001,'reason':'�����Ѵ���.'},
    60002:{'errcode':60002,'reason':'�û�������.'},
    60003:{'errcode':60003,'reason':'�������.'},
    60004:{'errcode':60001,'reason':'�����Ѵ���.'},
    60005:{'errcode':60005,'reason':'���ݿ��ύʧ��.'},
    60006:{'errcode':60006,'reason':'������ʧЧ.'},
    # 2. ���������֤���
    60100:{'errcode':60100,'reason':'ȱ�ٲ���.'},
    60101:{'errcode':60101,'reason':'�������Ȳ���.'},
    60102:{'errcode':60102,'reason':'��������Ϊjson��ʽ.'},
    60103:{'errcode':60103,'reason':'��Ҫtoken.'},
    60104:{'errcode':60104,'reason':'��Ч��token.'},
    60105:{'errcode':60105,'reason':'��Ч������.'},
    60106:{'errcode':60106,'reason':'��Ч���ֻ���.'},
    # 3.�ļ�����
    60200:{'errcode':60200,'reason':'�ϴ��ļ�ʧ��.'},
    # 4.����
    60300:{'errcode':60200,'reason':'�ȡ��.'},
    60301:{'errcode':60301,'reason':'������.'},
}
```
