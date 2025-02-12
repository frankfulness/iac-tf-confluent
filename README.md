# ☁️ iac-tf-confluent

## 📦 Terraform Confluent Provider:

https://registry.terraform.io/providers/confluentinc/confluent/latest

*Testing during lunch break/after work going through:*

https://registry.terraform.io/providers/confluentinc/confluent/latest/docs/guides/sample-project

## 📈 In 3 broad steps: (WIP)

1. Create trial confluent account, create a service account, assign `OrganizationAdmin` role to the service account, & create a cloud api key for the service account
2. Create resources on confluent cloud via Terraform ($400 to start), be careful because credit card attached in order to get this...
   - an env called `staging`
   - 3 service accounts `app_manager`, `app_producer`, & `app_consumer` with associated kafka key each
   - set permissions for service accounts using role based access conntrol or Access Control Lists, initialize and apply
3. use confluent cli to produce and consume messages from the topic  using the service accs kafka api keys then `DESTROY` all created resources ($)

## 📝 Notes & Findings


