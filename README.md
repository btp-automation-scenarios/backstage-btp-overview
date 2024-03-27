# Overview - Backstage, Terraform and SAP BTP

## Overview

This repository acts as a "meta-repository" for the combination of Backstage as Developer Portal, Terraform as Infrastructure as Code and SAP Business Technology Platform (BTP) as the target platform in combination with GitHub Actions as CI/CD tooling.

The details of this setup are described in the blog post [Enable Developers on SAP BTP with Terraform, GitHub Actions and Backstage](https://dev.to/lechnerc77/-enable-developers-on-sap-btp-with-terraform-github-actions-and-backstage-357e) on [dev.to](https://dev.to/).

There is also a short demo video available on YouTube:

<!-- YOUTUBE:START --><table><tr><td><a href="https://www.youtube.com/watch?v=WbNub2urQIY"><img width="100%" src="https://i.ytimg.com/vi/WbNub2urQIY/mqdefault.jpg"></a></td></tr><tr>
<td><a href="https://www.youtube.com/watch?v=WbNub2urQIY">Backstage + GitHub + Terraform + SAP BTP = 🎉</a></td></tr></table><!-- YOUTUBE:END -->

## Repository Structure

### backstage-btp-overview

This repository serves as the entry point foe the Backstage scenario. It contains the links and relations to the other scenarios and also some code snippets for the Backstage configuration in the folder `backstage_config`.

#### Backstage Configuration

You find the snippets for the Backstage configuration in the folder `backstage_config`. The following configurations are provided:

- `app-config.yaml`: Configuration for the Backstage app containing the references to the templates
- `btp-sample-remote`: This folder contains the configuration for the remote template that is used to create new repositories via Backstage (namely <https://github.com/btp-automation-scenarios/backstage-base-btp-template>) and create the infrastructure on SAP BTP via Terraform
- `btp-sample`: This folder contains the configuration for a setup as described in ![Alternative Setup](#alternative-setup) section. 

### backstage-base-btp-template

This is the repository that serves as a template for the creation of new repositories via Backstage. It contains the basic structure and configuration for a Backstage repository that is connected to a GitHub repository and uses GitHub Actions for CI/CD.

Link: <https://github.com/btp-automation-scenarios/backstage-base-btp-template>

### backstage-demo-btp

This is a repository that was created via Backstage following the remote template path. It shows how the created repository based on the `backstage-base-btp-template` repository looks like, especially the templated `catalog-info.yaml` file.

Link: <https://github.com/btp-automation-scenarios/backstage-demo-btp>

### Alternative Setup

I alos played with an alternative way to setup the repositories via Backstage namely copying a repository via a dedicated GitHub Action. The repositories for this setup can be found here:

- [sample-btptf-setup](https://github.com/btp-automation-scenarios/sample-btptf-setup): Blueprint for the repository that is copied
- [backstage-ghactions](https://github.com/btp-automation-scenarios/backstage-ghactions): Repository containing the GH Action that copies the content from the source to the target repository and triggers the GitHub Action to setup the SAP BTP subaccount via Terraform.
