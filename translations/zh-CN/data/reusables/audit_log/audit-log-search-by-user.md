---
ms.openlocfilehash: 7193be487b701029df5604b7253f683b5675c086
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: "145098327"
---
### 基于用户搜索

`actor` 限定符可将事件范围限于执行操作的人员。 例如：

  * `actor:octocat` 查找 `octocat` 执行的所有事件。
  * `actor:octocat actor:hubot` 查找 `octocat` 和 `hubot` 执行的所有事件。
  * `-actor:hubot` 排除 `hubot` 执行的所有事件。

请注意，只能使用 {% data variables.product.product_name %} 用户名，而不是个人的真实姓名。
