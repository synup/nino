# nino

Simplifies collaboration and a better CLI for AWS ECR.

* Repository names are namespaced appropriately.
* Does *not* require everyone on team to learn mile-lengthy commands.

Here's a simple workflow:

* Edit your `Dockerfile`
* `nino build <aws-profile>` will build the image using docker
* `nino tag <aws-profile> latest` will tag the image with `latest` and push it to ECR.

nino also allows other stuff, checkout the usage section below.

### Requirements

* docker
* AWS CLI

### Config

Set the `repo_name` in a `.ninorc` file in the project directory. Names of repositories created will be prefixed with the AWS profile name used. Here's a simple config:

```
repo_name=hello-world
```

### Usage

Most commands require the AWS profile name

* Add tag to a build
  ```
  nino tag:add <aws-profile> <tag>
  ```

* Pushed tag
  ```
  nino tag:push <aws-profile> <tag>
  ```

* Both `tag:add` and `tag:push`
  ```
  nino tag <aws-profile> <tag>
  ```

* Build image
  ```
  nino build <aws-profile>
  ```

* URL to the latest image in the repo
  ```
  nino repo:image <aws-profile>
  ```

* AWS ECR repo info
  ```
  nino repo:info <aws-profile>
  ```

* Create an ECR repository
  ```
  nino repo:create <aws-profile>
  ```

* Delete the ECR repository
  ```
  nino repo:delete <aws-profile>
  ```

* Display ECR repo host url
  ```
  nino repo:host
  ```


## Notes

Configure AWS CLI with your organization profile names. For synup, we would add the following AWS profiles on our development machines:

* `synup-production` - for production IAM account
* `synup-staging` - for staging IAM account
* `synup-akash` - for company-provided personal IAM account (for development purposes)

This way the repositories created would be prefixed with names we can identify with. For example `synup-staging-hello-world`.
