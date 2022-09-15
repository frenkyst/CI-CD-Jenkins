# CI-CD-Jenkins

1. Install docker terlebih dahulu dengan scrip bash

       nano autoDocker.sh
         
   ![image](https://user-images.githubusercontent.com/40049149/189819171-3692ccee-b0bf-4cfd-9cd0-0857b26e802f.png)
   
       #!/bin/bash

       sudo apt update

       sudo apt install \
         ca-certificates \
         curl \
         gnupg \
         lsb-release

       sudo mkdir -p /etc/apt/keyrings

       curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

       echo \
         "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
         $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

       sudo apt update
       sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin

2. Tambahkan permission execute di file yang kita buat tadi search.sh dengan command chmod

       chmod +x autoDocker.sh
       ls -l

   ![image](https://user-images.githubusercontent.com/40049149/189820014-51e4f4f9-00fb-48a2-8f3f-9f8018a6c802.png)

3. Jalankan script dengan command berikut

       ./autoDocker.sh

   ![image](https://user-images.githubusercontent.com/40049149/189820208-d1836bae-f59b-4f29-af60-3a18143bec25.png)

4. Cek versi docker

       docker -v
       docker version
    
   ![image](https://user-images.githubusercontent.com/40049149/189824694-9e9b74ee-2514-42c7-b37f-30dc2c249973.png)

5. Kita akan membuat perintah docker agar tidak menggunakan sudo lagi dengan perintah berikut:

       sudo usermod -aG docker menther

   ![image](https://user-images.githubusercontent.com/40049149/189825815-5672e9ee-2917-4049-871e-8fcf6eab13b4.png)

6. Instal Docker

       docker run --name jenkins1 -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts

   ![image](https://user-images.githubusercontent.com/40049149/190441802-a8802204-8f6f-47ed-8456-05003143d4cf.png)

   ![image](https://user-images.githubusercontent.com/40049149/190445666-e6b2df9d-8466-4cc0-92dd-4b24c0544e1e.png)






























