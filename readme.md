Automated Snapshot Cleanup Lambda Function
Overview
This project implements an AWS Lambda function using Python and the Boto3 library to automatically manage EBS snapshots in an AWS environment. 
The function regularly scans for and deletes snapshots that are no longer associated with running EC2 instances, reducing storage costs and improving resource management.

Key Features
• Automatically deletes EBS snapshots not associated with running EC2 instances.
• Implemented using AWS Lambda, Python, and Boto3.
• Configured IAM roles and policies for necessary permissions.
• Packaged Lambda function and dependencies into a ZIP file for deployment.
• Tested functionality using AWS CLI.

Prerequisites
• AWS CLI installed and configured with appropriate IAM credentials.
• Python 3.8 or later installed.
• Boto3 library installed (`pip install boto3`).

Setup:
1. Clone the repository:
git clone "https://github.com/EneeyaSenthil/AWSCostOptimization"
2. Navigate to the project directory:
cd automated-snapshot-cleanup-lambda
3. Install dependencies:
pip install boto3

Configuration
Ensure IAM role `SnapshotCleanupRole` has necessary permissions.

Deployment
1. Package Lambda function:
zip -r lambda_function.zip snapshot_cleanup.py
2. Create Lambda function:
aws lambda create-function \
    --function-name SnapshotCleanupFunction \
    --zip-file fileb://lambda_function.zip \
    --handler snapshot_cleanup.lambda_handler \
    --runtime python3.8 \
    --role arn:aws:iam::your-account-id:role/SnapshotCleanupRole

Testing
Invoke Lambda function:
aws lambda invoke \
    --function-name SnapshotCleanupFunction \
    --payload {} \
    output.txt