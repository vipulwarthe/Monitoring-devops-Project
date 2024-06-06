# Devops Monitoring Project:

* First create 2 ec2 instance with ubuntu 24.04 AMI with t2.medium instance type with 20 gb storage each.
* Security Group: SSH-22,HTTP-80,HTTPS-443,custom TCP-3000-10000,custom TCP-587,custom TCP-27017,SMTP-25,SMTPS-465

* Run below commands on Monitor server:
  
      1  clear
      2  sudo apt update
      3  wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
      4  ls
      5  tar xvfz prometheus-2.52.0.linux-amd64.tar.gz
      6  ls
      7  rm prometheus-2.52.0.linux-amd64.tar.gz 
      8  ls
      9  mv prometheus-2.52.0.linux-amd64/ prometheus
      10  ls
      11  wget https://github.com/prometheus/blackbox_exporter/releases/download/v0.25.0/blackbox_exporter-0.25.0.linux-amd64.tar.gz
      12  ls
      13  tar -xvf blackbox_exporter-0.25.0.linux-amd64.tar.gz 
      14  ls
      15  rm blackbox_exporter-0.25.0.linux-amd64.tar.gz 
      16  mv blackbox_exporter-0.25.0.linux-amd64/ blackbox_exporter
      17  ls
      18  wget https://github.com/prometheus/alertmanager/releases/download/v0.27.0/alertmanager-0.27.0.linux-amd64.tar.gz
      19  ls
      20  tar -xvf alertmanager-0.27.0.linux-amd64.tar.gz 
      21  ls
      22  rm alertmanager-0.27.0.linux-amd64.tar.gz 
      23  mv alertmanager-0.27.0.linux-amd64/ alertmanager
      24  ls
  
* On secod app-server run below commads:

      1  clear
      2  sudo apt update
      3  git clone https://github.com/vipulwarthe/Boardgame.git
      4  ls
      5  wget https://github.com/prometheus/node_exporter/releases/download/v1.8.1/node_exporter-1.8.1.linux-amd64.tar.gz
      6  ls
      7  tar -xvf node_exporter-1.8.1.linux-amd64.tar.gz 
      8  ls
      9  rm node_exporter-1.8.1.linux-amd64.tar.gz 
      10  mv node_exporter-1.8.1.linux-amd64/ node_exporter
      11  ls
      12  cd node_exporter/
      13  ls
      14  ls -al
      15  ./node_exporter &
      16  cd ..
      17  ls
      18  cd Boardgame/
      19  java
      20  sudo apt install openjdk-17-jre-headless
      21  sudo apt install maven -y
      22  ls
      23  mvn package
      24  ls
      25  cd target/
      26  ls
      27  java -jar database_service_project-0.0.2.jar 

