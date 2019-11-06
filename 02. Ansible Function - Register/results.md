# Ansible 실행

```
$ ansible-playbook -i hosts get-user.yml

PLAY [호스트의 사용자 목록을 얻는다] ******************************************************************************************************************************************************************

TASK [Gathering Facts] *******************************************************************************************************************************************************************
ok: [127.0.0.1]

TASK [/etc/passwd에서 사용자 이름 추출] ***********************************************************************************************************************************************************
changed: [127.0.0.1]

TASK [usernames_result 변수를 디버깅으로 표시] *****************************************************************************************************************************************************
ok: [127.0.0.1] => {
    "usernames_result": {
        "changed": true,
        "cmd": [
            "cut",
            "--delimiter=:",
            "--fields=1",
            "/etc/passwd"
        ],
        "delta": "0:00:00.003285",
        "end": "2019-11-06 05:16:11.513464",
        "failed": false,
        "rc": 0,
        "start": "2019-11-06 05:16:11.510179",
        "stderr": "",
        "stderr_lines": [],
        "stdout": "root\nbin\ndaemon\nadm\nlp\nsync\nshutdown\nhalt\nmail\noperator\ngames\nftp\nnobody\nsystemd-network\ndbus\npolkitd\nlibstoragemgmt\nsshd\nabrt\nrpc\npostfix\nntp\nchrony\ntcpdump\ndevelop04\nansible\nnginx",
        "stdout_lines": [
            "root",
            "bin",
            "daemon",
            "adm",
            "lp",
            "sync",
            "shutdown",
            "halt",
            "mail",
            "operator",
            "games",
            "ftp",
            "nobody",
            "systemd-network",
            "dbus",
            "polkitd",
            "libstoragemgmt",
            "sshd",
            "abrt",
            "rpc",
            "postfix",
            "ntp",
            "chrony",
            "tcpdump",
            "develop04",
            "ansible",
            "nginx"
        ]
    }
}

PLAY RECAP *******************************************************************************************************************************************************************************
127.0.0.1                  : ok=3    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

***

# Ansible 출력 항목

## 모듈간에 공통된 항목

| 내용 | 설명 |
|---|---|
| changed | 변경 계열의 처리를 할 경우는 true, 그렇지 않으면 false |
| start | 태스크 실행 시작 시각을 UTC로 입력 |
| end | 태스크 실행 종료 시각을 UTC로 입력 |
| delta | 태스크를 실행하는 시간. end - start |
| warnings | 모듈이 경고를 출력하면 여기에 입력. 자동으로 실행 로그 중에 경고문 출력 |

## command 모듈 고유의 항목

| 내용 | 설명 |
|---|---|
| cmd | 실행한 명령 문자열을 띄어쓰기로 구분 |
| rc | 명령 실행의 반환 코드로, 일반적으로 설공했을 경우는 0, 그 외에는 에러를 의미 |
| stderr | 명령의 표준 에러 |
| stdout | 명령의 표준 출력 |
| stdout_lines | 표준 출력을 행 단위로 구분한 목록 |
