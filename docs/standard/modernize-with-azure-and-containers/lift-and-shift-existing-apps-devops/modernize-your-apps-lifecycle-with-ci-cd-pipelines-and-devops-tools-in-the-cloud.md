---
title: "CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c0b87d01c1305695dacaf3ba112b387de2ee0cc1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>CI/CD ardışık düzen ve bulutta DevOps araçları ile uygulama yaşam döngüsü modernize

Günümüzün işletmeler markette rekabetçi olmasını hızlı hızda yenilik gerekir. Yüksek kaliteli teslim etmek, modern uygulamalar gerektirir DevOps araçları ve yenilik sabit bu döngüsünü uygulamak için kritik olan işlemleri. Sağ DevOps araçları ile geliştiriciler sürekli dağıtım kolaylaştırmak ve ellerini yenilikçi uygulamalara kullanıcıların daha hızlı alın.

Sürekli tümleştirme ve dağıtım yöntemleri iyi oluşturulmuş olsa da, özellikle çok kapsayıcı uygulamaları ile çalışırken kapsayıcıları giriş yeni konuları tanıtır.

Visual Studio Team Services sürekli tümleştirme ve resmi Team Services dağıtım görevleri aracılığıyla ortamları çeşitli çok kapsayıcı uygulamalarının dağıtımını destekler:

-   [Tek başına Docker ana VM dağıtmak](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux veya Windows Server 2016 veya üstü)

-   [Service Fabric dağıtma](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Azure kapsayıcı hizmeti – Kubernetes dağıtma](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

Ancak, aynı zamanda dağıtabilirsiniz [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) veya Team Services betik tabanlı görevleri kullanarak DC/OS.

Dağıtım çeviklik kolaylaştırmanın devam etmek için bir geliştirme ve CI/CD çözümleri seçimiyle kapsayıcı iş yükleri için mükemmel geliştirme için-test-için-Üretim dağıtımı karşılaştığında bu araçlar sağlar.

Şekil 4-12 Azure kapsayıcı hizmeti Kubernetes kümede dağıtır sürekli dağıtım ardışık gösterir.

![Visual Studio Team Services sürekli dağıtım ardışık, Kubernetes kümeye dağıtma](./media/image12.png)

> **Şekil 4-12.** Visual Studio Team Services sürekli dağıtım ardışık, Kubernetes kümeye dağıtma

>[!div class="step-by-step"]
[Önceki](modernize-your-apps-with-monitoring-and-telemetry.md)
[sonraki](migrate-to-hybrid-cloud-scenarios.md)
