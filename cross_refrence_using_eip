provider "aws"{
region="ap-south-1"
}

# Get existing resource part of TF state file
data "aws_instance" "my_ec2" {
 instance_id = "i-0c674a74fe577e6a3"
}

# Create a EIP
resource "aws_eip" "lb" {
  instance = data.aws_instance.my_ec2.id
  domain   = "vpc"
}

# Associate the EIP with Ec2
resource "aws_eip_association" "eip_assoc" {
  instance_id   = data.aws_instance.my_ec2.id
  allocation_id = aws_eip.lb.id
}

# Check return values using 'Output' block
output "my-ec2-id-is"{
description="ec2 id value"
value=data.aws_instance.my_ec2.id
}

output "EIP-is"{
description= "generated EIP value is"
value=aws_eip.lb.public_ip
}
