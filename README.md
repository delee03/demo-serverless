<!--
title: 'Serverless Framework Node Express API on AWS'
description: 'This template demonstrates how to develop and deploy a simple Node Express API running on AWS Lambda using the Serverless Framework.'
layout: Doc
framework: v4
platform: AWS
language: nodeJS
priority: 1
authorLink: 'https://github.com/serverless'
authorName: 'Serverless, Inc.'
authorAvatar: 'https://avatars1.githubusercontent.com/u/13742415?s=200&v=4'
-->

# Serverless Framework Node Express API on AWS

This template demonstrates how to develop and deploy a simple Node Express API service running on AWS Lambda using the Serverless Framework.

This template configures a single function, `api`, which is responsible for handling all incoming requests using the `httpApi` event. To learn more about `httpApi` event configuration options, please refer to [httpApi event docs](https://www.serverless.com/framework/docs/providers/aws/events/http-api/). As the event is configured in a way to accept all incoming requests, the Express.js framework is responsible for routing and handling requests internally. This implementation uses the `serverless-http` package to transform the incoming event request payloads to payloads compatible with Express.js. To learn more about `serverless-http`, please refer to the [serverless-http README](https://github.com/dougmoscrop/serverless-http).

## Usage

### Deployment

Install dependencies with:

```
npm install
```

and then deploy with:

```
serverless deploy
```

After running deploy, you should see output similar to:

```
Deploying "aws-node-express-api" to stage "dev" (us-east-1)

✔ Service deployed to stack aws-node-express-api-dev (96s)

endpoint: ANY - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com
functions:
  api: aws-node-express-api-dev-api (2.3 kB)
```

_Note_: In current form, after deployment, your API is public and can be invoked by anyone. For production deployments, you might want to configure an authorizer. For details on how to do that, refer to [`httpApi` event docs](https://www.serverless.com/framework/docs/providers/aws/events/http-api/).

### Invocation

After successful deployment, you can call the created application via HTTP:

```
curl https://xxxxxxx.execute-api.us-east-1.amazonaws.com/
```

Which should result in the following response:

```json
{ "message": "Hello from root!" }
```

### Local development

The easiest way to develop and test your function is to use the `dev` command:

```
serverless dev
```

This will start a local emulator of AWS Lambda and tunnel your requests to and from AWS Lambda, allowing you to interact with your function as if it were running in the cloud.

Now you can invoke the function as before, but this time the function will be executed locally. Now you can develop your function locally, invoke it, and see the results immediately without having to re-deploy.

When you are done developing, don't forget to run `serverless deploy` to deploy the function to the cloud.

## Some popular plugins used in this template

-   [serverless-offline](https://www.serverless.com/plugins/serverless-offline)
-   [serverless-dotenv-plugin](https://www.serverless.com/plugins/serverless-dotenv-plugin)
-   [serverless-pseudo-parameters](https://www.serverless.com/plugins/serverless-pseudo-parameters)
-   [serverless-prune-plugin](https://www.serverless.com/plugins/serverless-prune-plugin)
-   [serverless-plugin-tracing](https://www.serverless.com/plugins/serverless-plugin-tracing)

## Some popular templates used in this template

-   [aws-nodejs](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-nodejs)
-   [aws-nodejs-typescript](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-nodejs-typescript)
-   [aws-python](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-python)
-   [aws-python3](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-python3)
-   [aws-java-maven](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-java-maven)
-   [aws-java-gradle](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-java-gradle)
-   [aws-csharp](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-csharp)
-   [aws-fsharp](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-fsharp)
-   [aws-go](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-go)
-   [aws-ruby](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-ruby)
-   [aws-rust](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-rust)
-   [aws-php](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-php)
-   [aws-haskell](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-haskell)
-   [aws-elixir](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-elixir)
-   [aws-erlang](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-erlang)
-   [aws-clojure](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-clojure)
-   [aws-kotlin](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create#aws-kotlin)

## Some popular command used in this template

# Local Development

```
serverless offline start # Run locally
serverless offline --host 0.0.0.0 # Run locally and allow external access
```

# Deployment

```
serverless deploy # Deploy to AWS
serverless deploy -v # Verbose deployment
serverless deploy -f functionName # Deploy single function
```

# Information

```
serverless info # Get info about deployed service
serverless metrics # Get metrics
serverless logs -f functionName # Get logs for a function
```

# Development/Testing

```
serverless invoke local -f functionName # Test function locally
serverless invoke -f functionName # Test deployed function
```

# Cleanup

```
serverless remove # Remove deployed service
```

# Templates/Init

```
serverless create --template aws-nodejs # Create new project from template (Node.js)
```
