# Ansible-CentOS6-Basic
CentOS6ベース Ansible Playbook

# Software
* OS CentOS6
* Web apache2.2.4
* Runtime php5.6

<!-- command+shift+Vにて表示可能 -->
# Ansible実行前の作業

## GitHubからPlaybook一式ダウンロード
* Ansibleサーバ上に本ソース一式をDL

## conf.yml作成
* 以下の要領で作成する  
```
# Admin
admin_id: webmaster
# General User for Developer
developer_id: generaluser
developer_pass: hogehoge

# Domain
prod_domain: hoge.jp
test_domain: test.hoge.jp

# Basic Auth
test_basic_id: test
test_basic_pass: test

# VirtualHost Port
vh_port: xx

```

## hosts修正
* [webservers]のIPを修正
* 鍵ファイル名を修正

```:hosts
[webservers]
x.x.x.x ansible_ssh_user=user ansible_ssh_private_key_file=~/path/to/key
```

## site.yml修正
* 実施するタスクを調整

## 疎通確認
* 以下コマンドを実行  

    ```ansible all -i hosts -m ping -k```  
  SSH PASSを聞かれるので入力

# Ansible-Playbook実行
* 以下コマンドを実行  

    ```ansible-playbook site.yml -i hosts```  
  SSH PASSを聞かれるので入力

# Ansible実行後の作業

* 接続確認(SSH, Ansible)
