---
title: Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik
description: Mikro hizmetler, yüksek kullanılabilirlik sağlamak için esnek olmaları gereken geçici ağ ve bağımlılık hatalarına dayanacak şekilde tasarlanmalıdır.
ms.date: 09/20/2018
ms.openlocfilehash: 1c0f75a8c68d1f84ba24c550e854edc5372cf7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094222"
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Mikro hizmetlerde esneklik ve yüksek kullanılabilirlik

Beklenmeyen hatalarla başa çıkmak, özellikle dağıtılmış bir sistemde çözülmesi en zor sorunlardan biridir. Geliştiricilerin yazdığı kodun çoğu özel durumları işleme içerir ve bu da en çok zaman sınama harcanan yerdir. Sorun, hataları işlemek için kod yazmaktan daha fazla ilgilidir. Mikro hizmetin çalıştığı makine arızalandığında ne olur? Sadece bu microservice arıza (kendi başına zor bir sorun) algılamak gerekir, ama aynı zamanda microservice yeniden başlatmak için bir şey gerekir.

Bir mikro hizmetin hatalara karşı dayanıklı olması ve kullanılabilirlik için başka bir makinede sık sık yeniden başlatabilmesi gerekir. Bu esneklik aynı zamanda mikro hizmet adına kaydedilen duruma, mikro hizmetin bu durumu kurtarıp kurtaramayacağıve mikro hizmetin başarılı bir şekilde yeniden başlatılıp başlatılamayacağına da bağlıdır. Başka bir deyişle, bilgi işlem yeteneğinde esneklik (işlem her zaman yeniden başlatılabilir) yanı sıra durum veya veri (veri kaybı ve veri tutarlı kalır) esneklik olması gerekir.

Esneklik sorunları, uygulama yükseltmesi sırasında hatalar oluştuğunda olduğu gibi diğer senaryolar sırasında birleşir. Dağıtım sistemiyle çalışan microservice'in, tutarlı bir durumu korumak için daha yeni sürüme geçmeye devam edip edemeyeceğini veya bunun yerine önceki sürüme geri dönüp dönemeyeceğini belirlemesi gerekir. İlerlemeye devam etmek için yeterli makine nin kullanılabilir olup olmadığı ve mikrohizmetin önceki sürümlerini nasıl kurtarılacak gerektiği gibi soruların dikkate alınması gerekir. Bu, genel uygulama ve orkestratör bu kararları böylece sağlık bilgileri yayılmak için mikrohizmet gerektirir.

Buna ek olarak, esneklik bulut tabanlı sistemlerin nasıl olması gerektiğiyle ilgilidir. Belirtildiği gibi, bulut tabanlı bir sistem hataları benimsemeli ve otomatik olarak bunları kurtarmak için çalışmalısınız. Örneğin, ağ veya kapsayıcı hataları durumunda, istemci uygulamalarının veya istemci hizmetlerinin, buluttaki hatalar kısmi olduğundan, ileti göndermeyi veya istekleri yeniden denemeyi yeniden deneme stratejisi olmalıdır. Bu kılavuzdaki [Esnek Uygulamaları Uygulama](../implement-resilient-applications/index.md) bölümü, kısmi hatanın nasıl işleyeceğini ele almaktadır. Bu, bu konuyu işlemek için çok çeşitli ilkeler sunan [Polly](https://github.com/App-vNext/Polly)gibi kütüphaneleri kullanarak üstel geri tepme veya .NET Core'daki Devre Kesici deseni gibi yeniden denemeler gibi teknikleri açıklar.

## <a name="health-management-and-diagnostics-in-microservices"></a>Mikrohizmetlerde sağlık yönetimi ve tanılama

Bu açık görünebilir, ve genellikle göz ardı edilir, ama bir microservice sağlık ve tanı bildirmek gerekir. Aksi takdirde, bir operasyon açısından çok az içgörü var. Bir dizi bağımsız hizmet genelinde tanıolaylarının ilişkilendirilmesi ve olay düzenini anlamak için makine saat eğriliği ile uğraşmak zordur. Üzerinde anlaşmaya varılan protokoller ve veri biçimleri üzerinde bir mikro hizmetle etkileşimkurduğunuz gibi, sistem durumu ve tanılama olaylarını nasıl günlüğe kaydedebilirsiniz ve sonuçta sorgulama ve görüntüleme için bir olay deposunda son kullanmanız için de standardizasyon alabilirsiniz. Mikro hizmetler yaklaşımında, farklı ekiplerin tek bir günlük biçimi üzerinde anlaştığı anahtardır. Uygulamadaki tanıolaylarını görüntülemek için tutarlı bir yaklaşım olması gerekir.

### <a name="health-checks"></a>Sistem durumu denetimleri

Sağlık tanıdan farklıdır. Sağlık, uygun eylemleri yapmak için geçerli durumunu bildiren mikro hizmetle ilgilidir. İyi bir örnek, kullanılabilirliği korumak için yükseltme ve dağıtım mekanizmaları ile çalışmaktır. Bir hizmet şu anda bir işlem çökmesi veya makinenin yeniden başlatılması nedeniyle sağlıksız olsa da, hizmet yine de çalışır durumda olabilir. İhtiyacınız olan son şey bir yükseltme gerçekleştirerek bu daha kötü hale getirmektir. En iyi yaklaşım, ilk olarak bir araştırma yapmak veya mikro hizmetin kurtarılması için zaman tanımaktır. Bir mikro hizmetten gelen sağlık olayları bilinçli kararlar vermemize ve aslında kendi kendini iyileştirme hizmetleri oluşturmamıza yardımcı olur.

Bu kılavuzun ASP.NET Temel hizmetler bölümünde [sağlık denetimleri uygulamada,](../implement-resilient-applications/monitor-app-health.md#implement-health-checks-in-aspnet-core-services) uygun eylemleri gerçekleştirebilmeleri için durumlarını bir izleme hizmetine bildirebilmeleri için mikro hizmetlerinizde yeni bir ASP.NET HealthChecks kitaplığı nasıl kullanılacağını açıklarız.

Ayrıca, [GitHub'da](https://github.com/Xabaril/BeatPulse) ve [NuGet paketi](https://www.nuget.org/packages/BeatPulse/)olarak kullanılabilen Beat Pulse adlı mükemmel bir açık kaynak kitaplığını da kullanma seçeneğiniz vardır. Bu kitaplık aynı zamanda, bir bükülme ile sağlık denetimleri yapar, bu denetimleri iki tür işler:

- **Canlılık**: Mikro hizmetin canlı olup olmadığını, yani istekleri kabul edip yanıtveremeyeceklerini kontrol eder.
- **Hazırlık**: Mikro hizmetin bağımlılıklarının (Veritabanı, kuyruk hizmetleri, vb.) kendileri hazır olup olmadığını denetler, böylece mikro hizmet yapması gerekeni yapabilir.

### <a name="using-diagnostics-and-logs-event-streams"></a>Tanılama ve günlükolay akışlarını kullanma

Günlükler, özel durumlar, uyarılar ve basit bilgilendirme iletileri de dahil olmak üzere bir uygulamanın veya hizmetin nasıl çalıştırılaçlarla ilgili bilgiler sağlar. Genellikle, her günlük olay başına bir satıriçeren bir metin biçimindedir, ancak özel durumlar da genellikle yığın izlemeyi birden çok satır arasında gösterir.

Yekpare sunucu tabanlı uygulamalarda, diskteki bir dosyaya günlükler (günlük dosyası) yazabilir ve ardından herhangi bir araçla analiz edebilirsiniz. Uygulama yürütme sabit bir sunucu veya VM ile sınırlı olduğundan, genellikle olayların akışını çözümlemek için çok karmaşık değildir. Ancak, bir orkestratör kümesinde birçok düğüm boyunca birden çok hizmetin yürütüldüğü dağıtılmış bir uygulamada, dağıtılmış olayları ilişkilendirebilmek zor bir durumdur.

Mikro hizmet tabanlı bir uygulama, olayların çıktı akışını veya günlük dosyalarını tek başına depolamaya çalışmamalı ve olayların merkezi bir yere yönlendirmesini yönetmeye çalışmamalıdır. Saydam olmalıdır, yani her işlem olay akışını, çalıştığı yürütme ortamı altyapısı tarafından toplanacak standart bir çıktıya yazmalıdır. Bu olay akışı yönlendiricilerine bir örnek, birden çok kaynaktan olay akışları toplayan ve çıktı sistemlerine yayınlayan [Microsoft.Diagnostic.EventFlow'dur.](https://github.com/Azure/diagnostics-eventflow) Bunlar, bir geliştirme ortamı veya [Azure Monitörü](https://azure.microsoft.com/services/monitor//) ve [Azure Tanılama](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostics-extension-overview)gibi bulut sistemleri için basit standart çıktıyı içerebilir. [Splunk](https://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA)gibi gerçek zamanlı olarak bile günlükleri arayabilen, uyarabilen, raporlayabilen ve izleyebilen iyi üçüncü taraf günlük analiz platformları ve araçları da vardır.

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Sağlık ve teşhis bilgilerini yöneten orkestratörler

Mikro hizmet tabanlı bir uygulama oluşturduğunuzda, karmaşıklıkla başa çıkmanız gerekir. Tabii ki, tek bir microservice ile başa çıkmak için basit, ama düzinelerce veya yüzlerce türleri ve mikro hizmetler örnekleri binlerce karmaşık bir sorundur. Bu sadece mikro hizmet mimarinizi oluşturmakla ilgili değildir- aynı zamanda istikrarlı ve uyumlu bir sisteme sahip olmak istiyorsanız yüksek kullanılabilirlik, adreslenebilirlik, esneklik, sağlık ve tanılama gerekir.

![Mikro hizmetler için bir destek platformu sağlayan kümelerin diyagramı.](./media/resilient-high-availability-microservices/microservice-platform.png)

**Şekil 4-22**. Microservice Platformu, bir uygulamanın sağlık yönetimi için temel dir

Şekil 4-22'de gösterilen karmaşık problemleri kendi başınıza çözmek çok zordur. Geliştirme ekipleri, mikrohizmet tabanlı yaklaşımlarla iş sorunlarını çözmeye ve özel uygulamalar oluşturmaya odaklanmalıdır. Karmaşık altyapı sorunlarını çözmeye odaklanmamalılar; onlar olsaydı, herhangi bir microservice tabanlı uygulama maliyeti büyük olurdu. Bu nedenle, bir hizmet oluşturma ve çalıştırma ve altyapı kaynaklarını verimli bir şekilde kullanma nın zor sorunlarını çözmeye çalışan, orkestratör veya mikro hizmet kümeleri olarak adlandırılan mikro hizmet odaklı platformlar vardır. Bu, mikro hizmetler yaklaşımı kullanan bina uygulamalarının karmaşıklığını azaltır.

Farklı orkestratörler benzer gelebilir, ancak her biri tarafından sunulan tanılama ve sağlık kontrolleri özellikleri ve olgunluk durumu, bazen işletim sistemi platformuna bağlı olarak, bir sonraki bölümde açıklandığı gibi farklıdır.

## <a name="additional-resources"></a>Ek kaynaklar

- **On iki faktörlü uygulama. XI. Günlükler: Günlükleri olay akışı olarak ele** \
  <https://12factor.net/logs>

- **Microsoft Tanıolay Akışı Kitaplığı** GitHub repo. \
  <https://github.com/Azure/diagnostics-eventflow>

- **Azure Tanılama Nedir** \
  <https://docs.microsoft.com/azure/azure-diagnostics>

- **Windows bilgisayarlarını Azure Monitör hizmetine bağlama** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows>

- **Günlük Ne Demek: Anlamsal Günlük Uygulama Bloğu kullanma** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn440729(v=pandp.60)>

- **Splunk** Resmi site. \
  <https://www.splunk.com/>

- **EventSource Sınıfı** Windows (ETW) için izleme olayları için API \
  [https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource](xref:System.Diagnostics.Tracing.EventSource)

>[!div class="step-by-step"]
>[Önceki](microservice-based-composite-ui-shape-layout.md)
>[Sonraki](scalable-available-multi-container-microservice-applications.md)
