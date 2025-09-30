# AWS Resource Dashboard

A Flask-powered web application that delivers a real-time dashboard to visualize key AWS resources in your account. The dashboard presents information about EC2 instances, VPCs, Load Balancers, and AMIs in a clean, structured layout.

✨ Key Features

🔹 EC2 Instances
Display details like Instance ID, State, Type, and Public IP Address

🔹 VPC Overview
List VPC IDs alongside their associated CIDR blocks

🔹 Elastic Load Balancers
View Load Balancer names with their corresponding DNS names

🔹 Custom AMIs
List AMI images owned by your AWS account

🔹 Live Data
Pulls up-to-date resource information directly via AWS APIs

🔹 Minimal UI
Simple, responsive interface using neatly formatted tables for readability




# local requierments
-Python 3.7 or higher
-AWS Account with appropriate permissions
-AWS credentials configured




# Installation (**operation in BASH**)
bash::
   git clone <repository-url>           *Clone the repository*
   cd rolling_project
   cd python                            *Navigate to the Python directory*
   pip install -r requirements.txt      *Install dependencies*


   

# Configuration -- AWS Credentials AND Permissions Setup

configure AWS credentials using environment variables.
Create a `.env` file OR set the following environment variables:


----------  credentials ---------

bash::
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_REGION="your-preferred-region"  # e.g., us-east-1, eu-west-1

----------- premissions----------

Your AWS user/role must have the following permissions:

json::
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeVpcs",
                "ec2:DescribeImages",
                "elbv2:DescribeLoadBalancers"
            ],
            "Resource": "*"
        }
    ]
}




# Running the Application

Set your AWS credentials:

bash::
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_REGION="your-preferred-region"  # e.g., us-east-1, eu-west-1

Start the Flask application:

bash::
python app.py


Access the dashboard:

Open web browser to: http://localhost:5001








# Project Structure

rolling_project/
├── python/
│   ├── app.py                # Main Flask application
│   └── requirements.txt      # Python requirements
├── aws/
│   ├── ec2.png              # AWS EC2 screenshot
│   └── rollingproject.png   # Web application screenshot
└── README.md                


# technical Dependencies

Flask: Web framework for the dashboard
Boto3: AWS SDK for Python

# Application Architecture

AWS Integration: AWS API calls
Frontend: HTML templates with inline styling
Backend: Flask web server
Data Flow: Real-time API calls to Data processing to HTML

# Supported Services (AWS)

EC2:
   Instance details
   Instance states
   Public IP addresses

VPC:
   VPC IDs
   CIDR blocks

ELB:
   Load balancer names
   DNS names


# application usage (once running)

Navigate to http://localhost:5001
View your AWS resources in separate tables
Data is fetched from your AWS account
Refresh the page to refresh data

# Troubleshooting Common errors

AWS Credentials Not Found:
   Ensure environment variables are set correctly
   Check AWS credentials file (`~/.aws/credentials`)

Connection Timeout:
   Verify your internet connection
   Check if AWS region is correctly specified

Application Wont Start
   Ensure all are installed: `pip install -r requirements.txt`
   Check if port 5001 is open/avaliable

Permission Denied Errors:
   Verify your AWS user has the required permissions
   Check the IAM policy attached to your user/role

# Debug Mode (The application runs in debug mode by default)

python::
app.run(host="0.0.0.0", port=5001, debug=False)