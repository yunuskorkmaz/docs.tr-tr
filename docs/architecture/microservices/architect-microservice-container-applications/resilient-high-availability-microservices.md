---
title: Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik
description: Mikro hizmetlerin, geçici ağ ve bağımlılıklar hatalarıyla birlikte kullanılması için tasarlanmaları gerekir, bu da yüksek kullanılabilirlik elde etmek için dayanıklı olmalıdır.
ms.date: 09/20/2018
ms.openlocfilehash: 601255c1e6941b2de9fdb34098dea7edf6d8b987
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172456"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik

Beklenmedik hatalarla ilgilenirken, özellikle dağıtılmış bir sistemde çözülecek en zor sorunlardan biridir. Geliştiricilerin yazacağı kodun büyük bölümü özel durumları işlemeye ve bu da en fazla saatin test edilirken harcanmasını içerir. Sorun, hataların işlenmesi için kodun yazılmasından daha karmaşıktır. Mikro hizmetin çalıştığı makine başarısız olduğunda ne olur? Bu mikro hizmet başarısızlığını (kendi kendine yönelik bir sorun) algılamanıza gerek kalmaz, ancak mikro hizmetinizi yeniden başlatmak için de bir işlem yapmanız gerekir.

Mikro bir hizmetin hatalara karşı dayanıklı olması ve başka bir makinede kullanılabilirlik için sık olarak yeniden başlatılması gerekir. Bu esneklik, mikro hizmetin bu durumu ' den kurtarabileceği ve mikro hizmetin başarıyla yeniden başlatılıp başlatılmayacağını belirten mikro hizmet adına kaydedilmiş duruma da gelir. Diğer bir deyişle, işlem yeteneğinin dayanıklılık olması gerekir (işlem herhangi bir zamanda yeniden başlatılabilir) ve durum veya verilerde esnekliği (veri kaybı yoktur ve veriler tutarlı kalır).

Dayanıklılık sorunları, bir uygulama yükseltmesi sırasında hataların oluşma gibi başka senaryolar sırasında da bir bakış sürecinde olacaktır. Dağıtım sistemiyle çalışan mikro hizmetin, daha yeni bir sürüme ilerleyemeyeceğini veya daha önce tutarlı bir durumu korumak için önceki bir sürüme geri dönerek devam edip etmediğini belirlemesi gerekir. Daha önce taşınabileceği ve mikro hizmetin önceki sürümlerinin nasıl kurtarılacağı hakkında daha fazla sayıda makinenin kabul edilip edilmeyeceği gibi sorular. Bu, tüm uygulama ve Orchestrator bu kararları verebilmeleri için mikro hizmetin sistem durumu bilgilerini yaymasını gerektirir.

Ayrıca, dayanıklılık bulut tabanlı sistemlerin nasıl davranması ile ilgilidir. Belirtildiği gibi, bulut tabanlı bir sistem hatalara ve bunları otomatik olarak kurtarmayı denemelidir. Örneğin, ağ veya kapsayıcı hatalarıyla ilgili durumlarda, istemci uygulamalarının veya istemci hizmetlerinin iletileri göndermeyi veya istekleri yeniden denemeyi yeniden denemek için bir stratejisine sahip olması gerekir, çünkü buluttaki hataların çoğu kısmen kısmi bir durumdur. Bu kılavuzdaki dayanıklı [uygulamalar uygulama](../implement-resilient-applications/index.md) bölümünde kısmi hatanın nasıl işleneceği ele alınmaktadır. Bu konuyu işlemek için çok çeşitli ilkeler sunan, üstel geri alma veya .NET Core 'daki devre kesici düzeniyle yeniden denemeler [gibi teknikleri](https://github.com/App-vNext/Polly)açıklar.

## <a name="health-management-and-diagnostics-in-microservices"></a>Mikro hizmetlerde sistem durumu yönetimi ve tanılama

Açık görünebilir ve genellikle çok daha fazla görünür, ancak bir mikro hizmet, sistem durumunu ve tanılamayı raporlamaları gerekir. Aksi takdirde, bir işlem perspektifinden çok daha fazla öngörü vardır. Bir bağımsız hizmet kümesi genelinde tanılama olaylarının bağıntılandırın ve olay sırası 'nın mantıklı olması için makine saati eğimiyle ilgilenme. Kabul edilen protokoller ve veri biçimleri üzerinde bir mikro hizmetle etkileşimde bulunmanızın yanı sıra, sorgulama ve görüntüleme amacıyla bir olay deposunda son görüntülenen sistem durumu ve tanılama olaylarının nasıl günlüğe alınacağını belirleme gereksinimi vardır. Mikro hizmetler yaklaşımında, farklı takımların tek bir günlük biçiminde kabul ettığı anahtardır. Uygulamada Tanılama olaylarını görüntülemek için tutarlı bir yaklaşım olması gerekir.

### <a name="health-checks"></a>Sistem durumu denetimleri

Sağlık, tanılamalardan farklıdır. Sistem durumu, uygun işlemleri gerçekleştirmek için geçerli durumunu raporlayan mikro hizmet ile ilgilidir. İyi bir örnek, kullanılabilirliği sürdürmek için yükseltme ve dağıtım mekanizmalarıyla birlikte çalışıyor. Bir hizmet, işlem kilitlenmesi veya makinenin yeniden başlatılması nedeniyle şu anda sağlıksız olabilir, ancak hizmet hala çalışıyor olabilir. İhtiyacınız olan son şey, bir yükseltme gerçekleştirerek bunu daha kötü hale getirmenize olanak sağlar. En iyi yaklaşım, önce araştırılması veya mikro hizmetin kurtarılması için zaman vermaktır. Mikro bir hizmetten gelen sistem durumu olayları bilinçli kararlar almanıza ve etkili bir şekilde kendi kendine düzeltme hizmetleri oluşturmaya yardımcı olur.

Bu kılavuzun [ASP.NET Core Hizmetleri bölümünde sistem durumu denetimleri uygulama](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) bölümünde, mikro hizmetinizdeki yeni bir ASP.net healthdenetimleri kitaplığının nasıl kullanılacağını açıklayacağız. bu sayede, uygun işlemleri gerçekleştirmek için durumunu bir izleme hizmetine bildirebilirler.

Ayrıca [GitHub](https://github.com/Xabaril/BeatPulse) 'da ve bir [NuGet paketi](https://www.nuget.org/packages/BeatPulse/)olarak kullanılabilir olan uygun olmayan bir açık kaynaklı kitaplık kullanma seçeneğiniz de vardır. Bu kitaplık Ayrıca sistem durumu denetimleri de yapar ve bu da iki tür denetimi işler:

- **Lida**: mikro hizmetin etkin olup olmadığını denetler, diğer bir deyişle, istekleri kabul edip yanıtlayabilir.
- **Hazırlık**: mikro hizmetin bağımlılıklarının (veritabanı, kuyruk hizmetleri vb.) kendi kendine hazır olup olmadığını denetler, bu nedenle mikro hizmet, ne olması gerektiğini yapabilir.

### <a name="using-diagnostics-and-logs-event-streams"></a>Tanılama ve günlük olay akışlarını kullanma

Günlükler, özel durumlar, uyarılar ve basit bilgilendirici iletiler de dahil olmak üzere bir uygulama veya hizmetin nasıl çalıştığı hakkında bilgi sağlar. Genellikle, her günlük olay başına tek satırlık bir metin biçiminde bulunur, ancak özel durumlar genellikle birden çok satırda yığın izlemesini gösterir.

Tek parçalı sunucu tabanlı uygulamalarda, günlükleri disk üzerindeki bir dosyaya (günlük dosyası) yazabilir ve ardından herhangi bir araçla çözümleyebilirsiniz. Uygulama yürütmesi bir sabit sunucu veya VM ile sınırlı olduğundan, genellikle olay akışını çözümlemek için çok karmaşık değildir. Ancak, bir Orchestrator kümesindeki çok sayıda düğümde birden fazla hizmetin yürütüldüğü dağıtılmış bir uygulamada, dağıtılmış olayları ilişkilendirebilmek zor olur.

Mikro hizmet tabanlı bir uygulama, olayların veya günlük dosyalarının çıkış akışını tek başına depolamayı denememelidir, hatta olayların yönlendirilmesini merkezi bir yere yönetmeyi denememelidir. Saydam olmalıdır, yani her bir işlemin olay akışını, altında çalıştığı yürütme ortamı altyapısı tarafından toplanacak standart bir çıkışa yazması gerekir. Bu olay akışı yönlendiricilerine bir örnek, birden fazla kaynaktan gelen olay akışlarını toplayan ve çıkış sistemlerine yayımlayan [Microsoft. Diagnostic. EventFlow](https://github.com/Azure/diagnostics-eventflow)' dır. Bunlar, bir geliştirme ortamı için basit standart çıkış veya [Azure izleyici](https://azure.microsoft.com/services/monitor//) ve [Azure tanılama](/azure/azure-monitor/platform/diagnostics-extension-overview)gibi bulut sistemleri içerebilir. Ayrıca, ara, uyarı, rapor ve [izleme gibi çok](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA)farklı üçüncü taraf Günlük Analizi platformları ve araçları, gerçek zamanlı olarak da kullanabilirsiniz.

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Sistem durumu ve tanılama bilgilerini yöneten düzenleyiciler

Mikro hizmet tabanlı bir uygulama oluşturduğunuzda karmaşıklıkla uğraşmanız gerekir. Tabii ki tek bir mikro hizmet, ile uğraşmak için basittir, ancak onlarca veya yüzlerce tür ve mikro hizmetlerin binlerce örneği karmaşık bir sorundur. Yalnızca mikro hizmet mimarinizi oluşturma hakkında bilgi sahibi olmak için, kararlı ve birbirine bağlı bir sisteme sahip olmak istiyorsanız yüksek kullanılabilirlik, adreslenebilirlik, dayanıklılık, sağlık ve Tanılamalar da gereklidir.

![Mikro hizmetler için destek platformu sağlayan kümelerin diyagramı.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Şekil 4-22**. Mikro hizmet platformu, bir uygulamanın sistem durumu yönetimi için temel

Şekil 4-22 ' de gösterilen karmaşık sorunlar kendi başınıza çözülememektedir. Geliştirme ekipleri, mikro hizmet tabanlı yaklaşımlar sayesinde iş sorunlarının çözümüne ve özel uygulamalar oluşturmaya odaklanmalıdır. Karmaşık altyapı sorunlarını çözmeye odaklanmamalıdır; Bu durumda, mikro hizmet tabanlı uygulamaların maliyeti çok büyük olur. Bu nedenle, bir hizmet oluşturma ve çalıştırma ve altyapı kaynaklarını verimli bir şekilde kullanma hakkında Sabit sorunları çözmeye çalışan, düzenleyiciler veya mikro hizmet kümeleri olarak adlandırılan mikro hizmet odaklı platformlar vardır. Bu, mikro hizmetler yaklaşımını kullanan uygulamalar oluşturmanın karmaşıklıklarını azaltır.

Farklı düzenleyiciler benzer şekilde değişebilir, ancak her biri tarafından sunulan tanılama ve sistem durumu denetimleri, sonraki bölümde açıklandığı gibi, işletim sistemi platformuna bağlı olarak, bazen işletim sisteminde ve durum durumunda farklılık gösterir.

## <a name="additional-resources"></a>Ek kaynaklar

- **On Iki öğeli App. XI. Günlükler: günlükleri olay akışları olarak Işle** \
  <https://12factor.net/logs>

- **Microsoft tanılama EventFlow kitaplığı** GitHub deposu. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Azure Tanılama nedir?** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Windows bilgisayarlarını Azure Izleyici hizmetine bağlama** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Ne anlama geldiğini günlüğe kaydetme: anlam günlüğü uygulama bloğunu kullanma** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** Resmi site. \
  <https://www.splunk.com/>

- **EventSource sınıfı** Windows için olay izleme için API (ETW) \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Önceki](microservice-based-composite-ui-shape-layout.md) 
> [Sonraki](scalable-available-multi-container-microservice-applications.md)
