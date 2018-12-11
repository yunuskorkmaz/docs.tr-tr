---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 5630bfcc3173def670e2fa780d28024799b7c2a1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153933"
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcı uygulama hizmetlerini izleme

Uygulamalar için kapsayıcılar ve mikro hizmetler halinde bölme uygulama davranışını çözümlemenize yarayan bir yol sağlamak önemlidir.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) Canlı uygulamanızı izler, bir genişletilebilir bir analiz hizmetidir. Performans sorunlarını algılayıp tanılamanıza ve kullanıcıların gerçekten uygulamanızla neler anlamak için yardımcı olur. Sürekli olarak performansını artırmak için yardımcı hedefi ve hizmet veya uygulamalardan birinde kullanılabilirliği içeren, geliştiricilere yönelik tasarlanmıştır. Application Insights, şirket içinde barındırılan, .NET, Java, Node.js ve diğer birçok platformda gibi platformlarda veya bulutta çeşitli uygulamalar web/hizmetleri ve tek başına ile çalışır.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Docker uygulamaları QA ortamlarında Application Insights analiz etme

Docker için ilgili olarak yaşam döngüsü olayları ve performans sayaçlarını Application ınsights Docker kapsayıcılarından grafik. Çalıştırılacak yeterlidir [Application Insights Docker görüntüsü](https://hub.docker.com/r/microsoft/applicationinsights/) gibi ana bilgisayar ve bir kapsayıcıda yanı sıra konak için bir Docker görüntüleri için performans sayaçlarını görüntüler. Bu Application Insights Docker görüntüsü (Şekil 6 - 1), performans ve etkinliği (diğer bir deyişle, Linux Vm'leri) ana bilgisayarınızda Docker, Docker kapsayıcıları ve çalışan uygulamalar hakkında daha fazla telemetri toplama tarafından kapsayıcılı uygulamalarınızı izleme yardımcı olur bunların içinde.

![örnek](./media/image1.png)

Şekil 6-1: Application Insights Docker ana bilgisayarları ve kapsayıcıları izleme

Çalıştırdığınızda [Application Insights Docker görüntüsü](https://hub.docker.com/r/microsoft/applicationinsights/) ana bilgisayarınızda Docker üzerinde aşağıdakilerden yararlanabilir:

-   Yaşam döngüsü ana bilgisayarda çalışan tüm kapsayıcılar hakkında telemetri — başlatma, durdurma ve benzeri.

-   Tüm kapsayıcıları için performans sayaçları: CPU, bellek, ağ kullanımı ve daha fazlası.

-   Ayrıca yüklediyseniz [Application Insights SDK'sı](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) kapsayıcılarda çalıştırılan uygulamalar, bu uygulamaların tüm telemetri kapsayıcı ve ana makine tanımlayan ek özelliklere sahip. Birden fazla ana çalışan bir uygulamanın örneğine sahipseniz, bu nedenle, örneğin, kolayca uygulama telemetrinizi konağa göre filtrelemek mümkün olacaktır.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Docker uygulamaları ve Docker ana bilgisayarları izlemek için Application ınsights'ı ayarlama

Application Insights kaynağı oluşturmak için aşağıdaki listede verilen makalelerdeki yönergeleri izleyin. Azure portalında gerekli komut sizin için oluşturur.

-   **Application ınsights'ta Docker uygulamalarını izleme:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Application Insights Docker görüntüsünü Docker Hub ve Github:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) ve <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **ASP.NET için Application ınsights'ı ayarlayın:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Web sayfaları için Application Insights:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite'e

[Operations Management Suite](https://microsoft.com/oms) log analytics, otomasyon, backup ve site recovery sağlayan bir Basitleştirilmiş BT yönetimi çözümüdür. Temel [sorguları](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) , Operations Management Suite içinde yükseltebilirsiniz [uyarılar](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) ve düzeltme aracılığıyla [Azure Otomasyonu](https://docs.microsoft.com/azure/automation/). Ayrıca sorunsuz bir şekilde, tek bir cam bölmesinde görüntülemenizi sağlamak için mevcut yönetim çözümleri ile tümleşir. Operations Management Suite, yönetmek ve şirket içi koruma hem de bulut altyapısında yardımcı olur.

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite'e](https://microsoft.com/oms) Docker kapsayıcı çözümü

Değerli hizmetleri, kendi sağlamanın yanı sıra Operations Management Suite kapsayıcı çözümü yönetebilir ve kapsayıcılar ve kapsayıcı konağında olduğu hakkında bilgi göstererek Docker ana bilgisayarları ve kapsayıcıları izleme, çalışan kapsayıcılar "veya" hatalı ve Docker daemon'ı ve kapsayıcı günlüklerini gönderilen *stdout* ve *stderr*. Ayrıca CPU, bellek, ağ ve depolama kapsayıcısı ve sorun giderme ve gürültülü komşu kapsayıcıları bulmanıza yardımcı olması için ana bilgisayarları gibi performans ölçümlerini gösterir.

![](./media/image2.png)

Şekil 6-2: Operations Management Suite tarafından gösterilen Docker kapsayıcıları hakkında bilgi

Application Insights ve Operations Management Suite izleme etkinlikleri odaklanın; Ancak, Application Insights daha uygulama içinde çalışan kendi SDK sayesinde uygulamaları kendilerini izlemeyi üzerinde odaklanır. Ancak, Operations Management Suite altyapı konakları etrafında çok daha odaklanan yanı sıra çok esnek veri odaklı arama/sorgu sistem sunarken uygun ölçekte günlükleri üzerinde ayrıntılı analiz sunar.

Operations Management Suite bulut tabanlı bir hizmet olarak uygulandığından, çalışmaya hızlıca altyapı hizmetleri için çok az yatırım ile sağlayabilirsiniz. Yeni özellikler otomatik olarak devam eden bakım tasarruf sağlarsınız ve yükseltme maliyetlerinden.

Operations Management Suite kapsayıcı çözümü kullanarak bunu yapabilirsiniz:

-   Tek bir merkezden yönetin ve Docker kapsayıcıları ölçekleyerek günlüklerinden milyonlarca ilişkilendirin

-   Tek bir konumda tüm kapsayıcı konakları hakkında bilgi

-   Kapsayıcıları olduğunuzu çalıştırmak, hangi görüntüyü çalıştırdıkları ve bunların nereye çalıştırdığınızdan

-   Kapsayıcı konaklarda sorunlara neden olabilir "gürültülü komşu" kapsayıcıları hızlı bir şekilde tanılayın

-   Eylemler için bir denetim kaydı kapsayıcılarında bakın

-   Görüntüleme ve Docker ana bilgisayarları için uzaktan iletişim olmadan merkezi günlükleri arama ile ilgili sorunları giderme

-   "Gürültülü komşu" ve bir ana bilgisayarda kullanan aşırı kaynaklar kapsayıcılar Bul

-   Merkezileştirilmiş CPU, bellek, depolama ve kapsayıcılar için ağ kullanım ve performans bilgilerini görüntüleyin

-   Oluşturma Docker kapsayıcılarını Azure Otomasyonu ile test

Sorgu türü gibi çalıştırarak performans bilgileri görebilir performans, Şekil 6-3'te gösterildiği gibi =.

![DockerPerfMetricsView](./media/image3.png){width = "5.78625 in" height = "3,25 in"}

Şekil 6-3: Docker ana bilgisayarları Operations Management Suite tarafından gösterilen performans ölçümleri

Ayrıca Operations Management Suite'teki standart bir özellik olan sorguları kaydetme ve yardımcı olabilecek yararlı buldunuz ve sisteminizdeki eğilimleri sorguları tutun.

**Daha fazla bilgi** kapsayıcı çözümü, yükleme ve Docker yapılandırma bilgileri bulmak için [Operations Management Suite](https://microsoft.com/oms)Git <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
>[Önceki](manage-production-docker-environments.md)
>[İleri](../key-takeaways/index.md)