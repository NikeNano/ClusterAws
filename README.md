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

3) Create the configuration of the cluster, change settings accoring to demands:

```Bash
kops create cluster --node-count=2 --node-size=t2.small --zones=us-west-2a --name=${cluster name} --state ${s3 bucket}
```
To check the configurations run the following command:
```Bash
kops get instancegroups --name hansson.k8s.local --state s3://kubernetes-aws-niklas-hansson
```

To edit the types of the nodes run 
```Bash
kops edit ig nodes --name ${The name of the cluster} --state ${s3 bucket}
```

Change the editor to used nano (this will make you a happier person) 
```Bash
export KUBE_EDITOR=emacs
```

4) Launch the cluster
