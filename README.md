**Deploying Terraform with Ansible**

**Fill in the username and password to enable authentication**
** using Cloud environment in this Repo https://github.com/johnbayo/opentelekomcloud_templates.git**
  ```
vim credentials.auto.tfvars
tenant_name = "eu-de"
domain_name = "OTC-EU-DE-00000XXXXXXXXXXXXXXX"
auth_url    = "https://iam.eu-de.otc.t-systems.com:443/v3"
user_name   = "username"
password    = "password"
container   = "e.g. tf-state file name in the OBS service"
key    = "e.g. kms key for the tfstate file"
  ```
**manual execution**
  ```
cd templates
ansible-vault decrypt values.auto.tfvars
terraform init -backend-config=custom_credentials.auto.tfvars
terraform plan
terraform apply
  ```
**ansible execution**
  ```
echo "custom_password" > vault_password
ansible-playbook terraform_apply.yml --vault-password-file=vault_password
  ```
**AWX**
* **integration into AWX is possible**
