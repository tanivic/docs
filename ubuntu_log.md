# ubuntuでの作業ログ

```Bash
kei@kei-ubuntu:~$ sudo apt install ruby
kei@kei-ubuntu:~$ git clone https://github.com/tliron/install-gnome-themes ~/install-gnome-themes
Cloning into '/home/kei/install-gnome-themes'...
remote: Enumerating objects: 356, done.
remote: Total 356 (delta 0), reused 0 (delta 0), pack-reused 356
Receiving objects: 100% (356/356), 92.83 KiB | 184.00 KiB/s, done.
Resolving deltas: 100% (227/227), done.
```

## githubにsshで接続してみる。

SSHの鍵を作るのはお決まりの手順。

```Bash
kei@kei-ubuntu:~/Documents/docs$ cd ~/.ssh
kei@kei-ubuntu:~/.ssh$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/kei/.ssh/id_rsa): id_rsa_github
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in id_rsa_github.
Your public key has been saved in id_rsa_github.pub.
The key fingerprint is:
SHA256:t8Rfu25tj+77Lxlb5dx5Xu4MM/AXdvztkha4VsazEAY kei@kei-ubuntu
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|          E      |
|           .     |
|         .  o  ..|
|        S +..+.=*|
|         o oo+Oo%|
|          . .=*&*|
|            o XX=|
|           . *BBX|
+----[SHA256]-----+
```


[https://github.com/settings/keys](https://github.com/settings/keys)で公開鍵の登録ができる。*.pubの公開鍵ファイルを登録するとよい。

```Bash
kei@kei-ubuntu:~/Documents/docs$ git remote set-url origin git@github.com:tanivic/docs.git
kei@kei-ubuntu:~/Documents/docs$ git remote -v
origin	git@github.com:tanivic/docs.git (fetch)
origin	git@github.com:tanivic/docs.git (push)
kei@kei-ubuntu:~/Documents/docs$ git push origin master
Everything up-to-date
```


## ubuntuでクリップボードをコマンドラインから操作する。

xselパッケージがないといけないようだ。
id_rsa_github.pub の中身をクリップボードにコピーする。

```Bash
kei@kei-ubuntu:~/.ssh$ sudo apt install xsel
kei@kei-ubuntu:~/.ssh$ cat id_rsa_github.pub | xsel --clipboard --input
```
