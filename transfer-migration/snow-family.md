 Data Transfer and Migration
AWS Snow Family:

AWS Snowball: For petabyte-scale data transfer.
AWS Snowmobile: For exabyte-scale data migration using a physical truck.
AWS DataSync: Automates and accelerates data transfer between on-premises storage and AWS.

Amazon Transfer Family: Managed file transfer over protocols like SFTP, FTPS, and FTP.

Create a Snowball Job
aws snowball create-job \
    --job-type IMPORT \
    --resources '{"S3Resources":[{"BucketArn":"arn:aws:s3:::example-bucket","KeyRange":{}}]}' \
    --address-id a-bc123456 \
    --shipping-option SECOND_DAY \
    --snowball-type STANDARD \
    --description "Import job for Snowball"

Describe a Job
aws snowball describe-job --job-id JOB_ID


List Jobs
aws snowball list-jobs


Create an Address
Create a new shipping address for your Snow Family device.
aws snowball create-address \
    --address '{
        "AddressId": "unique-id",
        "Name": "John Doe",
        "Company": "Example Co.",
        "Street1": "1234 Example Street",
        "Street2": "Suite 567",
        "City": "Seattle",
        "StateOrProvince": "WA",
        "Country": "US",
        "PostalCode": "98101",
        "PhoneNumber": "1234567890"
    }'


 Get Snowball Device Unlock Code
Get the unlock code required to use a Snowball device.

aws snowball get-job-unlock-code --job-id JOB_ID


Get Snowball Device Manifest
Retrieve the manifest file for a Snowball device.

aws snowball get-job-manifest --job-id JOB_ID --manifest-output-path /path/to/manifest


Track a Job
Get shipping status for a Snow Family job.

aws snowball list-compatible-devices --job-type EXPORT

List Compatible Snowball Devices
Retrieve a list of Snowball devices that are compatible with your job type.
aws snowball list-compatible-devices --job-type EXPORT




