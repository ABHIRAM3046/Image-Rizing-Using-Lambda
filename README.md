# Thumbnail Image Generation using AWS Lambda

## Overview
This project demonstrates how to create an AWS Lambda function that automatically generates thumbnails for images uploaded to an Amazon S3 bucket. When an image is uploaded to the source S3 bucket, Lambda resizes the image and saves the thumbnail to a destination S3 bucket.

## Features
- Automatically generates thumbnails for images.
- Serverless architecture using AWS Lambda.
- Utilizes Amazon S3 for storing images and thumbnails.

## Technologies Used
- **AWS Lambda**: Executes the image resizing code.
- **Amazon S3**: Stores source images and resized thumbnails.
- **Python**: Programming language for Lambda function.
- **Pillow**: Python Imaging Library for image manipulation.

## Setup Instructions

### Prerequisites
- An AWS account.
- AWS CLI installed and configured.
- Python and pip installed.

### Step 1: Create S3 Buckets
1. **Source Bucket**: The bucket where images are uploaded.
2. **Destination Bucket**: The bucket where resized thumbnails will be saved.

   **Using AWS Management Console:**
   - Go to the S3 console.
   - Create two buckets:
     - **Source Bucket**: `my-source-bucket`
     - **Destination Bucket**: `my-destination-bucket`

### Step 2: Deploy the Lambda Function

1. **Lambda Function Code:**
   - The Lambda function code for resizing images is included in the repository. See `lambda_function.py`.

2. **IAM Role:**
   - The IAM role with the necessary permissions is provided in the repository. See `IAM_Role.json`.

3. **Deploy Lambda Function:**
   - Use the AWS CLI or Lambda console to deploy the Lambda function. Upload the `lambda_function.py` file containing the function code and dependencies.

### Step 3: Configure S3 Trigger for Lambda

1. **Add Trigger:**
   - Go to the Lambda console.
   - Select your Lambda function.
   - Add an S3 trigger for the source bucket:
     - Choose `S3` as the trigger.
     - Select the source bucket.
     - Set event type to `All object create events`.

### Step 4: Test the Lambda Function

1. **Test with a Dummy Event:**
   - Go to the Lambda console and choose your function.
   - Create a test event with the following JSON:

     ```json
     {
       "Records": [
         {
           "eventVersion": "2.0",
           "eventSource": "aws:s3",
           "awsRegion": "us-east-1",
           "eventTime": "1970-01-01T00:00:00.000Z",
           "eventName": "ObjectCreated:Put",
           "s3": {
             "bucket": {
               "name": "my-source-bucket",
               "arn": "arn:aws:s3:::my-source-bucket"
             },
             "object": {
               "key": "test-image.jpg"
             }
           }
         }
       ]
     }
     ```

   - Save and run the test.

2. **Upload an Image to Test:**
   - Upload an image to the source bucket.
   - Check the destination bucket for the resized thumbnail.

### Cleanup

1. **Delete Lambda Function:**
   - Go to the Lambda console and delete the function.

2. **Delete S3 Buckets:**
   - Go to the S3 console and delete both source and destination buckets.

3. **Delete IAM Role and Policy:**
   - Go to the IAM console and delete the role and policy created for this project.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
