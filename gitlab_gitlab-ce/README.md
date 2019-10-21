## 部署gitlab
    
```
mkdir /gitlab
mkdir /gitlab/config
mkdir /gitlab/logs
mkdir /gitlab/data


docker run --detach --hostname gitlab.grgchain.com \
    --publish 8443:443 --publish 8180:80 --name gitlab --restart always \
    --volume /gitlab/config:/etc/gitlab \
    --volume /gitlab/logs:/var/log/gitlab \
    --volume /gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest

```
## 运行gitlab-runner 
* 添加gitlab-runner库  
``` 
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.rpm.sh | sudo bash

yum install gitlab-runner
```



