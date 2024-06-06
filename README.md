# CI CD for Lambda Functions

## Purpose of this project
This project has as goal building a CI/CD Pipeline using Github Actions for Lambda Functions.

## Structure of the project
### Lambda code
The function code is in the `hello-world` folder alongside with its `Dockerfile` and a `requirements.txt` as example of external libraries.

```
├── hello-world
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt

```
### Pipeline Code
The pipeline code is in `.github/workflows`. However, it is only an example. The idea is that, for each Lambda code, one could build a pipeline. So, when a pull request is merged from `dev` to `main`, the Lambda is automatically updated on AWS.
```
./.github
└── workflows
    └── update-lambda-hello-world.yaml
```

## The pipeline code
Beforehand, it's necessary to create an `ECR` repository on AWS, a `Lambda Function` based on this repository and an IAM user with `lambda:UpdateFunctionCode` permission. Also, the user's credentials must be configured in the repository configurations.

In the `.yaml` file, you can set different environment variables, accordingly with the function you intend to update.

## Steps
The steps for the pipeline are:
- Checkout
- Configure AWS credentials
- Login to ECR
- Build, tag and push image to ECR
- Update Lambda
