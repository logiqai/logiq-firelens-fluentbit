# logiq-firelens-fluentbit
Custom Logiq fluent bit image for AWS firelens for Fargate, we have made use of the  'file' 'config-file-type' in FireLens.

**How to use:**
- Download the repository and Navigate into Custom-fluent-bit-image.
- Run the below.
  ```Docker build -t Logiq-config .  ```
- In order to push the image to AWS Private registry(reference:https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-push-ecr-image.html), tag the image by running the below, this should match the repository on AWS ECR in order to push the image successfully.</br>
   ```docker tag imag-id Username.dkr.region.amazon.com/logiqconfiguration ```
- execute the below to get the docker login credentials to AWS ECR. Use the same to login.</br>
   ``` aws ecr get-login ```
- Once logged in, push the image to private ECR registry.
- Reference the config file path in the FireLens configuration:</br>
```
"firelensConfiguration": {
    "type": "fluentbit",
    "options": {
        "config-file-type": "file",
        "config-file-value": "/firelens.conf"
    }
}
```
