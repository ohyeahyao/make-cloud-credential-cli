# Azure Cloud Init 

## 建立 IaC Role

```
$ SUBSCRIPTION_ID=
$ ROLE_JSON=$(sed "s/__SUBSCRIPTION_ID__/${SUBSCRIPTION_ID}/g" ./role-iac.json)
$ az role definition create --role-definition ${ROLE_JSON}
```

## 建立 Service Principal & Credential

refs: [create-a-service-principal](https://docs.microsoft.com/en-us/azure/developer/terraform/get-started-cloud-shell-bash?tabs=bash#create-a-service-principal) 

將 output 存成 json 存進 .credentials 資料夾中
```
$ az ad sp create-for-rbac --name tf-svc --role App-IaC --scopes /subscriptions/${SUBSCRIPTION_ID}
{
  "appId": "xxxx-xxxx-xxxx-xxxxxxxxx",
  "displayName": "tf-svc",
  "password": "xxxxxxxxxxxxxx",
  "tenant": "xxxx-xxxx-xxxx-xxxx-xxxxxxxxx"
}
```

