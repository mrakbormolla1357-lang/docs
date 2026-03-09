Disabling OAuth app access restrictions for your organization

Organization owners can disable restrictions on the OAuth apps that have access to the organization's resources.

> \[!WARNING]
> When you disable OAuth app access restrictions for your organization, any organization member will automatically authorize OAuth app access to the organization's private resources when they approve an application for use in their personal account settings.

1. In the upper-right corner of GitHub, click your profile picture, then click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-organization" aria-label="organization" role="img"><path d="M1.75 16A1.75 1.75 0 0 1 0 14.25V1.75C0 .784.784 0 1.75 0h8.5C11.216 0 12 .784 12 1.75v12.5c0 .085-.006.168-.018.25h2.268a.25.25 0 0 0 .25-.25V8.285a.25.25 0 0 0-.111-.208l-1.055-.703a.749.749 0 1 1 .832-1.248l1.055.703c.487.325.779.871.779 1.456v5.965A1.75 1.75 0 0 1 14.25 16h-3.5a.766.766 0 0 1-.197-.026c-.099.017-.2.026-.303.026h-3a.75.75 0 0 1-.75-.75V14h-1v1.25a.75.75 0 0 1-.75.75Zm-.25-1.75c0 .138.112.25.25.25H4v-1.25a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v1.25h2.25a.25.25 0 0 0 .25-.25V1.75a.25.25 0 0 0-.25-.25h-8.5a.25.25 0 0 0-.25.25ZM3.75 6h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 3.75A.75.75 0 0 1 3.75 3h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 3.75Zm4 3A.75.75 0 0 1 7.75 6h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 7 6.75ZM7.75 3h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5ZM3 9.75A.75.75 0 0 1 3.75 9h.5a.75.75 0 0 1 0 1.5h-.5A.75.75 0 0 1 3 9.75ZM7.75 9h.5a.75.75 0 0 1 0 1.5h-.5a.75.75 0 0 1 0-1.5Z"></path></svg> Organizations**.
2. Next to the organization, click **Settings**.
3. In the "Third-party Access" section of the sidebar, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-person" aria-label="person" role="img"><path d="M10.561 8.073a6.005 6.005 0 0 1 3.432 5.142.75.75 0 1 1-1.498.07 4.5 4.5 0 0 0-8.99 0 .75.75 0 0 1-1.498-.07 6.004 6.004 0 0 1 3.431-5.142 3.999 3.999 0 1 1 5.123 0ZM10.5 5a2.5 2.5 0 1 0-5 0 2.5 2.5 0 0 0 5 0Z"></path></svg> OAuth app policy**.
4. Click **Remove restrictions**.
5. After you review the information about disabling third-party application restrictions, click **Yes, remove application restrictions**.---
title: About OAuth app access restrictions
intro: 'Organizations can choose which {% data variables.product.prodname_oauth_apps %} have access to their repositories and other resources by enabling {% data variables.product.prodname_oauth_app %} access restrictions.'
redirect_from:
  - /articles/about-third-party-application-restrictions
  - /articles/about-oauth-app-access-restrictions
  - /github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions
  - /organizations/restricting-access-to-your-organizations-data/about-oauth-app-access-restrictions
versions:
  fpt: '*'
  ghec: '*'
shortTitle: '{% data variables.product.prodname_oauth_app %} restrictions'
---

## About {% data variables.product.prodname_oauth_app %} access restrictions

{% data reusables.apps.oauth-app-access-restrictions %}

{% data reusables.organizations.restricted-app-access-requests %}

Even if you restrict {% data variables.product.prodname_oauth_apps %} access in your organization, users can still authorize privileged {% data variables.product.prodname_oauth_apps %} and use them to access data from the organization. For more information, see [AUTOTITLE](/apps/oauth-apps/using-oauth-apps/privileged-oauth-apps).

{% data reusables.organizations.oauth_app_restrictions_default %}

> [!WARNING]
> When an organization has not set up {% data variables.product.prodname_oauth_app %} access restrictions, any {% data variables.product.prodname_oauth_app %} authorized by an organization member can also access the organization's private resources.

{% ifversion fpt %}
To further protect your organization's resources, you can upgrade to {% data variables.product.prodname_ghe_cloud %}, which includes security features like SAML single sign-on. {% data reusables.enterprise.link-to-ghec-trial %}
{% endif %}

## Setting up {% data variables.product.prodname_oauth_app %} access restrictions

When an organization owner sets up {% data variables.product.prodname_oauth_app %} access restrictions for the first time:

* **Applications that are owned by the organization** are automatically given access to the organization's resources.
* **{% data variables.product.prodname_oauth_apps %}** immediately lose access to the organization's resources.
* **SSH keys created before February 2014** immediately lose access to the organization's resources (this includes user and deploy keys).
* **SSH keys created by {% data variables.product.prodname_oauth_apps %} during or after February 2014** immediately lose access to the organization's resources.
* **Hook deliveries from private organization repositories** will no longer be sent to unapproved {% data variables.product.prodname_oauth_apps %}.
* **API access** to private organization resources is not available for unapproved {% data variables.product.prodname_oauth_apps %}. In addition, there are no privileged create, update, or delete actions on public organization resources.
* **Hooks created by users and hooks created before May 2014** will not be affected.
* **Private forks of organization-owned repositories** are subject to the organization's access restrictions.

## Resolving SSH access failures

When an SSH key created before February 2014 loses access to an organization with {% data variables.product.prodname_oauth_app %} access restrictions enabled, subsequent SSH access attempts will fail. Users will encounter an error message directing them to a URL where they can approve the key or upload a trusted key in its place.

## Webhooks

When an {% data variables.product.prodname_oauth_app %} is granted access to the organization after restrictions are enabled, any pre-existing webhooks created by that {% data variables.product.prodname_oauth_app %} will resume dispatching.

When an organization removes access from a previously-approved {% data variables.product.prodname_oauth_app %}, any pre-existing webhooks created by that application will no longer be dispatched (these hooks will be disabled, but not deleted).

## Re-enabling access restrictions

If an organization disables {% data variables.product.prodname_oauth_app %} access application restrictions, and later re-enables them, previously approved {% data variables.product.prodname_oauth_app %} are automatically granted access to the organization's resources.

## Further reading

* [AUTOTITLE](/organizations/managing-oauth-access-to-your-organizations-data/enabling-oauth-app-access-restrictions-for-your-organization)
* [AUTOTITLE](/organizations/managing-oauth-access-to-your-organizations-data/approving-oauth-apps-for-your-organization)
* [AUTOTITLE](/organizations/managing-programmatic-access-to-your-organization/reviewing-github-apps-installed-in-your-organization)
* [AUTOTITLE](/organizations/managing-oauth-access-to-your-organizations-data/denying-access-to-a-previously-approved-oauth-app-for-your-organization)
* [AUTOTITLE](/organizations/managing-oauth-access-to-your-organizations-data/disabling-oauth-app-access-restrictions-for-your-organization)
* [AUTOTITLE](/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/requesting-organization-approval-for-oauth-apps)
* [AUTOTITLE](/apps/oauth-apps/using-oauth-apps/authorizing-oauth-apps)
