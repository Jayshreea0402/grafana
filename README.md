# grafana

Grafana is a visualization tool that allows you to see and analyze all of your metrics in one unified dashboard. ![image](https://user-images.githubusercontent.com/76963030/205581350-2f466266-0f4a-4db2-a8a9-1a31b353766f.png)

STEPS:- 
Install the GRAFANA server
   wget https://dl.grafana.com/oss/release/grafana-6.7.3-1.x86_64.rpm
   sudo yum install grafana-6.7.3-1.x86_64.rpm
To change the default port:- 
   /etc/grafana/grafana.ini
To change the default DB from sqlite to mysql:- 
   Install mysql and mysql-server > start and enable mysqld 
   grep 'temporary password' /var/log/mysqld.log   :- copy this password
   mysql_secure_installation :- paste that password and set new password
   "reload privileges table now" >> yes 
To login to mysql :- 
   mysql -u root -p 
   show databases; 
   create database grafanadb
   CREATE USER 'grafana'@'localhost' IDENTIFIED BY 'Grafana@2022';
   GRANT ALL PRIVILEGES ON grafanadb.* TO 'grafana'@'localhost';
   FLUSH PRIVILEGES; 
   exit; 
   mysql -u grafana -p
   show databases; 
   show tables; 
   exit 
Creating dashboards to add db 
   mysql -u grafana -p grafanadb 
   entre password 
   show tables;  a script jo metric name k table me every min cpu utilization ki entry dalta hai 
   host: localhost:3306
   save test
   go to dashboard and query > add data source  
   FROM(this is the table name) 
   where click and remove 
To add threshold in a dashboard
   edit dashboard 
    panel settings  
      add threshold  
        "broken heart" about to reach threshold 
On a new machine 
Create a new data source 
  select influxdb from plugins port 8086

Alerts in grafana:- 
  configure smtp with grafana to send mails via email 
  alert list from panel properties will show all the alerts at one place![image](https://user-images.githubusercontent.com/76963030/205582201-db4d73c7-fb16-4016-ab4d-379f7f9bc8dd.png)

