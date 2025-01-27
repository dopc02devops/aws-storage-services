Hybrid Cloud Storage
AWS Storage Gateway:
Connects on-premises environments with AWS, providing hybrid cloud storage options.
Use Cases: Backups, disaster recovery, and tiering data to the cloud.
Types:
File Gateway: For NFS/SMB access.
Volume Gateway: Block storage volumes.
Tape Gateway: Replaces physical tape libraries.

Create a Storage Gateway

aws storagegateway create-gateway \
  --gateway-type FILE_S3 \
  --gateway-name MyFileGateway \
  --gateway-region us-east-1 \
  --activation-key <activation-key>


Activate a Gateway

aws storagegateway activate-gateway \
  --gateway-name MyActivatedGateway \
  --activation-key <activation-key> \
  --gateway-region us-east-1


List All Gateways
aws storagegateway list-gateways

Configure Local Disk as Cache
aws storagegateway add-cache \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --disk-ids ["/dev/sdb"]


Create a File Share
NFS File Share:
aws storagegateway create-nfs-file-share \
  --client-token unique-client-token \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --role arn:aws:iam::123456789012:role/StorageGatewayRole \
  --location-arn arn:aws:s3:::my-s3-bucket \
  --default-storage-class S3_STANDARD

SMB File Share:
aws storagegateway create-smb-file-share \
  --client-token unique-client-token \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --role arn:aws:iam::123456789012:role/StorageGatewayRole \
  --location-arn arn:aws:s3:::my-s3-bucket \
  --default-storage-class S3_STANDARD \
  --authentication ActiveDirectory

List File Shares
aws storagegateway list-file-shares


Retrieve File Share Metadata
aws storagegateway describe-nfs-file-shares \
  --file-share-arn arn:aws:storagegateway:us-east-1:123456789012:share/share-12345678


Create a Tape for Backup
aws storagegateway create-tapes \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --tape-size-in-bytes 107374182400 \
  --client-token unique-client-token \
  --tape-barcode "TAPE1234567"


Upload Local Snapshot to AWS
aws storagegateway create-snapshot \
  --volume-arn arn:aws:storagegateway:us-east-1:123456789012:volume/vol-12345678 \
  --snapshot-description "Snapshot of volume for backup"


Monitor Gateway Performance
aws cloudwatch get-metric-data \
  --metric-data-queries '[{"Id":"gatewayBytesIn","MetricStat":{"Metric":{"Namespace":"AWS/StorageGateway","MetricName":"GatewayBytesIn"},"Period":300,"Stat":"Sum"}}]' \
  --start-time 2025-01-25T00:00:00Z \
  --end-time 2025-01-26T00:00:00Z


Delete a Gateway
aws storagegateway delete-gateway \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678


Delete a File Share
aws storagegateway delete-file-share \
  --file-share-arn arn:aws:storagegateway:us-east-1:123456789012:share/share-12345678


