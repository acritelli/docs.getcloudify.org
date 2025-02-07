+++

title = "Get Terraform Blueprints from the Marketplace"
description = "Get Terraform based blueprints from the marketplace"
weight = 28
alwaysopen = false
+++

Getting Started guide to uploading and deploying Terraform based blueprints from the marketplace.

## Prerequisites
* Cloudify Manager Version 6.3 or later
* Cloud Provider Credentials (AWS in this case)


## Overview
In this guide we are going through following steps to upload a blueprint based on terraform from the marketplace and test it.
* Upload the Blueprint to Cloudify Manager
* Test the uploaded blueprint by creating a deployment and installing it

## Step 1 Upload the Blueprint
There are several places where to can enter the Marketplace Terraform section
*  Dashboard -> Run Terraform module button
*  Blueprints Page -> Run Terraform module button
*  Blueprints Page -> Upload button -> upload from the marketplace, select the Terraform tab

Click the upload button, After the upload has finished you will be forwarded to the blueprint's page


![Terraform Marketplace]( /images/trial_getting_started/tf/TtMarketplace.jpg )


## Step 2 Test the blueprint by creating a Deployment and Installing it
* Click The Create Deployment Button
* Review the inputs in the Deployment Creation dialog
* You would be prompted to define The Credentials to the cloud as secrets, those will be propagated to the Terraform Module

![Terraform Marketplace]( /images/trial_getting_started/tf/TtMarketplace.jpg )


## Step 3 Verify the installation.
* Inspect the install workflow execution graph until it will finished, The bars of the execution graph will turn green when operations will finish.
* Review the logs section of the deployment's page
* Click the Deployment info tab and review the outputs section, There you will find the outputs of the terraform module defined in the blueprint


![Terraform Marketplace]( /images/trial_getting_started/tf/TfInstall.jpg )
