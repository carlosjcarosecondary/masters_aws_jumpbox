# jumpbox
Process to create a jumpbox configuration in AWS

Process to create a jumpbox configuration in AWS
=

**Step 1 - Networking**
- To create a VPC
- To create 1 public subnet with an Internet Gateway
- To create 1 private subnet

**Step 2 - Instances**
- To create an EC2 instance for the application **in the private subnet**
- To create an EC2 instance for the jumpbox **in the public subnet** with a public IP address
- To create an EC2 instance for the NAT instance (instead of the NAT gateway managed by AWS) **in the public subnet** with a public IP address. The NAT image can be found on the Community AMIs
- Each instance must be created with an indeopendent security group

**Step 3 - Routing**
- Private routing table for the private subnet, it must have the NAT instance as the gateway
- Public routing table for the public subnet must have an Internet gateway
- **Important** The NAT instance must have the option "Change Source/Dest Check" disabled

**Step 4 - Security groups**
- NAT instance SG: inbound traffic from final instance SG
- Final instance: SSH traffic only from jumpbox SG
- Jumpbox SG: standard security considerations

Diagram
=
![JumpBox](https://user-images.githubusercontent.com/28940499/77299853-82f8fe00-6cc3-11ea-99c8-ffc622f81f9b.png)
