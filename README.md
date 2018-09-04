# ClusterAws
Test to set up a cluster on AWS using kubernetes

1) Create the bucket and set up so it will do versioning of the configs. 
```Bash
$ aws s3api create-bucket --bucket ${bucket name} --region ${region}
```

2) Set up so that I get the configuration of the cluster stored in the S3 bucket. 
3) Launch the cluster
