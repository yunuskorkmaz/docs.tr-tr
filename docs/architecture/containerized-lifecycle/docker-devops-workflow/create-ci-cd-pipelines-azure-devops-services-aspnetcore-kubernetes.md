---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295780"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Azure DevOps Services içinde Kapsayıcılar üzerindeki bir .NET Core 2.0 uygulaması için CI/CD işlem hatları oluşturma ve bir Kubernetes kümesine dağıtma

Şekil 5-12'de kod yönetimi, kod derleme, Docker görüntüleri oluşturma, Docker görüntüleri ve son olarak Azure'daki bir Kubernetes kümesine dağıtımı kapsayan uçdan uca DevOps senaryosunu görebilirsiniz.

![İş akışı: Geliştirme makinesinde başlar. Repo'ya itme, Docker kayıt defterine itilen özel bir görüntü kullanarak yapı/CI görevine başlar ve ardından CD/deploy görevi tarafından SON olarak AKS'ye iterek kullanılır.](media/docker-workflow-ci-cd-aks.png)

**Şekil 5-12**. Docker görüntüleri oluşturma ve Azure'daki bir Kubernetes kümesine dağıtma CI/CD senaryosu

Yapı/CD ve sürüm/CD olmak üzere iki boru hattının Docker Registry (Docker Hub veya Azure Konteyner Kayıt Defteri gibi) aracılığıyla bağlandığı vurgulanması önemlidir. Docker kayıt defteri, Docker olmadan geleneksel CI/CD sürecine kıyasla en önemli farklardan biridir.

Şekil 5-13'te gösterildiği gibi, ilk aşama yapı/CI boru hattıdır. Azure DevOps Hizmetleri'nde kodu derleyecek, Docker görüntülerini oluşturacak ve docker hub veya Azure Konteyner Kayıt Defteri gibi docker registry'ye itecek yapı/CI ardışık hatları oluşturabilirsiniz.

![Azure DevOps tarayıcı görünümü, Oluşturma işlemi görev tanımı.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Şekil 5-13**. Azure DevOps'lerde Docker görüntüleri oluşturma ve görüntüleri Docker kayıt defterine itme de geliştirme/CI ardışık

İkinci aşama bir dağıtım/sürüm ardışık hattı oluşturmaktır. Azure DevOps Hizmetlerinde, Şekil 5-14'te gösterildiği gibi Azure DevOps Hizmetleri için Kubernetes görevlerini kullanarak bir Kubernetes kümesini hedefleyen bir dağıtım ardışık hattı kolayca oluşturabilirsiniz.

![Azure DevOps tarayıcı görünümü, Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Şekil 5-14**. Bir Kubernetes kümesine dağıtılan Azure DevOps Hizmetleri'nde sürüm/CD ardışık

> [! Walkthrough] Kubernetes için eShopModernized dağıtma:
>
> Azure DevOps CI/CD ardışık birimlerinin Kubernetes'e dağıtışlarını ayrıntılı bir şekilde gözden geçirmek için aşağıdaki yazıya bakın: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Önceki](docker-application-outer-loop-devops-workflow.md)
>[Sonraki](../run-manage-monitor-docker-environments/index.md)
