---
title: Azure AD を使用して Enterprise の認証とプロビジョニングを設定する
shortTitle: Configure with Azure AD
intro: 'Azure Active Directory (Azure AD) のテナントをアイデンティティプロバイダ (IdP) として使用して、{% data variables.product.product_location %} の認証とユーザプロビジョニングを一元管理できます。'
permissions: 'Enterprise owners can configure authentication and provisioning for an enterprise on {% data variables.product.product_name %}.'
versions:
  ghae: '*'
type: how_to
topics:
  - Accounts
  - Authentication
  - Enterprise
  - Identity
  - SSO
redirect_from:
  - /admin/authentication/configuring-authentication-and-provisioning-for-your-enterprise-using-azure-ad
  - /admin/authentication/configuring-authentication-and-provisioning-with-your-identity-provider/configuring-authentication-and-provisioning-for-your-enterprise-using-azure-ad
  - /admin/identity-and-access-management/configuring-authentication-and-provisioning-with-your-identity-provider/configuring-authentication-and-provisioning-for-your-enterprise-using-azure-ad
ms.openlocfilehash: 6374081e3a0d71238b0ebd84e64575da55ea8e61
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '145116589'
---
## Azure AD を使用した認証とユーザプロビジョニングについて

Azure Active Directory (Azure AD) は、ユーザアカウントと Web アプリケーションへのアクセスを一元管理できる Microsoft のサービスです。 詳細については、Microsoft Docs の「[Azure Active Directory とは](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)」を参照してください。

{% data variables.product.product_name %} のアイデンティティとアクセスを管理するために、Azure AD テナントを認証用の SAML IdP として使用できます。 アカウントを自動的にプロビジョニングし、SCIM でメンバーシップにアクセスするように Azure AD を設定することもできます。これにより、{% data variables.product.prodname_ghe_managed %} ユーザを作成し、Azure AD テナントから Team と Organization のメンバーシップを管理できます。

Azure AD を使用して {% data variables.product.prodname_ghe_managed %} に対して SAML SSO と SCIM を有効にした後、Azure AD テナントから以下を実行できます。

* Azure AD の {% data variables.product.prodname_ghe_managed %} アプリケーションをユーザアカウントに割り当てて、{% data variables.product.product_name %} の対応するユーザアカウントを自動的に作成し、アクセスを許可します。
* {% data variables.product.prodname_ghe_managed %} アプリケーションの Azure AD のユーザアカウントへの割り当てを解除して、{% data variables.product.product_name %} の対応するユーザアカウントを非アクティブ化します。
* {% data variables.product.prodname_ghe_managed %} アプリケーションを Azure AD の IdP グループに割り当てて、IdP グループのすべてのメンバーの {% data variables.product.product_name %} 上のユーザアカウントを自動的に作成し、アクセスを許可します。 さらに、IdP グループは {% data variables.product.prodname_ghe_managed %} で利用でき、Team とその親 Organization に接続できます。
* IdP グループから {% data variables.product.prodname_ghe_managed %} アプリケーションの割り当てを解除して、その IdP グループを介してのみアクセスできるすべての IdP ユーザの {% data variables.product.product_name %} ユーザアカウントを非アクティブ化し、親 Organization からユーザを削除します。 IdP グループは {% data variables.product.product_name %} のどの Team からも切断されます

{% data variables.product.product_location %} でのエンタープライズの ID とアクセスの管理の詳細については、「[Enterprise の ID とアクセスを管理する](/admin/authentication/managing-identity-and-access-for-your-enterprise)」を参照してください。 IdP グループとのチームの同期の詳細については、「[チームを ID プロバイダー グループと同期する](/organizations/organizing-members-into-teams/synchronizing-a-team-with-an-identity-provider-group)」を参照してください。

## 前提条件

Azure AD を使用して {% data variables.product.product_name %} の認証とユーザプロビジョニングを設定するには、Azure AD アカウントとテナントが必要です。 詳細については、[Azure AD Web サイト](https://azure.microsoft.com/free/active-directory)および Microsoft Docs の「[クイックスタート: Azure Active Directory テナントを作成する](https://docs.microsoft.com/azure/active-directory/develop/quickstart-create-new-tenant)」を参照してください。

{% data reusables.saml.assert-the-administrator-attribute %} Azure AD からの SAML 要求に `administrator` 属性を含める方法の詳細については、Microsoft Docs の「[エンタープライズ アプリケーションの SAML トークンで発行された要求のカスタマイズ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-claims-customization)」を参照してください。

{% data reusables.saml.create-a-machine-user %}

## Azure AD を使用して認証とユーザプロビジョニングを設定する

{% ifversion ghae %}

1. Azure AD で、{% data variables.product.ae_azure_ad_app_link %} をテナントに追加し、シングルサインオンを設定します。 詳細については、Microsoft Docs の「[チュートリアル:Azure Active Directory シングル サインオン (SSO) と {% data variables.product.prodname_ghe_managed %} の統合](https://docs.microsoft.com/azure/active-directory/saas-apps/github-ae-tutorial)」を参照してください。

1. {% data variables.product.prodname_ghe_managed %} に、Azure AD テナントの詳細を入力します。

    - {% data reusables.saml.ae-enable-saml-sso-during-bootstrapping %}

    - 別の IdP を使用して {% data variables.product.product_location %} の SAML SSO を既に設定していて、代わりに Azure AD を使用する場合は、設定を編集できます。 詳細については、「[エンタープライズ向けの SAML シングル サインオンの構成](/admin/authentication/configuring-saml-single-sign-on-for-your-enterprise#editing-the-saml-sso-configuration)」を参照してください。

1. {% data variables.product.product_name %} でユーザプロビジョニングを有効化し、Azure AD でユーザプロビジョニングを設定します。 詳細については、「[エンタープライズ向けのユーザー プロビジョニングの構成](/admin/authentication/configuring-user-provisioning-for-your-enterprise#enabling-user-provisioning-for-your-enterprise)」を参照してください。

{% endif %}
