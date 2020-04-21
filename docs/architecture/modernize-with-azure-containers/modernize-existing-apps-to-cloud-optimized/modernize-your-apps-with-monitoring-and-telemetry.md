---
title: İzleme ve telemetri ile uygulamalarınızı modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | İzleme ve telemetri ile uygulamalarınızı modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: a5101f150d6548406db8638904fb4ab6375edf9c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739176"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>İzleme ve telemetri ile uygulamalarınızı modernleştirme

Üretimde bir uygulama çalıştırdığınızda, uygulamanızın nasıl performans gösterdiğine ilişkin öngörüleriniz olması çok önemlidir. Yüksek seviyede mi performans sergiliyor? Kullanıcılar hata alıyor mu, yoksa uygulama kararlı ve güvenilir mi? Uygulamanızın kullanılabilir olduğundan ve beklendiği gibi performans gösterdiğinden emin olmak için zengin performans izleme, güçlü uyarı ve panolara ihtiyacınız vardır. Ayrıca, bir sorun olup olmadığını hızlı bir şekilde görebilmeniz, kaç müşterinin etkilendiğini belirleyebilmeniz ve sorunu bulmak ve düzeltmek için bir kök neden çözümlemesi gerçekleştirebilmeniz gerekir.

## <a name="monitor-your-application-with-application-insights"></a>Uygulama Öngörüleri ile uygulamanızı izleyin

Application Insights, birden çok platformda çalışan web geliştiricileri için genişletilebilir bir Uygulama Performans Yönetimi (APM) hizmetidir. Canlı web uygulamanızı izlemek için kullanabilirsiniz. Uygulama Öngörüleri performans anormalliklerini otomatik olarak algılar. Sorunları tanılamanıza ve kullanıcıların uygulamanızla gerçekte ne yaptığını anlamanıza yardımcı olacak güçlü analiz araçları içerir. Application Insights, performansı ve kullanılabilirliği sürekli olarak geliştirmenize yardımcı olmak için tasarlanmıştır. .NET, Node.js ve J2EE gibi çok çeşitli platformlardaki uygulamalar için çalışır. Application Insights, DevOps süreçlerinizle bütünleşir ve çeşitli geliştirme araçlarına bağlantı noktaları na sahiptir.

Şekil 4-10, Application Insights'ın uygulamanızı nasıl izlediğine ve bu öngörüleri bir panoya nasıl yüzdürttteğine dair bir örnek gösterir.

![Uygulama Öngörüleri izleme panosunun ekran görüntüsü.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Şekil 4-10.** Uygulama Öngörüleri izleme panosu

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Docker altyapınızı Log Analytics ve Konteyner İzleme çözümü yle izleyin

[Azure Log Analytics,](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) [Microsoft Azure genel izleme çözümünün](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)bir parçasıdır. Aynı zamanda [Operasyon Yönetimi Paketi 'nde (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)bir hizmettir. Log Analytics, kullanılabilirliği ve performansı korumaya yardımcı olmak için bulutları ve şirket içi ortamları (şirket içi OMS) izler. Birden fazla kaynak arasında analiz sağlamak üzere bulut ve şirket içi ortamlarınızdaki kaynaklar ile diğer izleme araçları tarafından oluşturulan verileri toplar.

Azure altyapı günlükleri, Azure hizmeti olarak Log Analytics ile ilgili olarak, diğer Azure hizmetlerinden [(Azure Monitor), Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)VM'ler, Docker kapsayıcıları ve şirket içi veya diğer bulut altyapılarından günlük ve metrik veriler yutmaktadır. Log Analytics, bu verilerin üzerinde esnek günlük araması ve kutu dan sıcağa dayalı analizler sunar. Kaynaklar arasında verileri çözümlemek için kullanabileceğiniz zengin araçlar sağlar, tüm günlüklerde karmaşık sorgulara izin verir ve belirtilen koşullara bağlı olarak proaktif olarak uyarabilir. Hatta sorgulayıp görselleştirebileceğiniz merkezi Log Analytics deposunda özel veriler toplayabilir. Ayrıca, altyapınızın güvenliği ve işlevselliği hakkında hemen bilgi edinmek için Log Analytics yerleşik çözümlerinden de yararlanabilirsiniz.

Log Analytics'e, herhangi bir tarayıcıda çalışan OMS portalı veya Azure portalı üzerinden erişebilir ve toplanan verileri analiz etmek ve bunları etkinleştirmek için yapılandırma ayarlarına ve birden çok araça erişebilirsiniz.

Log Analytics'teki [Konteyner İzleme çözümü,](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) Docker ve Windows Container ana bilgisayarlarınızı tek bir konumda görüntülemenize ve yönetmenize yardımcı olur. Çözüm, hangi kapsayıcıların çalıştığını, hangi kapsayıcı görüntüsünü çalıştırdıklarını ve kapsayıcıların nerede çalıştığını gösterir. Kapsayıcılarla birlikte kullanılan komutlar da dahil olmak üzere ayrıntılı denetim bilgilerini görüntüleyebilirsiniz. Ayrıca, Docker veya Windows ana bilgisayarlarını uzaktan görüntülemenize gerek kalmadan merkezi günlükleri görüntüleyerek ve arayarak kapsayıcıları giderebilirsiniz. Gürültülü ve aşırı kaynakları bir ana bilgisayarda tüketen kapsayıcılar bulabilirsiniz. Ayrıca, kapsayıcılar için merkezi CPU, bellek, depolama ve ağ kullanımı ve performans bilgilerini görüntüleyebilirsiniz. Windows çalıştıran bilgisayarlarda, Windows Server, Hyper-V ve Docker kapsayıcılarından günlükleri merkezileştirebilir ve karşılaştırabilirsiniz. Çözüm aşağıdaki konteyner orkestratörlerini destekler:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Şekil 4-11 çeşitli konteyner ana bilgisayarları ve aracılar ve OMS arasındaki ilişkileri gösterir.

![Log Analytics Konteyner İzleme çözümünün ekran görüntüsü.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Şekil 4-11.** Log Analytics Konteyner İzleme çözümü

Log Analytics Konteyner İzleme çözümünü aşağıdakiler için kullanabilirsiniz:

- Tek bir konumdaki tüm kapsayıcı ana bilgisayarları hakkındaki bilgilere bakın.

- Hangi kapsayıcıların çalıştığını, hangi görüntüyü çalıştırdıklarını ve nerede çalıştırdıklarını bilin.

- Kapsayıcılar üzerindeki eylemler için bir denetim izine bakın.

- Docker ana bilgisayarlarına uzaktan giriş yapmadan merkezi günlükleri görüntüleyerek ve arayarak sorun giderme.

- "Gürültülü komşular" olabilecek kapsayıcıları bulun ve bir ana bilgisayarda fazla kaynakları tüketin.

- Kapsayıcılar için merkezi cpu, bellek, depolama ve ağ kullanımını ve performans bilgilerini görüntüleyin.

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft Azure'da izlemeye genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights nedir?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Log Analytics nedir?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure Monitör'de Konteyner İzleme çözümü**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure İzleyici’ye genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Operations Management Suite (OMS) nedir?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Önceki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Sonraki](life-cycle-ci-cd-pipelines-devops-tools.md)
