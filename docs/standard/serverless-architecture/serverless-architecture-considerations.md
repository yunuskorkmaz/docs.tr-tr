---
title: Sunucusuz mimari dikkat edilmesi gerekenler - sunucusuz uygulamalar
description: Durum Yönetimi ve ölçeklendirmek için kalıcı depolama sunucusuz uygulama mimarileri oluşturma sorunlarından günlüğe kaydetme, izleme ve tanılama anlayın.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: d1654375be1c815d1f46bd8983c38baf063eee04
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643577"
---
# <a name="serverless-architecture-considerations"></a>Sunucusuz mimaride dikkat edilmesi gerekenler

Sunucusuz bir mimari benimsenmesi, bazı zorluklar geliyor. Bu bölümde daha yaygın konuları dikkat edilmesi gereken bazı keşfediyor. Bu zorluklar çözümleri sahiptir. Tüm mimari seçenek olarak, sunucusuz mimariye geçin kararı yalnızca dikkatle Artıları ve eksileri dikkate sonra yapılması gerekir. Uygulamanızın ihtiyaçlarına bağlı olarak, sunucusuz bir uygulama belirli bileşenler için doğru çözüm değildir karar verebilirsiniz.

## <a name="managing-state"></a>Durumunu yönetme

Sunucusuz işlevler ile mikro gibi genel olarak, varsayılan olarak durum bilgisiz olduğundan. Kısa ömürlü, ölçeği genişletme ve merkezi bir hata noktası olmadan dayanıklılık sağlamak için kaçınarak durumunun sunucusuz sağlar. Bazı durumlarda, iş süreçlerini durumu gerektirir. İşleminiz, durumu gerektiriyorsa, iki seçeneğiniz vardır. Sunucusuz değerinden başka bir modelini benimseyin ve durumu sağlayan ayrı bir hizmet ile etkileşimde bulunma. Durum ekleme çözüm karmaşık hale Ölçekle daha zor hale ve olası bir tek hata noktası oluşturun. İşlevinizi durumu kesinlikle gerekli olup olmadığını dikkatlice düşünün. Yanıt "Evet" ise, hala ile sunucusuz uygulama mantıklıdır olup olmadığını belirler.

Sunucusuz avantajlarını ödün vermeden durumu benimsemek için çeşitli çözümler vardır. Diğer popüler çözümlerden bazıları şunlardır:

* Bir geçici veri deposu ve Redis gibi dağıtılmış önbellek kullanma
* Veritabanında, SQL veya CosmosDB gibi Store durumu
* Dayanıklı işlevler gibi bir iş akışı altyapısı aracılığıyla durum işleme

Alt çizgi ile sunucusuz uygulamak için kullanılabiliyor işlemleri içinde herhangi bir durumu yönetim gereksinimini farkında olmalıdır ' dir.

## <a name="long-running-processes"></a>Uzun süre çalışan işlemler

Birçok yararından biri sunucusuz kısa ömürlü olan işlemleri güvenir. Kısa çalışma zamanları, kaynakları konak arasında uç ve Paylaşım işlevleri işlevleri gibi boşaltmak sunucusuz sağlayıcı kolaylaştırır. Çoğu bulut sağlayıcıları işlevinizi yaklaşık 10 dakika olarak çalıştırabilirsiniz toplam süreyi sınırlamak. İşleminizi daha uzun sürebilir, alternatif bir uygulama düşünebilirsiniz.

Bazı özel durumlar ve çözümleri vardır. İşleminizi ayrı ayrı çalıştırmak için daha az zaman alan daha küçük bileşenlere ayırmak için bir çözüm olabilir. İşleminizi bağımlılıklar nedeniyle uzun çalışırsa, dayanıklı işlevler gibi bir çözüm kullanarak zaman uyumsuz iş akışı göz önünde bulundurabilirsiniz. Dayanıklı İşlevler, duraklatmak ve tamamlamak için bir dış işlem beklediği sırada işleminizin durumunu sürdürün. Zaman uyumsuz işleme gerçek işlem sürerken süreyi azaltır.

## <a name="startup-time"></a>Başlangıç zamanı

Sunucusuz uygulamalar ile olası bir sorunu başlangıç zamanı geldi. Kaynak tasarrufu yapmak için "üzerine." altyapı birçok sunucusuz sağlayıcısı oluşturma Sunucusuz bir işlev bir süre sonra tetiklendiğinde işlevi barındırmak için gereken kaynakları oluşturma veya yeniden başlatma gerekebilir. Bazı durumlarda, hazırlıksız başlatma işlemlerinden doğan birkaç saniye gecikmelerine neden olabilir. Başlangıç zaman sağlayıcıları ve hizmet düzeyleri arasında değişir. İçin uygulamanın başarısını en aza indirmek önemliyse adresi başlangıç süresi birkaç yaklaşımları vardır.

* Bazı sağlayıcılar, altyapı "her zaman açık" olduğu garanti hizmet düzeyleri için ödeme açmasına imkan tanıyın.
* ("Açık" olarak korumak için uç nokta ping) bir etkin tutma mekanizması uygulamayın.
* Kubernetes gibi Orchestration (yeni örnekleri hızla çalıştırarak son derece hızlı, bu nedenle konak zaten çalışıyor) kapsayıcılı işlevi bir yaklaşım kullanın.

## <a name="database-updates-and-migrations"></a>Veritabanı güncelleştirmelerine ve geçişler

Sunucusuz kod tüm uygulamayı yeniden dağıtmak zorunda kalmadan yeni işlevleri serbest bırakabilirsiniz avantajlıdır. Bu avantaj, ilgili ilişkisel bir veritabanı olduğunda bir dezavantajı hale gelebilir. Veritabanı şemalarını değişiklikler ile sunucusuz güncelleştirmelerini eşitlemek zordur. Ek zorlukları şeyler ters gittiğinde ve değişikliklerin geri alınması sorulmuş. Veri bütünlüğü mikro hizmetler ve sunucusuz işlevler için en iyi uygulama kendi verilerinin sahibi olan bir nedenidir. Değişiklikleri hesaplama ve verileri tek bir birim olarak dağıtmak mümkündür. Birçok eski sistemi sunucusuz mimari ile mutabık büyük bir arka uç veritabanı özelliği gerçeğidir.

Şema sürümü çözmek için yaygın bir yaklaşım, hiçbir zaman var olan özellikleri ve sütunları değiştirmek, ancak bunun yerine yeni bilgiler ekleyin sağlamaktır. Örneğin, Boole taşımak için bir değişiklik düşünün "tamamlandı" bayrak "tamamlanmış bir tarih." için bir Yapılacaklar listesi için Eski alan kaldırma yerine veritabanı değişiklik olur:

1. Yeni "tamamlanma tarihi" alanı ekleyin.
1. Tamamlanma tarihi geçerli tarihten sonra olup olmadığını değerlendirir hesaplanan bir işlev "tamamlandı" Boole alana dönüştürün.
1. Tamamlanan Boolean ayarlandığında geçerli tarihe tamamlanma tarihi ayarlamak için bir tetikleyici ekleme true.

Değişiklikler dizisini, eski kodu yeni sunucusuz işlevler yeni alan yararlanabilirsiniz "olduğu gibi" çalışmasına devam etmesini sağlar.

Verileri sunucusuz mimarileri hakkında daha fazla bilgi için bkz. [Dağıtılmış veri yönetimi için sorunlar ve çözümler](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Ölçeklendirme

Bu sunucusuz "sunucusu yok." anlamına yaygın bir yanılgıdır Bu aslında "daha az." sunucusudur Var. bir yedekleme altyapısı ölçeklendirme için ne zaman geldiğini anlamak önemlidir gerçeğidir. En sunucusuz platformları, bir dizi olay yoğunluklu artırdığı durumlarda altyapı nasıl ölçeklendirilmesi gereken işlemek için denetimleri sağlayın. Çeşitli seçenekler arasından seçim yapabilirsiniz, ancak stratejinizi işlevi bağlı olarak değişebilir. Ayrıca, böylece işlevleri aynı konakta aynı ölçek seçenekleri işlevleri genellikle bir ilgili konak altında çalışır. Bu nedenle düzenlemek ve birlikte ölçek gereksinimlerine göre hangi işlevleri barındırılan danışmanlık gereklidir.

Kurallar nasıl ölçek büyütme sıklığını belirtin (ana bilgisayar kaynakları artırabilirsiniz) ve çeşitli parametrelere göre ölçeklendirme (ana bilgisayar örneklerinin sayısının artması). Ölçekler için Tetikleyiciler, zamanlama, istek hızları, CPU kullanımı ve bellek kullanımını içerebilir. Genellikle daha yüksek performans, daha büyük bir maliyetle birlikte gelir. Hızlı bir şekilde ne zaman istek hızı anda arttıkça daha ucuz, tüketim tabanlı yaklaşımlar ölçeği değil. "Ödeme ve sigorta Maliyet" ön ödeme arasında bir denge olduğu kesin olarak "Git" ve riski talepte ani bir artış nedeniyle yavaş yanıtlar.

## <a name="monitoring-tracing-and-logging"></a>İzleme, izleme ve günlüğe kaydetme

DevOps genellikle kaçan bir yönünü uygulamalar dağıtıldıktan sonra izler. Sunucusuz işlevler izleme için bir strateji olması önemlidir. En büyük zorluk genellikle bağıntı veya bir kullanıcı aynı etkileşim bir parçası olarak birden çok işlevi çağırdığında algılamayı olur. Üçüncü taraf araçlarla günlük konsol aktarılabilen en sunucusuz platformları sağlar. Telemetri toplama işlemini otomatikleştirme, oluşturun ve bağıntı kimlikleri izleme ve ayrıntılı bilgiler sağlamak için belirli eylemleri izlemek için seçenekleri vardır. Azure Gelişmiş sağlar [Application Insights platform](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) izleme ve analiz için.

## <a name="inter-service-dependencies"></a>Hizmetler arası bağımlılıkları

Sunucusuz bir mimari diğer işlevleri kullanan işlevler içerebilir. Aslında, onu birden çok hizmet birbiriyle etkileşim ya da dağıtılmış işlem bir parçası olarak çağırmak için sunucusuz bir mimari seyrek değil. Güçlü bir bağ önlemek için Hizmetleri birbirine doğrudan başvuru yoksa önerilir. Bir hizmet için uç nokta değişmesi gerektiğinde, doğrudan başvuruların önemli yeniden düzenleme neden olabilir. Önerilen çözüm uygun uç noktaya bir istek türü sağlayan bir kayıt defteri gibi bir hizmet bulma mekanizma sağlamaktır. Hizmetler arasındaki iletişimi için kuyruklar veya konular gibi Mesajlaşma Hizmetleri yararlanarak başka bir çözümdür.

## <a name="managing-failure-and-providing-resiliency"></a>Hata Yönetimi ve dayanıklılık sağlama

Dikkate almak önemlidir *devre kesici düzeni*: Herhangi bir nedenle bir hizmet başarısız olmaya devam ederse, bu hizmeti tekrar tekrar çağırmak için önerilir değil. Bunun yerine alternatif bir hizmet olarak adlandırılır veya bağımlı hizmetinin sistem durumunu yeniden kurulur kadar bir ileti döndürdü. Sunucusuz mimari stratejisi çözme ve hizmet içi bağımlılıkları yönetmek için dikkate almanız gerekir.

Devre kesici düzeni devam etmek için Hizmetleri hataya dayanıklı ve dayanıklı olması gerekir. Hataya dayanıklılık özelliği bile beklenmeyen özel durum sonra çalışmaya devam etmesini uygulamanızın başvurduğu veya geçersiz durumları karşılaşıldı. Dayanıklılığı genellikle bir işlev kod ve özel durumları işlemek nasıl yazılmış oluşur. Dayanıklılık nasıl özellikli uygulamanın hatalardan Kurtarma sırasında olduğu için ifade eder. Dayanıklılığı genellikle sunucusuz platform tarafından yönetilir. Platform var olan bir başarısız olduğunda yeni bir sunucusuz işlev örneği oluşturan dönmeye başlatabilmeniz gerekir. Platform, ayrıca her yeni örneği başarısız olduğunda yeni örnekleri hızla çalıştırarak durdurmak akıllı olmalıdır.

Daha fazla bilgi için [devre kesici desenini uygulama](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Sürüm oluşturma ve yeşil/mavi dağıtımları

Sunucusuz, önemli bir avantajı tüm uygulamayı yeniden dağıtmak zorunda kalmadan belirli bir işlev yükseltmek yeteneğidir. Başarılı olması yükseltmeler için bunların çağrılması Hizmetleri kodunun doğru sürüme yönlendirilebilmesi işlevleri tutulan olması gerekir. Yeni sürümlerini dağıtmak için bir strateji de önemlidir. Yaygın bir yaklaşım "Yeşil/dağıtımları mavi." kullanmaktır. Yeşil dağıtım geçerli bir işlevdir. Yeni "mavi" sürümü üretime dağıtılmadan ve test. Yeni sürümü Canlı gelecektir geçişleri test ederken, yeşil ve mavi sürümleri değiştirilir. Herhangi bir sorun karşılaşılırsa geri değiştirilebilir. Sürüm oluşturma ve yeşil/mavi dağıtımlarını destekleyen bir bileşimi sürüm değişikliklerini uyum sağlamak için İşlevler yazma ve dağıtımları işlemek için sunucusuz platformu ile çalışma gerektirir. Olası bir yaklaşım açıklanmıştır proxy'leri kullanmaktır [Azure sunucusuz platformu](azure-functions.md#proxies) bölüm.

>[!div class="step-by-step"]
>[Önceki](serverless-architecture.md)
>[İleri](serverless-design-examples.md)
