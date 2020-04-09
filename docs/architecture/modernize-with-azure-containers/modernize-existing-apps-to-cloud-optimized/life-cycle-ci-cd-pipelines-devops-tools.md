---
title: Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Buluttaki CI/CD boru hatları ve DevOps araçlarıyla uygulamanızın yaşam döngüsünü modernize edin
ms.date: 04/30/2018
ms.openlocfilehash: ac2d9a1e9ab432cf69cb3da670fc91c681f802c2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987861"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Bulutta CI/CD işlem hatları ve DevOps araçları ile uygulama yaşam döngüsünü modernleştirme

Günümüzün işletmeleri pazarda rekabetçi olmak için hızlı bir hızda yenilik yapmak gerekir. Yüksek kaliteli, modern uygulamalar sunmak, bu sürekli yenilik döngüsünü uygulamak için kritik öneme sahip DevOps araçları ve süreçleri gerektirir. Doğru DevOps araçlarıyla, geliştiriciler sürekli dağıtımı düzene sokabilir ve yenilikçi uygulamaları kullanıcıların eline daha hızlı bir şekilde aktarabilir.

Sürekli tümleştirme ve dağıtım uygulamaları iyi kurulmuş olsa da, kapsayıcıların başlatılması, özellikle çok kapsayıcılı uygulamalarla çalışırken yeni hususlar sunar.

Azure DevOps Hizmetleri, resmi Azure DevOps Hizmetleri dağıtım görevleri aracılığıyla çoklu kapsayıcı uygulamalarının çeşitli ortamlara sürekli entegrasyonunu ve dağıtımını destekler:

- [Kapsayıcılar için Bir Azure Web Uygulamasına dağıtma](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Azure Kubernetes Service’e dağıtma](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Ancak, Azure DevOps Hizmetleri komut dosyası tabanlı görevleri kullanarak [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) veya DC/OS'ye de dağıtabilirsiniz.

Dağıtım çevikliğini kolaylaştırmaya devam etmek için bu araçlar, geliştirme ve CI/CD çözümleri seçenekleriyle konteyner iş yükleri için mükemmel geliştirme-test-üretim dağıtım deneyimleri sağlar.

Şekil 4-12, Azure Kapsayıcı Hizmeti'nde bir Kubernetes kümesine dağıtılan sürekli bir dağıtım ardışık hattını gösterir.

![Bir Kubernetes kümesine dağıtılatan Azure DevOps Hizmetlerinin ekran görüntüsü.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Şekil 4-12.** Azure DevOps Hizmetleri sürekli dağıtım boru hattı, bir Kubernetes kümesine dağıtım

>[!div class="step-by-step"]
>[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Sonraki](migrate-to-hybrid-cloud-scenarios.md)
