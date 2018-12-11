---
title: Mimari ve dağıtım yaklaşımları - sunucusuz uygulamalar
description: 'Farklı şekillerde Kurumsal Mimari Kılavuzu: Iaas, PaaS, kapsayıcılar, arasında karşılaştırma ile buluta dağıtılan ve sunucusuz.'
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5477b8c4531780fdebf194e4f798564e59cd2953
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152675"
---
# <a name="architecture-deployment-approaches"></a>Mimari dağıtım yaklaşımları

Mimarisi ne olursa olsun, bir iş uygulaması, uygulama veya söz konusu uygulamaların dağıtım tasarımı için kullanılan yaklaşım farklılık gösterebilir. İşletmeler, sunucusuz işlevler uygulamalara kadar her şeyi fiziksel donanım üzerinde barındırın.

## <a name="n-tier-applications"></a>N katmanlı uygulamalar

[N katmanlı mimari deseni](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) olgun bir mimaridir ve yalnızca ayrı ayrı fiziksel katmanlara çeşitli mantıksal katmanlara uygulamaları ifade eder. N katmanlı mimari, fiziksel bir N katmanlı mimari uygulamasıdır. Bu mimarinin en yaygın uygulama şunları içerir:

* Sunu katmanı, örneğin bir web uygulaması.
* API veya veri erişim katmanı, bir REST API gibi.
* SQL veritabanı gibi bir veri katmanı.

![N katmanlı mimari](./media/n-tier-architecture.png)

N katmanlı çözüm şu özelliklere sahiptir:

* Projeleri genellikle katmanları ile hizalanır.
* Testi farklı katmanı tarafından yaklaşıldığında.
* Katman Soyutlama Katmanı sağlar, örneğin sunu katmanı veri katmanı uygulama ayrıntılarını genellikle ignorant.
* Genellikle, Katmanlar yalnızca bitişik katmanları ile etkileşim kurun.
* Proje genellikle yönetilen ve bu nedenle katmanı, düzeyi serbest bırakır. Basit bir API değişiklik yeni kullanıma sunulan tüm bir orta katman gerektirebilir.

Bu yaklaşım, aşağıdakiler gibi birçok avantaj sağlar:

* Yalıtım veritabanının (genellikle ön uç, veritabanı arka ucu doğrudan erişimi yok).
* API (örneğin, mobil, masaüstü ve web uygulaması istemciler tüm yeniden API'leri) kullanılmasını.
* Katmanlarını birbirinden bağımsız olarak ölçeklendirme yeteneği.
* Yalıtım yeniden düzenleme: bir katmanlı yeniden düzenlenen diğer Katmanlar etkilemeden.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Şirket içi ve (Iaas) hizmet olarak altyapı

Donanım satın almak ve tüm işletim sistemi dahil olmak üzere, yazılım yüklemeleri yönetme uygulamalarını barındırmak için geleneksel yaklaşım gerektirir. İlk olarak bu pahalı veri merkezleri ve fiziksel donanım dahil. Fiziksel donanım işletim ile gelen zorlukların çoğu, dahil olmak üzere:

* "Durumda yalnızca" fazla satın alın ya da isteğe bağlı senaryolar en üst seviyeye gerek.
* Donanımına fiziksel erişim güvenliğini sağlama.
* Sorumluluk donanım hatası (örneğin, disk arızası).
* Soğutma.
* Yönlendiriciler ve yük dengeleyicileri yapılandırma.
* Yedek güç.
* Yazılım erişimi güvenli hale getirme.

![Iaas yaklaşımını](./media/iaas-approach.png)

"Sanal makineler" aracılığıyla bir donanım sanallaştırma (Iaas) hizmet olarak altyapı sağlar. Konak makinelerini örnekleri kaynaklara ayırmaları ile kendi bellek, CPU ve depolama sağlamak için etkili bir şekilde bölümlenir. Takım, gereken VM sağlar ve ilişkili ağ ve depolama erişimi yapılandırır.

Daha fazla bilgi için [sanal makine N katmanlı başvuru mimarisi](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Sanallaştırma ve altyapı (Iaas) olarak birçok endişelere rağmen yine de altyapı takım elinizde kadar sorumluluk bırakır. Takım işletim sistemi sürümlerini korur, güvenlik düzeltme eklerinin geçerlidir ve hedef makinelerde üçüncü taraf bağımlılıkları yükler. Uygulamalar genellikle farklı test ortamına kıyasla üretim makinelerinden davranır. Sorunları farklı bağımlılığı sürümlerini ve/veya işletim sistemi SKU'su düzeyleri nedeniyle ortaya çıkar. Birçok kuruluş bu hedefler için N katmanlı uygulamalar dağıtmak olsa da, daha fazla bulut yerel modeli dağıtma gibi birçok şirket fayda [bir hizmet olarak Platform](#platform-as-a-service-paas). İle mikro hizmet mimarileri, esneklik ve dayanıklılık için ölçeği genişletmek için gereksinimler nedeniyle daha zor olan.

Daha fazla bilgi için [sanal makineler](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>(PaaS) hizmet olarak Platform

Platform geliştiriciler doğrudan takın çözümler yapılandırılmış hizmet (PaaS) sunar. PaaS barındırma yönetilen başka bir terim belirtilir. Temel işletim sistemi yönetme ihtiyacını ortadan, güvenlik düzeltme ekleri ve çoğu üçüncü taraf bağımlılıkları durumlarda. Platform örnek veritabanları, web uygulamaları ve mobil arka uçlar.

PaaS, Iaas için ortak sorunlarını ele alır. PaaS yerine nasıl dağıtılacağını, kod veya veritabanı şeması odaklanmak Geliştirici sağlar. PaaS avantajları şunlardır:

* Boşta makinelerinizde yatırım ek yükü ortadan kullanım modelleri için ödeme yaparsınız.
* Dağıtım ve Gelişmiş DevOps, sürekli tümleştirme (CI) ve sürekli teslim (CD) işlem hatlarından yönlendirir.
* Otomatik yükseltmeler, güncelleştirmeler ve güvenlik yamaları.
* Basılabilir düğmeli ölçek genişletme ve ölçeği artırma (esnek ölçeklendirme).

PaaS dezavantajı, geleneksel olarak satıcı kilit açma olmuştur. Örneğin, bazı PaaS sağlayıcıları yalnızca ASP.NET, Node.js veya diğer belirli diller ve platformlar destekler. Azure App Service gibi ürünleri, web uygulamalarını barındırmak için çeşitli dillerde ve çerçevelerde destekler ve birden çok platforma yönelik şekilde gelişmiştir.

![Bir platform olarak hizmet mimarisi](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Yazılım (SaaS) hizmet olarak

SaaS ya da hizmet olarak yazılım merkezi olarak barındırılan ve yerel yüklemesi olmadan veya sağlama sunulur. SaaS, PaaS üzerinde yazılım dağıtmak için bir platform olarak genellikle barındırılır. SaaS ile mevcut yazılım bağlayın ve çalıştırmak için hizmetleri sağlar. SaaS, sektöre ve dikey özel genellikle olur. SaaS, genellikle lisansı olduğunu ve genellikle bir istemci/sunucu modeli sağlar. Çoğu modern SaaS teklifleri, web tabanlı uygulamalar istemcisini kullanabilirsiniz. Şirketler genellikle SaaS iş çözümü lisans teklifleri olarak göz önünde bulundurun. Genellikle, ölçeklenebilirlik ve uygulama bakımı için Mimari düşünmeniz olarak uygulanmadı. Aslında, SaaS çözümlerinin çoğu, Iaas, PaaS ve/veya sunucusuz arka uçları üzerinde oluşturulur.

SaaS ile hakkında daha fazla bilgi bir [örnek uygulama](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kapsayıcılar ve (FaaS) hizmet olarak işlevler

Kapsayıcılar, Iaas iş yükü olmadan PaaS benzeri avantajları sağlayan ilgi çekici bir çözümdür. Temelde benzersiz bir uygulamayı çalıştırmak için gereken tam temel bileşenleri içeren bir çalışma zamanı bir kapsayıcıdır. Konak işletim sistemi ve depolama gibi hizmetlerin çekirdek veya core bölümü bir ana bilgisayar arasında paylaşılır. Paylaşılan çekirdek basit kapsayıcılar sağlar (bazı tipik sanal makinelerin gigabayt boyutuna göre boyutunda boyutundaydı megabayt olan). Zaten çalıştıran konaklardan, yüksek kullanılabilirliği etkinleştirme kapsayıcıları hızlı bir şekilde başlatılabilir. Kapsayıcıları hızla çalıştırın olanağı da ek dayanıklılık katmanı sağlar. Docker kapsayıcıları daha popüler uygulamaları biridir.

Kapsayıcıları avantajları şunlardır:

* Basit ve taşınabilir
* Müstakil bağımlılıkları yüklemeniz gerek yoktur
* Ana bilgisayar (bir bulut sunucusu gibi şirket dizüstü bilgisayara tam olarak aynı çalıştırır) bağımsız olarak tutarlı bir ortam sağlar.
* Ölçek genişletme için hızlı bir şekilde sağlanabilir
* Hatadan kurtarmak için hızla başlatılabilir

Bir kapsayıcı (bu sırayla çıplak metal bir makine veya sanal makinede çalıştırabilir) bir kapsayıcı konağı üzerinde çalışır. Birden çok kapsayıcı ya da aynı kapsayıcı örneklerini tek bir ana bilgisayarda çalışabilir. Gerçek bir yük devretme ve dayanıklılık için kapsayıcı konak arasında ölçeği gerekir.

Docker kapsayıcıları hakkında daha fazla bilgi için bkz. [Docker nedir](../microservices-architecture/container-docker-introduction/docker-defined.md)?

Kapsayıcı konağı arasında genellikle yönetme, Kubernetes gibi bir düzenleme araç gerektirir. Yapılandırma ve düzenleme çözümlerinin yönetme ek yükünü ve karmaşıklığını projelerine ekleyebilirsiniz. Neyse ki, birçok bulut sağlayıcıları kapsayıcı yönetimini basitleştirmek için PaaS çözümleri aracılığıyla orchestration hizmetleri sağlar.

Aşağıdaki görüntüde, Kubernetes yükleme örneği gösterilmektedir. Düğümler yükleme, ölçeklendirme ve yük devretme adresi. Bunlar, Docker ana sunucusu tarafından yönetilen bir kapsayıcı örneği çalıştırın. *Kubelet* Kubernetes için Docker komutlarını geçişleri istemcidir.

![Kubernetes](./media/kubernetes-example.png)

Düzenleme hakkında daha fazla bilgi için bkz: [azure'da Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes).

(FaaS) hizmet olarak işlevleri, sunucusuz için benzer bir özel kapsayıcı hizmetidir. Adlı FaaS, belirli bir uyarlamasını [OpenFaaS](https://github.com/openfaas/faas), sunucusuz özellikler sağlamak için kapsayıcılar üstünde bulunur. OpenFaaS kapsayıcı bağımlılıklarının bir kod parçası çalıştırmak için gereken tüm paket şablonları sağlar. Şablonları kullanarak kod işlevsel bir birim olarak dağıtma işlemini basitleştirir. Mevcut altyapınızı kullanabileceğinizden, kapsayıcılar ve düzenleyicileri zaten içeren mimarileri OpenFaaS hedefler. Sunucusuz işlevler sağlar, ancak bu özellikle Docker ve bir orchestrator kullanmanızı gerekli hale getirmiş.

## <a name="serverless"></a>Sunucusuz

Sunucusuz kod ve kendi barındırma ortamı arasında NET bir ayrım sağlar. Koda uygulanması bir *işlevi* tarafından çağrılan bir *tetikleyici*. Bu işlev çıktıktan sonra tüm gerekli kaynakları serbest bırakılacak. Tetikleyici el ile zamanlanmış bir işlem, bir HTTP isteği veya bir dosya karşıya yükleme olabilir. Kod yürütmeyi tetikleyici sonucudur. Sunucusuz platformları farklı olsa da, bir veritabanı veya kuyruğa sonuçları yazma gibi görevleri kolaylaştırmak için önceden tanımlı API'lere ve bağlamaları en erişim sağlar.

Sunucusuz bir mimari yerine koda odaklanmasını ana bilgisayar ortamının özetleyen üzerinde yoğun olarak kullanır. Bu, olarak düşünülebilir *daha az sunucu*.

Kapsayıcı çözümleri, geliştiricilerin varolan yapı hazır sunucusuz görüntülere kod yayımlamak için komut dosyaları sağlar. Diğer uygulamalar, ölçeklenebilir bir mimari sağlamak için mevcut PaaS çözümleri kullanın.

Özet DevOps ekibinin sağlamak veya sunucular ya da belirli kapsayıcıları yönetmek zorunda değildir anlamına gelir. Sunucusuz platform konakları kodu betik veya paketlenmiş yürütülebilir dosyaları olarak ilgili bir SDK'sıyla oluşturulan ve ölçeklendirmek için kodu gerekli kaynakları ayırır.

Aşağıdaki çizimde, dört sunucusuz Bileşen diyagramları. Bir HTTP isteği Checkout API'si kodun çalışmasına neden olur. Checkout API'si kodu veritabanına ekler ve görevleri bilgi işlem ve siparişi yerine getirmesini gibi görevleri gerçekleştirmek için çalıştırılacak çeşitli işlevler INSERT tetikler.

![Sunucusuz uygulama](./media/serverless-implementation.png)

Sunucusuz avantajları şunlardır:

* **Yüksek yoğunluklu.** Kapsayıcılar veya sanal makinelere kıyasla aynı ana bilgisayardaki aynı sunucusuz kod pek çok örneğini çalıştırabilirsiniz. Örnekler ölçek birden fazla ana bilgisayar ölçek genişletme ve esneklik.
* **Micro-fatura**. Bazı senaryolarda büyük maliyetten tasarruf sunucusuz yürütme göre en sunucusuz sağlayıcıları fatura.
* **Anında ölçek**. Sunucusuz iş yükleri hızla ve otomatik olarak eşleşecek şekilde ölçeklendirebilirsiniz.
* **Pazara daha hızlı** geliştiriciler kodu odaklanın ve doğrudan sunucusuz platforma dağıtın. Bileşenleri birbirinden serbest bırakılabilir.

Sunucusuz, çoğunlukla işlem bağlamında ele alınmıştır, ancak verileri de uygulayabilirsiniz. Örneğin, [Azure SQL](https://docs.microsoft.com/azure/sql-database) ve [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) her ikisi de konak makine ya da küme yapılandırmanızı gerektirmeyen bulut veritabanları sağlar. Bu kitap, sunucusuz bir işlem üzerinde odaklanır.

## <a name="summary"></a>Özet

Seçenekler için Mimari, karma bir yaklaşım da dahil olmak üzere geniş bir yelpazedeki yoktur. Sunucusuz bir yaklaşım, yönetim ve maliyet denetimi ve taşınabilirlik çoğaltamaz uygulama özelliklerinin basitleştirir. Ancak, birçok sunucusuz platformları çözümü ayarlamanıza yardımcı olmak için yapılandırmayı kullanıma sunar. İyi bir programlama uygulamalarını da kodu daha taşınabilir ve sunucusuz platform kilit açma daha az yol açabilir. Aşağıdaki tabloda, yan yana mimari yaklaşım gösterilmektedir. Sunucusuz ölçek gereksinimlerini, çalışma zamanı yönetmek istediğiniz olup olmadığı ve ne kadar iyi iş yüklerinizi küçük bileşenlere bozabilir göre seçin. Sunucusuz ile olası zorlukları ve diğer sonraki bölümde karar noktaları hakkında bilgi edineceksiniz.

|         |Iaas     |PaaS     |Kapsayıcı|Sunucusuz|
|---------|---------|---------|---------|----------|
|**Ölçek**|VM       |Örnek |Uygulama      |İşlev  |
|**Özet**|Donanım|Platform|Konak işletim sistemi|Çalışma zamanı   |
|**Birim** |VM       |Proje  |Görüntü    |Kod      |
|**Ömür**|Ay|Ay gün|Dakika-gün|Dakika milisaniye|
|**Sorumluluk**|Uygulamalar, bağımlılıkları, çalışma zamanı ve işletim sistemi|Uygulamalar ve bağımlılıklar|Uygulamalar, bağımlılıklar ve çalışma zamanı|İşlev

* **Ölçek** uygulama ölçeklendirme için kullanılan birim başvuruyor
* **Soyutlar** uygulama tarafından soyutlanır katmanına başvuran
* **Birim** ne dağıtılır kapsamına başvuruyor
* **Yaşam süresi** belirli bir örneğinin normal çalışma zamanına başvuruyor
* **Sorumluluk** oluşturmanızı, dağıtmanızı ve uygulama sağlamak için ek yükü başvuruyor

Sonraki bölümde sunucusuz bir mimari temelinde odaklanmak, kullanım ve tasarım desenleri.

## <a name="recommended-resources"></a>Önerilen kaynaklar

* [Azure Uygulama Mimarisi Kılavuzu](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [N katmanlı mimari deseni](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Azure'da Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Mikro hizmetler](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Sanal makine N katmanlı başvuru mimarisi](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Sanal makineler](https://docs.microsoft.com/azure/virtual-machines/)
* [Docker nedir?](../microservices-architecture/container-docker-introduction/docker-defined.md)
* [Wingtip bilet SaaS uygulaması](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Önceki](architecture-approaches.md)
>[İleri](serverless-architecture.md)