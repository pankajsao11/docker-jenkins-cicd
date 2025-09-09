In this repo I've used Ubuntu linux for installing docker and creating container for jenkins. And then I'm using jenkins in localhost.

# docker-jenkins-cicd
CI/CD pipeline for Serverless Webapp {https://github.com/pankajsao11/serverless-webapp} using Docker-Jenkins

```
1. creating user
$ sudo adduser docker-admin

2. adding to docker group
$ sudo usermod -aG docker docker-admin

3. switch user
$ sudo su docker-admin
```

## Hosting Jenkins on EC2 server using Docker
Ensure to add port 8080 in security group inbound rule.
<img width="1355" height="636" alt="image" src="https://github.com/user-attachments/assets/c4d2b921-0451-4ea0-89e8-5bea78619362" />
