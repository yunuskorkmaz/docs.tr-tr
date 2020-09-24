---
title: Üretim Docker ortamlarını yönetme
description: Kapsayıcı tabanlı üretim ortamının yönetilmesi için önemli noktaları öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: dbc5f541478410060420f95f32e4ff5291354075
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160651"
---
# <a name="manage-production-docker-environments"></a>Üretim Docker ortamlarını yönetme

Küme yönetimi ve düzenleme, bir grup Konağı denetleme işlemidir. Bu durum, bir kümeden ana bilgisayar ekleme ve kaldırma, konaklardan ve kapsayıcıların geçerli durumu hakkında bilgi almanızı ve işlemlerin başlatılmasına ve durdurulmasına dahil olabilir. Zamanlayıcı 'nın Hizmetleri zamanlamak için kümedeki her bir konağa erişimi olması gerektiğinden, küme yönetimi ve düzenleme zamanlamaya yakın bir şekilde bağlanır. Bu nedenle, aynı araç genellikle her iki amaçla de kullanılır.

## <a name="container-service-and-management-tools"></a>Kapsayıcı hizmeti ve yönetim araçları

Kapsayıcı hizmeti, popüler açık kaynaklı kapsayıcı Kümelemesi ve düzenleme çözümlerinin hızlı dağıtımını sağlar. Uygulama kapsayıcılarınızın tamamen taşınabilir olmasını sağlamak için Docker görüntülerini kullanır. Kapsayıcı hizmeti 'ni kullanarak, bu uygulamaları binlerce (hatta binlerce kapsayıcı) ölçeklendirdiğinizden emin olmak için DC/OS 'yi (Mesosphere ve Apache Mesos tarafından desteklenir) ve Docker Sısınma kümelerini Azure Resource Manager şablonlarıyla veya Azure portal dağıtabilirsiniz.

Bu kümeleri, Azure Sanal Makine Ölçekleme Kümeleri kullanarak dağıtabilirsiniz, böylece kümeler Azure ağ ve depolama sunumlarından yararlanabilir. Kapsayıcı hizmetine erişmek için bir Azure aboneliğine ihtiyacınız vardır. Kapsayıcı hizmeti ile, düzenleme katmanları da dahil olmak üzere uygulama taşınabilirliği sağlarken Azure 'un kurumsal sınıf özelliklerinden yararlanabilirsiniz.

Tablo 6-1, düzenleyicilerinin, zamanlayıcılar ve kümeleme platformuyla ilgili yaygın yönetim araçlarını listeler.

**Tablo 6-1**. Docker yönetim araçları

| Yönetim araçları | Açıklama | İlgili düzenleyiciler |
|------------------|-------------|-----------------------|
| [Kapsayıcılar için Azure Izleyici](/azure/monitoring/monitoring-container-insights-overview) | Azure adanmış Kubernetes yönetim aracı | Azure Kubernetes Services (AKS) |
| [Kubernetes Web Kullanıcı arabirimi (Pano)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes Yönetim Aracı, yerel Kubernetes kümesini izleyebilir ve yönetebilir | Azure Kubernetes Hizmeti (AKS)<br/>Yerel Kubernetes |
| [Service Fabric için Azure portal](/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](/azure/service-fabric/service-fabric-visualizing-your-cluster) | Azure 'da, şirket içi, yerel geliştirme ve diğer bulutlarda Service Fabric kümelerini yönetmeye yönelik çevrimiçi ve masaüstü sürümü | Azure Service Fabric |
| [Kapsayıcı Izleme (Azure Izleyici)](/azure/azure-monitor/insights/containers) | Genel kapsayıcı yönetimi y izleme çözümü. , [Kapsayıcılar Için Azure izleyici](/azure/monitoring/monitoring-container-insights-overview)aracılığıyla Kubernetes kümelerini yönetebilir. | Azure Service Fabric<br/>Azure Kubernetes Hizmeti (AKS)<br/>Mesosphere DC/OS ve diğerleri. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Küme dağıtımı ve yönetimi için başka bir seçenek de Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) , kapsayıcı düzenlemesi ve yüksek düzeyde ölçeklenebilir mikro hizmet uygulamaları oluşturmak için geliştirici programlama modellerini Içeren bir Microsoft mikro hizmet platformudur. Service Fabric, Linux ve Windows kapsayıcılarındaki Docker 'ı destekler ve Windows ve Linux sunucularında çalıştırılabilir.

Service Fabric yönetim araçları aşağıda verilmiştir:

- Küme ile ilgili [Service Fabric işlemleri için Azure Portal](/azure/service-fabric/service-fabric-cluster-creation-via-portal) (oluşturma/güncelleştirme/silme) veya altyapısını yapılandırma (VM 'ler, yük dengeleyici, ağ vb.)

- [Azure Service Fabric Explorer](/azure/service-fabric/service-fabric-visualizing-your-cluster) , Service Fabric kümesinde, görünüm ve uygulama ve hizmetler noktasındaki düğümler/VM 'ler noktasından Öngörüler ve belirli işlemler sağlayan özel bir Web Kullanıcı arabirimi ve masaüstü çok platformlu bir araçtır.

>[!div class="step-by-step"]
>[Önceki](run-microservices-based-applications-in-production.md) 
> [Sonraki](monitor-containerized-application-services.md)
