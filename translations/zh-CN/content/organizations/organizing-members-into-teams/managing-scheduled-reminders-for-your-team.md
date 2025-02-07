---
title: 管理团队的预定提醒
intro: 当您的团队有等待审查的拉取请求时，您可以在 Slack 中收到提醒。
redirect_from:
  - /github/setting-up-and-managing-organizations-and-teams/managing-scheduled-reminders-for-pull-requests
  - /github/setting-up-and-managing-organizations-and-teams/managing-scheduled-reminders-for-your-team
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Organizations
  - Teams
shortTitle: Scheduled reminders
ms.openlocfilehash: 3c86b54c527c89409326840e0089a9a05ab9c49a
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '145101309'
---
## 关于团队的预定提醒

{% data reusables.reminders.about-scheduled-reminders-teams-orgs %}

团队维护员和组织所有者可为团队已请求审查的任何拉取请求设置预定提醒。 组织所有者必须先授权您的 Slack 工作区，然后您才可为团队创建预定提醒。 有关详细信息，请参阅“[管理组织的预定提醒](/organizations/managing-organization-settings/managing-scheduled-reminders-for-your-organization)”。

{% data reusables.reminders.scheduled-reminders-limitations %}

## 为团队创建预定提醒
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% data reusables.reminders.scheduled-reminders %} {% data reusables.reminders.add-reminder %} {% data reusables.reminders.authorize-slack %} {% data reusables.reminders.slack-channel %} {% data reusables.reminders.days-dropdown %} {% data reusables.reminders.times-dropdowns %} {% data reusables.reminders.tracked-repos %} {% data reusables.reminders.ignore-drafts %} {% data reusables.reminders.no-review-requests %} {% data reusables.reminders.author-reviews %} {% data reusables.reminders.approved-prs %} {% data reusables.reminders.min-age %} {% data reusables.reminders.min-staleness %} {% data reusables.reminders.ignored-terms %} {% data reusables.reminders.ignored-labels %} {% data reusables.reminders.required-labels %} {% data reusables.reminders.create-reminder %}

## 管理团队的预定提醒
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% data reusables.reminders.scheduled-reminders %} {% data reusables.reminders.edit-existing %} {% data reusables.reminders.edit-page %} {% data reusables.reminders.update-buttons %}

## Deleting a scheduled reminder for a team
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% data reusables.reminders.scheduled-reminders %} {% data reusables.reminders.delete %}

## 延伸阅读

- [管理组织的预定提醒](/organizations/managing-organization-settings/managing-scheduled-reminders-for-your-organization)
- [管理你的计划提醒](/github/setting-up-and-managing-your-github-user-account/managing-your-scheduled-reminders)
