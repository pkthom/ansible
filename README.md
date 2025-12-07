# ansibleサーバー構築手順

インストール
```
sudo apt update
sudo apt install -y ansible
```
キー作成
```
ssh-keygen -t ed25519
```
環境構築とpingテスト
```
ubuntu@Ansible:~$ mkdir ansible
ubuntu@Ansible:~$ cd ansible/
ubuntu@Ansible:~/ansible$ vi inventory.ini
ubuntu@Ansible:~/ansible$ vi ansible.cfg
ubuntu@Ansible:~/ansible$ ansible all -m ping
ubuntu-dev-01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
ubuntu@Ansible:~/ansible$
```
テストロール
```
ubuntu@Ansible:~/ansible$ vi ping.yml

ubuntu@Ansible:~/ansible$ ansible-playbook ping.yml

PLAY [Test connection] *************************************************************************************************

TASK [Ping all hosts] **************************************************************************************************
ok: [ubuntu-dev-01]

PLAY RECAP *************************************************************************************************************
ubuntu-dev-01              : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

ubuntu@Ansible:~/ansible$
```
