# tf-custom-vpc

This Terraform file is used to created 1 public subnet , 2 private subnet for custom vpc CIDR. 

Below is the set of logs returned during execution aws resource creation. 

[ec2-user@ip-172-31-94-121 tf-custom-vpc]$ terraform init

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/aws...
- Installing hashicorp/aws v4.30.0...
- Installed hashicorp/aws v4.30.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
[ec2-user@ip-172-31-94-121 tf-custom-vpc]$ terraform plan
var.region
  Enter a value: us-east-1


Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.nateIP will be created
  + resource "aws_eip" "nateIP" {
      + allocation_id        = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = (known after apply)
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags_all             = (known after apply)
      + vpc                  = true
    }

  # aws_internet_gateway.IGW will be created
  + resource "aws_internet_gateway" "IGW" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags_all = (known after apply)
      + vpc_id   = (known after apply)
    }

  # aws_nat_gateway.NATgw will be created
  + resource "aws_nat_gateway" "NATgw" {
      + allocation_id        = (known after apply)
      + connectivity_type    = "public"
      + id                   = (known after apply)
      + network_interface_id = (known after apply)
      + private_ip           = (known after apply)
      + public_ip            = (known after apply)
      + subnet_id            = (known after apply)
      + tags_all             = (known after apply)
    }

  # aws_route_table.PrivateRT will be created
  + resource "aws_route_table" "PrivateRT" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + core_network_arn           = ""
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = ""
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = (known after apply)
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "capstone Private Route"
        }
      + tags_all         = {
          + "Name" = "capstone Private Route"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.PublicRT will be created
  + resource "aws_route_table" "PublicRT" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + core_network_arn           = ""
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = (known after apply)
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = ""
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "capstone Public Route"
        }
      + tags_all         = {
          + "Name" = "capstone Public Route"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.PrivateRTassociation will be created
  + resource "aws_route_table_association" "PrivateRTassociation" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.PublicRTassociation will be created
  + resource "aws_route_table_association" "PublicRTassociation" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_subnet.privatesubnets will be created
  + resource "aws_subnet" "privatesubnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.0.192/26"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name" = "capstone private subnet"
        }
      + tags_all                                       = {
          + "Name" = "capstone private subnet"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.publicsubnets will be created
  + resource "aws_subnet" "publicsubnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.0.128/26"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name" = "capstone public subnet"
        }
      + tags_all                                       = {
          + "Name" = "capstone public subnet"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.Main will be created
  + resource "aws_vpc" "Main" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.0.0.0/24"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_classiclink                   = (known after apply)
      + enable_classiclink_dns_support       = (known after apply)
      + enable_dns_hostnames                 = (known after apply)
      + enable_dns_support                   = true
      + id                                   = (known after apply)
      + instance_tenancy                     = "default"
      + ipv6_association_id                  = (known after apply)
      + ipv6_cidr_block                      = (known after apply)
      + ipv6_cidr_block_network_border_group = (known after apply)
      + main_route_table_id                  = (known after apply)
      + owner_id                             = (known after apply)
      + tags                                 = {
          + "Name" = "capstone VPC"
        }
      + tags_all                             = {
          + "Name" = "capstone VPC"
        }
    }

Plan: 10 to add, 0 to change, 0 to destroy.

─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run
"terraform apply" now.
[ec2-user@ip-172-31-94-121 tf-custom-vpc]$ terraform apply
var.region
  Enter a value: us-east-1


Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.nateIP will be created
  + resource "aws_eip" "nateIP" {
      + allocation_id        = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = (known after apply)
      + id                   = (known after apply)
      + instance             = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags_all             = (known after apply)
      + vpc                  = true
    }

  # aws_internet_gateway.IGW will be created
  + resource "aws_internet_gateway" "IGW" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags_all = (known after apply)
      + vpc_id   = (known after apply)
    }

  # aws_nat_gateway.NATgw will be created
  + resource "aws_nat_gateway" "NATgw" {
      + allocation_id        = (known after apply)
      + connectivity_type    = "public"
      + id                   = (known after apply)
      + network_interface_id = (known after apply)
      + private_ip           = (known after apply)
      + public_ip            = (known after apply)
      + subnet_id            = (known after apply)
      + tags_all             = (known after apply)
    }

  # aws_route_table.PrivateRT will be created
  + resource "aws_route_table" "PrivateRT" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + core_network_arn           = ""
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = ""
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = (known after apply)
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "capstone Private Route"
        }
      + tags_all         = {
          + "Name" = "capstone Private Route"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table.PublicRT will be created
  + resource "aws_route_table" "PublicRT" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = [
          + {
              + carrier_gateway_id         = ""
              + cidr_block                 = "0.0.0.0/0"
              + core_network_arn           = ""
              + destination_prefix_list_id = ""
              + egress_only_gateway_id     = ""
              + gateway_id                 = (known after apply)
              + instance_id                = ""
              + ipv6_cidr_block            = ""
              + local_gateway_id           = ""
              + nat_gateway_id             = ""
              + network_interface_id       = ""
              + transit_gateway_id         = ""
              + vpc_endpoint_id            = ""
              + vpc_peering_connection_id  = ""
            },
        ]
      + tags             = {
          + "Name" = "capstone Public Route"
        }
      + tags_all         = {
          + "Name" = "capstone Public Route"
        }
      + vpc_id           = (known after apply)
    }

  # aws_route_table_association.PrivateRTassociation will be created
  + resource "aws_route_table_association" "PrivateRTassociation" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_route_table_association.PublicRTassociation will be created
  + resource "aws_route_table_association" "PublicRTassociation" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # aws_subnet.privatesubnets will be created
  + resource "aws_subnet" "privatesubnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.0.192/26"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name" = "capstone private subnet"
        }
      + tags_all                                       = {
          + "Name" = "capstone private subnet"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_subnet.publicsubnets will be created
  + resource "aws_subnet" "publicsubnets" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-east-1a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.0.128/26"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Name" = "capstone public subnet"
        }
      + tags_all                                       = {
          + "Name" = "capstone public subnet"
        }
      + vpc_id                                         = (known after apply)
    }

  # aws_vpc.Main will be created
  + resource "aws_vpc" "Main" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.0.0.0/24"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_classiclink                   = (known after apply)
      + enable_classiclink_dns_support       = (known after apply)
      + enable_dns_hostnames                 = (known after apply)
      + enable_dns_support                   = true
      + id                                   = (known after apply)
      + instance_tenancy                     = "default"
      + ipv6_association_id                  = (known after apply)
      + ipv6_cidr_block                      = (known after apply)
      + ipv6_cidr_block_network_border_group = (known after apply)
      + main_route_table_id                  = (known after apply)
      + owner_id                             = (known after apply)
      + tags                                 = {
          + "Name" = "capstone VPC"
        }
      + tags_all                             = {
          + "Name" = "capstone VPC"
        }
    }

Plan: 10 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_vpc.Main: Creating...
aws_eip.nateIP: Creating...
aws_eip.nateIP: Creation complete after 1s [id=eipalloc-0b1ada59e755b1ec9]
aws_vpc.Main: Creation complete after 1s [id=vpc-086505608f1f71ed1]
aws_subnet.privatesubnets: Creating...
aws_subnet.publicsubnets: Creating...
aws_internet_gateway.IGW: Creating...
aws_internet_gateway.IGW: Creation complete after 1s [id=igw-0e108d4fa3c5be3c8]
aws_route_table.PublicRT: Creating...
aws_subnet.publicsubnets: Creation complete after 1s [id=subnet-0a9eb7ebd172b212b]
aws_nat_gateway.NATgw: Creating...
aws_subnet.privatesubnets: Creation complete after 1s [id=subnet-08735a605dd0f3f79]
aws_route_table.PublicRT: Creation complete after 1s [id=rtb-03d853c35ae4c24ab]
aws_route_table_association.PublicRTassociation: Creating...
aws_route_table_association.PublicRTassociation: Creation complete after 0s [id=rtbassoc-08dc59813fdae500d]
aws_nat_gateway.NATgw: Still creating... [10s elapsed]
aws_nat_gateway.NATgw: Still creating... [20s elapsed]
aws_nat_gateway.NATgw: Still creating... [30s elapsed]
aws_nat_gateway.NATgw: Still creating... [40s elapsed]
aws_nat_gateway.NATgw: Still creating... [50s elapsed]
aws_nat_gateway.NATgw: Still creating... [1m0s elapsed]
aws_nat_gateway.NATgw: Still creating... [1m10s elapsed]
aws_nat_gateway.NATgw: Still creating... [1m20s elapsed]
aws_nat_gateway.NATgw: Still creating... [1m30s elapsed]
aws_nat_gateway.NATgw: Creation complete after 1m34s [id=nat-00c72df50c3b8ce2b]
aws_route_table.PrivateRT: Creating...
aws_route_table.PrivateRT: Creation complete after 1s [id=rtb-094fb2604912f07fb]
aws_route_table_association.PrivateRTassociation: Creating...
aws_route_table_association.PrivateRTassociation: Still creating... [10s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [20s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [30s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [40s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [50s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m0s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m10s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m20s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m30s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m40s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [1m50s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [2m0s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [2m10s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [2m20s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [2m30s elapsed]
aws_route_table_association.PrivateRTassociation: Still creating... [2m40s elapsed]
aws_route_table_association.PrivateRTassociation: Creation complete after 2m44s [id=rtbassoc-09ada525d317ad831]

Apply complete! Resources: 10 added, 0 changed, 0 destroyed.
