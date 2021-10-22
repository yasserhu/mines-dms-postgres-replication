# terraform-aws-mds-service

Module to migrate databases using AWS Data Migration Service from Postgres in Azure VM to AWS RDS Postgres database

## Sources Required

Source database and target database, in this configuration a VM in Azure and AWS RDS Postgres are pre-configured.

## Providers Requirements

| Name | Version |
|------|---------|
| aws | n/a |
| random | n/a |

## Inputs parameters for DMS Instance, Replication Task, and Endpoints

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| application | Client application | `string` | n/a | yes |
| client | Client name | `string` | n/a | yes |
| connection\_attributes | Connection attributes | `string` | n/a | no |
| dms\_engine\_version | Data migration service engine version | `string` | n/a | yes |
| environment | Environment like dev, staging, prod | `string` | n/a | yes |
| instance\_type | Migration instance type | `string` | n/a | yes |
| publicly\_accessible | True if you want DMS instance to be accessible publicly | `bolean` | n/a | yes |
| replication\_task\_settings | replication task settings | `string` | n/a | yes |
| source\_database\_host | Database host to migrate | `string` | n/a | yes |
| source\_database\_name | Source database | `string` | n/a | yes |
| source\_database\_password | Source database password | `string` | n/a | yes |
| source\_database\_username | Source database user | `string` | n/a | yes |
| source\_engine | Database engine to migrate | `string` | n/a | yes |
| source\_port | Source database port | `string` | n/a | yes |
| ssl\_mode | Enable SSL encryption | `string` | n/a | yes |
| storage\_size | Replication task storage | `number` | `"50"` | no |
| subnets | List of Subnets | `list(string)` | n/a | yes |
| target\_database\_host | Target database host | `string` | n/a | yes |
| target\_database\_name | Target database name | `string` | n/a | yes |
| target\_database\_password | Target database password | `string` | n/a | yes |
| target\_database\_username | Target database user | `string` | n/a | yes |
| target\_engine | Target database engine | `string` | n/a | yes |
| target\_port | Target database port | `string` | n/a | yes |

## For more detail please follow the link below

<https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/dms_replication_instance>

## Data Migration Service Infrastructure

Within DMS you can have multiple combinations of resources depending on your use case. For example (not an exhaustive list of possible combinations):

#### Simple

- One source endpoint
- One target/destination endpoint
- One replication task
- Two event subscriptions
  - Replication instance event subscription
  - Replication task event subscription

<p align="center">
  <img src="https://raw.githubusercontent.com/clowdhaus/terraform-aws-dms/main/.github/images/dms_simple.png" alt="DMS Simple" width="75%">
</p>

## Configuration Outputs

No output.
