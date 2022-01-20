---
title: "Organizations"
weight: -1
sidebarTitle: "Organizations"
description: |
  Organizations allow to manage your Platform.sh projects, users and billing.
---

{{< description >}}

## Manage your organization settings

As an organization owner, you can manage the basic settings for your organization such as its name and URL.

{{< codetabs >}}

---
title=Using the Console
file=none
highlight=false
---

1. Navigate to the organization you want to manage (or a project in it).
1. Open the user menu (your name or profile picture).
1. Click **Settings**.
1. Click **Edit** to edit the label or click in the **Organization URL** field to edit the URL.
1. Click **Save**.

<--->
---
title=Using the CLI
file=none
highlight=false
---

Say you want to change the organization named `acme-corp` with the label to `Great Org` and its URL to `greatest`:

```bash
platform organization:info --org acme label "Great Org" name greatest
```

To verify the changes, run `platform organization:info --org greatest`.

{{< /codetabs >}}

## Manage your organization billing

As an organization owner or an organization user with the **manage billing** permission,
you can access and download invoices and edit billing information such as the stored credit card and billing address.

{{< codetabs >}}

---
title=Using the Console
file=none
highlight=false
---

1. Navigate to the organization you want to manage (or a project in it).
1. Open the user menu (your name or profile picture).
1. Click **Billing**.

{{< /codetabs >}}

## Manage your organization users

As an organization owner or an organization user with the **manage users** permission,
you can invite other users to your organization and grant them the following permissions:

* **Manage plans** (`plans`):
  Add, remove, and edit plans and plan options for your existing projects.
  (Change plan, change storage, change the number of environments, change the number of user licenses)
* **Manage billing** (`billing`):
  Add, remove and edit billing information.
  Access invoices and vouchers.
* **Create projects** (`projects:create`):
  Create new projects within the organization.
* **Manage users** (`members`):
  Add, remove and edit organization-level users and permissions, including your own.

{{< note theme="warning" >}}

A user with the **manage users** (`members`) permission can add, edit, or remove _any_ user's permissions.

{{< /note >}}

{{< codetabs >}}

---
title=Using the Console
file=none
highlight=false
---

1. Navigate to the organization you want to manage (or a project in it).
1. Open the user menu (your name or profile picture).
1. Click **Users**.

<--->
---
title=Using the CLI
file=none
highlight=false
---

Say you want to invite `alice@example.com` with the **Manage users**, **Billing**, **Plans** and **Projects create** permissions to the `acme` organization.

```bash
platform organization:user:add alice@example.com --org=acme --permission=members,billing,plans,projects:create
```

After inviting `alice@example.com`, Alice will receive an invitation email asking to confirm her details and optionally, register for a Platform.sh account.

To update Alice's permissions in your organization, run:

```bash
platform organization:user:update alice@example.com --org=acme --permission=billing
```

This command would remove all previously granted permissions from Alice, and only grant the **Billing** permission.

{{< /codetabs >}}

Users who are a part of an organization can see all projects in that organization at the organization's URL,
which takes the form `https://console.platform.sh/<ORGANIZATION_NAME>`.

They can access only projects where they're an admin or have permissions for at least one environment type.
To see all projects you have access to, from the main console page
click **All projects&nbsp;<span aria-label="and then">></span> All projects**.
For more on access control for projects, see [user administration](./users.md).

## Create a new organization

As a Platform.sh user, when you create a new project, if you do not have an organization, one will be created for you automatically.

However, you can still create a new organization with a different payment method and billing address, and organize your projects the way you want.

{{< codetabs >}}

---
title=Using the Console
file=none
highlight=false
---

1. Navigate to organization menu on the top left of the page.
1. Click **Create a new organization**.
1. Enter the required information (label, URL, country).
1. Click **Save**.

<--->
---
title=Using the CLI
file=none
highlight=false
---

Say you want to create an organization with the label `Acme Corp` and the URL `acme`:

```bash
platform organization:create --label "Acme" --name acme
```

To verify the changes, run `platform organization:info`.

{{< /codetabs >}}

## Delete an existing organization

As an organization owner, and assuming that your organization does not own any remaining project and does not owe any outstanding invoices, you can delete the organization.

{{< codetabs >}}

---
title=Using the Console
file=none
highlight=false
---

1. Navigate to organization menu on the top left of the page.
1. Select the organization you want to delete.
1. Click **Delete the organization**.

<--->
---
title=Using the CLI
file=none
highlight=false
---

Say you want to delete the organization `acme`:

```bash
platform organization:delete --org acme
```

{{< /codetabs >}}

## Transfer project ownership

If you want to transfer a project to a different organization, please submit a support ticket from the current project to ask for the transfer.

This action will automatically transfer the subscription charges to the new organization.
