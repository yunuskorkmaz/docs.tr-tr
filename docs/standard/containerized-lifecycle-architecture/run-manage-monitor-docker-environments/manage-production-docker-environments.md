---
title: Üretim Docker ortamlarını yönetme
description: Bir kapsayıcı tabanlı üretim ortamı yönetmek için önemli noktaları tanışın.
ms.date: 02/15/2019
ms.openlocfilehash: 7d10f670745f8bac1084b8c33c5acde67bac6229
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641068"
---
# <a name="manage-production-docker-environments"></a>Üretim Docker ortamlarını yönetme

Küme yönetimi ve orchestration olduğu bir ana bilgisayar grubunu denetleme işlemi. Bu, ekleme ve konakları konakların ve kapsayıcılar, geçerli durumu hakkında bilgi alma, başlangıç ve işlemleri durdurma bir kümeden kaldırma gerektirebilir. Zamanlayıcı, zamanlama için kümedeki her konak erişimi olması gerektiğinden zamanlama için küme yönetimi ve orchestration yakından bağlıdır. Bu nedenle, aynı aracı genellikle iki amaçlar için kullanılır.

## <a name="container-service-and-management-tools"></a>Kapsayıcı hizmeti ve Yönetim Araçları

Kapsayıcı hizmeti popüler açık kaynak kapsayıcı Kümeleme ve düzenleme çözümlerinin hızlı dağıtımını sağlar. Docker görüntüleri, uygulama kapsayıcılarınızın tamamen taşınabilir olmasını sağlamak için kullanır. Container Service kullanarak DC/OS (Mesosphere ve Apache Mesos tarafından desteklenen) dağıtabilirsiniz ve Docker Swarm kümeleri ile Azure Resource Manager şablonları ya da bu uygulamaları binlerce göre ölçeklendirilebileceğinden emin olmak için Azure portalında — da on binlerce —, kapsayıcıları.

Azure sanal makine ölçek kümeleri'ni kullanarak bu kümeleri dağıtmak ve kümeler Azure ağ ve depolama sunumlarından yararlanın. Kapsayıcı Hizmeti'ne erişmek için bir Azure aboneliğinizin olması gerekir. Container Service ile Azure'un kuruluş düzeyindeki özelliklerinden faydalanırken düzenleme katmanına dahil olmak üzere uygulama taşınabilirliğini, yararlanabilirsiniz.

Tablo 6-1, kendi düzenleyicileri, zamanlayıcılar ve kümeleme platformu ile ilgili genel yönetim araçlarını listeler.

**Tablo 6-1**. Docker Yönetim Araçları

| Yönetim Araçları | Açıklama | İlgili düzenleyicileri |
|------------------|-------------|-----------------------|
| [Kapsayıcılar için Azure İzleyici](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Adanmış Azure Kubernetes yönetim aracı | Azure Kubernetes hizmeti (AKS) |
| [Kubernetes Web UI (dashboard)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes yönetim aracı, izleyebilir ve yerel Kubernetes kümesini yönetme | Azure Kubernetes Service'i (AKS)<br/>Yerel Kubernetes |
| [Service Fabric için Azure portalı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Azure'da, şirket içi, yerel geliştirme ve diğer bulutlarda Service Fabric kümelerini yönetmek için çevrimiçi ve Masaüstü sürümü | Azure Service Fabric |
| [Kapsayıcı (Azure İzleyici) izleme](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Genel kapsayıcı Yönetimi y izleme çözümüdür. Kubernetes kümelerini aracılığıyla yönetebilirsiniz [kapsayıcılar için Azure İzleyici](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service'i (AKS)<br/>Mesosphere DC/OS ve diğerleri. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Başka bir küme dağıtımı ve yönetimi için Azure Service Fabric seçimdir. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) olduğundan kapsayıcı düzenleme ve bunun yanı sıra Geliştirici içeren bir Microsoft mikro hizmet platformu programlama modelleri, yüksek düzeyde ölçeklenebilir bir mikro hizmet uygulamaları oluşturmak için. Service Fabric, Linux ve Windows kapsayıcıları Docker'ı destekler ve Windows ve Linux sunucularını çalıştırabilirsiniz.

Service Fabric araçlarını aşağıda verilmiştir:

- [Service Fabric için Azure portalı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) küme ilgili işlemleri (oluşturma/güncelleştirme/silme) bir küme veya (VM'ler, yük dengeleyici, ağ, vs.) altyapısını yapılandırma

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) özelleştirilmiş web UI ve Öngörüler ve Service Fabric kümesinde düğümler/VM'ler ekler açısından ve uygulama ve Hizmetleri açısından belirli işlemleri sağlayan masaüstü çoklu platform araç.

>[!div class="step-by-step"]
>[Önceki](run-microservices-based-applications-in-production.md)
>[İleri](monitor-containerized-application-services.md)
