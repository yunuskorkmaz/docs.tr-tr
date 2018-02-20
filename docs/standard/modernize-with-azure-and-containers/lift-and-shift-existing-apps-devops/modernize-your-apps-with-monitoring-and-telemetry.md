---
title: "Uygulamalarınızı izleme ve telemetri ile modernize"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulamalarınızı izleme ve telemetri ile modernize"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1535951eb648deab17cf8c2fe64db6ddf7df4cb5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Uygulamalarınızı izleme ve telemetri ile modernize

Üretimde bir uygulamayı çalıştırdığınızda, uygulamanızın nasıl gerçekleştirme hakkında Öngörüler olması önemlidir. Yüksek bir düzeyde çalışıyor? Kullanıcıların hatalarla karşılaşıyor ya da uygulama kararlı ve güvenilir? Zengin performans izleme, güçlü uyarı ve uygulamanızı kullanılabilir ve beklendiği gibi gerçekleştirme olmasına yardımcı olmak için panolar gerekir. Ayrıca, hızlı bir şekilde bir sorun olup olmadığını, kaç tane müşteriler etkilenir ve bulmak ve sorunu düzeltmek için kök neden analizi yapmak belirlemek mümkün olması gerekir.

## <a name="monitor-your-application-with-application-insights"></a>Uygulamanızı Application Insights ile izleme

Application Insights kuran genişletilebilir bir uygulama performansı Yönetimi (APM) hizmetini birden çok platformda çalışan web geliştiricileri için olur. Canlı web uygulamanızı izlemek için kullanın. Application Insights, performans anormalliklerini otomatik olarak algılar. Sorunları tanılamanıza yardımcı ve kullanıcıların gerçekte uygulamanızla ne anlamanıza yardımcı olması için güçlü analytics araçlar içerir. Application Insights sürekli performansını ve kullanımını geliştirmemize yardımcı olmak için tasarlanmıştır. Uygulamalar için çok çeşitli platformlar, .NET, Node.js ve J2EE, olup olmadığı gibi üzerinde çalışır şirket içi barındırılan veya bulutta. Application Insights DevOps işlemlerinizi ile tümleşir ve geliştirme araçları, çeşitli bağlantı noktalarına sahiptir.

Şekil 4-10 Application Insights uygulamanızı nasıl izler ve nasıl bir Pano bu Öngörüler kontrollerinden örneği gösterir.

![Application Insights izleme Panosu](./media/image10.png)

> **Şekil 4-10.** Application Insights izleme Panosu

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Günlük analizi ve kapsayıcı izleme çözümünün ile Docker altyapısını izleme

[Azure günlük analizi](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) parçası olan [izleme çözümüne genel Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Bu bir ayrıca bir hizmet olduğundan [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Günlük analizi bulut izler ve ortamları (OMS şirket içi için) kullanılabilirlik ve performans sağlanmasına yardımcı olmak için şirket içi. Bulut ve şirket içi ortamları ve analiz arasında birden çok kaynak sağlamak için diğer İzleme Araçları'ndan kaynaklar tarafından oluşturulan veri toplar.

Azure altyapı günlükleri ile ilgili olarak, günlük analizi, bir Azure hizmeti diğer Azure hizmetleriyle günlük ve ölçüm verilerini alır (aracılığıyla [Azure İzleyici](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure Vm'leri, Docker kapsayıcıları ve şirket içi veya diğer bulut altyapıları. Günlük analizi esnek günlük arama ve çıkış-yepyeni analytics bu veriler üzerinde sunar. Bu veri kaynakları genelinde çözümlemek için kullanabileceğiniz, karmaşık sorgular tüm günlükleri sağlar ve önceden uyarabilir zengin araçları belirtilen koşullara göre sağlar. Özel veri deposunda burada sorgulamak ve bu görselleştirme Merkezi günlük analizi, hatta toplayabilirsiniz. Ayrıca, hemen güvenlik Öngörüler elde etmek için günlük analizi yerleşik çözümleri avantajlarından ve altyapınızı işlevselliğini alabilir.

Günlük analizi OMS portalı veya herhangi bir tarayıcısında çalıştırmak, Azure portalı erişmek ve, yapılandırma ayarlarını erişimi olan ve birden çok araç çözümlemek ve toplanan verilerde işlem yapmak için sağlayın.

[Kapsayıcı izlemesi çözümü](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) günlük analizi yardımcı olur görüntüleyin ve Docker ve Windows kapsayıcı konaklarınızın tek bir konumda yönetin. Bir çözüm gösterilmektedir hangi kapsayıcılar olan çalışan, hangi kapsayıcı görüntü çalıştırdıkları ve kapsayıcıları çalıştırdığı. Kapsayıcılar ile kullanılan komutları dahil olmak üzere ayrıntılı denetim bilgileri görüntüleyebilirsiniz. Ayrıca, görüntüleme ve Uzaktan Docker ya da Windows ana bilgisayarları görüntülemek gerek kalmadan merkezi günlükleri, arama yaparak kapsayıcıları giderebilirsiniz. Bir ana bilgisayar üzerindeki gürültülü ve alan üst limiti aşan kaynakları olabilir kapsayıcıları bulabilirsiniz. Ayrıca, merkezi CPU, bellek, depolama ve ağ kullanımını ve kapsayıcıları için performans bilgileri görüntüleyebilirsiniz. Windows çalıştıran bilgisayarlarda, merkezileştirme ve Windows Server günlüklerinden karşılaştırmak Hyper-V ve Docker kapsayıcıları. Aşağıdaki kapsayıcı orchestrators çözümünü destekler:

-   Docker Swarm

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

Şekil 4-11 çeşitli kapsayıcı konakları ve aracıları ve OMS arasındaki ilişkileri gösterir.

![Günlük analizi kapsayıcı izlemesi çözümü](./media/image11.png)

> **Şekil 4-11.** Günlük analizi kapsayıcı izlemesi çözümü

Günlük analizi kapsayıcı izleme çözümü kullanabilirsiniz:

-   Konaklarda kapsayıcı tek bir konum hakkında bilgi bakın.

-   Hangi kapsayıcıları olduğunu biliyorsanız, hangi görüntü çalıştırdıkları çalıştırıp nerede çalışıyor.

-   Eylemler için bir denetim izi kapsayıcılarında bakın.

-   Görüntüleme ve Docker ana bilgisayarları için uzaktan oturum açma olmadan merkezi günlükleri arama yaparak sorunlarını giderin.

-   "Gürültülü komşu" olabilir ve bir ana bilgisayar üzerindeki fazla kaynak tüketmeye kapsayıcıları bulun.

-   Merkezi CPU, bellek, depolama ve ağ kullanımını ve kapsayıcıları için performans bilgilerini görüntüleyin.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Microsoft Azure'da izleme genel bakış**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Application Insights nedir?**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **Günlük analizi nedir?**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   Kapsayıcı izleme çözümüne günlük analizi

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Azure İzleyicisi'ne genel bakış**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Operations Management Suite (OMS) nedir?**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **Service Fabric OMS ile Windows Server kapsayıcıları izleme**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[Önceki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[sonraki](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
