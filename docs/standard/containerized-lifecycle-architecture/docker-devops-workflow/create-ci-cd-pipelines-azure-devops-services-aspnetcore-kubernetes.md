---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e11c9ec61ea7d5131595f01ce76b5bb810bb70c0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063309"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Azure DevOps Services içinde Kapsayıcılar üzerindeki bir .NET Core 2.0 uygulaması için CI/CD işlem hatları oluşturma ve bir Kubernetes kümesine dağıtma

Şekil 5-12'de, kod yönetimi, kod derleme kapsayan uçtan uca DevOps senaryo görebilirsiniz, Docker görüntülerinizi oluşturmak, bir Docker kayıt defteri ve son olarak dağıtım için azure'da bir Kubernetes kümesi için Docker görüntüleri gönderin.

![İş akışı: Geliştirme makinesinde başlatılır. Bir deposuna göndermeden bir Docker kayıt defterine gönderilmiştir ve ardından CD/dağıtma görevi, son olarak, AKS için gönderme kullandığı özel bir görüntü kullanarak derleme/CI görevi başlar.](media/docker-workflow-ci-cd-aks.png)

**Şekil 5-12**. CI/CD senaryo Docker görüntülerinizi oluşturmak ve azure'da bir Kubernetes kümesi dağıtma

İki işlem hattı, derleme/CI ve yayın/CD, Docker kayıt defteri (örneğin, Docker Hub veya Azure Container Registry) üzerinden bağlı vurgulamak önemlidir. Docker kayıt defteri, Docker olmadan geleneksel bir CI/CD işlem karşılaştırıldığında temel farklar biridir.

Şekil 5-13'te gösterildiği gibi ilk aşaması derleme/CI işlem hattı ' dir. Azure DevOps Hizmetleri'nde, kodu derlemek, Docker görüntüleri oluşturun ve bunları gibi Docker Hub veya Azure Container Registry'den bir Docker kayıt defterine itme derleme/CI işlem hatları oluşturabilirsiniz.

![Azure DevOps, yapı işlemi Görev tanımı tarayıcı görünümü.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Şekil 5-13**. Azure Docker görüntülerinizi oluşturmak ve bir Docker kayıt defterine görüntü gönderme DevOps derleme/CI işlem hattında

İkinci aşama dağıtımı/yayın işlem hattı oluşturmaktır. Azure DevOps Hizmetleri'nde bir Kubernetes kümesi için Azure DevOps Services, Kubernetes görevlerini kullanarak Şekil 5-14'te gösterildiği gibi hedefleyen bir dağıtım işlem hattı kolayca oluşturabilirsiniz.

![Azure DevOps, tarayıcı görünümünü Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Şekil 5-14**. Azure DevOps Services Kubernetes kümesine dağıtmak, yayın/CD işlem hattı

> [! İzlenecek yol] eShopModernized Kubernetes dağıtımı:
>
> Azure DevOps CI/CD işlem hatları ilişkin ayrıntılı bir kılavuz için Kubernetes dağıtımı yazıya bakın: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Önceki](docker-application-outer-loop-devops-workflow.md)
>[İleri](../run-manage-monitor-docker-environments/index.md)
