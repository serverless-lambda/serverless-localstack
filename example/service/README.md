## example to go through serverless-plugin-localstack

Use serverless example [aws-node-rest-api-with-dynamodb](https://github.com/serverless/examples/tree/master/aws-node-rest-api-with-dynamodb) and add below lines in its `serverless.yml`


```
plugins:
  - serverless-plugin-localstack
custom:
  localstack:
    host: 'http://localhost'
    endpoint: localstack_endpoints.json
```

Run 

```
cd example/service
docker-compose up -d
npm install
mkdir .serverless_plugins
ln -s ../src/index.js .serverless_plugins/serverless-plugin-localstack
sls deploy
```
