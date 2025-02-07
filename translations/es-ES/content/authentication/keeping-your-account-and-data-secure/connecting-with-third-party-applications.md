---
title: Conectar con aplicaciones de terceros
intro: 'Puedes conectar tu identidad {% data variables.product.product_name %} con aplicaciones de terceros mediante OAuth. Al autorizar una de estas aplicaciones, deberías asegurarte de que confías en la aplicación, revisar quién la desarrolló y revisar los tipos de información a la que desea acceder la aplicación.'
redirect_from:
  - /articles/connecting-with-third-party-applications
  - /github/authenticating-to-github/connecting-with-third-party-applications
  - /github/authenticating-to-github/keeping-your-account-and-data-secure/connecting-with-third-party-applications
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Identity
  - Access management
shortTitle: Third-party applications
ms.openlocfilehash: b8cd20d36926c373116061e211be62701b1bd2f6
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145115050'
---
Cuando una aplicación de terceros desea identificarte mediante tu inicio de sesión de {% data variables.product.product_name %}, verás una página con la información de contacto del programador y una lista de los datos específicos que se han solicitado.

## Contactarse con el programador de la aplicación

Dado que una aplicación está desarrollada por un tercero que no es {% data variables.product.product_name %}, no sabemos exactamente cómo una aplicación usa los datos a los que solicita acceso. Puedes usar la información del programador en la parte superior de la página para contactarte con el administrador de la aplicación si tienes preguntas o inquietudes sobre tu aplicación.

![Información del propietario de {% data variables.product.prodname_oauth_app %}](/assets/images/help/platform/oauth_owner_bar.png)

Si el programador ha elegido suministrarla, el lateral derecho de la página brinda una descripción detallada de la aplicación, así como su sitio web asociado.

![Información de la aplicación OAuth y sitio web](/assets/images/help/platform/oauth_app_info.png)

## Tipos de acceso a la aplicación y datos

Las aplicaciones pueden tener acceso de *lectura* o *escritura* a los datos de {% data variables.product.product_name %}.

- El **acceso de lectura** solo permite que una aplicación *examine los* datos.
- El **acceso de escritura** permite a una aplicación *cambiar* los datos.

### Acerca de los alcances de OAuth

Los *alcances* son grupos de permisos designados que una aplicación puede solicitar para acceder a los datos públicos y no públicos.

Cuando quieres usar una aplicación de terceros que se integra con {% data variables.product.product_name %}, esa aplicación te permite conocer qué tipo de acceso a tus datos serán necesarios. Si otorgas acceso a la aplicación, la aplicación podrá realizar acciones en tu nombre, como leer o modificar datos. Por ejemplo, si quiere usar una aplicación que solicita el ámbito `user:email`, la aplicación tendrá acceso de solo lectura a las direcciones de correo electrónico privadas. Para obtener más información, consulte "[Acerca de los alcances de {% data variables.product.prodname_oauth_apps %}](/apps/building-integrations/setting-up-and-registering-oauth-apps/about-scopes-for-oauth-apps)".

{% tip %}

**Nota:** Actualmente, no se puede definir el alcance del acceso al código fuente como de solo lectura.

{% endtip %}

### Tipos de datos solicitados

Existen varios tipos de datos que las aplicaciones pueden solicitar.

![Detalles de acceso a OAuth](/assets/images/help/platform/oauth_access_types.png)

{% tip %}

**Sugerencia:** {% data reusables.user-settings.review_oauth_tokens_tip %}

{% endtip %}

| Tipo de datos | Descripción |
| --- | --- |
| Estado de confirmación | Puedes otorgar acceso a una aplicación de terceros para que informe tu estado de confirmación. El acceso al estado de confirmación permite que las aplicaciones determinen si una construcción es exitosa frente a una confirmación específica. Las aplicaciones no tendrán acceso al código, pero <em>podrán</em> leer y escribir la información del estado de una confirmación específica. |
| Implementaciones | El acceso a los estados de despliegue les permite a las aplicaciones determinar si un despliegue es exitoso contra una confirmación específica para un repositorio. Las aplicaciones no tendrán acceso a tu código. |
| Gists | El acceso a [gists](https://gist.github.com) permite a las aplicaciones leer o escribir en {% ifversion not ghae %}tanto en gists públicos como{% else %}tanto en gists internos como{% endif %} secretos. |
| Enlaces | El acceso a [webhooks](/webhooks) permite a las aplicaciones leer o escribir configuraciones de enlace en repositorios que usted administra. |
| Notificaciones | El acceso a las notificaciones permite a las aplicaciones leer tus notificaciones de {% data variables.product.product_name %}, tales como los comentarios sobre las propuestas y las solicitudes de cambios. Sin embargo, las aplicaciones permanecen inhabilitadas para acceder a tus repositorios. |
| Las organizaciones y los equipos | El acceso a organizaciones y equipos permite que las apps accedan y administren la membresía de la organización y del equipo. |
| Datos de usuario personales | Entre los datos del usuario se incluye información que se encuentra en tu perfil de usuario, como tu nombre, dirección de correo electrónico y ubicación. |
| Repositorios | La información del repositorio incluye los nombres de los colaboradores, las ramas que creaste y los archivos actuales dentro de tu repositorio. Una aplicación puede solicitar acceso a todos tus repositorios en cualquier nivel de visibilidad. Para más información, vea "[Acerca de los repositorios](/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility)". |
| Eliminación de repositorio | Las aplicaciones pueden solicitar la eliminación de los repositorios que administras,, pero no tendrán acceso a tu código. |

## Solicitar permisos actualizados

Las aplicaciones pueden solicitar nuevos privilegios de acceso. Al solicitar permisos actualizados, la aplicación te notificará de las diferencias.

![Cambiar el acceso a aplicaciones de terceros](/assets/images/help/platform/oauth_existing_access_pane.png)
