---
title: Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik
description: Mikro hizmetler, geçici ağ ve yüksek kullanılabilirlik elde etmek için dayanıklı olması gereken bağımlılıklar hataları dayanacak şekilde tasarlanmış olması gerekir.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: a63b0c67e00ec91c5a91e1c6b84d1a38ab50e394
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672361"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik

Beklenmeyen hatalar uğraşmanızı uygulamalarınızdaki sorunları çözmeye özellikle dağıtılmış bir sistemde biridir. Özel durumları işleme geliştiriciler yazdığınız kod çoğunu içerir ve ayrıca test en çok zaman nerede harcandığını budur. Sorun, hataları işlemek için kod yazmaktan daha karmaşıktır. Mikro hizmet çalıştırıldığı makine başarısız olduğunda ne olur? Yalnızca bu mikro hizmet hatası (sabit sorun kendi kendine) algılamak ihtiyacınız, ancak ayrıca bir şey, mikro hizmet yeniden başlatmanız gerekir.

Bir mikro hizmet hatalara karşı dayanıklı olmalarını ve genellikle kullanılabilirlik için başka bir makinede yeniden başlatabiliyor olmanız gerekir. Bu esneklik aynı zamanda mikro hizmet adına mikro hizmet bu durumdan kurtarmak ve mikro hizmet başarıyla yeniden olmadığını kaydedilmiş duruma gelir. Diğer bir deyişle, vardır (işlem herhangi bir zamanda yeniden başlatabilirsiniz) işlem özelliği'nda dayanıklılık olması gerekir esnekliği durumu veya verileri (veri kaybı olmadan ve tutarlı veri kalır) yanı sıra.

Dayanıklılık sorunları, uygulama yükseltme sırasında hatalar oluştuğunda gibi diğer senaryolar sırasında compounded. En yeni sürüme ilerlemek veya bunun yerine tutarlı bir duruma korumak için önceki bir sürüme geri alma devam olup olmadığını belirlemek dağıtım sistemiyle çalışan mikro hizmet gerekir. Yetecek sayıda makine ileri taşıma tutmak kullanılabilir olup olmadığı ve mikro hizmet önceki sürümlerini kurtarmak nasıl gibi soruları göz önünde bulundurulması gerekir. Bu, bu kararların yapabilmeleri için uygulama ve orchestrator sistem durumu bilgileri yaymak üzere mikro hizmet gerektirir.

Dayanıklılık ek olarak, ilgili sistemlere nasıl bulut tabanlı davranmalıdır. Belirtildiği gibi bulut tabanlı bir sistemin hataları Kucak gerekir ve bunları otomatik olarak kurtarmaya denemeniz gerekir. Örneği için ağ veya kapsayıcı hatalar olması durumunda, istemci uygulamaları veya istemci hizmetlerini iletileri gönderme yeniden deneyin veya bulutta kısmi çoğu durumda olduğundan isteği yeniden denemek için bir strateji olması gerekir. [Dayanıklı uygulamalar uygulama](../implement-resilient-applications/index.md) bölümü bu kılavuzdaki kısmi hata işleme nasıl yöneliktir. Kitaplıklar gibi kullanarak üstel geri alma veya .NET Core devre kesici düzenini yeniden denemelerle tekniklerle açıklar [Polly](https://github.com/App-vNext/Polly), ilkeleri bu konu işlemek için çok çeşitli sunar.

## <a name="health-management-and-diagnostics-in-microservices"></a>Sistem durumu yönetimi ve mikro hizmet olarak tanılama

Belirgin, görünebilir ve genellikle kaçan, ancak bir mikro hizmet durumu ve tanılama bildirilmesi gerekir. Aksi takdirde, işlemleri açısından biraz Insight yoktur. Tanılama Olayları bağımsız bir hizmetler kümesi arasında ilişkilendirme ve olay siparişin anlamlı makine saat farklarından ilgilenme zordur. Anlaşılan protokolleri ve veri biçimleri üzerinde bir mikro hizmet ile etkileşimde bulunan aynı yolla Standartlaştırma sistem durumu ve sonuçta sorgulama ve görüntüleme için bir olay deposuna düştüğünden tanılama olayları günlüğe kaydetmek nasıl bir gereksinimi yoktur. Bir mikro hizmetler yaklaşımı sahip tuş, farklı ekipler, tek bir günlük biçimi kabul etmiş olursunuz. Var. uygulama tanılama olaylarını görüntüleme için tutarlı bir yaklaşım olması gerekir.

### <a name="health-checks"></a>Sistem durumu denetimleri

Sistem durumu, Tanılama'ya farklıdır. Geçerli durumuna uygun eylemleri raporlama mikro hizmet hakkında durumudur. İyi bir örnek, kullanılabilirliği sürdürmek için yükseltme ve dağıtım mekanizması ile çalışmaktadır. Bir hizmet şu anda bir işlem kilitlenmesi nedeniyle sağlıksız veya yeniden başlatma makine rağmen hizmet işletimsel olabilir. İhtiyacınız olan son bir şey bu yükseltme gerçekleştirerek yarışacağından olmasını sağlamaktır. İlk araştırma yapmak için en iyi yaklaşımdır veya kurtarmak mikro hizmet için zaman tanıyın. Bir mikro hizmet durumu olayları, bilgiye dayalı kararlar ve kendi kendini onaran hizmetleri oluşturma aslında yardımcı yardımcı olur.

İçinde [uygulama sistem durumu denetimleri ASP.NET Core Hizmetleri](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) bölümü bu kılavuz, biz durumlarına uygun olması için bir izleme hizmeti için rapor etmek için yeni bir ASP.NET HealthChecks kitaplıkta mikro hizmetlerin nasıl kullanıldığını açıklar Eylemler.

Beat Pulse, kullanılabilir adlı mükemmel bir açık kaynak kitaplığı kullanma seçeneğiniz de [GitHub](https://github.com/Xabaril/BeatPulse) ve bir [NuGet paketi](https://www.nuget.org/packages/BeatPulse/). Bu kitaplık bir sürpriz ile sistem durumu denetimleri de yapar, iki tür denetimi gerçekleştirir:

- **Canlılık**: İsteklerini kabul etmek ve yanıtlamak mümkün ise mikro hizmet başka bir deyişle, etkin olup olmadığını denetler. 
- **Hazırlık**: Mikro hizmet ne yapılacağını bakması yapabilmesi mikro hizmet'ın bağımlılıkları (veritabanı, kuyruk Hizmetleri, vb.) kendilerini hazır olup olmadığını kontrol. 

### <a name="using-diagnostics-and-logs-event-streams"></a>Tanılama ve günlükler, olay akışları kullanma

Günlükleri nasıl bir uygulama veya hizmeti, özel durumlar, uyarıları ve basit bilgilendirme iletileri de dahil olmak üzere çalışan hakkında bilgi sağlar. Özel durumlar da genellikle birden çok satırda yığın izlemesi gösterilmektedir, ancak genellikle, her olay, her bir satır içeren bir metin biçiminde günlüktür.

Tek parça sunucu tabanlı uygulamalarda yalnızca diskte (bir günlük dosyası) bir dosyaya günlükler yazar ve herhangi bir aracı ile analiz edin. Uygulama yürütme sabit bir sunucu veya VM için sınırlı olduğundan, genellikle akışı olayları çözümlemek için karmaşık değil. Ancak, birçok orchestrator küme düğümleri arasında birden çok hizmet nerede yürütülür dağıtılmış bir uygulamada dağıtılmış olayları ilişkilendirmenize işaretleyebilmesine zordur.

Bir mikro hizmet tabanlı uygulama olayları veya logfiles çıkış akışına kendisi tarafından depolamak deneyin değil ve merkezi bir yerde olaylara yönlendirme yönetmek bile deneyin. Bu, nerede çalıştığını yürütme ortamı altyapısı tarafından toplanacak altında bir standart çıktıya kendi olay akışı, her işlem yalnızca yazmalısınız anlamı saydam olmalıdır. Bu olay akışı yönlendiriciler örneğidir [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), olay akışları, birden fazla kaynaktan toplar ve sistemleri çıktı için yayımlar. Bunlar, bir geliştirme ortamı için basit standart çıktı içerebilir veya Bulut sistemleri [Azure İzleyici](https://azure.microsoft.com/services/monitor//) ve [Azure tanılama](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview). Ayrıca vardır iyi üçüncü taraf günlük analizi platformları ve uyarı raporu arayabilirsiniz araçları ve izleme günlükleri, hatta gerçek zamanlı gibi [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Düzenleyiciler durum ve tanılama bilgilerini yönetme

Mikro hizmet tabanlı bir uygulama oluşturduğunuzda, karmaşıklığı ile uğraşmak gerekir. Elbette, tek bir mikro hizmet uğraşmanız basittir, ancak düzinelerce, ister türleri yüzlerce ve binlerce örnek mikro hizmetler, karmaşık bir sorun olduğunu. Neredeyse, mikro hizmet mimarisi oluşturma değildir — bir kararlı ve cohesive sistemi olmasını istiyorsanız ayrıca yüksek kullanılabilirlik, çözümlenebilme, dayanıklılık, sistem durumu ve tanılama gerekir.

![Mikro hizmetlerin çalıştırmaya yönelik destek platform düzenleyicileri sağlayın.](./media/image22.png)

**Şekil 4-22**. Bir uygulamanın sistem durumu yönetimi için temel mikro hizmet platformudur

Şekil 4-22'de gösterilen karmaşık sorunları kendiniz çözmek çok zordur. Geliştirme ekiplerinin iş sorunlarını çözmeye ve mikro hizmet tabanlı bir yaklaşım ile özel uygulamalar oluşturan odaklanmanız gerekir. Bunlar karmaşık altyapı sorunlarını çözmeye odaklanın değil; kaldırdıysanız, herhangi bir mikro hizmet tabanlı uygulama maliyetini büyük olacaktır. Bu nedenle, mikro hizmet odaklı platformları için düzenleyiciler veya oluşturma ve bir hizmetin çalıştırılması ve altyapı kaynaklarını verimli bir şekilde kullanarak zor sorunları çözmek için çalışan mikro hizmet kümeleri olarak anılacaktır vardır. Bu, mikro hizmetler yaklaşımı kullanan uygulamalar oluşturma karmaşıklıkları azaltır.

Çeşitli düzenleyicileri benzer görünebilir, ancak tanılama ve sistem durumu denetimleri her biri tarafından sunulan özellikler ve işletim sistemi platformu bağlı olarak bazen bir olgunluk durumunu sonraki bölümde açıklandığı gibi farklı.

## <a name="additional-resources"></a>Ek kaynaklar

- **On iki Faktörlü uygulama. XI. Günlükleri: Günlükleri, olay akışları olarak değerlendir** \
  <https://12factor.net/logs>

- **Microsoft tanılama EventFlow Kitaplığı** GitHub deposu. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Azure tanılama nedir** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Windows bilgisayarları Azure İzleyici'hizmetine bağlayın** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Ne anlama gelir günlüğü: Semantik günlük uygulama bloğu kullanma** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** resmi sitesi. \
  <https://www.splunk.com/>

- **EventSource sınıfı** izleme için Windows (ETW) olayları için API \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Önceki](microservice-based-composite-ui-shape-layout.md)
>[İleri](scalable-available-multi-container-microservice-applications.md)
