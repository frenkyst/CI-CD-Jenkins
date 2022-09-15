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

7. Jalankan perintah berikut 

       docker logs jenkins
       
   ![image](https://user-images.githubusercontent.com/40049149/190452622-94bf88ac-5717-45bd-8df5-09138005418d.png)

8. Buka ip public:8080 

   ![image](https://user-images.githubusercontent.com/40049149/190452820-2d957736-45a0-4c12-8732-93b1594d1f89.png)

9. Pilih __Install suggested plugins__

   ![Screenshot from 2022-09-15 23-05-32](https://user-images.githubusercontent.com/40049149/190453292-676f9fe5-3f12-474b-b6ae-cca0e465de41.png)

10. Tunggu sampai ceklis semua

    ![Screenshot from 2022-09-15 23-06-34](https://user-images.githubusercontent.com/40049149/190453395-a70de0b1-4822-4b04-b6c4-8bf5a8805af1.png)

11. Isi sesuai kententuan

    ![image](https://user-images.githubusercontent.com/40049149/190453699-54ccaf45-e894-4e4b-8811-4aace8778179.png)

12. Biarkan default klik finish

    ![image](https://user-images.githubusercontent.com/40049149/190453786-8f3657d7-c773-445c-989b-648aa8dd502c.png)   

13. Lanjut skip aja

    ![image](https://user-images.githubusercontent.com/40049149/190453925-1b3c0c25-f684-4ffb-bebf-83bc15d3a573.png)

14. Jika sudah seperti ini sudah berhasil

    ![image](https://user-images.githubusercontent.com/40049149/190454037-64588e23-8320-48fa-89bc-f61114c6f97d.png) 

15. Clone aplikasi yang akan di deploy

        git clone https://github.com/dumbwaysdev/housy-backend

    ![image](https://user-images.githubusercontent.com/40049149/190454708-682113a7-29c7-4805-9087-939f2559b549.png)

16. Ke directory housy-backend dan bikin file Jenkinsfile

    ![image](https://user-images.githubusercontent.com/40049149/190456558-5bc9b92d-79a4-4cbf-bf71-b004689a64d1.png)

17. Push ke repository git

    ![image](https://user-images.githubusercontent.com/40049149/190462386-517a9e69-d0cf-498f-a004-2e8a9a476ab8.png)

18. Buat credential baru http://ipkalian:8080/manage/credentials/

    ![image](https://user-images.githubusercontent.com/40049149/190463577-826e46d1-c39d-48eb-964c-76003c72b7fb.png)

19. Pilih Pipeline

    ![image](https://user-images.githubusercontent.com/40049149/190463886-0c8986ab-c76c-45bd-a1ed-97f36cbcedf8.png)

20. Ceklis bagian __GitHub hook trigger for GITScm polling__

    ![image](https://user-images.githubusercontent.com/40049149/190464499-556bb996-7248-44e1-a8f1-3668f49bd1ac.png)

21. Pilih Pipeline script from SCM

    ![image](https://user-images.githubusercontent.com/40049149/190465515-d23c59e8-4a52-41a4-b328-2c3cb62f1c04.png)

22. Pilih Git

    ![image](https://user-images.githubusercontent.com/40049149/190465777-c47bc566-1e6c-480d-a7cb-117f851e9483.png)


























