---
ms.openlocfilehash: 0ee285efb8b386c47d2782151fdf6a2bb24589fc
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: "145111477"
---
1. データ ストアのレプリケーションを開始するには、`ghe-repl-start` コマンドを使います。
  ```shell
  $ ghe-repl-start
  ```
    {% warning %}

    **警告:** `ghe-repl-start` を実行すると、プライマリ サーバーを短時間使えなくなり、その間、ユーザーには内部サーバー エラーが表示されることがあります。 もっとわかりやすいメッセージを表示するには、`ghe-repl-start` をレプリカ ノードで実行する前にプライマリ ノード上で `ghe-maintenance -s` を実行し、アプライアンスをメンテナンス モードにします。 レプリケーションを開始したら、`ghe-maintenance -u` を使ってメンテナンス モードを無効にします。 プライマリ ノードがメンテナンス モードの間、Git レプリケーションは進行しません。

    {% endwarning %}
