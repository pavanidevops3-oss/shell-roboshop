#!/bin/bash

ami_id="ami-09c813fb71547fc4f"
sg_id="sg-0421c015ec6afe1d7"

# Loop through all names passed as arguments
for instance in "$@"
do
  echo "Launching instance: $instance"

  aws ec2 run-instances \
    --image-id $ami_id \
    --instance-type t3.micro \
    --security-group-ids $sg_id \
    --tag-specifications "ResourceType=instance,Tags=[{Key=Name,Value=$instance}]" \
    --query 'Instances[0].InstanceId' \
    --output text
done