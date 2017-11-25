# serverless-localstack
[Serverless](https://serverless.com/) Plugin to support running against [Localstack](https://github.com/localstack/localstack).

This plugin allows any requests to AWS to be redirected to a running Localstack instance.

WARNING: This plugin is very much WIP

Pre-requisites:
* Localstack

## Installation

The easiest way to get started is to install via npm.

    npm install -g serverless
    npm install -g serverless-localstack

## Installation (without npm)

In order for the plugin to be recognized it must first be enabled via the .serverless_plugins directory.

```
cd project-path/
npm install --save bluebird
npm install --save aws-sdk
mkdir .serverless_plugins
ln -s /<PATH TO THE PLUGIN DIRECTORY>/src/index.js .serverless_plugins/serverless-plugin-localstack
```

## Configuring

There are two ways to configure the plugin, via a JSON file or via serverless.yml. There are two supported methods for
configuring the endpoints, globally via the "host" property, or individually. These properties may be mixed, allowing for global override support while also override specific endpoints.

A "host" or individual endpoints must be configured or this plugin will be deactivated.

### Configuring endpoints via serverless.yml 

```
service: myService

plugins:
  - serverless-plugin-localstack

custom:
  localstack:
    host: http://localhost
    endpoints:
      S3: http://localhost:4572
      DynamoDB: http://localhost:4570
      CloudFormation: http://localhost:4581
      Elasticsearch: http://localhost:4571
      ES: http://localhost:4578
      SNS: http://localhost:4575
      SQS: http://localhost:4576
      Lambda: http://localhost:4574
      Kinesis: http://localhost:4568
```

### Configuring endpoints via JSON

```
service: myService

plugins:
  - serverless-plugin-localstack

custom:
  localstack:
    endpointFile: path/to/file.json
```

## Localstack

For full documentation, see https://bitbucket.org/atlassian/localstack

## example to go through serverless-plugin-localstack

```
cd example/service

# start localstack service
docker-compose up -d

# serverless deploy
npm install
sls deploy
```

## Optional Debug Flag

An optional debug flag is supported via serverless.yml that will enable additional debug logs.

```
custom:
  localstack:
    debug: true
```
