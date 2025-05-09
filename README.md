# 7.Project-Expense
====================

Step 1: Create AWS Instances - mysql,back,front

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

>> mysql> show database 
