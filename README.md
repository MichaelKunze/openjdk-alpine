# openjdk-alpine

Simple docker image with openjdk 11/12 based on alpine and ecr-login from awslabs. 
Makes it easy to upload a dockerimage to aws.

## Tags

* `11` ([11/Dockerfile](https://github.com/MichaelKunze/openjdk-alpine/blob/master/11/Dockerfile))
* `12` ([12/Dockerfile](https://github.com/MichaelKunze/openjdk-alpine/blob/master/12/Dockerfile))

## Usage

Best used with [https://github.com/GoogleContainerTools/jib/tree/master/jib-gradle-plugin](jib)

```
jib {
    from {
         image = "mkunze/openjdk-alpine:11"
   }
    to {
        image = "<account>.dkr.ecr.<region>.amazonaws.com/<repository>"
    }
    container {
        mainClass = "com.example.Startup"
    }
}
```
