### **Project Documentation: Hosting a Dockerized Website on AWS**



### **Project Overview**

This documentation provides the steps I followed to create and deploy a simple Dockerized website on an AWS EC2 instance. The website serves a basic HTML page with the content: "This is a simple test page."


### **Steps to Create and Deploy a Personalized Dockerized Website on AWS**



### **1. Create an AWS EC2 Instance**

1. **Launch EC2 Instance**:
   - Log in to your AWS Management Console.
   - Navigate to **EC2** service and click **Launch Instance**.
   - Choose an Amazon Machine Image (AMI) and an instance type (e.g., t2.micro).
   - Configure the instance with a security group and key pair.
   - Launch the instance and note the public IPv4 address.

![log in ]([images/sample1.jpg](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/log-in.png))

![click launch](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/click-launch-instance.png)

![server name](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/server-name.png)

![AMI](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/AMI.png)

![instance type](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/instance%20type.png)

![sg](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/network-sg.png)

![launch](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/launch-instance.png)

![click](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/click-launch-instance.png)

![click connect](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/click-connect.png)


### **2. Connect to Your EC2 Instance**

1. **Connect Using SSH**:
   ```bash
   ssh -i "path/to/your/key.pem" ec2-user@<your-ec2-public-ip>
``
   ![instance connect](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/ssh-terminal.png)

2. **Update the instance and install Docker**

bash
```
sudo apt update -y
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```
![update](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/sudo-apt-update.png)

![install](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/sudo-apt-install-docker.png)

![start docker](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/start-eneable-docker.png)


3. **Create a Directory and Add an HTML File**
Create a Directory:

mkdir my-docker-app && cd my-docker-app


4. **Add a Simple HTML File:**

bash
```
echo "<p>This is a simple test page using Docker.!</p>" > index.html
Verify the Content:
```

![html](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/html.png)


bash
```
cat index.html
```
![cat](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/html.png)

5. **Create a Dockerfile**
Create a Dockerfile:

```
bash
touch Dockerfile
```

6. **Add Content to Dockerfile:**

 ```dockerfile
   FROM nginx:alpine

   COPY index.html /usr/share/nginx/html/index.html
   ```

![df content](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/dockerfile-content.png)

7. **Build the Docker Image**


bash
```
docker build -t my-docker-app .
```

8. **Run the Docker Container**

bash
```
docker run -d -p 80:80 my-docker-app
```
![dc ](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/run-docker-container.png)

7. Verify the Deployment
Access Your Website:
Open a web browser and navigate to http://<your-ec2-public-ip> to view the personalized content served by the Docker container.

![web content](https://github.com/Joseph-Ibeh/Dev_Ninja_Docker_assignment/blob/main/images/docker/docker-output.png)



    
