---
title: github-action-keyless-auth-gcp
tags:
categories:
description:
---

## Introduction

## steps

```sh
# create workload identity pool
gcloud iam workload-identity-pools create github-wif-pool --location="global" --project

# create oidc provider
gcloud iam workload-identity-pools providers create-oidc githubwif \
--location="global" --workload-identity-pool="github-wif-pool"  \
--issuer-uri="https://token.actions.githubusercontent.com" \
--attribute-mapping="attribute.actor=assertion.actor,google.subject=assertion.sub,attribute.repository=assertion.repository" \
--project

# create service account
gcloud iam service-accounts create test-wif \
--display-name="Service account used by WIF POC" \
--project <project_id>

# binding IAM policy
gcloud projects add-iam-policy-binding <project_id> \
--member='serviceAccount:test-wif@<project_id>.iam.gserviceaccount.com' \
--role="roles/compute.viewer"
gcloud iam service-accounts add-iam-policy-binding test-wif@<project_id>.iam.gserviceaccount.com \
--project=<project_id> \
--role="roles/iam.workloadIdentityUser" \
--member="principalSet://iam.googleapis.com/projects/<project_number>/locations/global/workloadIdentityPools/github-wif-pool/attribute.repository/<github user>/<github repo>"
```

ref.

- [github GCP oidc setup](https://medium.com/google-cloud/github-oidc-integration-with-gcp-workload-identity-federation-d75d91d4d7d8)
- <https://cloud.google.com/blog/products/identity-security/enabling-keyless-authentication-from-github-actions>
