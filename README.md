# ☁️ iac-tf-confluent

## 📦 Terraform Confluent Provider:

https://registry.terraform.io/providers/confluentinc/confluent/latest

*Testing during lunch break/after work going through:*

https://registry.terraform.io/providers/confluentinc/confluent/latest/docs/guides/sample-project

📂 Documentation:

https://docs.confluent.io/cloud/current/overview.html

## 📈 In 3 broad steps:

1. Create trial confluent account, create a service account, assign `OrganizationAdmin` role to the service account, & create a cloud api key for the service account
2. Create resources on confluent cloud via Terraform ($400 to start), be careful because credit card attached in order to get this...
   - an env called `staging`
   - 3 service accounts `app_manager`, `app_producer`, & `app_consumer` with associated kafka key each
   - set permissions for service accounts using role based access conntrol or Access Control Lists, initialize and apply
3. use confluent cli to produce and consume messages from the topic  using the service accs kafka api keys then `DESTROY` all created resources ($)

### 📼 Video Example of Provider sending message on same topic to the Consumer after infra is up from tfa
https://github.com/user-attachments/assets/a30b1d6e-ea16-42e6-bc2e-6adef9c10ad1

## 📝 Notes & Findings

You have to set up with a credit card which is a little concerning, even if they do give you $400 credit for trial. After this, I'll likely delete my entire account to avoid concerns there.

1. API Key setup
<img width="1728" alt="1  API Key" src="https://github.com/user-attachments/assets/50873453-a280-48e8-9e96-dd5bdc3f96cc" />

2. `terraform init`
<img width="803" alt="2  TF init" src="https://github.com/user-attachments/assets/b5377bfd-d247-47d9-aec2-1730bd0839a4" />

3. service account `tf_runner` getting role `OrganizationAdmin`
<img width="1725" alt="3  tf_runner service acc getting role access" src="https://github.com/user-attachments/assets/28e6c57a-278b-4534-8c37-ae41e98ea081" />

4. `terraform validate` to confirm confluent api creds worked for tf
<img width="718" alt="4  terraform validate cloud key config" src="https://github.com/user-attachments/assets/f0bc3774-7fa7-412d-bc66-7c32eeaf6231" />

5. `terraform plan` verifies all IaC to occur
<img width="1840" alt="5  terraform plan" src="https://github.com/user-attachments/assets/08028ecf-abf6-4488-a1f7-40053eaf04bd" />

6. `terraform apply` to create the cluster, add 3 service accounts, set permissions including role access via ACLs, etc
<img width="1840" alt="6 1 terraform apply kicks off" src="https://github.com/user-attachments/assets/66e6358d-f507-45ae-869d-bc8972ea540f" />
<img width="1840" alt="6 2 terraform apply succeds" src="https://github.com/user-attachments/assets/283b006a-6d02-4f9b-b4ed-3b538b6377f9" />

7. Confluent staging cluster is up!
<img width="1840" alt="7  Confluent staging cluster up" src="https://github.com/user-attachments/assets/b2f6021d-32ca-4adc-abc7-a3af2c2d10ab" />

8. Valid Confluent cluster api keys for the 3 service accounts generated
<img width="1840" alt="8  Confluent cluster IaC API Keys" src="https://github.com/user-attachments/assets/7c775396-08b3-4dcc-a9ec-8f757d1bfa5b" />

9. `terraform destroy` to bring it all down.
<img width="1840" alt="9  Terraform destroy to bring it all down" src="https://github.com/user-attachments/assets/67e9887e-481e-4170-bad6-9d7a327afd6d" />

## 🛝 More Examples to reference for more advanced/custom stuff

https://github.com/confluentinc/terraform-provider-confluent/tree/master/examples/configurations
