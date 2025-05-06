# Lyon cloud 使用方法
参考 : [東京工科大学CS学部クラウドHP](https://sites.google.com/edu.teu.ac.jp/cscloud/)


以下の表はLyon cloud のある時の使用状況の表を参考に貼っています。  
使用率の低いマシンをご利用ください。  
[Lyon VM(共用)の情報](http://lyonreport.cloud.cs.priv.teu.ac.jp/report.php) こちらのリンクから使用状況を確認できます。アクセスには東京工科大学の**VPN**が必要です。  

| ホスト名 | vCPU使用率 | RAM使用率 | ディスク使用率 | GPU使用率 | GPU RAM使用率 |
|-|-|-|-|-|-|
| **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** |
| lyon031.cloud.cs.priv.teu.ac.jp | vCPU:0.0%/4vCPUs | RAM:15.1%/16GB | Disk:19.9%/421GB | GPU:0% | GPU RAM:0.4%/16GB |
| lyon032.cloud.cs.priv.teu.ac.jp | vCPU:0.0%/4vCPUs | RAM:14.3%/16GB | Disk:19.7%/421GB | GPU:0% | GPU RAM:0.4%/16GB |
| lyon033.cloud.cs.priv.teu.ac.jp | vCPU:0.2%/4vCPUs | RAM:13.7%/16GB | Disk:30.8%/421GB | GPU:0% | GPU RAM:0.4%/16GB |
| lyon034.cloud.cs.priv.teu.ac.jp | vCPU:0.3%/4vCPUs | RAM:17.1%/16GB | Disk:22.6%/421GB | GPU:0% | GPU RAM:6.5%/16GB |
| **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** | **・<br>・<br>・** |


Dockerアカウントを作成してください。
```
c0_____xx@edu.teu.ac.jp
```

ご自身の 大学のメールアドレスとパスワードでログインしてください
ID
```
c0_____xx
```
パスワード
```
!"$%&'()0
```

クラウドへのSSH接続コマンド
```bash
ssh { yourID }@{ ホスト名 }
```
今回は `lyon31` というマシンを使います。 
```bash
ssh c0_____@lyon031.cloud.cs.priv.teu.ac.jp
```

config でアクセス先を保存しSSH接続
```ssh
Host lyon031
    HostName lyon031.cloud.cs.priv.teu.ac.jp
    User c0_____xx
    ForwardX11 yes 
    Compression yes
```
```bash
ssh lyon031
```
RemoteSSH が可能になります。  
作業環境フォルダ `/home/CSB/2024/c0_____xx/`

---

### ローカルよりファイル送信
scpコマンドなどを利用して使用したいファイルをクラウドに送信する方法が推奨されています。  

scp でァイル送信  
```bash
scp {your_files} c0_____xx:@lyon031.cloud.cs.priv.teu.ac.jp:/home/CSB/2024/c0_____xx/
```

scp でディレクトリごと送信
```bash
scp -r {your_folder} c0_____xx@lyon031.cloud.cs.priv.teu.ac.jp:/home/CSB/2024/c0_____xx/
```

----

### クラウド内にて

### Docker
ご自身のDockerアカウントとパスワード

dockerコマンドで ID を入力
```bash
docker login -u {yourID}
```
パスワード or PAT アクセストークン を入力
```
dckr_pat_!"#$%&'()0=~|QWERTYUIOP
```

docker GPU 付き 実行
```bash
docker run -it  --gpus all -v $(pwd):/work [作成したイメージ名]:latest
```



----
