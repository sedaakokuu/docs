---
ms.openlocfilehash: dbc37853f288c92b80e2858c0e94b9a07ca9b60f
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: "145126400"
---
Se o provisionamento do SCIM for implementado para sua organização, qualquer alteração na associação à organização de um usuário deverá ser disparada por meio do provedor de identidade. Se um usuário for convidado para uma organização manualmente em vez de por uma integração existente do SCIM, a conta de usuário dele poderá não ser vinculada corretamente à identidade do SCIM. Isso pode impedir que a conta de usuário seja desprovisionada por meio do SCIM no futuro. Se um usuário for removido manualmente em vez de por uma integração existente do SCIM, uma identidade vinculada obsoleta permanecerá, o que poderá resultar em problemas se o usuário precisar ingressar novamente na organização.
