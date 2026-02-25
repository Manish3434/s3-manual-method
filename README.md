# s3-manual-method
I configured secure access between Amazon EC2 and Amazon S3 using an IAM Role from AWS Identity and Access Management instead of hardcoded keys. I automated daily backups with a bash script and cron, ensuring secure, role-based authentication and reliable cloud storage
Sudo -i
Sudo apt update
sudo apt install awscli -y - to install it to access the aws command  
snap install aws-cli --classic 
aws –version 
aws sts get-caller-identity 
aws s3 mb s3:// manish-s3-demo-1-done 
nano s3.html 
aws s3 cp s3.html s3://kanisma-ec2-project-00
aws s3api put-public-access-block \ 
-- manish-s3-demo-1-done \ 
--public-access-block-configuration BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=false,RestrictPublicBuckets=false 
BUCKET="manish-s3-demo-1-done" 
KEY="s3.html" 
REGION=$(aws s3api get-bucket-location --bucket $BUCKET --query 'LocationConstraint' --output text) 
REGION=${REGION:-us-east-1} 
echo https://$BUCKET.s3.$REGION.amazonaws.com/$KEY 
aws s3 rb s3:// manish-s3-demo-1-done 
