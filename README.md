# 7.Project-Expense
====================

Step 1: Create AWS Instances - mysql (Instance)

Login to: mqsql (server) 

>> sudo su -

>> dnf install mysql-server -y 

>> systemctl enable mysqld

>> systemctl start mysqld

>> netstat -lntp

>> mysql_secure_installation --set-root-pass ExpenseApp@1

Note : Goto AWS Create Records at Route 53  >> Click DNS management  >> Select : site  >>  Click on Create record >> Record name : mysql  >> Value >> mysql public IP  >> TTL : 1  >> Click Create records

Note : Goto mqsql (server) 

>> nslookup mysql.devsecops-ai.site    

>> mysql_secure_installation --set-root-pass ExpenseApp@1

>> mysql -h mysql.devsecops-ai.site -u root -pExpenseApp@1

>> mysql show database  >> mysql use mysql  >> mysql  show tables  >> mysql select * from user

===========================================================================================

Step 2: Create AWS Instances - back (Instance)

Login to: mqsql (server) 

>> sudo su -

>> dnf module disable nodejs -y

>> dnf module enable nodejs:20 -y

>> dnf install nodejs -y

>> useradd --system --home /app --shell /sbin/nologin --comment "expense user" expense    ||||  Note : Add Application User  ||||

>> id expense

>> mkdir /app

>> curl -o /tmp/backend.zip https://expense-builds.s3.us-east-1.amazonaws.com/expense-backend-v2.zip

>> cd /app

>> unzip /tmp/backend.zip

>> ls -l

>> npm install

>> ls -l

>> vim /etc/systemd/system/backend.service

>> [Unit] Description = Backend Service [Service] User=expense Environment=DB_HOST="<MYSQL-SERVER-IPADDRESS>" ExecStart=/bin/node /app/index.js SyslogIdentifier=backend [Install] WantedBy=multi-user.target

>> Note : goto (AWS) copy=>> mysql.devscops-ai.site  |||| goto (back-server) paste=>> it  atEnvironment=DB_HOST="mysql.devsecops-ai.site"  |||| save :wq!   |||| copy DB server = paste App server

>> systemctl daemon-reload

>> systemctl start backend

>> systemctl enable backend

>> systemctl status backend

>> Note : Why its failed ??

>> ls -l

>> cd schema/

>> ls -l

>> cat backend.sql

>> dnf install mysql -y

>> mysql -h mysql.devsecops-ai.site -uroot -pExpenseApp@1 < /app/schema/backend.sql

>> systemctl restart backend

>> systemctl status backend

>> netstat -lntp

>> telnet mysql.devsecops-ai.site 3306 

===========================================================================================
