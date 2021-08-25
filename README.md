Rough Verbal Idea given by the customer for their upcoming Product Requirement
1.	We have an Insurance Plan to be build
a.	Channel Partners
b.	Selling these mobile
c.	And sale the insurance with the mobile
d.	Monitor glass is broken
e.	That can get it repaired
f.	They can exchange
2.	Register Themselves, Metadata
3.	Claiming 500 Rs  - Redeem
4.	Parse the document and get the data into the system
5.	And then to send some data
6.	Once the allocation is done, customer will upload the document and 

Customer Tech Team understanding for below AWS usage
1.	Scalable and Redundant architecture
2.	Data Redundancy
3.	PSS
4.	Different Region
5.	Data Security
6.	Security @ Rest (PII Data)
7.	Low bandwidth area users (OTP)
8.	SNS
9.	SFTP
10.	SSO
11.	IAM – Role, Group, Policy
12.	Data Trace
13.	Data at Transit

Solution: 1. Diagram 2. Descriptions

![Scalable-Secure-Insurance-Exchange-Application](https://user-images.githubusercontent.com/13980382/130314662-a5a2f89a-ba46-4cef-8698-a22f0f698ca8.png)

Note: Above Solution can be divided into 3 Different Requirement
1.	How to Protect Data at Rest with Amazon EC2 Instance Store Encryption
a.	The administrator encrypts a secret password by using KMS. The encrypted password is stored in a file.
b.	The administrator puts the file containing the encrypted password in an S3 bucket.
c.	At instance boot time, the instance copies the encrypted file to an internal disk.
d.	The EC2 instance then decrypts the file using KMS and retrieves the plaintext password. The password is used to configure the Linux encrypted file system with LUKS. All data written to the encrypted file system is encrypted by using an AES-256 encryption algorithm when stored on disk.
2.	AWS Transfer for SFTP with a custom authentication configured to allow uploading to S3 via SFTP using Azure Active Directory credentials. We will also validate the end user is a part of a specific security group. If both authentication and group validation is true, we will grant access to the S3 bucket via AWS Transfer for SFTP.
a.	User initiates an SFTP transfer
b.	AWS Transfer for SFTP then sends the login request to the AWS API Gateway
c.	AWS Lambda function receives the User Name and Password from the API Gateway invocation
d.	AWS Lambda function calls the Azure AD API call to validate the User Login and then Validates that the user is a part of the specified Security Group
e.	If both Authentication and Group Membership returns true, then the function continues to build our custom IAM Policy for the specified user
f.	the AWS Lambda function returns the specified IAM Role as well as a custom Scoped Down IAM Policy
g.	End user now has access to upload and download files and create new directories in the specified directory: MY_BUCKET/USER_NAME
h.	
3.	To achieve the interaction we just described, we build a Insurance order bot first with the following intents: GetInsuranceCatalog and OrderInsurance. The OTP password is used in intents that involve transactions, such as Order Insurance.
a.	Amazon Lex for building the conversational interface.
b.	AWS Lambda to run data validation and fulfilment.
c.	Amazon DynamoDB to store and retrieve data.
d.	Amazon Simple Notification Service (SNS) to publish SMS messages.
e.	AWS Key Management Service (KMS) to encrypt and decrypt the OTP.
f.	Amazon Cognito identity pool to obtain temporary AWS credentials to use KMS
# scalable-secure-vendor-insurance-app-on-aws
