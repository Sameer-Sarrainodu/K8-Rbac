

### OIDC provider
trust and authentication provider

REGION_CODE=us-east-1
CLUSTER_NAME=roboshop
ACC_ID=968220652823
```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```
# create policy of secret and get the arn and paste below command

### Create IAM Role and K8 ServiceAccount.
Mapping between IAM ROle and K8 Service account
```
eksctl create iamserviceaccount \
--cluster=$CLUSTER_NAME \
--namespace=roboshop \
--name=mysql-secret-reader \
--attach-policy-arn=arn:aws:iam::968220652823:policy/mysql-secret-reader \
--override-existing-serviceaccounts \
--region $REGION_CODE \
--approve
```

