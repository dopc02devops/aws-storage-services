Data Lake Storage
Lake Formation: Helps create and manage data lakes using S3, making it easier to manage large-scale analytics and data integration.

1. Granting Permissions
Grant a specific permission (e.g., SELECT) to a principal (e.g., IAM user or role).
aws lakeformation grant-permissions \
  --principal DataLakePrincipalIdentifier=arn:aws:iam::123456789012:user/YourUser \
  --permissions SELECT \
  --resource '{"Table":{"DatabaseName":"my_database","Name":"my_table"}}'

2. Revoking Permissions
Revoke permissions from a principal.
aws lakeformation revoke-permissions \
  --principal DataLakePrincipalIdentifier=arn:aws:iam::123456789012:user/YourUser \
  --permissions SELECT \
  --resource '{"Table":{"DatabaseName":"my_database","Name":"my_table"}}'


3. Registering a Data Lake Location
Register a new S3 path as a data lake location.
aws lakeformation register-resource \
  --resource-arn arn:aws:s3:::my-data-lake-bucket \
  --use-service-linked-role

4. Deregistering a Data Lake Location
Deregister a previously registered S3 location.
aws lakeformation deregister-resource \
  --resource-arn arn:aws:s3:::my-data-lake-bucket


3. Registering a Data Lake Location
Register a new S3 path as a data lake location.
aws lakeformation register-resource \
  --resource-arn arn:aws:s3:::my-data-lake-bucket \
  --use-service-linked-role

4. Deregistering a Data Lake Location
Deregister a previously registered S3 location.
aws lakeformation deregister-resource \
  --resource-arn arn:aws:s3:::my-data-lake-bucket

7. Creating an LF-Tag
Create a new LF-tag for tagging resources.
aws lakeformation create-lf-tag \
  --tag-key "department" \
  --tag-values "finance" "engineering"

8. Deleting an LF-Tag
Delete an LF-tag.
aws lakeformation delete-lf-tag \
  --tag-key "department"

