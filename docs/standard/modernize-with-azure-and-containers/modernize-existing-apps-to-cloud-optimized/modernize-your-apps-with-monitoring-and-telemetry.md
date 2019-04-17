---
title: İzleme ve telemetri ile uygulamalarınızı modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İzleme ve telemetri ile uygulamalarınızı modernleştirin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cd54861600127191b852e0a966baae6e0fe7914e
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613882"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>İzleme ve telemetri ile uygulamalarınızı modernleştirme

Üretim ortamında bir uygulamayı çalıştırdığınızda, uygulamanızın performansıyla ilgili içgörüler olması önemlidir. Bu, yüksek bir düzeyde çalışıyor mu? Kullanıcılar hataları alıyorsanız veya düzenli ve güvenilir uygulamasıdır? Zengin performans izleme, güçlü uyarı ve uygulamanızın kullanılabilir ve beklendiği gibi olduğunu sağlamak için panolar ihtiyacınız var. Ayrıca, hızlı bir şekilde bir sorun olup olmadığını görmek için kaç müşterinin etkilendiğini ve bulmak ve sorunu düzeltmek için bir kök neden analizi gerçekleştirmek belirlemek mümkün olması gerekir.

## <a name="monitor-your-application-with-application-insights"></a>Uygulamanızı Application Insights ile izleme

Application Insights, birden çok platformda çalışan web geliştiricilerine yönelik kapsamlı bir uygulama performans yönetimi (APM) hizmetidir. Bunu, canlı web uygulamanızı izlemek için kullanabilirsiniz. Application Insights performans anormalliklerini otomatik olarak algılar. Bu sorunları tanılamanıza yardımcı olmak ve ne kullanıcıların uygulamanızla aslında yaptığını anlamanıza yardımcı olacak güçlü analiz araçları içerir. Application Insights, performansı ve kullanılabilirliği sürekli geliştirmenize yardımcı olmak için tasarlanmıştır. Uygulamalar için çok çeşitli platformlarda, .NET, Node.js ve J2EE, dahil, üzerinde çalıştığı şirket içinde barındırılan veya bulutta. Application Insights, DevOps süreçlerinizin ile tümleşir ve geliştirme araçları çeşitli bağlantı noktaları vardır.

Şekil 4-10 nasıl Application Insights uygulamanızı izler ve nasıl bir panoya içgörüleri yüzeyler örneği gösterilmektedir.

![Application Insights izleme Panosu](./media/image10.png)

> **Şekil 4-10.** Application Insights izleme Panosu

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Log Analytics ve kapsayıcı izleme çözümü ile Docker altyapısını izleme

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) parçasıdır [izleme çözümü genel Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Ayrıca bir hizmetin içinde bulunduğu [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics bulut izler ve ortamları (OMS şirket içi) kullanılabilirliğini ve performansını sağlamak için şirket içinde. Birden fazla kaynak arasında analiz sağlamak üzere bulut ve şirket içi ortamlarınızdaki kaynaklar ile diğer izleme araçları tarafından oluşturulan verileri toplar.

Azure altyapı günlükleri ile ilgili olarak, bir Azure hizmeti olduğundan Log Analytics, diğer Azure Hizmetleri'den günlük ve ölçüm verilerini alır. (aracılığıyla [Azure İzleyici](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure Vm'leri, Docker kapsayıcıları ve şirket içinde veya diğer bulut altyapıları. Log Analytics, esnek bir günlük araması ve bu veriler üzerinde analiz out-hazır sunar. Bu, veri kaynaklarında analiz etmek için kullanabileceğiniz, tüm günlükleri arasında karmaşık sorgular sağlar ve proaktif olarak uyarabilir zengin Araçlar belirli koşullara göre sağlar. Hatta, sorgu ve bunları görselleştirmek merkezi Log Analytics deposunda, özel veri toplayabilir. Hemen güvenliği hakkında Öngörüler elde etmek için Log Analytics yerleşik çözümleri avantajlarından ve altyapınızı işlevselliğini da yararlanabilirsiniz.

OMS portalı veya tüm tarayıcılarda çalıştırmak, Azure portalı Log Analytics'e erişimi ve yapılandırma ayarlarını erişmenizi ve çok sayıda araç çözümlemek ve toplanan verilerde işlem yapmak için sağlayın.

[Kapsayıcı izleme çözümü](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) Log Analytics yardımcı olarak görüntüleyin ve Docker ve Windows kapsayıcı konaklarınız tek bir konumda yönetin. Çözüm gösterir hangi kapsayıcıları çalıştırmak, hangi kapsayıcı görüntüsü ister çalışıyor ve kapsayıcıları çalıştığı. Kapsayıcılar ile kullanılan komutları dahil olmak üzere ayrıntılı denetim bilgileri görüntüleyebilirsiniz. Kapsayıcılar, Docker veya Windows konak uzaktan görüntülemeye gerek kalmadan merkezi günlükleri, arama ve görüntüleme de giderebilirsiniz. Bir konakta gürültülü ve alıcı aşırı kaynakları olabilecek kapsayıcıları bulabilirsiniz. Ayrıca, merkezileştirilmiş CPU, bellek, depolama ve ağ kullanımını ve kapsayıcılar için performans bilgilerini görüntüleyebilirsiniz. Windows çalıştıran bilgisayarlarda, merkezileştirme ve Windows Server günlüklerinden karşılaştırın Hyper-V ve Docker kapsayıcıları. Çözüm, aşağıdaki kapsayıcı düzenleyicileri destekler:

-   Docker Swarm

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

Şekil 4-11 çeşitli kapsayıcı konakları ve aracıları ve OMS arasındaki ilişkiler gösterilmektedir.

![Log Analytics kapsayıcı izleme çözümü](./media/image11.png)

> **Şekil 4-11.** Log Analytics kapsayıcı izleme çözümü

Log Analytics kapsayıcı izleme çözümü kullanabilirsiniz:

-   Tek bir konumda tüm kapsayıcı konakları hakkında bilgi.

-   Kapsayıcıları olduğunuzu çalıştırmak, hangi görüntüyü çalıştırdıkları ve bunların nereye çalıştırdığınızdan.

-   Eylemler için bir denetim kaydı kapsayıcılarında bakın.

-   Docker ana bilgisayarları için uzaktan oturum açma olmadan Merkezi günlük arama ve görüntüleme sorunlarını giderin.

-   "Gürültülü komşu" olabilir ve bir konak üzerinde aşırı kaynakları kullanan kapsayıcıları bulun.

-   Merkezileştirilmiş CPU, bellek, depolama ve ağ kullanımını ve kapsayıcılar için performans bilgilerini görüntüleyin.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Microsoft Azure'da izlemeye genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

-   **Application Insights nedir?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

-   **Log Analytics nedir?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

-   **Azure İzleyici'de kapsayıcı izleme çözümü**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

-   **Azure İzleyicisi'ne genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

-   **Operations Management Suite (OMS) nedir?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

-   **Windows Server kapsayıcıları Service fabric'te OMS ile izleme**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[Önceki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[İleri](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
