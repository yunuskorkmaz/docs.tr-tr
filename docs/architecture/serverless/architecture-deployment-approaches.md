---
title: Mimari dağıtım yaklaşımları - Sunucusuz uygulamalar
description: IaaS, PaaS, kapsayıcılar ve sunucusuzlar arasında karşılaştırma yla birlikte, kurumsal mimarilerin buluta farklı şekillerde dağıtılanın yolu kılavuzu.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522732"
---
# <a name="architecture-deployment-approaches"></a>Mimari dağıtım yaklaşımları

Bir iş uygulaması tasarlamak için kullanılan mimari yaklaşımne bakılmaksızın, bu uygulamaların uygulanması veya dağıtımı değişebilir. İşletmeler, fiziksel donanımdan sunucusuz işlevlere kadar her konuda uygulamaları barındırır.

## <a name="n-tier-applications"></a>N-Tier uygulamaları

[N-Tier mimari deseni](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) olgun bir mimaridir ve yalnızca çeşitli mantıksal katmanları ayrı fiziksel katmanlara ayıran uygulamaları ifade eder. N-Tier mimarisi, N-Layer mimarisinin fiziksel bir uygulamasıdır. Bu mimarinin en yaygın uygulaması şunları içerir:

- Bir sunum katmanı, örneğin bir web uygulaması.
- REST API gibi bir API veya veri erişim katmanı.
- SQL veritabanı gibi bir veri katmanı.

![N katmanlı mimari](./media/n-tier-architecture.png)

N katmanlı çözümler aşağıdaki özelliklere sahiptir:

- Projeler genellikle katmanlarla hizalanır.
- Sınama katmana göre farklı yaklaşılabilir.
- Katmanlar soyutlama katmanları sağlar, örneğin sunu katmanı genellikle veri katmanının uygulama ayrıntılarından habersizdir.
- Tipik olarak, katmanlar yalnızca bitişik katmanlarla etkileşime girer.
- Sürümler genellikle projede yönetilir ve bu nedenle katman, düzey. Basit bir API değişikliği, tüm orta katmanın yeni bir sürümü gerektirebilir.

Bu yaklaşım, şunları dahil olmak üzere çeşitli avantajlar sağlar:

- Veritabanının yalıtımı (genellikle ön uç veritabanı arka ucuna doğrudan erişim yok).
- API'nin yeniden kullanımı (örneğin, mobil, masaüstü ve web uygulaması istemcilerinin tümü aynı API'leri yeniden kullanabilir).
- Katmanları birbirinden bağımsız ölçeklendirme yeteneği.
- Yeniden düzenleme yalıtımı: bir katman diğer katmanları etkilemeden yeniden kullanılabilir.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Hizmet Olarak Şirket İçi ve Altyapı (IaaS)

Uygulamaları barındırmak için geleneksel yaklaşım donanım satın alma ve işletim sistemi de dahil olmak üzere tüm yazılım yüklemeleri, yönetme gerektirir. Başlangıçta bu pahalı veri merkezleri ve fiziksel donanım içeriyordu. Fiziksel donanımı çalıştırmanın getirdiği zorluklar şunlardır:

- "Her ihtimale karşı" veya en yüksek talep senaryoları için fazlasatın alma ihtiyacı.
- Donanıma fiziksel erişimi güvence altına alma.
- Donanım hatası sorumluluğu (disk hatası gibi).
- Soğutma.
- Yönlendiricileri ve yük dengeleyicilerini yapılandırma.
- Güç artıklığı.
- Yazılım erişimini güvence altına alma.

![IaaS yaklaşımı](./media/iaas-approach.png)

Donanımın "sanal makineler" aracılığıyla sanallaştırılması, Hizmet Olarak Altyapı'yı (IaaS) mümkün kılar. Ana bilgisayar makineleri, kendi bellekleri, CPU'ları ve depolama ları için ayırmaları olan örneklere kaynak sağlamak için etkin bir şekilde bölümlere ayrılmıştır. Ekip gerekli VM'leri sağlar ve ilişkili ağları ve depolamaya erişimi yapılandırır.

Daha fazla bilgi için [sanal makine N katmanlı başvuru mimarisine](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)bakın.

Sanallaştırma ve Hizmet Olarak Altyapı (IaaS) birçok endişeyi giderse de, yine de altyapı ekibinin elinde çok fazla sorumluluk bırakmaktadır. Takım işletim sistemi sürümlerini korur, güvenlik yamaları uygular ve hedef makinelere üçüncü taraf bağımlılıkları yükler. Uygulamalar genellikle üretim makinelerinde test ortamına göre farklı davranmaktadır. Sorunlar, farklı bağımlılık sürümleri ve/veya OS SKU düzeyleri nedeniyle ortaya çıkar. Birçok kuruluş bu hedeflere N-Tier uygulamaları dağıtsa da, birçok şirket Hizmet [Olarak Platform](#platform-as-a-service-paas)gibi daha bulut yerel bir modele dağıtım dan yararlanır. Mikro hizmetlere sahip mimariler, esneklik ve esneklik için ölçeklendirme gereksinimleri nedeniyle daha zorlu.

Daha fazla bilgi için [sanal makinelere](https://docs.microsoft.com/azure/virtual-machines/)bakın.

## <a name="platform-as-a-service-paas"></a>Hizmet Olarak Platform (PaaS)

Hizmet Olarak Platform (PaaS), geliştiricilerin doğrudan takabilecekleri yapılandırılmış çözümler sunar. PaaS yönetilen barındırma için başka bir terimdir. Temel işletim sistemini, güvenlik düzeltme eklerini ve çoğu durumda üçüncü taraf bağımlılıklarını yönetme gereksinimini ortadan kaldırır. Platformlara örnek olarak web uygulamaları, veritabanları ve mobil arka uçlar verilebilir.

PaaS, IaaS'ın ortak zorluklarını ele alıyor. PaaS, geliştiricinin nasıl dağıtılanından çok koda veya veritabanı şemasına odaklanmasına olanak tanır. PaaS'ın faydaları şunlardır:

- Boşta makinelere yatırım yapmanın genel giderini ortadan kaldıran kullanım modelleri için ödeme yapın.
- Doğrudan dağıtım ve geliştirilmiş DevOps, sürekli entegrasyon (CI) ve sürekli teslimat (CD) boru hatları.
- Otomatik yükseltmeler, güncelleştirmeler ve güvenlik yamaları.
- Push-button ölçekve ölçek (elastik ölçek).

PaaS ana dezavantajı geleneksel satıcı kilitleme olmuştur. Örneğin, bazı PaaS sağlayıcıları yalnızca ASP.NET, Düğüm.js'yi veya diğer belirli dilleri ve platformları destekler. Azure Uygulama Hizmeti gibi ürünler, birden çok platforma hitap etmek ve web uygulamalarını barındırmak için çeşitli dilleri ve çerçeveleri desteklemek üzere evrilmiştir.

![Hizmet Mimarisi Olarak Platform](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Hizmet Olarak Yazılım (SaaS)

Hizmet veya SaaS olarak yazılımlar merkezi olarak barındırılır ve yerel kurulum veya sağlama olmadan kullanılabilir. SaaS genellikle paas üstüne yazılım dağıtmak için bir platform olarak barındırılan. SaaS, mevcut yazılımları çalıştırmak ve onlarla bağlantı kurmak için hizmetler sağlar. SaaS genellikle endüstri ve dikey özgüdür. SaaS genellikle lisanslıdır ve genellikle bir istemci/sunucu modeli sağlar. Modern SaaS tekliflerinin çoğu müşteri için web tabanlı uygulamalar kullanır. Şirketler genellikle SaaS'ı lisans teklifleri için bir iş çözümü olarak görürler. Genellikle ölçeklenebilirlik ve bir uygulamanın bakımı için mimari dikkate olarak uygulanmaz. Gerçekten de, çoğu SaaS çözümleri IaaS, PaaS ve / veya sunucusuz arka uçları üzerine inşa edilmiştir.

Örnek bir [uygulama](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)aracılığıyla SaaS hakkında daha fazla bilgi edinin.

## <a name="containers-and-functions-as-a-service-faas"></a>Hizmet Olarak Kapsayıcılar ve Fonksiyonlar (FaaS)

Konteynerler IaaS havai olmadan PaaS benzeri faydalar sağlayan ilginç bir çözümdür. Kapsayıcı aslında benzersiz bir uygulama çalıştırmak için gerekli çıplak temel içeren bir çalışma zamanıdır. Ana bilgisayar işletim sisteminin çekirdek veya temel bölümü ve depolama gibi hizmetler bir ana bilgisayar arasında paylaşılır. Paylaşılan çekirdek, kapların hafif olmasını sağlar (bazıları tipik sanal makinelerin gigabayt boyutuna kıyasla sadece megabayt boyutudur). Ana bilgisayarlar zaten çalışıyorsa, konteynerler hızlı bir şekilde başlatılabilir ve bu da yüksek kullanılabilirliği kolaylaştırır. Konteynerleri hızlı bir şekilde döndürme yeteneği de ekstra esneklik katmanları sağlar. Docker konteynerlerin daha popüler uygulamalarından biridir.

Konteynerlerin faydaları şunlardır:

- Hafif ve taşınabilir
- Bağımsız olarak, bağımlılıkları yüklemenize gerek kalmadan
- Ana bilgisayardan bağımsız olarak tutarlı bir ortam sağlayın (dizüstü bilgisayarda bulut sunucusunda olduğu gibi çalışır)
- Ölçeklendirme için hızlı bir şekilde sağlanabilir
- Hatadan kurtarmak için hızlı bir şekilde yeniden başlatılabilir

Bir konteyner bir konteyner ana bilgisayarüzerinde çalışır (bu da çıplak metal bir makine veya sanal bir makine üzerinde çalışabilir). Aynı kapsayıcıların birden çok kapsayıcısı veya örnekleri tek bir ana bilgisayarda çalışabilir. Gerçek arıza ve esneklik için, kapsayıcılar ana bilgisayarlar arasında ölçeklendirilmelidir.

Docker konteynerleri hakkında daha fazla bilgi için [Docker nedir' e](../microservices/container-docker-introduction/docker-defined.md)bakın.

Kapsayıcıları ana bilgisayarlar arasında yönetmek genellikle Kubernetes gibi bir düzenleme aracı gerektirir. Configuring and managing orchestration solutions may add additional overhead and complexity to projects. Neyse ki, birçok bulut sağlayıcısı kapların yönetimini kolaylaştırmak için PaaS çözümleri aracılığıyla orkestrasyon hizmetleri sağlar.

Aşağıdaki resim, Kubernetes yüklemesi örneğini göstermektedir. Yükleme adresindeki düğümler ölçeklendirilir ve başarısız olursa. Ana sunucu tarafından yönetilen Docker kapsayıcı örneklerini çalıştırıyorlar. *Kubelet,* Kubernetes'ten Docker'a komut lar gönderen müşteridir.

![Kubernetes](./media/kubernetes-example.png)

Orkestrasyon hakkında daha fazla bilgi için [Azure'daki Kubernetes'e](https://docs.microsoft.com/azure/aks/intro-kubernetes)bakın.

Hizmet Işlevi (FaaS), sunucusuzlara benzeyen özel bir kapsayıcı hizmetidir. FaaS belirli bir uygulama, [OpenFaaS](https://github.com/openfaas/faas)denilen , sunucusuz yetenekleri sağlamak için kapsayıcıların üstüne oturur. OpenFaaS, bir kod parçasını çalıştırmak için gereken tüm kapsayıcı bağımlılıklarını paketleyen şablonlar sağlar. Şablonları kullanmak, kodu işlevsel bir birim olarak dağıtma işlemini kolaylaştırır. OpenFaaS, mevcut altyapıyı kullanabildiği için kapsayıcıları ve orkestratörleri içeren mimarileri hedefler. Sunucusuz işlevsellik sağlamasına rağmen, özellikle Docker ve bir orkestratör kullanmanız gerekir.

## <a name="serverless"></a>Sunucusuz

Sunucusuz mimari, kod ve barındırma ortamı arasında açık bir ayrım sağlar. Tetikleyici tarafından çağrılan bir *işlevde* kodu *trigger*uygularsınız. Bu işlev çıktıktan sonra, gerekli tüm kaynakları serbest bırakılabilir. Tetikleyici el ile, zamanlanmış bir işlem, bir HTTP isteği veya dosya yüklemesi olabilir. Tetikleyicinin sonucu kodun yürütülmesidir. Sunucusuz platformlar farklılık gösterse de, çoğu veritabanına yazma veya sıraya girme sonuçları gibi görevleri kolaylaştırmak için önceden tanımlanmış API'lere ve bağlamalara erişim sağlar.

Serverless, koda odaklanmak için ana bilgisayar ortamını soyutlamaya büyük ölçüde dayanan bir mimaridir. Daha *az sunucu*olarak düşünülebilir.

Kapsayıcı çözümleri, geliştiricilere sunucusuz hazır görüntülere kod yayımlamaları için varolan yapı komut dosyaları sağlar. Diğer uygulamalar ölçeklenebilir bir mimari sağlamak için varolan PaaS çözümlerini kullanır.

Soyutlama, DevOps ekibinin sunucuları veya belirli kapsayıcıları sağlaması veya yönetmesi gerekmediği anlamına gelir. Sunucusuz platform, ilgili Bir SDK ile oluşturulmuş komut dosyası veya paketyürütülebilir kod olarak kodu barındırır ve kodun ölçeklendirmesi için gerekli kaynakları ayırır.

Aşağıdaki çizimdört sunucusuz bileşendiyagramları. BIR HTTP isteği, Ödeme API kodunun çalışmasına neden olur. Ödeme API'si bir veritabanına kod ekler ve ekleme, görevleri hesaplama ve siparişi yerine getirme gibi görevleri gerçekleştirmek için çalıştırmak için birkaç başka işlevi tetikler.

![Sunucusuz uygulama](./media/serverless-implementation.png)

Sunucusuz avantajları şunlardır:

- **Yüksek yoğunluklu.** Aynı sunucusuz kodun birçok örneği kapsayıcılarla veya sanal makinelerle karşılaştırıldığında aynı ana bilgisayarda çalıştırılabilir. Örnekler, birden çok ana bilgisayar arasında ölçeklendirilir ve esneklik sağlar.
- **Mikro faturalama.** Çoğu sunucusuz sağlayıcı, belirli senaryolarda büyük maliyet tasarrufu sağlayarak sunucusuz yürütmeleri temel alarak faturalandırılır.
- **Anlık ölçek.** Sunucusuz, iş yüklerini otomatik olarak ve hızlı bir şekilde eşleşecek şekilde ölçeklendirilebilir.
- **Pazara daha hızlı zaman.** Geliştiriciler koda odaklanır ve doğrudan sunucusuz platforma dağıtılır. Bileşenler birbirinden bağımsız olarak serbest bırakılabilir.

Sunucusuz en sık bilgi işlem bağlamında tartışılır, ancak veriler için de geçerli olabilir. Örneğin, [Azure SQL](https://docs.microsoft.com/azure/sql-database) ve [Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db) ana bilgisayar makinelerini veya kümeleri yapılandırmanızı gerektirmeyen bulut veritabanları sağlar. Bu kitap sunucusuz bilgi işlem üzerinde duruluyor.

## <a name="summary"></a>Özet

Mimari için karma bir yaklaşım da dahil olmak üzere geniş bir seçenek yelpazesi vardır. Serverless, uygulama özelliklerinin yaklaşımını, yönetimini ve maliyetini kontrol ve taşınabilirlik pahasına basitleştirir. Ancak, birçok sunucusuz platform, çözümde ince ayar yapmanıza yardımcı olmak için yapılandırmayı ortaya çıkarır. İyi programlama uygulamaları da daha taşınabilir kod ve daha az sunucusuz platform kilitleme yol açabilir. Aşağıdaki tabloda mimari yaklaşımları yan yana gösterilmiştir. Çalışma süresini yönetmek isteyip istemediğinize ve iş yüklerinizi ne kadar iyi küçük bileşenlere dönüştürebileceğinize bağlı olarak, ölçek gereksinimlerinize göre sunucusuz seçin. Bir sonraki bölümde sunucusuz ve diğer karar noktalarıyla olası zorluklar hakkında bilgi edineceksiniz.

|         |IaaS     |PaaS     |Kapsayıcı|Sunucusuz|
|---------|---------|---------|---------|----------|
|**Ölçeklendirme**|VM       |Örnek |Uygulama      |İşlev  |
|**Özetleri**|Donanım|Platform|İşletim Sistemi Ana Bilgisayar|Çalışma Zamanı   |
|**Birim** |VM       |Project  |Görüntü    |Kod      |
|**Ömür boyu**|Ay|Günlerden Aylara|Günlere Dakikalar|Dakikaya Milisaniye|
|**Sorumluluk**|Uygulamalar, bağımlılıklar, çalışma zamanı ve işletim sistemi|Uygulamalar ve bağımlılıklar|Uygulamalar, bağımlılıklar ve çalışma zamanı|İşlev

- **Ölçek,** uygulamayı ölçeklendirmek için kullanılan birimi ifade eder
- **Özetler,** uygulama tarafından soyutlanan katmanı ifade eder
- **Birim,** dağıtılan şeyin kapsamını ifade eder
- **Yaşam boyu,** belirli bir örneğin tipik çalışma zamanını ifade eder
- **Sorumluluk,** uygulamanın oluşturulması, dağıtılması ve sürdürülmesi için ek yükü ifade eder

Bir sonraki bölümde sunucusuz mimari, kullanım örnekleri ve tasarım desenleri üzerinde durulacaktır.

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Azure uygulama mimarisi kılavuzu](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [N-Tier mimari deseni](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Azure’da Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Mikro Hizmetler](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Sanal makine N katmanlı referans mimarisi](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Sanal makineler](https://docs.microsoft.com/azure/virtual-machines/)
- [Docker nedir?](../microservices/container-docker-introduction/docker-defined.md)
- [Wingtip Biletleri SaaS uygulaması](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Önceki](architecture-approaches.md)
>[Sonraki](serverless-architecture.md)
