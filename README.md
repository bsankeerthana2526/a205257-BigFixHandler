This Lambda function automates the rebooting of EC2 instances based on instance names listed in a CSV file stored in an S3 bucket.
It's designed to work with ServiceNow-generated tickets exported as CSVs.

#How It Works
1. CSV Extraction from S3
The function downloads a CSV file from a specified S3 bucket.
It reads the SERVER_NAME(INSTANCEID) column to get EC2 instance names.
2. Instance ID Resolution
For each instance name, it uses the EC2 describe_instances API to find the corresponding instance ID (based on the Name tag).
3. Rebooting Instances
Once it collects all valid instance IDs, it calls reboot_instances to reboot them.
4. Logging and Error Handling
Logs are generated for debugging and monitoring.
If no valid instances are found or an error occurs, appropriate messages are returned.
5. Local Testing Support
The __main__ block allows you to test the function locally by simulating a Lambda event and context.
