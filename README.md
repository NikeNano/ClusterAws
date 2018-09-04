# ClusterAws
Test to set up a cluster on AWS using kubernetes

1) Create the bucket and set up so it will do versioning of the configs. 
```Bash
$ aws s3api create-bucket --bucket ${bucket name} --region ${region}
```

Seam to be problem if not us-east-1

```Bash
aws s3api create-bucket --bucket ${bucket name} --region ${region} --create-bucket-configuration LocationConstraint=${region}
```

2) Set up so that I get the configuration of the cluster stored in the S3 bucket. 
```Bash
$ aws s3api put-bucket-versioning --bucket ${bucket name}  --versioning-configuration Status=Enabled
```

3) Create the configuration of the cluster


4) Launch the cluster
