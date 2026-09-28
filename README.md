# microservice-project-yml
# 1. What AZs does my ELB have?
aws elb describe-load-balancers --load-balancer-names a2060... --region us-east-1

# 2. What AZ is my EC2 in?
aws ec2 describe-instances --instance-ids i-02a9... --region us-east-1

# 3. Is EC2 healthy behind ELB?
aws elb describe-instance-health --load-balancer-name a2060... --region us-east-1

# 4. If AZ is missing, enable it
aws elb enable-availability-zones-for-load-balancer \
  --load-balancer-name a2060... \
  --availability-zones us-east-1a \
  --region us-east-1

# 5. If instance isn't registered, register it
aws elb register-instances-with-load-balancer \
  --load-balancer-name a2060... \
  --instances i-02a9... \
  --region us-east-1
