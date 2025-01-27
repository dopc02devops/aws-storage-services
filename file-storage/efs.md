Amazon EFS (Elastic File System):
A fully managed, scalable file storage service for use with EC2 instances and other AWS services.

Use Cases: Content management, development environments, and shared storage.
Features:
NFS-based file storage.
Pay-per-use pricing and automatic scaling.
Amazon FSx:

FSx for Windows File Server: Managed Windows file storage.
FSx for Lustre: High-performance file systems for compute-intensive workloads (e.g., machine learning, HPC).

Create an EFS File System
aws efs create-file-system \
  --creation-token MyEFS \
  --performance-mode generalPurpose \
  --throughput-mode bursting


List All File Systems
aws efs describe-file-systems \
  --file-system-id fs-12345678


Create Mount Targets
aws efs create-mount-target \
  --file-system-id fs-12345678 \
  --subnet-id subnet-12345678 \
  --security-groups sg-12345678


List Mount Targets
aws efs describe-mount-targets \
  --file-system-id fs-12345678

 Delete a Mount Target
 aws efs delete-mount-target \
  --mount-target-id mt-12345678


Delete an EFS File System

aws efs delete-file-system \
  --file-system-id fs-12345678


Create an Access Point
aws efs create-access-point \
  --file-system-id fs-12345678 \
  --posix-user Uid=1001,Gid=1001 \
  --root-directory Path=/data,CreationInfo={OwnerUid=1001,OwnerGid=1001,Permissions="0755"}


List Access Points
aws efs describe-access-points \
  --file-system-id fs-12345678


 Delete an Access Point
 aws efs delete-access-point \
  --access-point-id fsap-12345678


3. Example Workflow
Step 1: Create a File System
bash
Copy
Edit
aws efs create-file-system --creation-token MyEFS
Step 2: Create Mount Targets
bash
Copy
Edit
aws efs create-mount-target \
  --file-system-id fs-12345678 \
  --subnet-id subnet-12345678 \
  --security-groups sg-12345678
Step 3: Mount the File System on an EC2 Instance
Install NFS client:
bash
Copy
Edit
sudo yum install -y nfs-utils
Mount the file system:
bash
Copy
Edit
sudo mount -t nfs4 -o nfsvers=4.1 fs-12345678.efs.us-east-1.amazonaws.com:/ /mnt/efs
Step 4: Delete the File System
Delete mount targets:
bash
Copy
Edit
aws efs delete-mount-target --mount-target-id mt-12345678
Delete the file system:
bash
Copy
Edit
aws efs delete-file-system --file-system-id fs-12345678
4. Monitoring and Tags
1. Add Tags to a File System
bash
Copy
Edit
aws efs tag-resource \
  --resource-id fs-12345678 \
  --tags Key=Environment,Value=Production
2. List Tags
bash
Copy
Edit
aws efs describe-tags \
  --file-system-id fs-12345678