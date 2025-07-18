# Introduction to Cloud Computing – Security &amp; Identity management (IAM)
Step-by-step process for your mini project on AWS Identity and Access Management (IAM), broken into logical phases — from understanding the concepts to hands-on setup and best practices.
#
## Phase 1: Set Up Your Environment
### Step 1: Create an AWS Free Tier Account (if not done)
* Visit [https://aws.amazon.com/free](https://aws.amazon.com/free)
* Click “Create a Free Account” and follow the prompts to register.
* Enable Multi-Factor Authentication (MFA) for the ‘root user’.
* Sign in to the AWS Management Console.
#
## Phase 2: Understand IAM Concepts
### Step 2: Study Core IAM Concepts
Read and understand the following key IAM elements:

* Users: Individuals or applications that need access.
* Groups: Collections of users with similar permissions.
* Policies: JSON documents that define permissions.
* Roles: Temporary permissions for services or users.
* MFA & Password Policies: Security controls.
Use AWS docs: [AWS IAM Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
#
## Phase 3: Hands-On Implementation in AWS Console
### Step 3: Create IAM Users
1. Go to IAM Dashboard → Users → Add users
2. Enter username (e.g., `DevUser`)
3. Select Programmatic access and/or AWS Management Console access
4. Set custom password and require password reset
5. Assign permissions (choose “Attach existing policies directly” or add to group later)
6. Download the credentials `.csv` file
#
### Step 4: Create IAM Groups
1. IAM → User groups → Create group
2. Name the group (e.g., `Developers`)
3. Attach policies like `AmazonS3ReadOnlyAccess`, `EC2ReadOnlyAccess`
4. Add users to the group
#
### Step 5: Create IAM Policies (Custom)
1. IAM → Policies → Create policy
2. Choose JSON tab
3. Paste a custom policy like:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
```
4. Name the policy (e.g., `ListS3BucketPolicy`) and save
5. Attach it to a user, group, or role
#
### Step 6: Create IAM Roles
1. IAM → Roles → Create role
2. Select AWS service or another AWS account
3. Use case example: “EC2”
4. Attach a policy like `AmazonS3FullAccess`
5. Name and create the role
6. Launch an EC2 instance and attach this role to give it S3 access
#
## Phase 4: Enforce Security Best Practices
### Step 7: Enable MFA for IAM Users

1. IAM → Users → Select user → Security credentials
2. Activate MFA (virtual MFA app like Google Authenticator)
#
### Step 8: Set a Password Policy
1. IAM → Account settings
2. Set:
   * Minimum password length (e.g., 8)
   * Require symbols, numbers, uppercase, lowercase
   * Password expiration
#
## Phase 5: Test and Review
### Step 9: Test Access
* Log in as IAM user and check if permissions match expectations
* Try accessing services like EC2, S3
* Modify permissions and observe changes
#
## Phase 6: Document and Conclude
### Step 10: Write a Summary Report
Include:
* What each IAM component is and how you used it
* Sample policy created
* MFA enforcement screenshot
* Challenges and lessons learned
* Security recommendations
#
## Bonus: Best Practices Checklist
* Use groups to manage permissions, not individuals
* Apply least privilege principle
* Rotate access keys regularly
* Use roles for applications (not long-term credentials)
* Enable logging with AWS CloudTrail for auditing.
