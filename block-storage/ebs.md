
Amazon EBS (Elastic Block Store):
Provides block-level storage volumes for use with EC2 instances.
Use Cases: Databases, enterprise applications, and file systems requiring low-latency, high-throughput storage.
Features:
SSD and HDD-based storage types (e.g., General Purpose SSD, Provisioned IOPS SSD).
Snapshots for data backup and recovery.
AWS Local Zones and Storage Gateway: Supports workloads that require ultra-low latency and local block storage.

Create an EBS Volume
aws ec2 create-volume \
    --size 10 \
    --volume-type gp2 \
    --availability-zone us-east-1a \
    --tag-specifications 'ResourceType=volume,Tags=[{Key=Name,Value=MyVolume}]'


Attach the Volume to an EC2 Instance
aws ec2 attach-volume \
    --volume-id vol-0abcd1234ef56789a \
    --instance-id i-0123456789abcdef0 \
    --device /dev/xvdf

Describe the Volume
aws ec2 describe-volumes --volume-ids vol-0abcd1234ef56789a


Detach the Volume
aws ec2 detach-volume --volume-id vol-0abcd1234ef56789a


Delete the Volume
aws ec2 delete-volume --volume-id vol-0abcd1234ef56789a
