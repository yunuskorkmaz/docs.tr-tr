---
title: Sunucusuz mimari değerlendirmeleri-sunucusuz uygulamalar
description: Durum yönetiminden ve kalıcı depolamadan, genişleme, günlüğe kaydetme, izleme ve Tanılama için sunucusuz uygulamalar tasarlama sorunlarını anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522429"
---
# <a name="serverless-architecture-considerations"></a>Sunucusuz mimaride dikkat edilmesi gerekenler

Sunucusuz bir mimariyi benimsemek, bazı güçlüklerle birlikte gelir. Bu bölümde, dikkat edilmesi gereken bazı yaygın hususlar incelenmektedir. Bu güçlüklerin tümünde çözüm vardır. Tüm mimari seçimlerinin yanı sıra, go sunucusuz kararı yalnızca, olumlu ve dezavantajların dikkatle ele alındıktan sonra yapılmalıdır. Uygulamanızın ihtiyaçlarına bağlı olarak, bir sunucusuz uygulamanın belirli bileşenler için doğru çözüm olmadığını belirleyebilirsiniz.

## <a name="managing-state"></a>Durumu yönetme

Mikro hizmetlerde olduğu gibi sunucusuz işlevler varsayılan olarak durum bilgisiz değildir. Önleme durumu sunucusuz 'ın daha kısa olmasını, ölçeğini genişletmek ve merkezi bir hata noktası olmadan dayanıklılık sağlamasını sağlar. Bazı durumlarda, iş süreçlerini durum gerektirir. İşleminiz durum gerektiriyorsa, iki seçeneğiniz vardır. Sunucusuz dışında bir modeli benimseyebilirsiniz veya durum sağlayan ayrı bir hizmetle etkileşim kurabilirsiniz. Durum eklemek çözümü karmaşıklaştırır ve ölçeği daha zor hale getirebilir ve tek bir hata noktası oluşturabilir. İşlevinizin kesinlikle durum gerektirip gerektirmediğini dikkatle düşünün. Yanıt "Evet" ise, bunu sunucusuz ile uygulamayı hala mantıklı olup olmadığını saptayın.

Sunucusuz 'ın avantajlarından ödün vermeden, benimseme durumuna yönelik birkaç çözüm vardır. Daha popüler çözümlerden bazıları şunlardır:

- Geçici bir veri deposu veya dağıtılmış önbellek kullanın, örneğin Redsıs
- Durumu SQL veya CosmosDB gibi bir veritabanında depola
- Dayanıklı işlevler gibi bir iş akışı altyapısı aracılığıyla durumu işleme

En alttaki satır, sunucusuz ile uygulamayı düşündüğünde işlem içinde herhangi bir durum yönetimine gerek duyduğuna dikkat etmeniz gerekir.

## <a name="long-running-processes"></a>Uzun süre çalışan süreçler

Sunucusuz 'in birçok avantajı, işlemlerin kısa ömürlü olmasını sağlar. Kısa çalışma süreleri, sunucusuz sağlayıcının kaynakları boşalttığından ve konaklar genelinde işlevleri paylaştığı ve paylaştığı kaynakları daha kolay hale getirir. Çoğu bulut sağlayıcısı, işlevinizin çalışacağı toplam süreyi 10 dakika içinde sınırlandırır. İşleminiz daha uzun sürbaşlayabilir, alternatif bir uygulama düşünebilirsiniz.

Birkaç özel durum ve çözüm vardır. Tek bir çözüm, işleminizi bir kez daha az çalışacak şekilde daha küçük bileşenlere bölmek olabilir. İşlem bağımlılıkları nedeniyle uzun süre çalışırsa, dayanıklı işlevler gibi bir çözüm kullanarak zaman uyumsuz bir iş akışını da düşünebilirsiniz. Dayanıklı işlevler, bir dış işlemin tamamlanmasını beklerken işleminizin durumunu duraklatır ve korur. Zaman uyumsuz işleme, gerçek işlemin çalışma süresini azaltır.

## <a name="startup-time"></a>Başlangıç zamanı

Sunucusuz uygulamalarla ilgili olası bir sorun başlangıç zamanı. Kaynakları korumak için, birçok sunucusuz sağlayıcı "isteğe bağlı" altyapıyı oluşturur. Bir sunucusuz işlev bir süre sonra tetiklendiğinde, işlevi barındıracak kaynakların oluşturulması veya yeniden başlatılması gerekebilir. Bazı durumlarda, soğuk başlar birkaç saniyelik gecikmeler oluşmasına neden olabilir. Başlangıç süresi sağlayıcılar ve hizmet düzeyleri arasında farklılık gösterir. Uygulamanın başarısı için en aza indirmek önemliyse, başlangıç zamanına yönelik birkaç yaklaşım vardır.

- Bazı sağlayıcılar, kullanıcıların altyapının "her zaman açık" olduğunu garanti eden hizmet düzeyleri için ödeme yapmasına olanak tanır.
- Canlı tutma mekanizması uygulayın ("uyanık" durumunda tutmak için uç noktaya ping yapın).
- Kapsayıcılı bir işlev yaklaşımı ile Kubernetes gibi Orchestration kullanın (konak zaten çalışıyor, yeni örneklerin dönmesini son derece hızlıdır).

## <a name="database-updates-and-migrations"></a>Veritabanı güncelleştirmeleri ve geçişleri

Sunucusuz kodun avantajı, uygulamanın tamamını yeniden dağıtmaya gerek kalmadan yeni işlevleri serbest bırakabilmenizi sağlar. Bu avantaj, ilişkili ilişkisel bir veritabanı olduğunda olumsuz bir hale gelebilir. Veritabanı şemalarında yapılan değişikliklerin sunucusuz güncelleştirmelerle eşitlenmesi zordur. Ek sorunlar, şeyler yanlış olduğunda ve değişikliklerin geri alınması gerektiğinde ortaya çıkmıştır. Veri bütünlüğü, mikro hizmetler ve sunucusuz işlevler için en iyi uygulama, kendi verilerinin sahibi olmasının bir nedenidir. Değişiklikleri tek bir işlem ve veri birimi olarak dağıtmak mümkündür. Gerçeklik, birçok eski sistem sunucusuz mimariyle mutabakatı gereken büyük bir arka uç veritabanı özelliğidir.

Şema sürümü oluşturmayı çözmeye yönelik popüler bir yaklaşım, mevcut özellikleri ve sütunları hiçbir şekilde değiştirmemek, bunun yerine yeni bilgiler eklemektir. Örneğin, yapılacaklar listesi için Boole "tamamlandı" bayrağını "tamamlanma tarihi" olarak değiştirmek için bir değişikliği göz önünde bulundurun. Eski alanı kaldırmak yerine veritabanı değişikliği şu şekilde olur:

1. Yeni bir "tamamlanma tarihi" alanı ekleyin.
1. "Tamamlandı" Boole alanını, tamamlanma tarihinin geçerli tarihten sonra olup olmadığını değerlendiren bir hesaplanan işleve dönüştürün.
1. Tamamlanan Boole değeri true olarak ayarlandığında tamamlandı tarihini geçerli tarihe ayarlamak için bir tetikleyici ekleyin.

Değişiklik dizisi, eski kodun "olduğu gibi" çalışmaya devam etmesini sağlar ve daha yeni sunucusuz işlevler yeni alandan faydalanabilir.

Sunucusuz mimarilerde bulunan veriler hakkında daha fazla bilgi için bkz. [Dağıtılmış veri yönetimi Için sorunlar ve çözümler](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Lemeyle

Sunucusuz "sunucu yok" anlamına gelen yaygın bir yanıltıcı olur. Aslında "daha az sunucu" gibi. Bir destek altyapısı, ölçeklendirmenin ne zaman geldiğini anlamak için önemlidir. Çoğu sunucusuz platform, olay yoğunluğu arttıkça altyapının ölçeklendirilmesi için bir denetim kümesi sağlar. Çeşitli seçeneklerden birini seçebilirsiniz, ancak stratejiniz işleve bağlı olarak farklılık gösterebilir. Ayrıca, işlevler genellikle ilgili bir ana bilgisayar altında çalıştırılır, böylece aynı konaktaki işlevler aynı ölçek seçeneklerine sahip olacaktır. Bu nedenle, ölçek gereksinimlerine göre hangi işlevlerin birlikte barındırıldığını düzenlemek ve stratejik hale eklemek gereklidir.

Kurallar, değişen parametrelere bağlı olarak genellikle ölçeği artırma (konak kaynaklarını artırma) ve genişleme (konak örneği sayısını artırma) belirler. Ölçek Tetikleyicileri için zamanlama, istek hızları, CPU kullanımı ve bellek kullanımı dahil olabilir. Daha yüksek performans genellikle daha fazla maliyetle gelir. Daha ucuz, tüketim tabanlı yaklaşımlar, istek oranı aniden arttıkça hızla ölçeklenmeyebilir. Önde gelen "sigorta maliyeti" ve kesin olarak "gitirken" ödeme yaparak, istek üzerine ani artışlar nedeniyle daha az yanıt vermek arasında bir denge vardır.

## <a name="monitoring-tracing-and-logging"></a>İzleme, izleme ve günlüğe kaydetme

DevOps 'ın genellikle daha fazla bir yönü dağıtıldıktan sonra uygulamaları izlerdir. Sunucusuz işlevleri izlemeye yönelik bir stratejinin olması önemlidir. En büyük zorluk genellikle bağıntılandır veya bir kullanıcı aynı etkileşimin bir parçası olarak birden çok işlevi çağırdığında, bu şekilde tanınması gerekir. Sunucusuz platformların çoğu, üçüncü taraf araçlara aktarılabilecek konsol günlüğüne izin verir. Telemetri toplamayı otomatik hale getirmek, bağıntı kimliklerini oluşturmak ve izlemek ve ayrıntılı Öngörüler sağlamak için belirli eylemleri izlemek için de seçenekler vardır. Azure, izleme ve analiz için Gelişmiş [Application Insights platformu](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) sağlar.

## <a name="inter-service-dependencies"></a>Hizmetler arası bağımlılıklar

Sunucusuz bir mimari, diğer işlevlere bağlı olan işlevleri içerebilir. Aslında, bir etkileşim ya da dağıtılmış işlemin bir parçası olarak birden fazla hizmetin her birini aramasını sağlamak için sunucusuz bir mimaride yaygın olmayan bir durumdur. Güçlü kuponu önlemek için, hizmetlerin birbirini doğrudan başvurmaması önerilir. Bir hizmetin uç noktasının değişmesi gerektiğinde, doğrudan başvurular büyük yeniden düzenleme ile sonuçlanabilir. Önerilen bir çözüm, bir istek türü için uygun uç noktasını sağlayan bir kayıt defteri gibi bir hizmet bulma mekanizması sağlamaktır. Farklı bir çözüm, hizmetler arasındaki iletişim için kuyruklar veya konular gibi mesajlaşma hizmetlerinden faydalanmaya yöneliktir.

## <a name="managing-failure-and-providing-resiliency"></a>Hatayı yönetme ve dayanıklılık sağlama

*Devre kesici deseninin*göz önünde bulundurulması de önemlidir: bazı nedenlerle bir hizmet başarısız olmaya devam ederse, bu hizmetin tekrar tekrar çağırmasının önerilmez. Bunun yerine, alternatif bir hizmet çağrılır veya bağımlı hizmetin sistem durumu yeniden oluşturulana kadar bir ileti döndürülür. Sunucusuz mimarinin, hizmet dışı bağımlılıkların çözümlenmesi ve yönetilmesi için strateji hesabına sahip olması gerekir.

Devre kesici düzenine devam etmek için, hizmetlerin hata toleranslı ve dayanıklı olması gerekir. Hata toleransı, uygulamanızın beklenmedik özel durumlar veya geçersiz durumlardan sonra bile çalışmaya devam etmesini sağlar. Hata toleransı genellikle kodun kendisinin bir işlevidir ve özel durumları işlemek için nasıl yazıldığı. Dayanıklılık, uygulamanın hatalardan kurtarılırken ne kadar uyumlu olduğunu ifade eder. Dayanıklılık genellikle sunucusuz platform tarafından yönetilir. Mevcut bir hata oluştuğunda platformun yeni bir sunucusuz işlev örneği alabilmesi gerekir. Her yeni örnek başarısız olduğunda, platformun yeni örnekleri dönmesini durdurmak için de yeterince akıllı olması gerekir.

Daha fazla bilgi için bkz. [devre kesici modelini uygulama](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Sürüm oluşturma ve yeşil/mavi dağıtımlar

Sunucusuz 'ın önemli bir avantajı, uygulamanın tamamını yeniden dağıtmaya gerek kalmadan belirli bir işlevi yükseltmeme özelliğidir. Yükseltmelerin başarılı olabilmesi için işlevlerin doğru kod sürümüne yönlendirilmesi için işlevleri sürümlenmiş olmalıdır. Yeni sürümleri dağıtmaya yönelik bir strateji da önemlidir. Yaygın bir yaklaşım, "yeşil/mavi dağıtımlar" kullanmaktır. Yeşil dağıtım, geçerli işlevdir. Yeni bir "mavi" sürümü üretime dağıtılır ve test edilir. Testler başarılı olduğunda, yeni sürümün canlı olması için yeşil ve mavi sürümler takas edilir. Herhangi bir sorunla karşılaşıldığında, geri dönebilir. Sürüm oluşturma ve yeşil/mavi dağıtımları desteklemek, sürüm değişikliklerini barındırmak ve dağıtımları işlemek için sunucusuz platformla çalışmak üzere işlevleri yazmanın bir birleşimini gerektirir. Olası bir yaklaşım, [Azure sunucusuz platform](azure-functions.md#proxies) bölümünde açıklanan proxy 'leri kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](serverless-architecture.md)
>[İleri](serverless-design-examples.md)
