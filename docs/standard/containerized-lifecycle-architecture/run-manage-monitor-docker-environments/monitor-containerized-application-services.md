---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Kapsayıcı mimarileri izleme bazı önemli noktalar öğrenin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975751"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Tüm uygulama davranışını çözümlemenize yarayan bir yol sağlamak bölme birden fazla kapsayıcılar ve mikro hizmet uygulamaları için önemlidir.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) Canlı uygulamanızı izler, bir genişletilebilir bir analiz hizmetidir. Performans sorunlarını algılayıp tanılamanıza ve kullanıcıların gerçekten uygulamanızla neler anlamak için yardımcı olur. Sürekli olarak performansını artırmak için yardımcı hedefi ve hizmet veya uygulamalardan birinde kullanılabilirliği içeren, geliştiricilere yönelik tasarlanmıştır. Application Insights, şirket içinde barındırılan, .NET, Java, Node.js ve diğer birçok platformda gibi platformlarda veya bulutta çeşitli uygulamalar web/hizmetleri ve tek başına ile çalışır.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Docker uygulamaları QA ortamlarında Application Insights analiz etme

Docker için ilgili olarak yaşam döngüsü olayları ve performans sayaçlarını Application ınsights Docker kapsayıcılarından grafik. Çalıştırılacak yeterlidir [Application Insights Docker görüntüsü](https://hub.docker.com/r/microsoft/applicationinsights/) gibi ana bilgisayar ve bir kapsayıcıda yanı sıra konak için bir Docker görüntüleri için performans sayaçlarını görüntüler. Bu Application Insights Docker görüntüsü (Şekil 6 - 1), performans ve etkinliği (diğer bir deyişle, Linux Vm'leri) ana bilgisayarınızda Docker, Docker kapsayıcıları ve çalışan uygulamalar hakkında daha fazla telemetri toplama tarafından kapsayıcılı uygulamalarınızı izleme yardımcı olur bunların içinde.

![örnek](./media/image1.png)

**Şekil 6-1**. Application Insights Docker ana bilgisayarları ve kapsayıcıları izleme

Çalıştırdığınızda [Application Insights Docker görüntüsü](https://hub.docker.com/r/microsoft/applicationinsights/) ana bilgisayarınızda Docker üzerinde aşağıdakilerden yararlanabilir:

- Yaşam döngüsü ana bilgisayarda çalışan tüm kapsayıcılar hakkında telemetri — başlatma, durdurma ve benzeri.

- Tüm kapsayıcıları için performans sayaçları: CPU, bellek, ağ kullanımı ve daha fazlası.

- Ayrıca yüklediyseniz [Application Insights SDK'sı](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) kapsayıcılarda çalıştırılan uygulamalar, bu uygulamaların tüm telemetri kapsayıcı ve ana makine tanımlayan ek özelliklere sahip. Birden fazla ana çalışan bir uygulamanın örneğine sahipseniz, bu nedenle, örneğin, kolayca uygulama telemetrinizi konağa göre filtrelemek mümkün olacaktır.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Docker uygulamaları ve Docker ana bilgisayarları izlemek için Application ınsights'ı ayarlama

Application Insights kaynağı oluşturmak için aşağıdaki listede verilen makalelerdeki yönergeleri izleyin. Azure portalında gerekli komut sizin için oluşturur.

- **Application ınsights'ta Docker uygulamalarını izleme:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **Application Insights Docker görüntüsünü Docker Hub ve GitHub:** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> ve \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **ASP.NET web uygulamaları ve ASP.NET Core için Application ınsights'ı ayarlayın:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **Web sayfaları için Application Insights:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>Güvenlik, yedekleme ve hizmetlerini izleme

Çok bileşenli uygulamalar ve altyapı iş gereksinimlerini desteklemek için üstteki dişli durumda olduklarından emin olmak için işlemesine gerek ayrıntıları birçok destek işlerini vardır ve böylece, bir şekilde durum mikro hizmetler erişim, daha karmaşık hale gelir üst düzey ve ayrıntılı görünümlerini işlem yapması gerekir.

Azure, yönetmek ve hem bulut hem de şirket içi kaynaklar dört önemli yönlerini birleşik bir görünümünü sağlamak için geliştirme araçlarına sahiptir:

- **Güvenlik**. İle [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/).
  - Sanal makineler, uygulamalarınızı ve iş yüklerinin güvenliğini üzerinde tam görünürlük ve denetim alın.
  - Güvenlik ilkelerinizin yönetimini merkezileştirin; mevcut işlemleri ve araçları tümleştirin.
  - Gelişmiş analiz sayesinde gerçek tehditleri algılayın.

- **Yedekleme**. İle [Azure yedekleme](https://azure.microsoft.com/services/backup/).
  - Maliyetli iş kesintilerinden kaçının, uyumluluk hedeflerinizi karşılayın ve verilerinizi fidye yazılımlarına ve insan hatalarına karşı koruyun.
  - Yedekleme verileriniz aktarımda ve bekleme sırasında şifrelenmiş tutun.
  - Yetkisiz kullanımı önlemek için çok faktörlü kimlik doğrulamasını temel alan erişim emin olun.

- **İzleme**. İle [Azure izleme](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), ve [Application Insights](https://azure.microsoft.com/services/application-insights/).
  - Tam görünürlük durumunu ve performansını Azure iş yükleri, uygulamalar ve altyapı alın.
  - Herhangi bir kaynaktan veri toplayın ve, sanal makineler, kapsayıcılar ve uygulamalarınızı zengin Öngörüler edinin.
  - Etkileşimli sorgular ve tam metin aramasını kullanarak bilgileri bulun. 
  - Makine öğrenimi algoritmaları içeren Gelişmiş analiz ile kök neden analizi gerçekleştirin.

- **Şirket içi kaynaklara**. İle [tamamen tutarlı hibrit bulut](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md)
>[İleri](../key-takeaways/index.md)
