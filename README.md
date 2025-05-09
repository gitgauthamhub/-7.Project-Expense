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

=======================================================================================================

Step 2: Create AWS Instances - back (Instance)

Login to: mqsql (server) 

>> sudo su -

>> dnf module disable nodejs -y

>> dnf module enable nodejs:20 -y

>> dnf install nodejs -y

>> useradd --system --home /app --shell /sbin/nologin --comment "expense user" expense    ||||  Note : Add Application User






