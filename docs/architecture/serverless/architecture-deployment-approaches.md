---
title: Mimari dağıtımı yaklaşımları-sunucusuz uygulamalar
description: IaaS, PaaS, kapsayıcılar ve sunucusuz arasında karşılaştırma ile kurumsal mimarilerin buluta dağıtıldığı farklı yollarla ilgili kılavuz.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8a1203ea2fc7089223c03b3a3e02fd3303610272
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676816"
---
# <a name="architecture-deployment-approaches"></a>Mimari dağıtım yaklaşımları

Bir iş uygulaması tasarlamak için kullanılan mimari yaklaşımdan bağımsız olarak, bu uygulamaların uygulanması veya dağıtımı farklılık gösterebilir. İşletmeler, fiziksel donanımlardan sunucusuz işlevlere kadar her şeye yönelik uygulamalar barındırır.

## <a name="n-tier-applications"></a>N katmanlı uygulamalar

[N katmanlı mimari model](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) , yetişkinlere yönelik bir mimaridir ve yalnızca çeşitli mantıksal katmanları ayrı fiziksel katmanlara ayıran uygulamalara başvurur. N katmanlı mimari, N katmanlı mimarinin fiziksel bir uygulamasıdır. Bu mimarinin en yaygın uygulanması şunları içerir:

* Bir sunu katmanı, örneğin bir Web uygulaması.
* REST API gibi bir API veya veri erişim katmanı.
* SQL veritabanı gibi bir veri katmanı.

![N katmanlı mimari](./media/n-tier-architecture.png)

N katmanlı çözümler aşağıdaki özelliklere sahiptir:

* Projeler genellikle katmanlarla hizalanır.
* Test, katman tarafından farklı approached olabilir.
* Katmanlar, Özet katmanları sağlar; örneğin, sunum katmanı genellikle veri katmanının uygulama ayrıntılarının üzerinde yok edilir.
* Genellikle, Katmanlar yalnızca bitişik katmanlarla etkileşime geçin.
* Yayınlar genellikle projede ve bu nedenle katman düzeyinde yönetilir. Basit bir API değişikliği, orta katmanın tamamının yeni bir sürümünü gerektirebilir.

Bu yaklaşım aşağıdakiler dahil olmak üzere çeşitli avantajlar sağlar:

* Veritabanı yalıtımı (genellikle ön uç, veritabanı arka ucuna doğrudan erişim sahibi değildir).
* API 'nin yeniden kullanılması (örneğin, mobil, masaüstü ve Web uygulaması istemcilerinin hepsi aynı API 'Leri yeniden kullanabilir).
* Katmanları birbirinden bağımsız olarak ölçeklendirebilme olanağı.
* Yeniden düzenleme yalıtımı: bir katman, diğer katmanları etkilemeden yeniden düzenlenmiş olabilir.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Şirket içi ve hizmet olarak altyapı (IaaS)

Uygulamaları barındırmak için geleneksel yaklaşım, işletim sistemi dahil olmak üzere donanım satın alma ve yazılım yüklemelerinin tümünü yönetme gerektirir. Bu, başlangıçta pahalı veri merkezleri ve fiziksel donanımlar dahil değildir. İşletim fiziksel donanımıyla birlikte gelen sorunlar da dahil olmak üzere çok.

* "Yalnızca büyük/küçük harf" veya en yoğun talep senaryolarında aşırı satın alma ihtiyacı.
* Donanıma fiziksel erişimin güvenliğini sağlama.
* Donanım hatası sorumluluğu (örneğin, disk arızası).
* Maya.
* Yönlendiricileri ve yük dengeleyicileri yapılandırma.
* Güç artıklığı.
* Yazılım erişiminin güvenliğini sağlama.

![IaaS yaklaşımı](./media/iaas-approach.png)

Donanım sanallaştırma, "sanal makineler" aracılığıyla hizmet olarak altyapı (IaaS) etkinleştirilir. Konak makineler, kendilerine ait bellek, CPU ve depolama alanları için ayırmaları olan örneklere kaynak sağlamak üzere etkili bir şekilde bölümlenir. Takım, gerekli VM 'Leri sağlar ve ilişkili ağları ve depolama alanına erişimi yapılandırır.

Daha fazla bilgi için bkz. [sanal makine N katmanlı başvuru mimarisi](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Sanallaştırma ve hizmet olarak altyapı (IaaS) ile ilgili birçok sorun ele gelse de, altyapı ekibinin elleri için de çok fazla sorumluluk bırakır. Takım, işletim sistemi sürümlerini korur, güvenlik düzeltme eklerini uygular ve hedef makinelere üçüncü taraf bağımlılıklarını kurar. Uygulamalar, genellikle test ortamıyla karşılaştırılan üretim makinelerinde farklı şekilde davranır. Farklı bağımlılık sürümleri ve/veya işletim sistemi SKU düzeyleri nedeniyle sorunlar ortaya çıkar. Birçok kuruluş bu hedeflere N katmanlı uygulamalar dağıtmakla birlikte, çoğu şirket [hizmet olarak platform](#platform-as-a-service-paas)gibi daha fazla bulut Yerel modeline dağıtmaktan yararlanır. Mikro hizmetlerle mimariler, esneklik ve dayanıklılık açısından ölçeği genişletme gereksinimleri nedeniyle daha zordur.

Daha fazla bilgi için bkz. [sanal makineler](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Hizmet olarak platform (PaaS)

Hizmet olarak platform (PaaS), geliştiricilerin doğrudan girebileceği yapılandırılmış çözümler sunar. PaaS, yönetilen barındırma için başka bir terimdir. Temel işletim sistemi, güvenlik düzeltme ekleri ve birçok durumda, üçüncü taraf bağımlılıkları yönetme ihtiyacını ortadan kaldırır. Platform örnekleri arasında Web uygulamaları, veritabanları ve mobil arka uçlar sayılabilir.

PaaS, IaaS 'de ortak olan zorlukları ele alır. PaaS, geliştiricinin dağıtım şekli yerine koda veya veritabanı şemasına odaklanmasını sağlar. PaaS 'nin avantajları şunlardır:

* Boştaki makinelere yatırım yükünü ortadan kaldıran kullanım modellerini ödeyin.
* Doğrudan dağıtım ve geliştirilmiş DevOps, sürekli tümleştirme (CI) ve sürekli teslim (CD) işlem hatları.
* Otomatik yükseltmeler, güncelleştirmeler ve güvenlik düzeltme ekleri.
* Basma düğmesi ölçeği genişletme ve ölçeği artırma (elastik ölçek).

PaaS geleneksel 'nin ana dezavantajı, satıcı kilidi olmuştur. Örneğin, bazı PaaS sağlayıcıları yalnızca ASP.NET, Node. js veya diğer belirli dilleri ve platformları destekler. Azure App Service gibi ürünler, birden çok platformu ele almak ve Web uygulamalarını barındırmak için çeşitli dilleri ve çerçeveleri desteklemek için geliştirilmiştir.

![Hizmet mimarisi olarak platform](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Hizmet olarak yazılım (SaaS)

Hizmet olarak yazılım veya SaaS, yerel yükleme veya sağlama olmadan merkezi olarak barındırılır ve kullanılabilir. SaaS genellikle yazılım dağıtımı platformu olarak PaaS üzerinde barındırılır. SaaS, Hizmetleri çalıştırıp mevcut yazılımlarla bağlantı kurmak için hizmetler sağlar. SaaS genellikle sektör ve dikey özel. SaaS genellikle lisanslanır ve genellikle bir istemci/sunucu modeli sağlar. Çoğu modern SaaS teklifi, istemci için Web tabanlı uygulamalar kullanır. Şirketler genellikle SaaS 'yi lisans sunumlarına bir iş çözümü olarak kabul etmeyi düşünmelidir. Genellikle bir uygulamanın ölçeklenebilirlik ve bakım açısından bir mimari değerlendirmesi olarak uygulanmaz. Aslında, birçok SaaS çözümü IaaS, PaaS ve/veya sunucusuz arka uçlarından oluşturulmuştur.

[Örnek bir uygulama](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)aracılığıyla SaaS hakkında daha fazla bilgi edinin.

## <a name="containers-and-functions-as-a-service-faas"></a>Kapsayıcılar ve hizmet olarak Işlevler (FaaS)

Kapsayıcılar, IaaS ek yükü olmadan PaaS benzeri avantajlar sağlayan ilginç bir çözümdür. Bir kapsayıcı temelde, benzersiz bir uygulamayı çalıştırmak için gereken çıplak uygulamaları içeren bir çalışma zamanı. Ana bilgisayar işletim sisteminin çekirdek veya çekirdek bölümü ve depolama gibi hizmetler bir konakta paylaşılır. Paylaşılan çekirdek, kapsayıcıların hafif olmasını sağlar (bazıları, tipik sanal makinelerin gigabayt boyutuyla karşılaştırıldığında boyut olarak boyutlardır). Zaten çalışan konaklar ile, kapsayıcılar hızla başlatılabilir ve yüksek oranda kullanılabilirliği kolaylaştırılabilirler. Kapsayıcıları hızlı bir şekilde çalıştırabilme özelliği, ek dayanıklılık katmanları da sağlar. Docker, kapsayıcıların daha popüler uygulamalarından biridir.

Kapsayıcıların avantajları şunlardır:

* Hafif ve taşınabilir
* Bu nedenle, bağımlılıkları yüklemeye gerek yoktur
* Ana bilgisayardan bağımsız olarak tutarlı bir ortam sağlayın (bir bulut sunucusunda olduğu gibi bir dizüstü bilgisayarda tam olarak aynı çalışır)
* Ölçek genişletme için hızlı bir şekilde sağlanabilir
* Hatadan kurtarmak için hızlı bir şekilde yeniden başlatılabilir

Bir kapsayıcı bir kapsayıcı ana bilgisayarında çalışır (Bu, sırasıyla bir çıplak makinede veya sanal makinede çalıştırılabilir). Birden çok kapsayıcı veya aynı kapsayıcıların örnekleri tek bir konakta çalışabilir. Doğru yük devretme ve dayanıklılık için kapsayıcılar ana bilgisayarlar arasında ölçeklendirilmesi gerekir.

Docker Kapsayıcıları hakkında daha fazla bilgi için bkz. [Docker](../microservices/container-docker-introduction/docker-defined.md)nedir?

Her ana bilgisayar genelinde kapsayıcıları yönetmek için genellikle Kubernetes gibi bir düzenleme aracı gerekir. Orchestration çözümlerini yapılandırma ve yönetme, projelere ek yük ve karmaşıklık ekleyebilir. Neyse ki birçok bulut sağlayıcısı, kapsayıcıların yönetimini basitleştirmek için PaaS çözümleri aracılığıyla düzenleme hizmetleri sağlar.

Aşağıdaki görüntüde örnek bir Kubernetes yüklemesi gösterilmektedir. Yükleme adresindeki düğümlerin ölçeği genişleme ve yük devretme. Ana sunucu tarafından yönetilen Docker kapsayıcı örneklerini çalıştırırlar. *Kubelet* , komutları Kubernetes 'Den Docker 'a aktaran istemcidir.

![Kubernetes](./media/kubernetes-example.png)

Düzenleme hakkında daha fazla bilgi için bkz. [Azure 'Da Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Hizmet olarak işlevler (FaaS) sunucusuz ile benzer özel bir kapsayıcı hizmetidir. [Openfaas](https://github.com/openfaas/faas)adlı belirli FAAS uygulamaları sunucusuz yetenekler sağlamak için kapsayıcıların en üstünde bulunur. OpenFaaS, bir kod parçasını çalıştırmak için gereken tüm kapsayıcı bağımlılıklarını paketleyip şablon sağlar. Şablon kullanımı, kodu işlevsel birim olarak dağıtma işlemini basitleştirir. Zaten kapsayıcı ve düzenleyicilerin bulunduğu OpenFaaS hedefleri, var olan altyapıyı kullanabilmesi için. Sunucusuz işlevsellik sunmakla birlikte, özellikle Docker ve Orchestrator kullanmanız gerekir.

## <a name="serverless"></a>Sunucusuz

Sunucusuz bir mimari, kod ve barındırma ortamı arasında net bir ayrım sağlar. Kodu bir *tetikleyici*tarafından çağrılan bir *işlevde* uygulamalısınız. Bu işlev çıktıktan sonra, gereken tüm kaynaklar serbest bırakılmış olabilir. Tetikleyici el ile, süreli bir işlem, bir HTTP isteği veya karşıya dosya yükleme olabilir. Tetikleyicinin sonucu kodun yürütülmesinden kaynaklanır. Sunucusuz platformlar farklılık gösterebilse de, bir veritabanına yazma veya sonuçları sıraya alma gibi görevleri kolaylaştırmak için önceden tanımlanmış API 'lere ve bağlamalara erişim sağlar.

Sunucusuz, büyük ölçüde ana bilgisayar ortamının koda odaklanmak için soyutlanması gereken bir mimaridir. Bu, *daha az sunucu*olarak düşünülebilir.

Kapsayıcı çözümleri, geliştiricilerin sunucusuz özellikli görüntülere kod yayımlaması için mevcut derleme betikleri sağlar. Diğer uygulamalar, ölçeklenebilir bir mimari sağlamak için mevcut PaaS çözümlerini kullanır.

Soyutlama, DevOps ekibinin sunucu veya belirli kapsayıcılar sağlamak veya yönetmek zorunda olmadığı anlamına gelir. Sunucusuz platform, komut dosyası veya ilgili SDK ile oluşturulan paketlenmiş yürütülebilir dosyalar olarak kod barındırır ve kodun ölçeklendirilmesi için gerekli kaynakları ayırır.

Aşağıdaki çizim diyagramlarında dört sunucusuz bileşen. Bir HTTP isteği, kullanıma alma API kodunun çalışmasına neden olur. Kullanıma alma API 'SI bir veritabanına kod ekler ve ekleme, görevleri hesaplama ve siparişi yerine getirmek için çalıştırılacak diğer birkaç işlevi tetikler.

![Sunucusuz uygulama](./media/serverless-implementation.png)

Sunucusuz 'in avantajları şunlardır:

* **Yüksek yoğunluklu.** Aynı sunucusuz kodun birçok örneği, kapsayıcılara veya sanal makinelere kıyasla aynı konakta çalışabilir. Örnekler, birden çok ana bilgisayarda ölçek genişletme ve dayanıklılık arasında ölçeklenir.
* **Mikro faturalandırma**. Çoğu sunucusuz sağlayıcı, belirli senaryolarda büyük maliyet tasarrufu sağlayan sunucusuz yürütmeler temelinde faturalandırılır.
* **Anında ölçeklendirme**. Sunucusuz, iş yüklerine otomatik olarak ve hızla uyacak şekilde ölçeklendirebilir.
* **Pazara daha hızlı bir süre** Geliştiriciler koda odaklanarak sunucusuz platforma doğrudan dağıtılır. Bileşenler birbirinden bağımsız olarak serbest bırakıbilirler.

Sunucusuz genellikle işlem bağlamında tartışılır, ancak veriler için de uygulanabilir. Örneğin, [Azure SQL](https://docs.microsoft.com/azure/sql-database) ve [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) her ikisi de konak makinelerini veya kümelerini yapılandırmanızı gerektirmeyen bulut veritabanları sağlar. Bu kitap sunucusuz işlem üzerine odaklanır.

## <a name="summary"></a>Özet

Bir karma yaklaşım da dahil olmak üzere mimaride kullanılabilecek geniş kapsamlı seçenekler vardır. Sunucusuz, denetim ve taşınabilirlik masrafına uygulama özelliklerinin yaklaşımını, yönetimini ve maliyetini basitleştirir. Ancak, çok sayıda sunucusuz platform çözümün ince ayar yapmanıza yardımcı olmak için yapılandırmayı kullanıma sunar. İyi programlama yöntemleri, daha taşınabilir koda ve daha az sunucusuz platform kilitlemeye de yol açabilir. Aşağıdaki tabloda yan yana mimari yaklaşımlar gösterilmektedir. Ölçek gereksinimlerinize göre sunucusuz ' ı seçin, çalışma zamanını yönetmek isteyip istemediğiniz ve iş yüklerinizi küçük bileşenlere ne kadar iyi bir şekilde bozabileceğinizi belirtin. Sonraki bölümde sunucusuz ve diğer karar noktalarıyla ilgili olası sorunlar hakkında bilgi edineceksiniz.

|         |IaaS     |PaaS     |Kapsayıcı|Sunucusuz|
|---------|---------|---------|---------|----------|
|**Ölçek**|VM       |Örnek |Uygulama      |İşlev  |
|**Soyutlar**|Donanım|Platform|İşletim sistemi Konağı|Çalışma zamanı   |
|**Birim** |VM       |Project  |Görüntü    |Kod      |
|**Ömür**|Ay|Gün-ay|Dakika-gün|Milisaniye-dakika|
|**Ğuna**|Uygulamalar, bağımlılıklar, çalışma zamanı ve işletim sistemi|Uygulamalar ve bağımlılıklar|Uygulamalar, bağımlılıklar ve çalışma zamanı|İşlev

* **Ölçek** , uygulamayı ölçeklendirmek için kullanılan birimi ifade eder
* **Soyutlar** , uygulama tarafından soyutlanan katmana başvurur
* **Birim** , dağıtılmasının kapsamını ifade eder
* **Yaşam süresi** belirli bir Örneğin tipik çalışma zamanına başvurur
* **Sorumluluk** , uygulamanın derlenmesi, dağıtılması ve bakımını yapma yükünü ifade eder

Sonraki bölüm sunucusuz mimariye, kullanım örneklerine ve tasarım düzenlerine odaklanacaktır.

## <a name="recommended-resources"></a>Önerilen Kaynaklar

* [Azure Uygulama Mimarisi Kılavuzu](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [N katmanlı mimari model](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Azure 'da Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Mikro hizmetler](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Sanal makine N katmanlı başvuru mimarisi](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Sanal makineler](https://docs.microsoft.com/azure/virtual-machines/)
* [Docker nedir?](../microservices/container-docker-introduction/docker-defined.md)
* [Wingtip bilet SaaS uygulaması](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Önceki](architecture-approaches.md)İleri
>[](serverless-architecture.md)
