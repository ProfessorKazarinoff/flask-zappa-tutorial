# flask-zappa-tutorial

An example of using Python, Flask and Zappa to deploy as very simple serverless web app on aws lambda

follows Pretty Printed YouTube Video: https://youtu.be/Vl5wroVmSuk

## To run

### AWS credentials

Log into AWS IAM, create a new user with admin credentials

in ~/.aws/credentials

```
[default]
aws_access_key_id = XXXXXXXXXXXXXXXXXXXXXXXXXX
aws_secret_access_key = XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

### Run Zappa init

```
pip install flask zappa
# create app.py
zappa init
```

### Modify zappa_setting.json

profile name comes from .aws/credentials. aws_region needs to be set, all others from zappa init are OK

```
{
    "dev": {
        "app_function": "app.app",
        "profile_name": "default",
        "project_name": "flask-zappa-tut",
        "runtime": "python3.7",
        "s3_bucket": "zappa-9cf4j0c1h",
        "aws_region": "us-west-2"
    }
}
```

### Deploy 

```
zappa deploy dev
```

### Make changes and update

```
zappa update dev
```


