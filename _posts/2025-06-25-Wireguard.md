---
layout: post
title: Wireguard
feature-img:
categories: cloud
tags: [vpn, wireguard, aws, ansible, terraform, iac]
---

How to setup your very own Wireguard VPN on AWS

# Manual PoC


## AWS

### IAM

Before starting we are going to configure our local aws cli.
(screen 1)

Go to IAM.

Create a terraform user with limited rights.

For now lets create a user, then an access key :
Use case : command line interface. ignore the warning, we ll discuss safer access management later on. NOT FOR PROD

run aws configuration

use the aws access key id you just generated
use the aws secret access key you just created
choose your region (visible on your aws console)
default output format : json

# TODO 

detail the user creation process. Explore options, users, identity providers (oidc, token, github options, ...), policies...


### EC2

### Networking


## Wireguard

### Server

### Client

### System

### Scripts


# Automation Bananza

## Terraform

