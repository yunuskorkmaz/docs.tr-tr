---
title: Üretim Docker ortamlarını yönetme
description: Konteyner tabanlı üretim ortamını yönetmek için önemli noktaları tanıyın.
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834499"
---
# <a name="manage-production-docker-environments"></a>Üretim Docker ortamlarını yönetme

Küme yönetimi ve orkestrasyon, bir grup ana bilgisayarını kontrol etme işlemidir. Bu, ana bilgisayarların kümeden eklenmesini ve kaldırılmasını, ana bilgisayarların ve kapsayıcıların geçerli durumu hakkında bilgi almayı ve başlatma ve durdurma işlemlerini içerebilir. Zamanlayıcının hizmetleri zamanlamak için kümedeki her ana bilgisayara erişimi olması gerektiğinden, küme yönetimi ve orkestrasyon zamanlamaya yakından bağlıdır. Bu nedenle, aynı araç genellikle her iki amaç için de kullanılır.

## <a name="container-service-and-management-tools"></a>Konteyner Servis ve yönetim araçları

Konteyner Hizmeti, popüler açık kaynak kapsayıcı kümeleme ve orkestrasyon çözümlerinin hızlı bir şekilde dağıtılmasını sağlar. Uygulama kaplarınızın tamamen taşınabilir olduğundan emin olmak için Docker görüntülerini kullanır. Konteyner Hizmeti'ni kullanarak, bu uygulamaları binlerce (hatta on binlerce kapsayıcıya) ölçeklendirebilmeniz için DC/OS'yi (Mezosphere ve Apache Mesos tarafından desteklenmektedir) ve Docker Swarm kümelerini Azure Kaynak Yöneticisi şablonlarıyla veya Azure portalıyla dağıtabilirsiniz.

Bu kümeleri, Azure Sanal Makine Ölçekleme Kümeleri kullanarak dağıtabilirsiniz, böylece kümeler Azure ağ ve depolama sunumlarından yararlanabilir. Kapsayıcı Hizmetine erişmek için bir Azure aboneliğine ihtiyacınız var. Konteyner Hizmeti ile, düzenleme katmanları da dahil olmak üzere uygulama taşınabilirliğini korurken Azure'un kurumsal düzeydeki özelliklerinden yararlanabilirsiniz.

Tablo 6-1, orkestratörleri, zamanlayıcıları ve kümeleme platformuyla ilgili ortak yönetim araçlarını listeler.

**Tablo 6-1**. Docker yönetim araçları

| Yönetim araçları | Açıklama | İlgili orkestrasyoncular |
|------------------|-------------|-----------------------|
| [Kapsayıcılar için Azure Monitörü](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Azure'a özel Kubernetes yönetim aracı | Azure Kubernetes Hizmetleri (AKS) |
| [Kubernetes Web UI (pano)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes yönetim aracı, yerel Kubernetes kümesini izleyebilir ve yönetebilir | Azure Kubernetes Hizmeti (AKS)<br/>Yerel Kubernetes |
| [Hizmet Kumaşı için Azure portalı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Servis Kumaş Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Azure'da, şirket içinde, yerel geliştirmede ve diğer bulutlarda Service Fabric kümelerini yönetmek için çevrimiçi ve masaüstü sürümü | Azure Service Fabric |
| [Konteyner İzleme (Azure Monitörü)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Genel konteyner yönetimi y izleme çözümü. [Kapsayıcılar için Azure Monitörü](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview)aracılığıyla Kubernetes kümelerini yönetebilirsiniz. | Azure Service Fabric<br/>Azure Kubernetes Hizmeti (AKS)<br/>Mezosfer DC / OS ve diğerleri. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Küme dağıtım ve yönetim için bir diğer seçenek de Azure Hizmet Kumaşı'dır. [Service Fabric,](https://azure.microsoft.com/services/service-fabric/) yüksek ölçeklenebilir mikrohizmetler uygulamaları oluşturmak için konteyner orkestrasyonunun yanı sıra geliştirici programlama modellerini de içeren bir Microsoft mikrohizmet platformudur. Service Fabric, Linux ve Windows Kapsayıcılarında Docker'ı destekler ve Windows ve Linux sunucularında çalıştırılabilir.

Service Fabric yönetim araçları şunlardır:

- [Hizmet Kumaşı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) kümeyle ilgili işlemler için Azure portalı (küme oluşturma/güncelleştirme/silme) veya altyapısını yapılandırma (VM'ler, yük dengeleyicisi, ağ, vb.)

- [Azure Hizmet Kumaş Explorer,](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) düğümler/VM'ler açısından ve uygulama ve hizmetler açısından Hizmet Kumaşı kümesinde öngörüler ve belirli işlemler sağlayan özel bir web Kullanıcı Arabirimi ve masaüstü çok platformlu bir araçtır.

>[!div class="step-by-step"]
>[Önceki](run-microservices-based-applications-in-production.md)
>[Sonraki](monitor-containerized-application-services.md)
