---
title: "Dayanıklılık ve yüksek kullanılabilirlik mikro"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Dayanıklılık ve yüksek kullanılabilirlik mikro"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 149e28ac7bd7383e4e960ed8a226943e2b9bdaa1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Dayanıklılık ve yüksek kullanılabilirlik mikro

Beklenmeyen hatalar postalarla özellikle dağıtılmış bir sistemde çözmenin en zor sorunlar biridir. Bu aynı zamanda testinde en uzun süre burada harcandığını olup ve geliştiricilerin yazma kodu çoğunu özel durumları işleme içerir. Sorun daha hataları işlemek için kod yazma daha karmaşıktır. Mikro hizmet çalıştığı makine başarısız olduğunda ne olur? Yalnızca bu mikro hizmet hatası (sabit kendi başına bir sorun) algılayan gerekir, ancak ayrıca şey, mikro hizmet yeniden başlatmanız gerekir.

Bir mikro hizmet hatalarına dayanıklı olmasını ve kullanılabilirlik için başka bir makinede sık sık yeniden başlatmanız gerekir. Bu esneklik de mikro hizmet adına mikro hizmet bu durumdan kurtarabilir ve mikro hizmet başarılı bir şekilde yeniden olup olmadığını kaydedilmiş duruma gelir. Diğer bir deyişle, vardır (işlemi herhangi bir zamanda yeniden başlatabilirsiniz) işlem yeteneği dayanıklılık olması gerekir esnekliği durumu veya verileri (veri kaybı ve tutarlı veri kalır) yanı sıra.

Dayanıklılık sorunları hataları uygulama yükseltme sırasında ortaya çıktığında gibi diğer senaryolar sırasında araya geldiğinde. İleri daha yeni bir sürüme taşıyın veya bunun yerine tutarlı bir duruma korumak için bir önceki sürüme geri sürdürebilirsiniz olup olmadığını belirlemek dağıtım sistemiyle çalışma mikro hizmet gerekir. Yeterli makineler ileri taşıma tutmak kullanılabilir olup olmadığı ve mikro hizmet önceki sürümlerini kurtarmak nasıl gibi soruları ele alınması gerekir. Bu, böylece bu kararlar genel uygulama ve orchestrator sistem durumu bilgisi yayması için mikro hizmet gerektirir.

Ayrıca, dayanıklılık ilgili nasıl bulut tabanlı sistemler için hareket etmesi gerekir. Belirtildiği gibi bulut tabanlı bir sistemi hataları çekirdeğin gerekir ve bunları otomatik olarak kurtarmaya denemeniz gerekir. Örneğin, ağ veya kapsayıcı hataları durumunda iletileri gönderme yeniden deneyin ya da çoğu durumda bulutta hataları kısmi olduğundan istekleri, yeniden denemek için bir strateji istemci uygulamaları veya istemci Hizmetleri olması gerekir. [Uygulama dayanıklı uygulamaları](#implementing_resilient_apps) bu kılavuzdaki bölümü kısmi hatası nasıl ele alınacağını yöneliktir. Gibi kitaplıklarını kullanarak yeniden deneme üstel geri alma veya .NET Core devre kesici desende gibi teknikleri açıklar [Polly](https://github.com/App-vNext/Polly), bu konu işlemek için ilkeler çeşitliliğini sunar.

## <a name="health-management-and-diagnostics-in-microservices"></a>Sistem Yönetimi ve mikro tanılama

Açıktır, görünebilir ve genellikle atlamış, ancak bir mikro hizmet, durum ve tanılama raporu gerekir. Aksi takdirde işlemleri açısından biraz Insight yoktur. Tanılama Olayları bağımsız Hizmetleri kümesi arasında ilişkilendirme ve olayı sırası anlamlı makine saat eğriltir ilgilenme zordur. Üzerinde anlaşılan protokolleri ve veri biçimleri mikro hizmet ile etkileşime aynı şekilde, sistem durumu ve sorgulama ve görüntülemek için bir olay deposunda sonuçta şunun tanılama olayları günlüğe kaydetme hakkında standartlaştırma gereksinimi yoktur. İsteğe bağlı olarak bir mikro yaklaşım anahtarı olan farklı ekipler'in tek günlük biçimi kabul etmiş olursunuz. Uygulama Tanılama Olayları görüntülemek için tutarlı bir yaklaşım vardır gibi gerekir.

### <a name="health-checks"></a>Sistem durumu denetimleri

Sistem durumu tanılama farklıdır. Sistem durumu geçerli durumuna uygun eylemleri raporlama mikro hizmet hakkında ' dir. İyi bir örnek kullanılabilirliğini sağlamak için yükseltme ve dağıtım mekanizmaları ile çalışmaktadır. Bir hizmet şu anda bir işlem kilitlenme nedeniyle sağlıksız veya yeniden başlatma makine rağmen hizmet işletimsel olabilir. Gereksinim duyduğunuz son şey bu yükseltme gerçekleştirerek kötü olmasını sağlamaktır. Önce bir araştırma yapmak için en iyi yaklaşımdır veya kurtarmak mikro hizmet için zaman tanıyın. Bir mikro hizmet sistem durumu olayları bilinçli kararlar almanıza ve etkili, kendini onarma hizmetleri oluşturmanıza yardımcı yardımcı olur.

Uygulama durumu denetler ASP.NET Core services bölümünde bu kılavuzun size uygun eylemleri için bir izleme hizmetine durumlarına rapor etmek için yeni bir ASP.NET HealthChecks Kitaplığı'nda, mikro kullanımı açıklanmaktadır.

### <a name="using-diagnostics-and-logs-event-streams"></a>Tanılama ve günlükleri Olay akışları kullanma

Günlükleri nasıl bir uygulama veya hizmet, özel durumlar, uyarıları ve basit bilgilendirici iletileri de dahil olmak üzere çalıştıran hakkında bilgi sağlar. Özel durum yığın izlemesi birden çok satıra yayılmış ayrıca sıklıkla gösterir. genellikle, her günlük olay, her bir satır içeren bir metin biçiminde olsa.

Tek yapılı sunucu tabanlı uygulamalar, yalnızca disk (bir günlük dosyası) bir dosyaya günlüklerini yazma ve herhangi bir aracı olarak analiz edin. Uygulamanın yürütülmesini sabit bir sunucu veya VM ile sınırlı olduğundan, bu genellikle olayları akışını çözümlemek için çok karmaşık değil. Ancak, burada bir orchestrator kümedeki birçok düğümleri arasında birden fazla hizmet yürütülen bir dağıtılmış uygulamada dağıtılmış olayları ilişkilendirmenize yapamamasına bir iştir.

Mikro hizmet tabanlı bir uygulama olayları veya logfiles çıkış akışına tek başına depolamak deneyin değil ve merkezi bir yerde olaylara yönlendirme yönetmek bile deneyin. Altında nerede çalıştığına yürütme ortamı altyapısı tarafından toplanacak bir standart çıktı için olay akışı, her işlem yalnızca yazmalısınız anlamı saydam olmalıdır. Bu olay akışı yönlendiriciler örneğidir [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), olay akışları birden fazla kaynaktan toplar ve sistemler çıktı için yayımlar. Bunlar bir geliştirme ortamı için basit standart çıktı içerebilir veya Bulut sistemleri ister [Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (için şirket içi uygulamalar için) ve [Azure tanılama](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Bile, gerçek zamanlı izleme günlükleri gibi ve ayrıca vardır iyi üçüncü taraf günlük analizi platformları ve uyarı, rapor, arayabilirsiniz Araçları [Splunk](http://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators durum ve tanılama bilgilerini yönetme

Mikro hizmet tabanlı bir uygulama oluşturduğunuzda, karmaşıklık ile ilgilenir gerekir. Elbette, tek bir mikro hizmet uğraşmanız basit olmakla birlikte düzinelerce veya türleri yüzlerce ve mikro örnekleri binlerce karmaşık bir sorun. Bunu neredeyse mikro hizmet mimarisi oluşturuyor değildir — kararlı ve bağlı bir sisteme sahip olmanız istiyorsanız, ayrıca yüksek kullanılabilirlik, çözümlenebilme, dayanıklılık, durum ve tanılama gerekir.

![](./media/image22.png)

**Şekil 4-22**. Bir uygulamanın sistem yönetimi için temel mikro hizmet platformudur

Şekil 4-22'de gösterilen karmaşık sorunları başınıza gidermenize çok zordur. Geliştirme ekiplerinin iş sorunlarını çözme ve mikro hizmet tabanlı yaklaşımlar olan özel uygulamalar oluşturmaya durmalısınız. Bunlar karmaşık altyapı sorunlarını çözme üzerinde durmalısınız değil; Bunlar kaldırdıysanız, mikro hizmet tabanlı bir uygulama maliyetini büyük olacaktır. Bu nedenle, orchestrators veya oluşturma ve bir hizmeti çalıştıran ve altyapı kaynakları verimli şekilde kullanma sabit sorunları çözmeyi deneyin mikro hizmet kümeler, olarak adlandırılır, mikro hizmet odaklı platformları vardır. Bu, bir mikro yaklaşım kullanan uygulamalar oluşturmanın karmaşıklıkları azaltır.

Farklı orchestrators benzer gibi görünebilir, ancak tanılama ve bunların her biri tarafından sunulan durumu denetimleri özellikler ve bazen OS platforma bağlı olarak olgunluk durumunu sonraki bölümde açıklandığı gibi farklı.

## <a name="additional-resources"></a>Ek kaynaklar

-   **On iki öğeli uygulama. XI. Günlükleri: Günlükleri Olay akışları olarak kabul**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Microsoft tanılama EventFlow kitaplığı.** GitHub depo.

    [*https://github.com/Azure/Diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **Azure tanılama nedir**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Windows bilgisayarları Azure günlük analizi hizmeti bağlanmak**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **Hangi, ortalama günlük: semantik günlük uygulama bloğu kullanarak**
    [*https://msdn.microsoft.com/library/dn440729 (v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk.** Resmi sitesi.
    [*http://www.splunk.com*](http://www.splunk.com)

-   **EventSource sınıfı**. Windows (ETW) için izleme olayları için API [ *https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)




>[!div class="step-by-step"]
[Önceki] (microservice-based-composite-ui-shape-layout.md) [sonraki] (scalable-available-multi-container-microservice-applications.md)
