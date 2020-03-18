---
title: Sunucusuz mimari hususlar - Serverless uygulamaları
description: Devlet yönetiminden kalıcı depolamadan ölçeklendirmeye, günlüğe kaydetmeye, izlemeve tanılamaya kadar sunucusuz uygulamaları tanımlamanın zorluklarını anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522429"
---
# <a name="serverless-architecture-considerations"></a>Sunucusuz mimaride dikkat edilmesi gerekenler

Sunucusuz bir mimari benimsemek bazı zorluklarla birlikte gelir. Bu bölümde dikkat edilmesi gereken daha yaygın hususlardan bazıları incelenebilmelidir. Tüm bu zorlukların çözümleri vardır. Tüm mimari seçimlerde olduğu gibi, sunucusuz gitme kararı ancak artıları ve eksileri dikkatlice göz önünde bulundurularak verilmelidir. Uygulamanızın gereksinimlerine bağlı olarak, sunucusuz bir uygulamanın belirli bileşenler için doğru çözüm olmadığına karar verebilirsiniz.

## <a name="managing-state"></a>Devleti yönetme

Sunucusuz işlevler, genel olarak mikro hizmetlerde olduğu gibi, varsayılan olarak durumsuz. Durum kaçınmak, sunucusuzların geçici olmasını, ölçeklendirmesini ve merkezi bir hata noktası olmadan esneklik sağlamasını sağlar. Bazı durumlarda, iş süreçleri devlet gerektirir. İşleminizin durum gerektiriyorsa, iki seçeneğiniz var. Sunucusuz dışında bir model benimseyebilir veya durum sağlayan ayrı bir hizmetle etkileşimkurabilirsiniz. Durum eklemek çözümü zorlaştırabilir ve ölçeklendirmeyi zorlaştırabilir ve potansiyel olarak tek bir hata noktası oluşturabilir. İşlevinizin kesinlikle durum gerekip gerekmediğini dikkatlice düşünün. Yanıt "evet" ise, sunucusuz olarak uygulamanın mantıklı olup olmadığını belirleyin.

Sunucusuz yararları ödün vermeden devlet benimsemek için çeşitli çözümler vardır. Daha popüler çözümlerden bazıları şunlardır:

- Redis gibi geçici bir veri deposu veya dağıtılmış önbellek kullanma
- SQL veya CosmosDB gibi bir veritabanında depo durumu
- Duruma dayanıklı işlevler gibi bir iş akışı altyapısı üzerinden işleme

Alt satırda, sunucusuz ile uygulamayı düşündüğünüz işlemler içinde herhangi bir devlet yönetimi için ihtiyaç farkında olması gerektiğidir.

## <a name="long-running-processes"></a>Uzun süren süreçler

Sunucusuzların birçok faydası, işlemlerin geçici olmasına dayanır. Kısa çalışma süreleri, sunucusuz sağlayıcının işlevleri sona ererken kaynakları boşaltmasını ve işlevleri ana bilgisayarlar arasında paylaşmasını kolaylaştırır. Çoğu bulut sağlayıcısı, işlevinizin çalıştırabileceği toplam süreyi yaklaşık 10 dakika ile sınırlar. İşleminiz daha uzun sürebilirse, alternatif bir uygulama düşünebilirsiniz.

Birkaç istisna ve çözüm vardır. Bir çözüm, işleminizi tek tek çalıştırmanın daha az zaman alan daha küçük bileşenlere dönüştürülmesi olabilir. İşlemleriniz bağımlılıklar nedeniyle uzun sürüyorsa, dayanıklı işlevler gibi bir çözüm kullanarak eşzamanlı bir iş akışı da düşünebilirsiniz. Dayanıklı işlevler, tamamlanması için harici bir işlemi beklerken işleminizin durumunu duraklatabilir ve korur. Eşzamanlı işleme, gerçek işlemin çalışma süresini azaltır.

## <a name="startup-time"></a>Başlangıç zamanı

Sunucusuz uygulamalarla ilgili olası endişelerden biri başlangıç zamanıdır. Kaynakları korumak için, birçok sunucusuz sağlayıcı "isteğe bağlı" altyapı oluşturur. Bir süre sonra sunucusuz bir işlev tetiklendiğinde, işlevi barındıracak kaynakların oluşturulması veya yeniden başlatılması gerekebilir. Bazı durumlarda, soğuk başlar birkaç saniye gecikmelere neden olabilir. Başlangıç süresi sağlayıcılar ve hizmet düzeyleri arasında değişir. Uygulamanın başarısı için en aza indirmek önemliyse, başlangıç süresini ele almak için birkaç yaklaşım vardır.

- Bazı sağlayıcılar, kullanıcıların altyapının "her zaman açıktır" garanti eden hizmet düzeyleri için ödeme ödemesine izin verir.
- Bir keep-alive mekanizması uygulayın ("uyanık" tutmak için bitiş noktası ping).
- Kapsayıcı bir işlev yaklaşımı ile Kubernetes gibi orkestrasyon kullanın (ana bilgisayar zaten yeni örnekleri kadar dönen son derece hızlı çalışıyor).

## <a name="database-updates-and-migrations"></a>Veritabanı güncelleştirmeleri ve geçişler

Sunucusuz kodun bir avantajı, tüm uygulamayı yeniden dağıtmak zorunda kalmadan yeni işlevler serbest bırakabilmektir. İlişkisel bir veritabanı söz konusu olduğunda bu avantaj bir dezavantaj haline gelebilir. Veritabanı şemalarında yapılan değişiklikleri sunucusuz güncelleştirmelerle eşitlemek zordur. İşler ters gittiğinde ve değişiklikler geri alınmalıdır. Veri bütünlüğü, mikro hizmetler ve sunucusuz işlevler için en iyi uygulamanın kendi verilerine sahip olmalarının bir nedenidir. Değişiklikleri tek bir bilgi işlem ve veri birimi olarak dağıtmak mümkündür. Gerçek şu ki, birçok eski sistem, sunucusuz mimarisi ile uzlaştırılması gereken büyük bir arka uç veritabanına sahiptir.

Şema sürümünü çözmek için popüler bir yaklaşım varolan özellikleri ve sütunları değiştirmek için asla, ancak yeni bilgi eklemektir. Örneğin, bir yapılacaklar listesi için Boolean "tamamlanmış" bayrağından "tamamlanmış tarihe" geçmek için bir değişiklik düşünün. Veritabanı değişikliği, eski alanı kaldırmak yerine:

1. Yeni bir "tamamlanmış tarih" alanı ekleyin.
1. "Tamamlanmış" Boolean alanını, tamamlanan tarihin geçerli tarihten sonra olup olmadığını değerlendiren bir hesaplanmış işleve dönüştürün.
1. Tamamlanan Boolean'ın doğru ayarlandığı geçerli tarihe tamamlanmış tarihi ayarlamak için bir tetikleyici ekleyin.

Yeni sunucusuz işlevler yeni alandan yararlanabiliyorken, değişiklik sırası eski kodun "olduğu gibi" çalıştırılabilmesini sağlar.

Sunucusuz mimarideki veriler hakkında daha fazla bilgi [için, dağıtılmış veri yönetimi için Zorluklar ve çözümler](../microservices/architect-microservice-container-applications/distributed-data-management.md)bölümüne bakın.

## <a name="scaling"></a>Ölçeklendirme

Sunucusuz'un "sunucu yok" anlamına geldiğini niçin yanlış bir yoruma sayılsın? Aslında "daha az sunucu." Bir destek altyapısı nın olması, ölçekleme söz konusu olduğunda anlaşılması önemlidir. Çoğu sunucusuz platform, olay yoğunluğu arttığında altyapının nasıl ölçeklendirilebildiğini işlemek için bir denetim kümesi sağlar. Çeşitli seçenekler arasından seçim yapabilirsiniz, ancak stratejiniz işleve bağlı olarak değişebilir. Ayrıca, işlevler genellikle ilgili bir ana bilgisayar altında çalıştırılır, böylece aynı ana bilgisayardaki işlevler aynı ölçek seçeneklerine sahiptir. Bu nedenle ölçek gereksinimlerine göre hangi işlevlerin birlikte barındırıldığı organize etmek ve stratejilendirmek gerekir.

Kurallar genellikle değişen parametrelere göre nasıl ölçeklendirileceği (ana bilgisayar kaynaklarını artıracağını) ve ölçeklendirmeyi (ana bilgisayar örneklerinin sayısını artıracağını) belirtir. Ölçekler için tetikleyiciler zamanlama, istek oranları, CPU kullanımı ve bellek kullanımını içerebilir. Daha yüksek performans genellikle daha büyük bir maliyetle gelir. Daha az pahalı, tüketime dayalı yaklaşımlar, istek oranı aniden arttığında o kadar hızlı ölçeklendirilemez. Ön "sigorta maliyeti" kadar ödeme arasında bir trade-off kesinlikle "gitmek" ve talep ani artışlar nedeniyle daha yavaş tepkiler riski ödeme arasında dır.

## <a name="monitoring-tracing-and-logging"></a>İzleme, izleme ve günlüğe kaydetme

DevOps'un gözden kaçan bir yönü, dağıtıldıktan sonra uygulamaları izlemektir. Sunucusuz işlevleri izlemek için bir stratejiye sahip olmak önemlidir. En büyük zorluk genellikle korelasyon veya bir kullanıcı aynı etkileşimin bir parçası olarak birden fazla işlevi aradığında tanıma. Çoğu sunucusuz platform, üçüncü taraf araçlara içe aktarılabilen konsol günlüğe kaydetmeye izin verir. Telemetri koleksiyonunu otomatikleştirmek, korelasyon iLikleri oluşturmak ve izlemek ve ayrıntılı öngörüler sağlamak için belirli eylemleri izlemek için seçenekler de vardır. Azure, izleme ve analiz için gelişmiş [Application Insights platformünü](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) sağlar.

## <a name="inter-service-dependencies"></a>Servisler arası bağımlılıklar

Sunucusuz bir mimari, diğer işlevlere dayanan işlevler içerebilir. Aslında, sunucusuz bir mimaride birden çok hizmetin etkileşim veya dağıtılmış işlemin bir parçası olarak birbirini araması nadir değildir. Güçlü bağlantıdan kaçınmak için, hizmetlerin doğrudan birbiriyle referans vermemeleri önerilir. Bir hizmetin bitiş noktasının değişmesi gerektiğinde, doğrudan başvurular büyük yeniden düzenlemeyle sonuçlanabilir. Önerilen çözüm, bir istek türü için uygun bitiş noktasını sağlayan kayıt defteri gibi bir hizmet bulma mekanizması sağlamaktır. Başka bir çözüm, kuyruklar veya hizmetler arasındaki iletişim konuları gibi mesajlaşma hizmetlerinden yararlanmaktır.

## <a name="managing-failure-and-providing-resiliency"></a>Başarısızlığı yönetme ve esneklik sağlama

*Devre kesici deseni*de göz önünde bulundurmak da önemlidir: Bir nedenle bir hizmet başarısız olmaya devam ederse, bu hizmeti tekrar tekrar aramak tavsiye edilmez. Bunun yerine, bağımlı hizmetin durumu yeniden kurulana kadar alternatif bir hizmet çağrılır veya ileti döndürülür. Sunucusuz mimari, servisler arası bağımlılıkları çözme ve yönetme stratejisini dikkate almalıdır.

Devre kesici desenini devam ettirebilmek için hizmetlerin hataya dayanıklı ve esnek olması gerekir. Hata toleransı, beklenmeyen özel durumlar veya geçersiz durumlarla karşılaşıldıktan sonra bile uygulamanızın çalışmaya devam etme yeteneğini ifade eder. Hata toleransı genellikle kodun kendisi ve özel durumları işlemek için nasıl yazıldığının bir fonksiyonudur. Esneklik, uygulamanın hatalardan kurtulmada ne kadar yetenekli olduğunu ifade eder. Esneklik genellikle sunucusuz platform tarafından yönetilir. Platform, varolan başarısız olduğunda yeni bir sunucusuz işlev örneği döndürebilmelidir. Platform aynı zamanda her yeni örnek başarısız olduğunda yeni örnekler kadar dönen durdurmak için yeterince akıllı olmalıdır.

Daha fazla bilgi için bkz: [Devre Kesici deseni uygulama.](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)

## <a name="versioning-and-greenblue-deployments"></a>Sürüm ve yeşil/mavi dağıtımlar

Sunucusuz olmanın en önemli yararı, tüm uygulamayı yeniden dağıtmak zorunda kalmadan belirli bir işlevi yükseltme yeteneğidir. Yükseltmelerin başarılı olabilmesi için işlevlerin, onları çağıran hizmetlerin kodun doğru sürümüne yönlendirilmesi için sürülmesi gerekir. Yeni sürümleri dağıtmak için bir strateji de önemlidir. Yaygın bir yaklaşım "yeşil/mavi dağıtımlar" kullanmaktır. Yeşil dağıtım geçerli işlevdir. Yeni bir "mavi" sürümü üretime dağıtılır ve test edilir. Test geçtiğinde, yeşil ve mavi sürümler yeni sürümün canlı olarak gelmesi için değiştirilir. Herhangi bir sorunla karşılaşılırsa, bunlar geri değiştirilebilir. Sürüm ve yeşil/mavi dağıtımları desteklemek, sürüm değişikliklerini karşılamak için işlevleri yazma nın ve dağıtımları işlemek için sunucusuz platformla çalışmanın bir birleşimini gerektirir. Olası bir yaklaşım, [Azure sunucusuz platform](azure-functions.md#proxies) bölümünde açıklanan yakınlıkları kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](serverless-architecture.md)
>[Sonraki](serverless-design-examples.md)
