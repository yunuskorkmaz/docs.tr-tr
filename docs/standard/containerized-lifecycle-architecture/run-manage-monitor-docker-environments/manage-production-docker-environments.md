---
title: Üretim Docker ortamlarını yönetebilir
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72ae92c89ed9b51815016205e20b09fc4dced1e1
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="manage-production-docker-environments"></a>Üretim Docker ortamlarını yönetebilir

Küme yönetimi ve orchestration işlemidir, ana bilgisayar grubunu denetleme. Bu, ekleme ve ana bilgisayarlar ve kapsayıcılar, geçerli durumu hakkında bilgi alma ve başlatma ve işlemleri durdurma bir kümeden konakları kaldırma gerektirebilir. Zamanlayıcı, hizmetleri zamanlamak için kümedeki her ana bilgisayar erişimi olmalıdır çünkü zamanlama için küme yönetimi ve orchestration yakından bağlıdır. Bu nedenle, aynı aracı genellikle iki amaçlar için kullanılır.

## <a name="container-service-and-management-tools"></a>Kapsayıcı hizmeti ve Yönetim Araçları

Kapsayıcı hizmeti popüler açık kaynak kapsayıcı Kümeleme ve düzenleme çözümlerinin hızlı dağıtımını sağlar. Uygulama kapsayıcıları tümüyle taşınabilir olduğundan emin olmak için Docker görüntüleri kullanır. Kapsayıcı hizmetini kullanarak, DC/OS (Mesosphere ve Apache Mesos tarafından desteklenen) dağıtabilirsiniz ve Docker Swarm kümeleri Azure Resource Manager şablonları ya da bu uygulamaları binlerce ölçeklendirebilirsiniz emin olmak için Azure portal ile — bile on binlerce —, kapsayıcı.

Azure sanal makine ölçekleme kümeleri kullanarak bu kümeler dağıtmak ve kümeler Azure ağ ve depolama sunumlarının yararlanın. Kapsayıcı Hizmeti'ne erişmek için bir Azure aboneliği gerekir. Kapsayıcı hizmeti ile Azure Kurumsal düzeyde özelliklerini hala düzenleme katmanları dahil olmak üzere uygulama taşınabilirliği korurken yararlanabilirsiniz.

Tablo 6-1 kendi orchestrators, zamanlayıcılar ve kümeleme platform ilgili genel yönetim araçlarını listeler.

Tablo 6-1: Docker Yönetim Araçları


| Yönetim Araçları      | Açıklama           | İlgili orchestrators |
|-----------------------|-----------------------|-----------------------|
| Kapsayıcı hizmeti\(Azure portalında kullanıcı Arabirimi yönetim) | [Kapsayıcı hizmeti](https://azure.microsoft.com/en-us/services/container-service/) almak bir kolay sağlar şekilde çalışmaya [Azure kümesinde kapsayıcı dağıtma](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) Mesosphere DC/OS, Kubernetes ve Docker Swarm gibi popüler orchestrators göre. <br /><br /> Kapsayıcı hizmeti bu platformlar yapılandırma en iyi duruma getirir. Boyut, ana bilgisayar sayısı ve orchestrator araçları seçimine seçmek yeterlidir ve kapsayıcı hizmeti şey işler. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Docker Evrensel denetim düzlemi\(şirket içi veya Bulut) | [Docker Evrensel denetim düzlemi](https://docs.docker.com/v1.11/ucp/overview/) Docker Kurumsal düzeyde küme yönetimi çözümünden değil. Tüm küme tek bir yerden yönetmenize yardımcı olur. <br /><br /> Docker Evrensel denetim düzlemi Docker Docker Swarm, Docker Evrensel denetim düzlemi ve Docker güvenilen kayıt sağlayan veri merkezi adlı ticari çarpımını bir parçası olarak dahil edilir. <br /><br /> Docker Datacenter veya Azure gibi genel bulut gelen sağlanan içi yüklü olabilir. | Docker Swarm\(kapsayıcı hizmeti tarafından desteklenen) |
| Docker bulut\(Tutum; bulut SaaS olarak da bilinir) | [Docker bulut](https://docs.docker.com/docker-cloud/) orchestration yetenekleri ve Docker kayıt defteri yapı ve test tesis Dockerized uygulama görüntülerde ayarlamak ve ana bilgisayar altyapınızı yönetmenize yardımcı olan araçlar sağlar barındırılan Yönetim Hizmeti (SaaS) ve resimlerinizi somut altyapınızı dağıtmak otomatikleştirmenize yardımcı olmak için dağıtım özellikleri. SaaS Docker bulut hesabınızı altyapınızda kapsayıcı Docker Swarm kümesi çalıştıran hizmeti bağlanabilir. | Docker Swarm\(kapsayıcı hizmeti tarafından desteklenen) |
| Mesosphere Marathon\(şirket içi veya Bulut) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) Mesosphere'nın DC/OS ve Apache Mesos üretim düzeyde kapsayıcı orchestration ve Zamanlayıcı platform içindir. <br /><br /> Mesos ile çalışır (Apache Mesos üzerinde DC/OS tabanlı) uzun süre çalışan denetlemek için hizmetleri ve sağlayan bir [işlemi ve kapsayıcı yönetimi için web kullanıcı Arabirimi](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Bir web kullanıcı Arabirimi yönetim aracı sunar | Mesosphere DC/OS\(üzerinde Apache Mesos dayalı; kapsayıcı hizmeti tarafından desteklenen) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) yönetme, zamanlama ve küme altyapısı yayılır. Bu kapsayıcı merkezli altyapısı sağlayan ana bilgisayarları, kümeler arasında dağıtım, ölçeklendirme ve uygulama kapsayıcıları işlemlerini otomatikleştirmek için bir açık kaynak platformudur. | Google Kubernetes\(kapsayıcı hizmeti tarafından desteklenen) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Başka bir küme dağıtımı ve yönetimi için Azure Service Fabric seçimdir. [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) olduğu Geliştirici yanı sıra kapsayıcı orchestration içeren bir Microsoft mikro platform programlama modeli yüksek düzeyde ölçeklenebilir mikro uygulamaları oluşturmak için. Service Fabric olarak geçerli Linux Önizleme sürümlerinde, Docker destekleyen [Service Fabric Önizleme Linux'ta](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)ve Windows kapsayıcıları için [sonraki sürümdeki](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric yönetim araçları şunlardır:

-   [Service Fabric için Azure portalı](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) küme ilgili işlemleri (oluşturma/güncelleştirme/silme) bir küme veya kendi altyapısını (VM'ler, yük dengeleyici, ağ, vs.) yapılandırma

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) Öngörüler ve belirli işlemleri Service Fabric kümesindeki düğümler/VMs açısından ve açısından uygulama ve hizmetleri sağlayan bir özel web kullanıcı Arabirimi aracıdır.


>[!div class="step-by-step"]
[Önceki] (run-microservices-based-applications-in-production.md) [sonraki] (İzleyicisi-kapsayıcılı-uygulama-services.md)
