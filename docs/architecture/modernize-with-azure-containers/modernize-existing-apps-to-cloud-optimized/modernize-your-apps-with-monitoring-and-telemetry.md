---
title: İzleme ve telemetri ile uygulamalarınızı modernleştirme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | İzleme ve telemetri ile uygulamalarınızı modernleştirin
ms.date: 04/30/2018
ms.openlocfilehash: a6094435eece661d99904876ac49b3ca85ec45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172007"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>İzleme ve telemetri ile uygulamalarınızı modernleştirme

Bir uygulamayı üretimde çalıştırdığınızda uygulamanızın nasıl çalıştığı hakkında öngörülere sahip olmanız önemlidir. Yüksek düzeyde mi gerçekleştiriliyor? Kullanıcılar hata alıyor mu, ya da uygulama kararlı ve güvenilir mi? Uygulamanızın kullanılabilir olduğundan ve beklendiği gibi çalıştığından emin olmak için zengin performans izleme, güçlü uyarı ve panolarınız olmalıdır. Ayrıca bir sorun olup olmadığını hızlı bir şekilde görmeniz, kaç müşterinin etkilendiğini belirlemeniz ve sorunu bulmak ve çözmek için bir kök neden analizi yapmanız gerekir.

## <a name="monitor-your-application-with-application-insights"></a>Uygulamanızı Application Insights izleyin

Application Insights, birden çok platformda çalışan Web geliştiricileri için genişletilebilir bir uygulama performans yönetimi (APM) hizmetidir. Canlı web uygulamanızı izlemek için kullanabilirsiniz. Application Insights, performans bozuklularını otomatik olarak algılar. Sorunları tanılamanıza yardımcı olacak güçlü analiz araçları içerir ve uygulamanızla gerçekten ne yaptığını anlamanıza yardımcı olur. Application Insights, performansı ve kullanılabilirliği sürekli olarak iyileştirmenize yardımcı olmak için tasarlanmıştır. Şirket içinde veya bulutta barındırılıp, .NET, Node.js ve J2EE dahil olmak üzere çok çeşitli platformlarda uygulamalar için geçerlidir. Application Insights, DevOps süreçlerinizle tümleştirilir ve çeşitli geliştirme araçlarına bağlantı noktaları içerir.

Şekil 4-10 Application Insights, uygulamanızı nasıl izlediğini ve bu öngörüleri bir panoya nasıl yüzey olarak gösterdiğini gösteren bir örnek gösterir.

![Application Insights izleme panosunun ekran görüntüsü.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Şekil 4-10.** Application Insights izleme panosu

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Docker altyapınızı Log Analytics ve kapsayıcı Izleme çözümü ile izleyin

[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) , [Microsoft Azure genel izleme çözümünün](/azure/monitoring-and-diagnostics/monitoring-overview)bir parçasıdır. Ayrıca [Operations Management Suite 'te (OMS)](/azure/operations-management-suite/operations-management-suite-overview)bir hizmettir. Log Analytics, kullanılabilirliği ve performansı sürdürmenize yardımcı olmak üzere bulutu ve şirket içi ortamları (Şirket içi için OMS) izler. Birden fazla kaynak arasında analiz sağlamak üzere bulut ve şirket içi ortamlarınızdaki kaynaklar ile diğer izleme araçları tarafından oluşturulan verileri toplar.

Azure altyapı günlükleriyle ilgili olarak, Azure hizmeti olarak Log Analytics, diğer Azure hizmetlerinden ( [Azure izleyici](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)aracılığıyla), Azure VM 'Leri, Docker kapsayıcılarından ve şirket içi veya diğer bulut altyapılarından günlük ve ölçüm verileri alır. Log Analytics, bu verilerin en üstünde esnek günlük araması ve kullanıma hazır analizler sunmaktadır. Kaynak genelinde verileri çözümlemek için kullanabileceğiniz zengin araçlar sağlar, tüm günlüklerde karmaşık sorgulara izin verir ve belirtilen koşullara göre proaktif bir şekilde uyarı verebilir. Ayrıca, merkezi Log Analytics depoda özel verileri toplayabilir ve burada bunları sorgulayabilir ve görselleştirebilirsiniz. Ayrıca, altyapınızın güvenlik ve işlevlerine yönelik Öngörüler elde etmek için Log Analytics yerleşik çözümlerin avantajlarından yararlanabilirsiniz.

Her tarayıcıda çalışan OMS portalı veya Azure portal üzerinden Log Analytics erişebilirsiniz ve toplanan verileri çözümlemek ve üzerinde işlem yapmak için yapılandırma ayarlarına ve birden çok araca erişim sağlamanıza olanak sağlayabilirsiniz.

Log Analytics [kapsayıcı izleme çözümü](/azure/log-analytics/log-analytics-containers) , Docker ve Windows kapsayıcı konaklarınızı tek bir konumda görüntülemenize ve yönetmenize yardımcı olur. Çözüm hangi kapsayıcıların çalıştığını, hangi kapsayıcı görüntüsünün çalıştığını ve kapsayıcıların nerede çalıştığını gösterir. Kapsayıcılarla kullanılmakta olan komutlar dahil olmak üzere ayrıntılı denetim bilgilerini görüntüleyebilirsiniz. Ayrıca, Docker veya Windows konaklarını uzaktan görüntülemeniz gerekmeden, merkezi günlükleri görüntüleyip arayarak kapsayıcılarda da sorun giderme yapabilirsiniz. Gürültülü olabilecek ve bir konakta fazla kaynak tüketen kapsayıcıları bulabilirsiniz. Ayrıca, kapsayıcı için merkezi CPU, bellek, depolama ve ağ kullanımı ve performans bilgilerini görüntüleyebilirsiniz. Windows çalıştıran bilgisayarlarda, günlükleri Windows Server, Hyper-V ve Docker kapsayıcılarından merkezileştirmek ve karşılaştırmak için kullanabilirsiniz. Çözüm aşağıdaki kapsayıcı düzenleyiciler destekler:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Şekil 4-11, çeşitli kapsayıcı konakları ve aracılar ile OMS arasındaki ilişkileri gösterir.

![Log Analytics kapsayıcı Izleme çözümünün ekran görüntüsü.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Şekil 4-11.** Log Analytics kapsayıcı Izleme çözümü

Log Analytics kapsayıcı Izleme çözümünü kullanarak şunları yapabilirsiniz:

- Tek bir konumdaki tüm kapsayıcı Konakları hakkındaki bilgilere bakın.

- Hangi kapsayıcıların çalıştığını, hangi görüntünün çalıştığını ve nerede çalıştığını öğrenin.

- Kapsayıcılardaki eylemler için bir denetim izi görüntüleyin.

- Docker konaklarına uzaktan oturum açmadan merkezi günlükleri görüntüleyip arayarak sorun giderin.

- "Gürültülü komşu komşuları" olabilecek kapsayıcıları bulun ve bir konakta fazla kaynak tüketiyor olabilirsiniz.

- Kapsayıcılar için merkezi CPU, bellek, depolama ve ağ kullanımı ve performans bilgilerini görüntüleyin.

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft Azure 'da izlemeye genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Application Insights nedir?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Log Analytics nedir?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure Izleyici 'de kapsayıcı Izleme çözümü**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure İzleyici’ye genel bakış**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Operations Management Suite (OMS) nedir?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Önceki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md) 
> [Sonraki](life-cycle-ci-cd-pipelines-devops-tools.md)
