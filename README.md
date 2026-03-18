# Museum of Candy - AWS CDK Infrastructure

This project uses the AWS Cloud Development Kit (CDK) with TypeScript to provision cloud infrastructure for the "Museum of Candy" static website. 

<img width="1892" height="886" alt="image" src="https://github.com/user-attachments/assets/be55be53-3137-40d7-af78-5503fb8b14a4" />


## Architecture

This CDK stack (`TatsCdkStack`) automatically provisions two Amazon S3 buckets:

1. **Standard Storage Bucket**: A standard, private S3 bucket. The name of this bucket is outputted to the console upon successful deployment.
2. **"Museum of Candy" Website Bucket**: An S3 bucket specifically configured for static website hosting. 
   - Uses `index.html` as the entry point.
   - Public read access is enabled.
   - Public access blocks are disabled to allow global web traffic.

*Note: Both buckets are configured with `autoDeleteObjects: true` and `RemovalPolicy.DESTROY`. This means if you delete the CDK stack, the buckets and all files inside them will be automatically cleaned up to prevent unwanted AWS charges.*

## Getting Started

### Prerequisites
* Node.js installed
* AWS CLI installed and configured with your credentials
* AWS CDK CLI installed globally (`npm install -g aws-cdk`)

### Useful Commands

* `npm install`     - Installs the required dependencies
* `npm run build`   - Compiles TypeScript to JavaScript
* `npx cdk synth`   - Emits the synthesized CloudFormation template
* `npx cdk deploy`  - Deploys the stack to your default AWS account/region
* `npx cdk destroy` - Tears down the stack and deletes the S3 buckets

## Deploying the Website

1. Run `npx cdk deploy` to create the buckets in your AWS account.
2. Once deployed, upload your "Museum of Candy" static website files (including your `index.html`) to the newly created Website S3 bucket. You can do this via the AWS S3 Console or the AWS CLI.
3. Access your website using the S3 bucket's generated static website endpoint URL.
