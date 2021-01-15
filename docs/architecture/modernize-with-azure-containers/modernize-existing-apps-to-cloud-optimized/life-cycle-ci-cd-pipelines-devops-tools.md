---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulamanızın yaşam döngüsünü modernleştirin
ms.date: 12/21/2020
ms.openlocfilehash: f8517ebe8570b8d2be7b49c3cb9e1bc436076af2
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235345"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme

Günümüzde işletmelerin Market 'te rekabet etmek için hızlı bir hızla yenilik yapın gerekir. Yüksek kaliteli, modern uygulamalar sunma, bu sabit yenilik döngüsünü uygulamak için kritik olan DevOps araçları ve işlemleri gerektirir. Geliştiriciler doğru DevOps araçlarıyla sürekli dağıtımı kolaylaştırabilir ve yenilikçi uygulamaları kullanıcılara daha hızlı bir şekilde alabilir.

Sürekli tümleştirme ve dağıtım uygulamaları iyi şekilde kurulabilse de, kapsayıcıların tanıtımı özellikle çok Kapsayıcılı uygulamalarla çalışırken yeni hususlar sağlar.

Azure DevOps Services, çok Kapsayıcılı uygulamaların, resmi Azure DevOps Services dağıtım görevleri aracılığıyla çeşitli ortamlara sürekli tümleştirmeyi ve dağıtılmasını destekler:

- [Azure Kapsayıcılar için Web App dağıtma](/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Azure Kubernetes Service’e dağıtma](/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ancak, komut dosyası tabanlı görevleri Azure DevOps Services kullanarak [Docker Sısınma](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) veya DC/OS 'a da dağıtabilirsiniz.

Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme ve test aşamasına dağıtım deneyimleri sağlar.

Şekil 4-12 Azure Container Service bir Kubernetes kümesine dağıtan bir sürekli dağıtım işlem hattı gösterir.

![Bir Kubernetes kümesine dağıtmanın Azure DevOps Services ekran görüntüsü.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Şekil 4-12.** Azure DevOps Services sürekli dağıtım işlem hattı, bir Kubernetes kümesine dağıtma

>[!div class="step-by-step"]
>[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md) 
> [Sonraki](migrate-to-hybrid-cloud-scenarios.md)
