# Chat_Server_using_Microservices
This repository contains the code for CS552: Introduction to Cloud Computing.

## Task 1: Native Case 
Run the MongoDB correctly in the native case. 
-> sudo mongod --bind_ip=0.0.0.0 &

 Run the webserver correctly in the native case
Open the new ssh window and give command-
-> cd miniproject2/

-> python3 run.py

The live chat service can be accessed externally (using browsers)

-> external-ip from vm: 8080
-> http://104.197.187.65:8080/


## Task 2: Containerization

Run the MongoDB correctly in the container case
-> cd miniproject2-container/

-> cd mongodb/

-> sudo make run

But, the first time got the error because the previous docker file is created. So, to remove this docker file that already existed give the following command-
-> docker ps -a

-> docker rm mongodb

Then again give the command-
-> sudo make run

Run the webserver correctly in the container case
-> If you are in the minidocker file, give following command-

-> cd ..
	
-> cd miniproject2-container/webserver
	
	-> make run 
The live chat service can be accessed externally (using browsers)
-> external-ip from vm: 8080

-> http://104.197.187.65:8080/


Task 3:  Orchestration (MiniKube)

 Deploy the MongoDB object correctly in the miniKube case.
-> ls 

-> cd miniproject2-minikube/

-> minikube start

-> alias kubectl="minikube kubectl --"

->kubectl apply -f mongodb-deploy.yaml

->kubectl get deployments

 Deploy the MongoDB service object correctly in the miniKube case. 
 
->kubectl apply -f serviceDB.yaml

 Deploy the web server object correctly in the miniKube case.
-> kubectl apply -f webserver-deploy.yaml

->kubectl get deployments

 Deploy the web server service object correctly in the miniKube case.  
 
-> kubectl apply -f serviceWEB.yaml

-> kubectl port-forward --address 0.0.0.0 service/webserver-service 8080:8080

