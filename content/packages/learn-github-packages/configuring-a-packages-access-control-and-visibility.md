---
title: Configuring a package's access control and visibility
intro: 'Choose who has read, write, or admin access to your package and the visibility of your packages on {% data variables.product.prodname_dotcom %}.'
product: '{% data reusables.gated-features.packages %}'
redirect_from:
  - /packages/managing-container-images-with-github-container-registry/configuring-access-control-and-visibility-for-container-images
  - /packages/guides/configuring-access-control-and-visibility-for-container-images
versions:
  fpt: '*'
  ghec: '*'
  ghes: '*'
shortTitle: Access control & visibility
---
{% data reusables.package_registry.container-registry-ghes-beta %}{% ifversion packages-registries-v2 %}

Packages with granular permissions are scoped to a personal account or organization. You can change the access control and visibility of a package separately from the repository that it is connected (or linked) to.

Some registries only support repository-scoped permissions. For the list of these registries, see "[AUTOTITLE](/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

{% else %}A package inherits the permissions and visibility of the repository in which the package is published.{% endif %} For more information about permissions for packages, packages-related scopes for PATs, or managing permissions for your actions workflows, see "[AUTOTITLE](/packages/learn-github-packages/about-permissions-for-github-packages)."

{% ifversion packages-registries-v2 %}

## Visibility and access permissions for packages

{% data reusables.package_registry.visibility-and-access-permissions %}

{% endif %}

## Configuring access to packages for your personal account

If you have admin permissions to a package that's scoped to a personal account, you can assign read, write, or admin roles to other users. For more information about these permission roles, see "[Visibility and access permissions for packages](#visibility-and-access-permissions-for-packages)."

If your package is private or internal and scoped to an organization, then you can only give access to other organization members or teams.

{% data reusables.package_registry.package-settings-option %}
1. On the package settings page, click **Invite teams or people** and enter the name, username, or email of the person you want to give access. Teams cannot be given access to a package that is scoped to a personal account.
  ![Container access invite button](/assets/images/help/package-registry/container-access-invite.png)
1. Next to the username or team name, use the "Role" drop-down menu to select a desired permission level.
  {% ifversion packages-delete-with-github-token-api %}![Permission access levels to give to repositories](/assets/images/help/package-registry/package-access-control-options.png){% else %}![Permission access levels to give to repositories](/assets/images/help/package-registry/container-access-control-options.png){% endif %}

The selected users will automatically be given access and don't need to accept an invitation first.

## Configuring access to packages for an organization

If you have admin permissions to a package that is scoped to an organization, you can assign read, write, or admin roles to other users and teams. For more information about these permission roles, see "[Visibility and access permissions for packages](#visibility-and-access-permissions-for-packages)."

If your package is private or internal and scoped to an organization, then you can only give access to other organization members or teams.

{% data reusables.package_registry.package-settings-from-org-level %}
{% data reusables.package_registry.package-settings-option %}
1. On the package settings page, click **Invite teams or people** and enter the name, username, or email of the person you want to give access. You can also enter a team name from the organization to give all team members access.
  ![Container access invite button](/assets/images/help/package-registry/container-access-invite.png)
1. Next to the username or team name, use the "Role" drop-down menu to select a desired permission level.
  {% ifversion packages-delete-with-github-token-api %}![Container access options](/assets/images/help/package-registry/package-access-control-options.png){% else %}![Container access options](/assets/images/help/package-registry/container-access-control-options.png){% endif %}

The selected users or teams will automatically be given access and don't need to accept an invitation first.

{% ifversion packages-registries-v2 %}
## Inheriting access for a package from a repository

For packages scoped to a personal account or an organization, to simplify package management through {% data variables.product.prodname_actions %} workflows, you can enable a package to inherit the access permissions of a repository.

If you inherit the access permissions of the repository where your package's workflows are stored, then you can adjust access to your package through the repository's permissions.

Once a repository is synced, you can't access the package's granular access settings. To customize the package's permissions through the granular package access settings, you must remove the synced repository first.

{% data reusables.package_registry.package-settings-from-org-level %}
{% data reusables.package_registry.package-settings-option %}
2. Under "Repository source", select **Inherit access from repository (recommended)**.
  ![Inherit repo access checkbox](/assets/images/help/package-registry/inherit-repo-access-for-package.png)

## Ensuring workflow access to your package

For packages scoped to a personal account or an organization, to ensure that a {% data variables.product.prodname_actions %} workflow has access to your package, you must give explicit access to the repository where the workflow is stored.

The specified repository does not need to be the repository where the source code for the package is kept. You can give multiple repositories workflow access to a package.

{% note %}

**Note:** Syncing your package with a repository through the **Actions access** menu option is different than connecting your package to a repository. For more information about linking a repository to your package, see "[AUTOTITLE](/packages/learn-github-packages/connecting-a-repository-to-a-package)."

{% endnote %}

### {% data variables.product.prodname_actions %} access for packages scoped to personal accounts 

{% data reusables.package_registry.package-settings-option %}
1. In the left sidebar, click **Actions access**.
  !["Actions access" option in left menu](/assets/images/help/package-registry/organization-repo-access-for-a-package.png)
2. To ensure your workflow has access to your package, you must add the repository where the workflow is stored. Click **Add repository** and search for the repository you want to add.
   !["Add repository" button](/assets/images/help/package-registry/add-repository-button.png)
3. Using the "role" drop-down menu, select the default access level that you'd like the repository to have to your package.
  {% ifversion packages-delete-with-github-token-api %}![Permission access levels to give to repositories](/assets/images/help/package-registry/package-access-control-options.png){% else %}![Permission access levels to give to repositories](/assets/images/help/package-registry/container-access-control-options.png){% endif %}

To further customize access to your package, see "[Configuring access to packages for your personal account](#configuring-access-to-packages-for-your-personal-account)."

### {% data variables.product.prodname_actions %} access for packages scoped to organizations

{% data reusables.package_registry.package-settings-from-org-level %}
{% data reusables.package_registry.package-settings-option %}
1. In the left sidebar, click **Actions access**.
  !["Actions access" option in left menu](/assets/images/help/package-registry/organization-repo-access-for-a-package.png)
2. Click **Add repository** and search for the repository you want to add.
   !["Add repository" button](/assets/images/help/package-registry/add-repository-button.png)
3. Using the "role" drop-down menu, select the default access level that you'd like repository members to have to your package. Outside collaborators will not be included.
  {% ifversion packages-delete-with-github-token-api %}![Permission access levels to give to repositories](/assets/images/help/package-registry/package-access-control-options.png){% else %}![Permission access levels to give to repositories](/assets/images/help/package-registry/container-access-control-options.png){% endif %}

To further customize access to your package, see "[Configuring access to packages for an organization](#configuring-access-to-packages-for-an-organization)."
{% endif %}

{% ifversion fpt or ghec %}
## Ensuring {% data variables.product.prodname_github_codespaces %} access to your package

By default, a codespace can seamlessly access certain packages in registries that support granular permissions, such as packages published in the same repository with the **Inherit access** option selected. For the list of {% data variables.product.prodname_registry %} registries that support granular permissions and seamless {% data variables.product.prodname_github_codespaces %} access, see "[AUTOTITLE](/packages/learn-github-packages/about-permissions-for-github-packages#granular-permissions-for-userorganization-scoped-packages)."

Otherwise, to ensure that a codespace has access to your package, you must grant access to the repository where the codespace is being launched.

The specified repository does not need to be the repository where the source code for the package is kept. You can give codespaces in multiple repositories access to a package.

Once you've selected the package you're interested in sharing with codespaces in a repository, you can grant that repo access.

1. In the right sidebar, click **Package settings**.

   !["Package settings" option in right menu](/assets/images/help/package-registry/package-settings.png)

2. Under "Manage Codespaces access", click **Add repository**.

   !["Add repository" button](/assets/images/help/package-registry/manage-codespaces-access-blank.png)

3. Search for the repository you want to add.

   !["Add repository" button](/assets/images/help/package-registry/manage-codespaces-access-search.png)

4. Repeat for any additional repositories you would like to allow access.

5. If the codespaces for a repository no longer need access to a package, you can remove access.

   !["Remove repository" button](/assets/images/help/package-registry/manage-codespaces-access-item.png)

{% endif %}
## Configuring visibility of packages for your personal account

When you first publish a package that is scoped to your personal account, the default visibility is private and only you can see the package. You can modify a private or public  package's access by changing the access settings.

A public package can be accessed anonymously without authentication. Once you make your package public, you cannot make your package private again.

{% data reusables.package_registry.package-settings-option %}
5. Under "Danger Zone", choose a visibility setting:
    - To make the package visible to anyone, click **Make public**.
    {% warning %}

    **Warning:** Once you make a package public, you cannot make it private again.

    {% endwarning %}
    - To make the package visible to a custom selection of people, click **Make private**.
  ![Container visibility options](/assets/images/help/package-registry/container-visibility-option.png)

## Package creation visibility for organization members

For registries that support granular permissions, you can choose the visibility of packages that organization members can publish by default. For the list of these registries, see "[AUTOTITLE](/packages/learn-github-packages/about-permissions-for-github-packages#granular-permissions-for-userorganization-scoped-packages)."

{% data reusables.profile.access_org %}
{% data reusables.profile.org_settings %}
4. On the left, click **Packages**.
6. Under "Package Creation", choose whether you want to enable the creation of public, private, or internal packages.
    - To enable organization members to create public packages, click **Public**.
    - To enable organization members to create private packages that are only visible to other organization members, click **Private**. You can further customize the visibility of private packages.
    - To enable organization members to create internal packages that are visible to all organization members, click **Internal**. If the organization belongs to an enterprise, the packages will be visible to all enterprise members.

## Configuring visibility of packages for an organization

When you first publish a package, the default visibility is private and only you can see the package. You can grant users or teams different access roles for your package through the access settings.

A public package can be accessed anonymously without authentication. Once you make your package public, you cannot make your package private again.

{% data reusables.package_registry.package-settings-from-org-level %}
{% data reusables.package_registry.package-settings-option %}
5. Under "Danger Zone", choose a visibility setting:
    - To make the package visible to anyone, click **Make public**.
    {% warning %}

    **Warning:** Once you make a package public, you cannot make it private again.

    {% endwarning %}
    - To make the package visible to a custom selection of people, click **Make private**.
  ![Container visibility options](/assets/images/help/package-registry/container-visibility-option.png)
