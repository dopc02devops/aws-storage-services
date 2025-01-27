Amazon S3 Glacier:
Cost-effective storage for data archiving and long-term backup.
S3 Glacier Flexible Retrieval: Faster data retrieval for active archives.
S3 Glacier Deep Archive: Lowest-cost storage for rarely accessed data.


Create a Glacier Vault
aws glacier create-vault --account-id - --vault-name my-glacier-vault


List All Vaults
aws glacier list-vaults --account-id -


 Upload an Archive to Glacier
 aws glacier upload-archive --account-id - --vault-name my-glacier-vault --body /path/to/your/file


Retrieve Inventory of a Vault
aws glacier initiate-job --account-id - --vault-name my-glacier-vault --job-parameters '{"Type": "inventory-retrieval"}'


aws glacier describe-job --account-id - --vault-name my-glacier-vault --job-id <JobId>


aws glacier get-job-output --account-id - --vault-name my-glacier-vault --job-id <JobId> output.json


Retrieve a Specific Archive
aws glacier initiate-job --account-id - --vault-name my-glacier-vault --job-parameters '{"Type": "archive-retrieval", "ArchiveId": "<ArchiveId>"}'

aws glacier get-job-output --account-id - --vault-name my-glacier-vault --job-id <JobId> output-file-path


Delete an Archive
aws glacier delete-archive --account-id - --vault-name my-glacier-vault --archive-id <ArchiveId>


 Delete a Vault
 aws glacier delete-vault --account-id - --vault-name my-glacier-vault


Enable Vault Notifications
aws glacier set-vault-notifications --account-id - --vault-name my-glacier-vault --vault-notification-config file://notification.json


Monitor Vault Capacity
aws glacier describe-vault --account-id - --vault-name my-glacier-vault



