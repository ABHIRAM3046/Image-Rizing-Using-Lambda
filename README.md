# Thumbnail Generator

This project uses AWS Lambda to automatically generate thumbnails for images uploaded to an S3 bucket.

## Setup Instructions

### Prerequisites
- An AWS account
- AWS CLI installed and configured

### Step 1: Create an S3 Bucket
1. Sign in to the AWS Management Console.
2. Open the Amazon S3 console.
3. Create a new bucket (e.g., `my-image-bucket`).

### Step 2: Create an AWS Lambda Function
1. Open the AWS Lambda console.
2. Create a Lambda Function:
   - Click on `Create function`.
   - Choose `Author from scratch`.
   - Enter the function name (e.g., `ThumbnailGenerator`).
   - Choose the runtime (e.g., `Python 3.12`).
   - Create a new role with basic Lambda permissions.
3. Add Code to Lambda Function:
   - Copy the code from `lambda_function.py` and paste it into the Lambda function code editor.
4. Set Up S3 Trigger:
   - Configure the S3 bucket to trigger the Lambda function on object creation.

### Step 3: Configure IAM Role
Ensure the Lambda execution role has the necessary permissions to read from and write to the S3 bucket.


