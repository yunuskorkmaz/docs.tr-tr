---
title: "Kapsayıcılı İzleyici uygulama hizmetleri"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58bf96dfa06a78892563698200e6f4df5f371346
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="monitor-containerized-application-services"></a>Kapsayıcılı İzleyici uygulama hizmetleri

İzleme ve uygulama davranışını çözümlemek için bir yol sağlamak birden çok kapsayıcı ve mikro bölünen uygulamaları için önemlidir.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) Canlı uygulamanızı izler bir genişletilebilir bir analiz hizmetidir. Performans sorunlarını tanılamak ve algılamak ve kullanıcıların gerçekte uygulamanızla ne anlamak için yardımcı olur. Sürekli olarak performansını artırmak için yardımcı amacı ve hizmetlerin ve uygulamaların kullanılabilirliğini ile geliştiriciler için tasarlanmıştır. Application Insights, çeşitli .NET, Java, Node.js ve diğer birçok platformda şirket içi barındırılan gibi platformlarının veya bulutta uygulamalara web/hizmetleri ve tek başına ile çalışır.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Application Insights kullanarak QA ortamlarda Docker uygulamaları analiz etme

Docker için ilgili olarak yaşam döngüsü olayları ve performans sayaçlarını Application Insights Docker kapsayıcılarında grafik. Çalıştırmak yeterlidir [uygulama Öngörüler Docker görüntü](https://hub.docker.com/r/microsoft/applicationinsights/) ana bilgisayarınız ve kapsayıcısında yanı sıra konak diğer Docker görüntüleri ettirilmesi için performans sayaçlarını görüntüler olarak. Bu uygulama Öngörüler Docker görüntü (Şekil 6 - 1) yardımcı olur, performans ve etkinliği, Docker ana bilgisayarı (diğer bir deyişle, Linux VM'ler), Docker kapsayıcıları ve çalışan uygulamalar hakkında telemetri toplayarak kapsayıcılı uygulamalarınızı izlemek için bunların içinde.

![örnek](./media/image1.png)

Şekil 6-1: Application Insights Docker ana bilgisayarları ve kapsayıcıları izleme

Çalıştırdığınızda [uygulama Öngörüler Docker görüntü](https://hub.docker.com/r/microsoft/applicationinsights/) , Docker ana bilgisayarda aşağıdakini yararlanır:

-   Yaşam döngüsü ana bilgisayarda çalışan tüm kapsayıcıları hakkında telemetriyi — başlatma, durdurma ve benzeri.

-   Tüm kapsayıcıları için performans sayaçları: CPU, bellek, ağ kullanımını ve daha fazla.

-   Ayrıca yüklediyseniz [Application Insights SDK'sı](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) kapsayıcılarında çalışan uygulamalar, bu uygulamaların tüm telemetri kapsayıcı ve ana bilgisayar makine tanımlayan ek özellikleri sahip olur. Bir uygulama içinde birden fazla ana çalışan örneklerini varsa, bu nedenle, örneğin, kolayca ana bilgisayarı tarafından uygulama telemetrinizi filtrelemek görebilirsiniz.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Docker uygulamaları ve Docker ana bilgisayarları izlemek için Application Insights'ı ayarlama

Application Insights kaynağı oluşturmak için aşağıdaki listeden sunulan makaleleri'ndaki yönergeleri izleyin. Azure Portal sizin için gerekli komut dosyası oluşturur.

-   **Application ınsights'ta Docker uygulamaları izleme:**[https://docs.microsoft.com/azure/application-insights/app-insights-docker  ](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Uygulama Öngörüler Docker görüntüsü Docker hub'a ve Github:**  
[https://Hub.docker.com/r/Microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) ve <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **ASP.NET için Application Insights'ı ayarlayın:**  
[https://docs.microsoft.com/Azure/Application-insights/App-insights-ASP-NET](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Web sayfaları için Application Insights:**  
<https://docs.microsoft.com/Azure/Application-insights/App-insights-JavaScript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms) günlük analizi, otomasyon, yedekleme ve site kurtarma sağlayan basitleştirilmiş bir BT yönetimi çözümüdür. Temel [sorguları](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) Operations Management Suite içinde ortaya çıkarabilir [uyarıları](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) ve düzeltme aracılığıyla [Azure Otomasyonu](https://docs.microsoft.com/azure/automation/). Aynı zamanda sorunsuz bir şekilde, tek bir cam bölmesinde görünümünü sağlamak için mevcut yönetim çözümleri ile tümleşir. Operations Management Suite, yönetmek ve şirket içi korumak ve altyapı bulut yardımcı olur.

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) Docker kapsayıcısı çözümü

Değerli hizmetleri, kendi sağlamanın yanı sıra Operations Management Suite kapsayıcı çözüm yönetebilir ve Docker ana bilgisayarları ve kapsayıcıları kapsayıcıları ve kapsayıcı konakları nerede hakkında bilgi göstererek izleyebilirsiniz hangi kapsayıcıları çalışıyor "veya" hatalı ve Docker arka plan programı ve kapsayıcı günlükleri gönderilen *stdout* ve *stderr*. Ayrıca, performans ölçümleri CPU, bellek, ağ ve depolama kapsayıcısı ve sorun giderme ve gürültülü komşu kapsayıcıları bulmanıza yardımcı olmak için ana bilgisayarların gibi gösterir.

![](./media/image2.png)

Şekil 6-2: Operations Management Suite tarafından gösterilen Docker kapsayıcıları hakkında bilgi

Application Insights ve Operations Management Suite izleme etkinlikleri odaklanmak; Ancak, Application Insights daha uygulama içinde çalışan kendi SDK sayesinde uygulamaları kendilerini izlemeyi odaklanır. Ancak, Operations Management Suite konakları geçici altyapı çok daha odaklanır ve ayrıca çok esnek veri odaklı Ara/sorgu sistem sağlarken ölçekte günlükleri üzerinde derin çözümleme sunar.

Operations Management Suite bulut tabanlı bir hizmet olarak uygulandığı için hazır ve çalışır hızlı bir şekilde minimal yatırım altyapı hizmetleri ile sağlayabilirsiniz. Yeni özellikler otomatik olarak devam eden bakım kaydetme teslim edilir ve maliyetleri yükseltin.

Operations Management Suite kapsayıcı çözümünü kullanarak, aşağıdakileri yapabilirsiniz:

-   Merkezileştirmek ve Docker kapsayıcıları ölçekte günlüklerinden milyonlarca ilişkilendirmek

-   Konaklarda kapsayıcı tek bir konum hakkında bilgi

-   Hangi kapsayıcıları olduğunu biliyorsanız, hangi görüntü çalıştırdıkları çalıştırıp nerede çalışıyor

-   Kapsayıcı konaklarda sorunlara neden olabilir "gürültülü komşu" kapsayıcıları hızla tanılamak

-   Eylemler için bir denetim izi kapsayıcılarında bakın

-   Görüntüleme ve Docker ana bilgisayarları için uzaktan iletişim olmadan merkezi günlükleri arama yaparak sorun giderme

-   "Gürültülü komşu" ve bir ana bilgisayardaki kullanıcı aşırı kaynakları olabilir kapsayıcıları Bul

-   Merkezi CPU, bellek, depolama ve ağ kullanımı ve performans bilgilerini kapsayıcıları için görüntüleme

-   Oluştur test Azure Automation Docker kapsayıcıları

Sorgu türü gibi çalıştırarak performans bilgileri görebilirsiniz Perf, Şekil 6-3'te gösterildiği gibi =.

![DockerPerfMetricsView](./media/image3.png){width = "5.78625 in" yükseklik = "3,25 inç"}

Şekil 6-3: performans ölçümleri Operations Management Suite tarafından gösterilen Docker ana bilgisayarları

Ayrıca bir standart Operations Management Suite özelliğidir ve yardımcı olabilir sorguları kaydetme yararlı buldunuz ve sisteminizdeki eğilimleri bulmak sorguları tutun.

**Daha fazla bilgi** kapsayıcı çözümde yükleme ve Docker yapılandırma hakkında bilgi bulmak için [Operations Management Suite](http://microsoft.com/oms)gidin <https://docs.microsoft.com/azure/ Günlük-analytics/günlük-analytics-kapsayıcıları>.

>[!div class="step-by-step"]
[Önceki] (yönetme-üretim-docker-environments.md) [sonraki] (.. /Key-takeaways/index.MD)
