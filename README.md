# AWS AppSync GraphQL Photo Sample

**Please submit issues to the [appsync-sdk-js](https://github.com/awslabs/aws-mobile-appsync-sdk-js/issues) repository.**

![Demo](media/demo.gif)

This sample application shows how to use GraphQL to build an application that a user can login to the system, then upload and download photos which are private to them. The sample is written in React and uses AWS AppSync, Amazon Cognito, Amazon DynamoDB and Amazon S3 as well as the AWS Mobile CLI.

## Architecture Overview
![Architecture](media/architecture_diagram.png)

## Prerequisites
+ [AWS Account](https://aws.amazon.com/mobile/details/)

+ [NodeJS](https://nodejs.org/en/download/) with [NPM](https://docs.npmjs.com/getting-started/installing-node)

+ [AWS Mobile CLI v1.1.0](https://github.com/aws/awsmobile-cli)
  - `npm install -g awsmobile-cli`
  - `awsmobile configure aws` 
    - Configure your access and secret keys of your aws account that has AppSync permissions (or AdminAccess) and your preferred region. 
    - If you never used AWS MobileHub before, awsmobile-cli will pop-up a Web Browser Window to enable MobileHub on your account.


## Getting Started

1. Clone this repo locally.

2. Go to the photo-client folder inside of the cloned repo.
```
cd ./photo-client
```

3. Run awsmobile init with default settings
```
awsmobile init --yes
```

4. Configure **Amazon Cognito User Pool** as authentication type
```
awsmobile appsync configure
```
- Select **AMAZON_COGNITO_USER_POOLS**
- Confirm defaults

5. Update changes
```
awsmobile push
```

6. Run your app
```
awsmobile run
```

The awsmobile-cli will create your Amazon Cognito User Pool and Identity Pool, an Amazon S3 bucket with private directories to store each user's photo and an AWS AppSync API that uses Amazon DynamoDB to store data. 

The sample uses [AWS Amplify](https://github.com/aws/aws-amplify) to perform the Sign-Up and Sign-In flows with a Higher Order Component.

If the application runs successfully you should be able to enter the name of a photo, choose a file and then press **Add photo**. This will make a GraphQL call to enter the record into the database and simultaneously upload the object to S3. An immediate fetch of the record will then be at the bottom of the screen.

