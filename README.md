# Generic Alarm Module

This module will setup all generic alarms including required components based on the parameter passed in alarm variable.

## Input parameters:
```
1. alarm        = << available values are listed below >>
1. alarm_prefix = << value to be added in various component names - ex. prod/stage/dev/sdbx >>
```
NB: Max length of alarm prefix is 6 charrecters and should starts with alphabates
### Available values for alarm parameter: 

   1. "S3-ALARM" 
   1. "SG-ALARM" 
   1. "NACL-ALARM" 
   1. "VPC-ALARM" 
   1. "IAM-ALARM" 
   1. "HEALTH-ALARM" 
   1. "CLOUDTRAIL-ALARM" 

## Example:
``` HCL
module "Health" {
  source = "."
  alarm = "HEALTH-ALARM"
  alarm_prefix = "prod"
}
module "IAM-ALARM" {
  source = "."
  alarm = "IAM-ALARM"
  alarm_prefix = "prod"
}
```
If you want to directly run it from git.
``` HCL
module "Health" {
  source = "git::git@github.com:wiley/terraform-aft-cloudwatch?ref=v0.0.1"
  alarm = "HEALTH-ALARM"
  alarm_prefix = "${var.prefix}"
}
```
## Output Variables
```
topic_arn
event_rule_name
```
