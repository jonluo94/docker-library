## 构建破解jira
```
docker build -t jira/jira-mysql:8.1.0 .
```
## 运行jira
```
docker run -d -it -p 8080:8080 -v /jira:/var/atlassian/jira --name jira jira/jira-mysql:8.1.0 
```
## 使用mysql示例
* 创建jira数据库及用户 帐号jirauser 密码jira
```
docker run -p 3306:3306 --name atlassian-mysql \
-v /atlassian/data:/var/lib/mysql \
-v /atlassian/conf:/etc/mysql/conf.d \
           -e MYSQL_ROOT_PASSWORD=123456 \
           -d mysql:5.7 
```
``` 
create database jiradb character set utf8 collate utf8_bin;
create user jirauser identified by 'jira';
grant all privileges on *.* to 'jirauser'@'%' identified by 'jira' with grant option;
grant all privileges on *.* to 'jirauser'@'localhost' identified by 'jira' with grant option;
flush privileges;
```



