---
ms.openlocfilehash: 9960ade469b1d52c0f880067e4dd449082b190c6
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: "145092815"
---
Una cola de combinación puede aumentar la velocidad a la que se combinan las solicitudes de incorporación de cambios en una rama de destino muy activa, a la vez que garantiza que se superen todas las comprobaciones de protección de rama necesarias.

Una vez que una solicitud de incorporación de cambios ha superado todas las comprobaciones de protección de rama necesarias, un usuario con acceso de escritura al repositorio puede agregar esa solicitud de incorporación de cambios a una cola de combinación.

Un cola de combinación puede usar {% data variables.product.prodname_actions %}. Para más información, vea "[{% data variables.product.prodname_actions %}](/actions/)".
