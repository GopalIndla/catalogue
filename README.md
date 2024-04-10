# Catalogue Service

This service is responsible for showing the list of items that are to be sold by the RobotShop e-commerce portal.
This service is written in NodeJS, Hence need to install NodeJS in the system.

Catalogue uses nodejs 18

Disabling the default nodejs:10 repo and enabling nodejs18 

[ You can list modules by using dnf module list by 'dnf module list`]

```
# dnf module disable nodejs -y
# dnf module enable nodejs:18 -y
```

Install Nodejs 

```
# dnf install nodejs -y  
```


Let's now set up the catalogue application.

As part of operating system standards, we run all the applications and databases as a normal user but not with root user.

So to run the catalogue service we choose to run as a normal user and that user name should be more relevant to the project. Hence we will use `roboshop` as the username to run the service.

```
# useradd roboshop
```

So let's switch to the `roboshop` user and run the following commands.

```
$ curl -s -L -o /tmp/catalogue.zip "https://github.com/stans-robot-project/catalogue/archive/main.zip"
$ cd /home/roboshop
$ unzip /tmp/catalogue.zip
$ mv catalogue-main catalogue
$ cd /home/roboshop/catalogue
$ npm install 
```

## NOTE: We need to update the IP address of MONGODB Server in systemd.service file 


Now, lets set up the service with systemctl.

```
# mv /home/roboshop/catalogue/systemd.service /etc/systemd/system/catalogue.service
# systemctl daemon-reload
# systemctl start catalogue
# systemctl enable catalogue
```


# demo to show tags