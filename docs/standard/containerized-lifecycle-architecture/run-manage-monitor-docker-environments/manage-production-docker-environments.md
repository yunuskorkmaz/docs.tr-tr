---
title: Üretim Docker ortamlarını yönetme
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3bafdd9f6a6aa4f850fd28b6315e68c643d1f8c0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202861"
---
# <a name="manage-production-docker-environments"></a>Üretim Docker ortamlarını yönetme

Küme yönetimi ve orchestration olduğu bir ana bilgisayar grubunu denetleme işlemi. Bu, ekleme ve konakları konakların ve kapsayıcılar, geçerli durumu hakkında bilgi alma, başlangıç ve işlemleri durdurma bir kümeden kaldırma gerektirebilir. Zamanlayıcı, zamanlama için kümedeki her konak erişimi olması gerektiğinden zamanlama için küme yönetimi ve orchestration yakından bağlıdır. Bu nedenle, aynı aracı genellikle iki amaçlar için kullanılır.

## <a name="container-service-and-management-tools"></a>Kapsayıcı hizmeti ve Yönetim Araçları

Kapsayıcı hizmeti popüler açık kaynak kapsayıcı Kümeleme ve düzenleme çözümlerinin hızlı dağıtımını sağlar. Docker görüntüleri, uygulama kapsayıcılarınızın tamamen taşınabilir olmasını sağlamak için kullanır. Container Service kullanarak DC/OS (Mesosphere ve Apache Mesos tarafından desteklenen) dağıtabilirsiniz ve Docker Swarm kümeleri ile Azure Resource Manager şablonları ya da bu uygulamaları binlerce göre ölçeklendirilebileceğinden emin olmak için Azure portalında — da on binlerce —, kapsayıcıları.

Azure sanal makine ölçek kümeleri'ni kullanarak bu kümeleri dağıtmak ve kümeler Azure ağ ve depolama sunumlarından yararlanın. Kapsayıcı Hizmeti'ne erişmek için bir Azure aboneliğinizin olması gerekir. Container Service ile Azure'un kuruluş düzeyindeki özelliklerinden faydalanırken düzenleme katmanına dahil olmak üzere uygulama taşınabilirliğini, yararlanabilirsiniz.

Tablo 6-1, kendi düzenleyicileri, zamanlayıcılar ve kümeleme platformu ile ilgili genel yönetim araçlarını listeler.

Tablo 6-1: Docker Yönetim Araçları


| Yönetim Araçları      | Açıklama           | İlgili düzenleyicileri |
|-----------------------|-----------------------|-----------------------|
| Container Service\(Azure portalındaki kullanıcı Arabirimi yönetim) | [Kapsayıcı hizmeti](https://azure.microsoft.com/services/container-service/) almak bir kolayca sağlar şekilde çalışmaya [azure'da kapsayıcı kümesi dağıtma](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) Mesosphere DC/OS, Kubernetes ve Docker Swarm gibi popüler düzenleyicilerle göre. <br /><br /> Kapsayıcı hizmeti bu platformların yapılandırma en iyi duruma getirir. Boyutu, konak sayısını ve istediğiniz düzenleyici araçlarını seçmek yeterlidir ve kapsayıcı hizmeti, diğer her şey yapar. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Docker Evrensel denetim düzlemi\(şirket içi veya Bulut) | [Docker Evrensel denetim düzlemi](https://docs.docker.com/v1.11/ucp/overview/) docker kurumsal sınıf küme yönetimi çözümüdür. Bu, tüm küme tek bir yerden yönetmenize yardımcı olur. <br /><br /> Docker Evrensel denetim düzlemi, adlı Docker Swarm, Docker Evrensel denetim düzlemi ile Docker Trusted Registry sağlayan Docker Datacenter'a ticari ürünün bir parçası olarak dahil edilir. <br /><br /> Docker Datacenter veya Azure gibi genel bir buluttan sağlanan şirket yüklü olabilir. | Docker Swarm\(Container Service tarafından desteklenen) |
| Docker Bulutu\(Tutum; bulut SaaS olarak da bilinir) | [Docker Bulutu](https://docs.docker.com/docker-cloud/) düzenleme özelliklerinden ve bir Docker kayıt defteri derleme ve test olanakları Dockerized uygulama görüntülerini ayarlama ve ana bilgisayar altyapınızı yönetmenize yardımcı olacak araçlar sağlar barındırılan bir yönetim hizmeti (SaaS) ve görüntülerinizi somut altyapınızı dağıtmaya otomatikleştirmenize yardımcı olmak için dağıtım özellikleri. Altyapınızı Container Service'teki Docker Swarm kümesi çalıştıran SaaS Docker Bulutu hesabınıza bağlanabilirsiniz. | Docker Swarm\(Container Service tarafından desteklenen) |
| Mesosphere Marathon\(şirket içi veya Bulut) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) üretim düzeyinde kapsayıcı düzenleme ve Zamanlayıcı platformu mesosphere tarafından sunulan DC/OS ve Apache Mesos içindir. <br /><br /> Mesos ile çalışır (Apache Mesos üzerinde DC/OS tabanlı) uzun süre çalışan denetimine Hizmetleri ve sağlayan bir [işlemi ve kapsayıcı yönetimi için web kullanıcı Arabirimi](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Web kullanıcı Arabirimi yönetim aracını sağlar | Mesosphere DC/OS\(üzerinde Apache Mesos tabanlı; Container Service tarafından desteklenen) |
| Google Kubernetes | [Kubernetes](https://kubernetes.io/docs/user-guide/ui/#dashboard-access) işlemlerini, zamanlama ve küme altyapısı yayılır. Bu kümeleri arasında kapsayıcı merkezli altyapı sağlama konakları, dağıtım, ölçeklendirme ve uygulama kapsayıcıların işlemlerini otomatikleştirmek için bir açık kaynak platformudur. | Google Kubernetes\(Container Service tarafından desteklenen) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Başka bir küme dağıtımı ve yönetimi için Azure Service Fabric seçimdir. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) olduğundan kapsayıcı düzenleme ve bunun yanı sıra Geliştirici içeren bir Microsoft mikro hizmet platformu programlama modelleri, üst düzeyde ölçeklenebilir bir mikro hizmet uygulamaları oluşturmak için. Service Fabric gibi geçerli Linux Önizleme sürümlerinde Docker destekler [Linux üzerinde Service Fabric Önizleme](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)ve Windows kapsayıcıları için [sonraki sürümde](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric araçlarını aşağıda verilmiştir:

-   [Service Fabric için Azure portalı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) küme ilgili işlemleri (oluşturma/güncelleştirme/silme) bir küme veya (VM'ler, yük dengeleyici, ağ, vs.) altyapısını yapılandırma

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) Öngörüler ve Service Fabric kümesinde düğümler/VM'ler ekler açısından ve uygulama ve Hizmetleri açısından belirli işlemleri sağlayan bir özel web kullanıcı Arabirimi aracıdır.


>[!div class="step-by-step"]
[Önceki](run-microservices-based-applications-in-production.md)
[İleri](monitor-containerized-application-services.md)
