Backup and Recovery
AWS Backup:
Centralized service to automate backups for AWS services like S3, EBS, RDS, and DynamoDB.
Features:
Policy-based backups.
Compliance monitoring.


1. S3 (Backup and Recovery)
Backup
Copy a local directory to S3:
aws s3 cp /local/path s3://your-bucket-name/backup-path/ --recursive


Sync local files to S3 (only new or updated files):
aws s3 sync /local/path s3://your-bucket-name/backup-path/


Recovery
Download from S3 to local:
aws s3 cp s3://your-bucket-name/backup-path/ /local/path --recursive


Sync from S3 to local:
aws s3 sync s3://your-bucket-name/backup-path/ /local/path


EBS (Backup and Recovery)
Create a snapshot of an EBS volume:
aws ec2 create-snapshot --volume-id vol-1234567890abcdef0 --description "Backup snapshot"

Automate backup using tags:
aws ec2 create-snapshot --volume-id vol-1234567890abcdef0 --tag-specifications 'ResourceType=snapshot,Tags=[{Key=Backup,Value=True}]'

Recovery
Restore from a snapshot (create a new volume):
aws ec2 create-volume --availability-zone us-east-1a --snapshot-id snap-1234567890abcdef0

Attach the restored volume:
aws ec2 attach-volume --volume-id vol-0987654321fedcba0 --instance-id i-1234567890abcdef0 --device /dev/xvdf


RDS (Backup and Recovery)
Create a manual RDS snapshot:
aws rds create-db-snapshot --db-instance-identifier mydbinstance --db-snapshot-identifier mydbsnapshot

List automated backups:
aws rds describe-db-snapshots --db-instance-identifier mydbinstance

Recovery
Restore from a DB snapshot:
aws rds restore-db-instance-from-db-snapshot --db-instance-identifier newdbinstance --db-snapshot-identifier mydbsnapshot

Point-in-time recovery (requires automated backups):
aws rds restore-db-instance-to-point-in-time --source-db-instance-identifier mydbinstance --target-db-instance-identifier restoreddbinstance --restore-time 2023-01-20T12:00:00Z


DynamoDB (Backup and Recovery)
Create an on-demand backup:
aws dynamodb create-backup --table-name my-table --backup-name my-backup

List backups:
aws dynamodb list-backups --table-name my-table

Recovery
Restore a table from a backup:
aws dynamodb restore-table-from-backup --target-table-name restored-table --backup-arn arn:aws:dynamodb:region:account-id:table/my-table/backup/backup-id

Restore a table to a point in time:
aws dynamodb restore-table-to-point-in-time --source-table-name my-table --target-table-