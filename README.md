# AWS-Automated_Receipt
This project focuses on automating receipt processing using AWS services. Instead of manually handling receipts which can be time-consuming, error-prone, and difficult to scale—this system extracts structured data from receipts and stores it efficiently for record-keeping and auditing.




2) Dynamo DB

  Why Dynamo DB?
    lalala
    Dynamo DB Tables store all the extracted receipt data in a structed format

  step-by-step:
    1. Search and click on "Dynamo DB" on the search bar at the AWS console.
    2. Go to "Tables" > Click on "Create Table"
    3. Important fields:
        Table name: <name>
        Partition key: <receipt_id> ; <String>
        Sort key - optional: <date> ; <String>
  
4) 
