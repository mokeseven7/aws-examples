# AWS, Serverless, And Automation

In my most humble opinion, this is what it looks like to be a full stack dev in 2023. One should be able to create and own the infra-structure they deploy their application code too. All Infra should be expressed as code with almost zero exceptions, and automations should be priortized at every level. Docker solved the "works on my machine" problem over 10 years ago.   

AWS gave us cloudformation. Many others have contributed ideas like Micro Service and Event Driven arcitectures. These things are more than just buzzwords, they are the building blocks (esp. IAAC) of what becoming "Agile" truley looks like in practice. 



```

An AWS construct that can be used to easily create reproducable Docker Images and ship them to ECR using local Dockerfiles.   

The construct is optimized for PHP images. 

The CDK/Infra code has 100% test coverage, automations for testing, and npm publishing. 

It also features a unique approach to deployment using codebuild and step functions. 

```
> [See Code](https://github.com/mokeseven7/phpbuilder) | [See NPM Package](https://www.npmjs.com/package/@mikemcgrath/phpbuilder) | [See Example Implentation](https://github.com/mokeseven7/phpbuilder-example)

```

An example implementation using the above construct to build a php iamge. 

This iamge uses the lambda/provided as its base, builds php 8, makes php executable in lambda. 

This image is used to create a custom JWT authorizer lambda function for api gateway using okta. 


```
> [See Code](https://github.com/mokeseven7/lambda-jwt-authorizer)



```

IAAC approach to shipping a container to AWS fargate. 

Including programtically making the github -> codebuild oauth connection to enable rebuilding of images on pushes to master. 

Includes incremental rollouts using health checks. 

If newly pushed images fail health checks, they are rolled back in ecr, and the current versions running in production are "re-tagged" as 'latest'


```
>[See Code](https://github.com/mokeseven7/cdk-fargate)

 
```

See another example of how to ship PHP code to lambda. 

This was back in the dark ages when you had to use "layers", and AWS did not provide the lambda runtime as a simple dockerfile. 


```

> [See Code](https://github.com/mokeseven7/php-lambda-creator) | [See Medium Article](https://mike-48770.medium.com/aws-lambda-php-via-run-time-api-69a65c516c3e)


   
```

A IAAC approach to creating a completely serverless wordpress instance.

It uses Fargate, Aurora, and EFS. 

Would I reccomend wordpress? Probably not. 

Bbut if you're going to anyway, make it serverless!

```
> [See Code](https://github.com/mokeseven7/cdk-wordpress)

