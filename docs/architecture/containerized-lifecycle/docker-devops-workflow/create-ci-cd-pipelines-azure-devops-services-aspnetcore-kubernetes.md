---
title: Bir Docker uygulaması için dış döngü DevOps iş akışındaki adımlar
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 08/06/2020
ms.openlocfilehash: 1a973407d59484899f99fb6e326b8d7c8e97079b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915215"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Kapsayıcılar üzerinde bir .NET Core uygulaması ve bir Kubernetes kümesine dağıtım için Azure DevOps Services CI/CD işlem hatları oluşturma

Şekil 5-12 ' de, kod yönetimi, kod derleme, Docker görüntüleri oluşturma, Docker görüntüleri bir Docker kayıt defterine gönderme ve son olarak Azure 'daki bir Kubernetes kümesine dağıtım gibi uçtan uca DevOps senaryosunu görebilirsiniz.

![İş akışı: geliştirme makinesinde başlatılır. Bir depoya gönderim, bir Docker kayıt defterine gönderilen özel bir görüntü kullanarak Build/CI görevine başlar ve ardından CD/dağıt görevi tarafından, son olarak AKS 'ye itilmiş olarak kullanılır.](media/docker-workflow-ci-cd-aks.png)

**Şekil 5-12**. Azure 'da Docker görüntüleri oluşturma ve bir Kubernetes kümesine dağıtma CI/CD senaryosu

İki işlem hattı, derleme/CI ve yayın/CD 'nin Docker kayıt defteri (Docker Hub veya Azure Container Registry gibi) aracılığıyla bağlandığını vurgulamak önemlidir. Docker kayıt defteri, Docker olmadan geleneksel bir CI/CD işlemine kıyasla ana farklardan biridir.

Şekil 5-13 ' de gösterildiği gibi, ilk aşama Build/CI ardışık düzeni olur. Azure DevOps Services, kodu derlemek, Docker görüntülerini oluşturmak ve bunları Docker Hub veya Azure Container Registry gibi bir Docker kayıt defterine göndermek için derleme/CI işlem hatları oluşturabilirsiniz.

![Azure DevOps 'un tarayıcı görünümü, derleme işlemi görev tanımı.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Şekil 5-13**. Azure DevOps 'daki derleme/CI işlem hattı Docker görüntülerini oluşturma ve görüntüleri bir Docker kayıt defterine iletme

İkinci aşama, bir dağıtım/yayın işlem hattı oluşturmaktır. Azure DevOps Services, Şekil 5-14 ' de gösterildiği gibi, Azure DevOps Services için Kubernetes görevlerini kullanarak bir Kubernetes kümesini hedefleyen bir dağıtım işlem hattını kolayca oluşturabilirsiniz.

![Azure DevOps tarayıcı görünümü, Kubernetes görev tanımına dağıtın.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Şekil 5-14**. Bir Kubernetes kümesine dağıtma Azure DevOps Services içindeki yayın/CD işlem hattı

> [! İzlenecek yol] Kubernetes 'e Eshopmodernıtes dağıtma:
>
> Kubernetes 'e dağıtan Azure DevOps CI/CD işlem hatları hakkında ayrıntılı bir anlatım için şu gönderiyi inceleyin: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Önceki](docker-application-outer-loop-devops-workflow.md) 
> [Sonraki](../run-manage-monitor-docker-environments/index.md)
