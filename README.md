# Devops Monitoring Project:

* First create 2 ec2 instance with ubuntu 24.04 AMI with t2.medium instance type with 20 gb storage each.
* Security Group: SSH-22,HTTP-80,HTTPS-443,custom TCP-3000-10000,custom TCP-587,custom TCP-27017,SMTP-25,SMTPS-465
* to create the code for email alerts go to this link: https://myaccount.google.com/apppasswords (wgjz fwvr sfqy qhfa)

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
      27  cd prometheus/
      28  ls
      29  ./prometheus &
      30  cd ..
      31  cd alertmanager/
      32  ls
      33  cd ..
      34  cd prometheus/
      35  ls
      36  vi alert_rules.yml
      37  vi prometheus.yml 
      38  cd ..
      39  cd alertmanager/
      40  ./alertmanager &
      41  cd ..
      42  cd prometheus/
      43  ls
      44  pgrep prometheus 
      45  kill 1661
      46  ./prometheus &
      47  vi prometheus.yml 
      48  pgrep prometheus 
      49  kill 1745
      50  ./prometheus &
      51  vi prometheus.yml 
      52  pgrep prometheus 
      53  kill 1829
      54  ./prometheus &
      55  cd ..
      56  ls
      57  cd blackbox_exporter/
      58  ls
      59  ./blackbox_exporter &
      60  vi blackbox.yml 
      61  cd ..
      62  ls
      63  cd prometheus/
      64  ls
      65  vi prometheus.yml 
      66  pgrep prometheus 
      67  kill 1904
      68  ./prometheus &
      69  cd ..
      70  ls
      71  cd alertmanager/
      72  ls
      73  vi alertmanager.yml 
      74  ls
      75  rm alertmanager.yml 
      76  vi alertmanager.yml
      77  pgrep alertmanager 
      78  kill 1712
      79  ./alertmanager &
      80  cd ..
      81  cd prometheus/
      82  pgrep prometheus 
      83  kill 2008
      84  ./prometheus &
      85  history

  
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
      28  ps
      29  kill PID of Boardgame application so that alert will send on our email Id.
