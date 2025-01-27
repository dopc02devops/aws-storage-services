Edge Storage
Amazon S3 on Outposts:
Extends S3 to AWS Outposts for low-latency storage closer to on-premises workloads.
Amazon S3 on Outposts is used to store data on-premises using AWS Outposts.
AWS IoT Greengrass: For edge storage and processing with IoT devices.


Create an S3 Bucket on Outposts
aws s3control create-bucket \
    --bucket <bucket-name> \
    --outpost-id <outpost-id> \
    --region <region> \
    --endpoint-url <endpoint-url>


aws s3control create-bucket \
    --bucket my-outposts-bucket \
    --outpost-id op-1234567890abcdef \
    --region us-west-2 \
    --endpoint-url https://s3-outposts.us-west-2.amazonaws.com


List Buckets on Outposts

aws s3control list-buckets \
    --outpost-id op-1234567890abcdef \
    --endpoint-url https://s3-outposts.us-west-2.amazonaws.com


Create an Access Point for an S3 Outposts Bucket
aws s3control create-access-point \
    --name my-access-point \
    --bucket my-outposts-bucket \
    --vpc-configuration VpcId=vpc-1234567890abcdef \
    --endpoint-url https://s3-outposts.us-west-2.amazonaws.com


Upload an Object to an S3 Outposts Bucket

aws s3api put-object \
    --bucket <access-point-arn> \
    --key <object-key> \
    --body <file-path> \
    --endpoint-url <endpoint-url>


 Get an Object from an S3 Outposts Bucket
 aws s3api get-object \
    --bucket <access-point-arn> \
    --key <object-key> \
    <output-file> \
    --endpoint-url <endpoint-url>

Delete an Object from an S3 Outposts Bucket
aws s3api delete-object \
    --bucket <access-point-arn> \
    --key <object-key> \
    --endpoint-url <endpoint-url>

Delete an S3 Outposts Bucket

aws s3control delete-bucket \
    --bucket <bucket-name> \
    --endpoint-url <endpoint-url>
