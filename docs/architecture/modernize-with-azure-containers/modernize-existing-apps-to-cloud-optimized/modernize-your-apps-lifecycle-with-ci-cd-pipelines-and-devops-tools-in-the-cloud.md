---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulamanızın yaşam döngüsünü modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: 75ac3fa06f442570a0a5043a88409b3fdebb5810
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318561"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme

Günümüzde işletmelerin Market 'te rekabet etmek için hızlı bir hızla yenilik yapın gerekir. Yüksek kaliteli, modern uygulamalar sunma, bu sabit yenilik döngüsünü uygulamak için kritik olan DevOps araçları ve işlemleri gerektirir. Geliştiriciler doğru DevOps araçlarıyla sürekli dağıtımı kolaylaştırabilir ve yenilikçi uygulamaları kullanıcılara daha hızlı bir şekilde alabilir.

Sürekli tümleştirme ve dağıtım uygulamaları iyi şekilde kurulabilse de, kapsayıcıların tanıtımı özellikle çok Kapsayıcılı uygulamalarla çalışırken yeni hususlar sağlar.

Azure DevOps Services, çok Kapsayıcılı uygulamaların, resmi Azure DevOps Services dağıtım görevleri aracılığıyla çeşitli ortamlara sürekli tümleştirmeyi ve dağıtılmasını destekler:

- [Azure Kapsayıcılar için Web App dağıtma](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Azure Kubernetes hizmetine dağıtma](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ancak, komut dosyası tabanlı görevleri Azure DevOps Services kullanarak [Docker Sısınma](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya DC/OS 'a da dağıtabilirsiniz.

Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme ve test aşamasına dağıtım deneyimleri sağlar.

Şekil 4-12 Azure Container Service bir Kubernetes kümesine dağıtan bir sürekli dağıtım işlem hattı gösterir.

![Bir Kubernetes kümesine dağıtmanın Azure DevOps Services ekran görüntüsü.](./media/modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud/deploy-mvc-app-container-kubernetes.png)

**Şekil 4-12.** Azure DevOps Services sürekli dağıtım işlem hattı, bir Kubernetes kümesine dağıtma

>[!div class="step-by-step"]
>[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
>[İleri](migrate-to-hybrid-cloud-scenarios.md)
