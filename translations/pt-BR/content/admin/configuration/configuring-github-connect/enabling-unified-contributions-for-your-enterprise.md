---
title: Habilitando contribuições unificadas para a sua empresa
shortTitle: Unified contributions
intro: 'Você pode permitir que os usuários incluam o número de contribuições anonimizadas pelo trabalho deles em {% data variables.product.product_location %} nos seus gráficos de contribuição em {% data variables.product.prodname_dotcom_the_website %}.'
redirect_from:
  - /enterprise/admin/guides/developer-workflow/enabling-unified-contributions-between-github-enterprise-and-github-com
  - /enterprise/admin/guides/developer-workflow/enabling-unified-contributions-between-github-enterprise-server-and-github-com
  - /enterprise/admin/developer-workflow/enabling-unified-contributions-between-github-enterprise-server-and-githubcom
  - /enterprise/admin/installation/enabling-unified-contributions-between-github-enterprise-server-and-githubcom
  - /enterprise/admin/configuration/enabling-unified-contributions-between-github-enterprise-server-and-githubcom
  - /admin/configuration/enabling-unified-contributions-between-github-enterprise-server-and-githubcom
  - /admin/configuration/managing-connections-between-github-enterprise-server-and-github-enterprise-cloud/enabling-unified-contributions-between-github-enterprise-server-and-githubcom
  - /admin/configuration/managing-connections-between-your-enterprise-accounts/enabling-unified-contributions-between-your-enterprise-account-and-githubcom
permissions: 'Enterprise owners can enable unified contributions between {% data variables.product.product_location %} and {% data variables.product.prodname_dotcom_the_website %}.'
versions:
  ghes: '*'
  ghae: '*'
type: how_to
topics:
  - Enterprise
  - GitHub Connect
ms.openlocfilehash: af07f30a8f164f6bec3d3c0f44c77181f1e8db7b
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '145096000'
---
{% data reusables.github-connect.beta %}

## Sobre contribuições unificadas

Como proprietário de uma empresa, você pode permitir que os usuários finais enviem contagens de contribuições anônimas pelo trabalho deles de {% data variables.product.product_location %} para seu gráfico de contribuição de {% data variables.product.prodname_dotcom_the_website %}.

Após habilitar {% data variables.product.prodname_unified_contributions %}, antes que os usuários individuais possam enviar contagens de contribuição de {% data variables.product.product_location %} para {% data variables.product.prodname_dotcom_the_website %}, cada usuário também deverá conectar sua conta de usuário em {% data variables.product.product_name %} com uma conta pessoal em {% data variables.product.prodname_dotcom_the_website %}. Para obter mais informações, confira "[Como enviar contribuições corporativas para o seu perfil do {% data variables.product.prodname_dotcom_the_website %}](/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-graphs-on-your-profile/sending-enterprise-contributions-to-your-githubcom-profile)".

{% data reusables.github-connect.sync-frequency %}

Se o proprietário da empresa desabilitar a funcionalidade ou usuários individuais optarem por não conectar a contagem de contribuição de {% data variables.product.product_name %} será excluída em {% data variables.product.prodname_dotcom_the_website %}. Se o usuário reconectar os perfis após desabilitá-los, as contagens de contribuição dos últimos 90 dias serão restauradas.

O {% data variables.product.product_name %} **só** envia a contagem e a origem da contribuição ({% data variables.product.product_name %}) para os usuários conectados. Nenhuma informação sobre a contribuição ou sobre como ela foi feita é enviada.

## Habilitando contribuições unificadas

Antes de habilitar {% data variables.product.prodname_unified_contributions %} em {% data variables.product.product_location %}, você deverá habilitar {% data variables.product.prodname_github_connect %}. Para obter mais informações, confira "[Como gerenciar o {% data variables.product.prodname_github_connect %}](/admin/configuration/configuring-github-connect/managing-github-connect)".

{% ifversion ghes %} {% data reusables.github-connect.access-dotcom-and-enterprise %} {% data reusables.enterprise_site_admin_settings.access-settings %} {% data reusables.enterprise_site_admin_settings.business %} {% data reusables.enterprise-accounts.github-connect-tab %}{% else %}
1. Entre no {% data variables.product.product_location %} e no {% data variables.product.prodname_dotcom_the_website %}.
{% data reusables.enterprise-accounts.access-enterprise %}{% data reusables.enterprise-accounts.github-connect-tab %}{% endif %}
1. Em "Os usuários podem compartilhar contagens de contribuições para o {% data variables.product.prodname_dotcom_the_website %}", clique em **Solicitar acesso**.
  ![Opção Solicitar acesso às contribuições unificadas](/assets/images/enterprise/site-admin-settings/dotcom-ghe-connection-request-access.png){% ifversion ghes %}
2. [Entre](https://enterprise.github.com/login) no site do {% data variables.product.prodname_ghe_server %} para receber instruções adicionais.

Ao solicitar acesso, podemos redirecioná-lo para o site {% data variables.product.prodname_ghe_server %} para verificar os termos de serviço atuais.
{% endif %}
