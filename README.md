# ACME Shop: Payment Provider Sandbox

Stand-in for the external payment service provider (PSP) in non-production accounts. Deployed to dev and staging only, never to production.

- Component: `payment-provider-sandbox` (service, experimental)
- Owner: **partner-integrations-team**
- System: `payments`

## Origin and license

This repository is derived from [aws-samples/aws-serverless-ecommerce-platform](https://github.com/aws-samples/aws-serverless-ecommerce-platform) at commit [`3b9ef36`](https://github.com/aws-samples/aws-serverless-ecommerce-platform/tree/3b9ef36dd3e338c8ab697c2bcb1b672e064e303c), split out of that monorepo with its commit history and modified as listed below. Original code: Copyright 2019 Amazon.com, Inc. or its affiliates, licensed under MIT-0 (see [LICENSE](LICENSE)).

ACME Retail Group is a fictional company used for demos. This repository is not affiliated with, or endorsed by, Amazon Web Services.

## Changes from upstream

- Split out of the upstream monorepo into one repository per service, with history.
- The shared `ecom` library is installed from [acme-shop-ecom-lib](https://github.com/kaku0/acme-shop-ecom-lib) instead of a relative path.
- SSM-backed template parameters have a `dev` default, so the template can be read on its own.
- `catalog-info.yaml` (Backstage) describes ownership, system, APIs and dependencies.
- SSM parameter names in the CDK stack use template literals instead of string concatenation (same values).

---

# 3rd party payment service

This service simulates a third party backend system.

## API

See [resources/openapi.yaml](resources/openapi.yaml) for a list of available API paths.

## Events

_This service does not emit any event._

## SSM Parameters

This service defines the following SSM parameters:

* `/ecommerce/{Environment}/payment-3p/api/url`: URL for the API Gateway