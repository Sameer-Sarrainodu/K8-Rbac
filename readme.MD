

### OIDC provider
trust and authentication provider

REGION_CODE=us-east-1
CLUSTER_NAME=roboshop-dev
ACC_ID=968220652823
```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```
# run this command to configure kube api
```
eksctl update kubeconfig --region $REGION_CODE --name $CLUSTER_NAME
```


### Create IAM Role and K8 ServiceAccount.
Mapping between IAM ROle and K8 Service account
```
eksctl create iamserviceaccount \
--cluster=$CLUSTER_NAME \
--namespace=roboshop \
--name=roboshop-mysql-secret-reader \
--attach-policy-arn=arn:aws:iam::968220652823:policy/Mysql-secret-reader \
--override-existing-serviceaccounts \
--region $REGION_CODE \
--approve
```

