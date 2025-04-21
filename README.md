# AWS-Automated_Receipt
This project focuses on automating receipt processing using AWS services. Instead of manually handling receipts which can be time-consuming, error-prone, and difficult to scale—this system extracts structured data from receipts and stores it efficiently for record-keeping and auditing.


## 2) Dynamo DB

  Why Dynamo DB: lalala Dynamo DB Tables store all the extracted receipt data in a structed format

  Step-By-Step:
    
    1. Search and access on "Dynamo DB" on the search bar at the AWS console.
    2. Go to "Tables" > Click on "Create Table"
    3. Important fields:
        Table name: <name>
        Partition key: <receipt_id> ; <String>
        Sort key - optional: <date> ; <String> -> This will allow to us qury data by date / date ranges
        Leave the rest as default
  
## 3) Amazon SES (Simple Email Service) 

  Why Amazon SES: lalala

  Step-by-Step:

    1. Search and access on "Amazon Simple Email Service" on the search bar at the AWS console.
    2. In "Configuration" > go to "Identities" > Click on "Create Identity"
    3. Type your email on the "Email Address" field -> AWS will send an email verification for that emal address provided. Just go to your email box and confirm verification.

## 4) Create a IAM Role

  Why using IAM: IAM is important because you need all your services to communicate.

  Step-by-Step:

    1. Search and access "IAM" on the search bar at the AWS console.
    2. In "Access management", go to "Roles" > Click on "Create role"
    3. Step 1:
        Click on AWS Service
        Choose Lambda as the Service
        ![image](https://github.com/user-attachments/assets/8a472352-5f0e-45dc-8e9c-5ccdcb0456a9)
       Step 2:
         We gona attach policies that the role can do
         -> AmazonS3ReadOnlyAccess
         -> AmazonTextractFullAccess
         -> AmazonDynamoDBFullAccess
         -> AmazonSESFullAccess
         -> AWSLambdaBasicExecutionRole
         Click "Next".
         
         Step 3:
         Role name <name>
         Descrition: exemaple:This Role Allows lambda access and process receipt automation. Services: SES, S3, Textract, DynamoDB and Lambda>

## 4) Create the Lambda Function

  Why using Lambda:

  Step-by-Step:

    1. Search and access "Lambda" on the search bar at the AWS console.
    2. Go to "Functions" > Click on "Create function"
    3. Create Function:
        Select "Author from Scratch" -> Allow us to create a custom fuction
        Fuction name: <name>
        Runtime: Select "Python 3.13"
        On tge "Change default execution role" drop down menu, select the role created on IAM "ReceiprprocessingLambdaRole"
    4. Go to "Configuration" after the Lambda menu creation was created and click on "edit"
        Change the timeout to 3 minutes -> this is necessary because Textract take minutes to complex receipts.
    5. Go to Environment Variables > Edit
        Click on "Add environment variable" and add 3 variables:
        * Key: DYNAMODB_TABLE, Value: Receipts;
        * Key: SES_RECIPIENT_EMAIL, Value: caio.valcazara@aluno.ufabc.edu.br;
        * Key: SES_SENDER_EMAIL, Value: caio.valcazara@aluno.ufabc.edu.br.r
    6. Go to Code














    
