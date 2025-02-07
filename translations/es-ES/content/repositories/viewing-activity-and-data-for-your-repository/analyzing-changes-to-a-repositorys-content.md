---
title: Analizar cambios en el contenido de un repositorio
intro: 'Puedes ver los cambios en el contenido de un repositorio al analizar las confirmaciones del repositorio, la frecuencia de confirmación, y las incorporaciones y eliminaciones de contenido.'
product: '{% data reusables.gated-features.repository-insights %}'
redirect_from:
  - /articles/visualizing-additions-and-deletions-to-content-in-a-repository
  - /github/visualizing-repository-data-with-graphs/visualizing-additions-and-deletions-to-content-in-a-repository
  - /articles/viewing-commit-frequency-in-a-repository
  - /articles/analyzing-changes-to-a-repository-s-content
  - /articles/analyzing-changes-to-a-repositorys-content
  - /articles/visualizing-commits-in-a-repository
  - /github/visualizing-repository-data-with-graphs/visualizing-commits-in-a-repository
  - /github/visualizing-repository-data-with-graphs/analyzing-changes-to-a-repositorys-content
  - /github/visualizing-repository-data-with-graphs/analyzing-changes-to-a-repositorys-content/visualizing-commits-in-a-repository
  - /github/visualizing-repository-data-with-graphs/analyzing-changes-to-a-repositorys-content/visualizing-additions-and-deletions-to-content-in-a-repository
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Repositories
shortTitle: Analyze changes
ms.openlocfilehash: 7b6c9918b5d3de0fbae3b94fb8e90ece694a4076
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145136627'
---
## Ver confirmaciones en un repositorio

Puedes ver todas las confirmaciones realizadas a un repositorio en el último año (excluidas las confirmaciones de fusión) en el gráfico de confirmación.

El gráfico superior muestra las confirmaciones del año completo por semana.

![Gráfico anual de confirmaciones de un repositorio](/assets/images/help/graphs/repo_commit_activity_year_graph.png)

El gráfico inferior muestra la cantidad promedio de confirmaciones por día de la semana para la semana seleccionada.

![Gráfico semanal de confirmaciones de un repositorio](/assets/images/help/graphs/repo_commit_activity_week_graph.png)

### Acceder al gráfico de confirmación

{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.accessing-repository-graphs %}
3. En la barra lateral de la izquierda, haga clic en **Commits** (Confirmaciones).
![Pestaña de confirmaciones](/assets/images/help/graphs/commits_tab.png)

## Ver incorporaciones y eliminaciones del contenido de un repositorio

El gráfico de frecuencia de código muestra las incorporaciones y eliminaciones de contenido de cada semana en el historial de un repositorio.

{% ifversion fpt or ghec %}

![Gráfico de frecuencia de código](/assets/images/help/graphs/repo_code_frequency_graph_dotcom.png)

{% endif %}

### Acceder al gráfico de frecuencia de código

{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.accessing-repository-graphs %}
3. En la barra lateral izquierda, haga clic en **Code frequency** (Frecuencia de código).
![Pestaña de frecuencia de código](/assets/images/help/graphs/code_frequency_tab.png)
