# Week 1 — App Containerization

## Required Homework

### Required Tasks

* I  Watched [How to Ask for Technical Help](https://youtu.be/tDPqmwKMP7Y) video.
* I Watched [Grading Homework Summaries](https://youtu.be/FKAScachFgk) video.
* I Watched [Week 1 Live Streamed Video](https://www.youtube.com/live/zJnNe5Nv4tE?feature=share) during the livestream and followed along with the tasks.
* I Watched [Commit Your Code](https://youtu.be/b-idMgFFcpg) video.
* I Watched [Chirag's Week 1 Spend Consideration](https://youtu.be/OAMHu1NiYoI) video.
* I Watched [Ashish's Week 1 Security Consideration](https://youtu.be/OjZz4D0B-cA) video.
* I Watched [Week 1 - Create the notification feature (Backend and Front)](https://youtu.be/k-_o0cCpksk) video.
 

### Actions

* Completed all steps during the livestream to containerize the application.
  * Reviewed notes and code in [Github - Week 1](https://github.com/omenking/aws-bootcamp-cruddur-2023/blob/week-1/journal/week1.md).
  * I containerized my backend and frontend filkes using Docker. Docker for VSCode makes it easy to work with Docker while in VScode
   ![Dockerfile running](assets/docker%20built.png)  

* Went through [video](https://youtu.be/k-_o0cCpksk) steps and added frontend and backend notifications functionality.
  * Documented notification endpoint for OpenAPI document.
  * Wrote Flask backend endpoint for notifications.
  * Wrote React page for notifications. 
  ![Working web page]()  
  
* Went through [video](https://youtu.be/CbQNMaa6zTg) steps to set up PostgreSQL and DynamoDB Local
  * Ran DynamoDB Local container to ensure it worked
  * Ran Postgres container to ensure it worked  
  * [AWS Documentation - DynamoDB Local](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.DownloadingAndRunning.html)
  * [100 Days of Cloud - DynamoDB Local Challenge](https://github.com/100DaysofCloud/challenge-dynamodb-local)

  * Tested connecting to DynamoDB Local using ```aws dynamodb list-tables --endpoint-url http://localhost:8000``` which returned empty table info successfully. 
 
![Dynamodb](assets/Week%201%20-%20Dynamodb.png)  

  * Added steps to install PostgreSQL Client into [.gitpod.Dockerfile](../.gitpod.Dockerfile) and tested using ```psql -h localhost -p 5432 -U postgres -d postgres```
 
![Postgres](assets/Week%201%20-Postgres.png)

## Stretch Homework


