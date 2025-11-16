$ nvm use 16
Now using node v16.9.1 (npm v7.21.1)
$ node -v
v16.9.1
$ nvm use 14
Now using node v14.18.0 (npm v6.14.15)
$ node -v
v14.18.0
$ nvm install 12
Now using node v12.22.6 (npm v6.14.5)
$ node -v
v12.22.6---
title: 'Viewing the secret risk assessment report for your organization'
shortTitle: 'View risk report'
intro: 'Understand your organization''s exposure to leaked secrets at a glance by viewing your most recent {% data variables.product.prodname_secret_risk_assessment %} report.'
product: '{% data reusables.gated-features.secret-risk-assessment-report %}'
permissions: '{% data reusables.permissions.secret-risk-assessment-report-generation %}'
allowTitleToDifferFromFilename: true
type: how_to
versions:
  feature: secret-risk-assessment
topics:
  - Code Security
  - Secret scanning
  - Secret Protection
  - Organizations
  - Security
---

{% data reusables.organizations.navigate-to-org %}
{% data reusables.organizations.security-overview %}
{% data reusables.security-overview.open-assessments-view %} You can see the most recent report on this page.
