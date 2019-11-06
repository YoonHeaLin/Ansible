# Ansible 실행

```
$ ansible-playbook -i hosts site.yml

PLAY [플리이북 튜토리얼] *****************************************************************************************                                                                        ********

TASK [Gathering Facts] *******************************************************************************************
ok: [127.0.0.1]

TASK [libselinux-python 설치] ************************************************************************************                                                                        **
ok: [127.0.0.1]

TASK [EPEL Repository 설치] **************************************************************************************                                                                        *******
ok: [127.0.0.1]

TASK [nginx 설치] ************************************************************************************************                                                                        **
changed: [127.0.0.1]

TASK [nginx 서비스 시작과 자동 시작 설정] ************************************************************************                                                                        ************
changed: [127.0.0.1]

PLAY RECAP *******************************************************************************************************
127.0.0.1                  : ok=5    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

***

# nginx 실행 여부 확인

```
$ systemctl status nginx

● nginx.service - The nginx HTTP and reverse proxy server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2019-11-05 05:26:20 UTC; 7s ago
  Process: 9879 ExecStart=/usr/sbin/nginx (code=exited, status=0/SUCCESS)
  Process: 9875 ExecStartPre=/usr/sbin/nginx -t (code=exited, status=0/SUCCESS)
  Process: 9873 ExecStartPre=/usr/bin/rm -f /run/nginx.pid (code=exited, status=0/SUCCESS)
 Main PID: 9881 (nginx)
   CGroup: /system.slice/nginx.service
           ├─9881 nginx: master process /usr/sbin/nginx
           ├─9882 nginx: worker process
           ├─9883 nginx: worker process
           ├─9884 nginx: worker process
           └─9885 nginx: worker process
```
