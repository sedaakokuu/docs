---
title: 查看仓库中的分支
intro: '分支是 {% data variables.product.product_name %} 上协作的中心，查看分支的最佳途径是分支页面。'
redirect_from:
  - /articles/viewing-branches-in-your-repository
  - /github/administering-a-repository/viewing-branches-in-your-repository
  - /github/administering-a-repository/managing-branches-in-your-repository/viewing-branches-in-your-repository
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Repositories
shortTitle: View branches
ms.openlocfilehash: 286c8eb8c717f5a002db0059e65c416ccc3981e8
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '145129388'
---
{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.navigate-to-branches %}
3. 使用页面顶部的导航可查看特定的分支列表：
    - 你的分支：在具有推送访问权限的存储库中，“你的”视图显示已推送到的所有分支（不包括默认分支），最新分支排在最前 。
    - 活动分支：“活动”视图显示过去三个月内任何人已提交的所有分支，按分支进行排序，最新提交分支排在最前 。
    - 过时分支：“过时”视图显示过去三个月内没有人提交的所有分支，按分支进行排序，最早提交分支排在最前 。 使用此列表确定[要删除的分支](/articles/creating-and-deleting-branches-within-your-repository)。
    - 所有分支：“所有”视图显示默认分支，后跟所有其他分支，按分支进行排序，最新提交分支排在最前 。

4. （可选）使用右上角的搜索字段。 它在分支名称上提供简单、不区分大小写的子字符串搜索。 它不支持任何其他查询语法。

![Atom 仓库的分支页面](/assets/images/help/branches/branches-overview-atom.png)

## 延伸阅读

- [在存储库中创建和删除分支](/articles/creating-and-deleting-branches-within-your-repository)
- [删除未使用的分支](/articles/deleting-unused-branches)
