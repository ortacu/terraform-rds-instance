# Module to create RDS instance
## Create a file and add the following
```
module "db" {
source = "./instance"
region = "us-east-2"
subnet_ids = [
"subnet-xxxxxxx", 
"subnet-xxxxxxx", 
"subnet-xxxxxxx"
]
security_group_name = "db"
allowed_hosts = [
"0.0.0.0/0"
]
db_name = "dbname"
engine = "mysql"
engine_version = "5.7"
instance_class = "db.t2.micro"
username = "foo"
password = "foobarbaz"
publicly_accessible = true
}
```

## Create another file output.tf
```
output "region" {
value = "${module.db.region}"
}
output "subnet_list" {
value = "${module.db.subnet_list}"
}
output "allows_hosts" {
value = "${module.db.allowed_hosts}"
}
output "DB_NAME" {
value = "${module.db.DB_NAME}"
}
```

# Run 
```
terraform init 
terraform apply
```
