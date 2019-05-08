# Tomcat8.5の導入方法

* 必要なソフトのインストール

```bash
sudo yum -y install unzip
sudo yum -y install java-1.8.0-openjdk
```

* tomcatユーザー作成

```bash
sudo useradd -s /sbin/nologin tomcat
```

* tomcatのダウンロード

```bash
wget http://ftp.tsukuba.wide.ad.jp/software/apache/tomcat/tomcat-8/v8.5.39/bin/apache-tomcat-8.5.39.zip
```

* 適当な位置に解凍して、所有者をtomcatに

```bash
unzip apache-tomcat-8.5.39.zip
sudo mv apache-tomcat-8.5.39 /usr/local/tomcat
sudo chown -R tomcat:tomcat /usr/local/tomcat
```

* サービスファイルを作成

```bash
sudoedit /etc/systemd/system/tomcat.service
------------------------------------------------------
[Unit]
Description=Apache Tomcat 8
After=syslog.target network.target

[Service]
User=tomcat
Group=tomcat
Type=oneshot
PIDFile=/usr/local/tomcat/tomcat.pid
RemainAfterExit=yes

ExecStart=/usr/local/tomcat/bin/startup.sh
ExecStop=/usr/local/tomcat/bin/shutdown.sh
ExecReStart=/usr/local/tomcat/bin/shutdown.sh;/usr/local/tomcat/bin/startup.sh

[Install]
WantedBy=multi-user.target
------------------------------------------------------
```

* サービスファイルなどへアクセス権付与

```bash
sudo chmod 755 /etc/systemd/system/tomcat.service
sudo chmod 775 /usr/local/tomcat/bin/startup.sh
sudo chmod 775 /usr/local/tomcat/bin/catalina.sh
```

* 自動起動を有効に

```bash
sudo systemctl enable tomcat
```

* サービス開始

```bash
sudo systemctl start tomcat
```