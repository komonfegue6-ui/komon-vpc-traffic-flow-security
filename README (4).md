<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](https://nextwork.ai/projects/fe5ed473-5874-57e1-a58f-d9b3d652330c)

**Author:** Komeezzy  
**Email:** komonservices@gmail.com

---

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_92b0b0b4)

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private, isolated section of the AWS cloud where I control networking, and it is useful because it lets resources communicate securely without being exposed to everyone else on AWS.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to set up traffic flow and security by adding a route table, a security group, and a network ACL to my existing VPC.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was that a subnet named "Public 1" still isn't actually public until it has a route to an internet gateway naming it public doesn't make it public.

### This project took me...

This project took me about an hour.

## Route tables

Route tables are a set of rules that determine direct traffic from your resource to your internet gateway.

Route tables are needed to make a subnet public because without a route directing internet-bound traffic (0.0.0.0/0) to the internet gateway, resources in the subnet have no way to reach or be reached by the internet.

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_0a07b191)

## Route destination and target

Routes are defined by their destination and target, which mean the destination is the IP range the traffic is trying to reach, and the target is where that traffic gets sent to reach it.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of my internet gateway, NextWork IG.

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_0a07b191)

## Security groups

Security groups are security checkpoints for network passing by.

### Inbound vs Outbound rules

Inbound rules are rules that control what traffic is allowed to enter a resource. I configured an inbound rule that allows HTTP traffic from anywhere (0.0.0.0/0).

Outbound rules are rules that control what traffic is allowed to leave a resource. By default, my security group's outbound rule allows all outbound traffic.

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_92b0b0b4)

## Network ACLs

Network ACLs are a layer of security that controls traffic in and out at the subnet level, checking every packet against a set of rules before letting it through.

### Security groups vs. network ACLs

The difference between a security group and a network ACL is that security groups control traffic at the individual resource level, while network ACLs control traffic at the subnet level.

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic in and out.

In contrast, a custom ACL's inbound and outbound rules are automatically set to deny all traffic until I manually add rules to allow it.

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_4faeb056)

## Tracking VPC Resources

I created additional VPC resources a VPC, an internet gateway, and a security group using the AWS CLI. Instead of my usual region (af-south-1), I used a different region to simulate a multi-region setup. Teams would use multiple regions to improve latency for users closer to that region, and to protect against outages if one region goes down.

EC2 Global View is a tool where you can find all your EC2 and VPC resources across every AWS region in one place. I could even narrow down my search by resource type or region. Without EC2 Global View, you'd have to manually switch between regions in the console to check for resources one by one.

Now that I've learnt about EC2 Global View, I'd use it again to quickly check whether I've left any resources running in a region I forgot about, especially before wrapping up a project to avoid unnecessary charges.

![Image](https://nextwork.ai/content_turquoise_clever_cumin/uploads/aws-networks-security_b03ea6162)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/fe5ed473-5874-57e1-a58f-d9b3d652330c)*
