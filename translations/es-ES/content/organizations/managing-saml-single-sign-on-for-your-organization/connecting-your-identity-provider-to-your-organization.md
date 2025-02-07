---
title: Conectar tu proveedor de identidad con tu organización
intro: 'Para usar el inicio de sesión único de SAML y SCIM, debes conectar tu proveedor de identidades con tu organización en {% data variables.product.product_name %}.'
redirect_from:
  - /articles/connecting-your-identity-provider-to-your-organization
  - /github/setting-up-and-managing-organizations-and-teams/connecting-your-identity-provider-to-your-organization
versions:
  ghec: '*'
topics:
  - Authentication
  - Organizations
  - Teams
shortTitle: Connect an IdP
ms.openlocfilehash: fe20822b6f3381b6cdc6dbf844c84a93d8d4ea0f
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145126208'
---
## Acerca de la conexión del IdP a la organización

Cuando habilitas el SSO de SAML para tu organización de {% data variables.product.product_name %}, conectas tu proveedor de identidad (IdP) a ella. Para más información, vea ["Habilitación y prueba del inicio de sesión único de SAML para la organización](/organizations/managing-saml-single-sign-on-for-your-organization/enabling-and-testing-saml-single-sign-on-for-your-organization)".

{% data reusables.saml.ghec-only %}

Puedes encontrar los detalles de implementación de SAML y de SCIM para tu IdP en la documentación de este.
- Active Directory Federation Services (AD FS): [SAML](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services)
- Azure Active Directory (Azure AD): [SAML](https://docs.microsoft.com/azure/active-directory/active-directory-saas-github-tutorial) y [SCIM](https://docs.microsoft.com/azure/active-directory/active-directory-saas-github-provisioning-tutorial)
- Okta: [SAML](http://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Github-com.html) y [SCIM](http://developer.okta.com/standards/SCIM/)
- OneLogin: [SAML](https://onelogin.service-now.com/support?id=kb_article&sys_id=2929ddcfdbdc5700d5505eea4b9619c6) y [SCIM](https://onelogin.service-now.com/support?id=kb_article&sys_id=5aa91d03db109700d5505eea4b96197e)
- PingOne: [SAML](https://support.pingidentity.com/s/marketplace-integration/a7i1W0000004ID3QAM/github-connector)
- Shibboleth: [SAML](https://wiki.shibboleth.net/confluence/display/IDP30/Home)

{% note %}

**Nota:** Los proveedores de identidad de {% data variables.product.product_name %} admitidos para SCIM son Azure AD, Okta y OneLogin. Para obtener más información sobre SCIM, consulta "[Acerca de SCIM para las organizaciones](/organizations/managing-saml-single-sign-on-for-your-organization/about-scim-for-organizations)".

{% data reusables.scim.enterprise-account-scim %} 

{% endnote %}

## Metadatos SAML

Para obtener más información sobre los metadatos de SAML para la organización, consulta "[Referencia de configuración de SAML](/admin/identity-and-access-management/using-saml-for-enterprise-iam/saml-configuration-reference)".
