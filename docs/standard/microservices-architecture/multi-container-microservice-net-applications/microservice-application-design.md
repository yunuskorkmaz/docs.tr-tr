---
title: Mikro hizmet odaklı bir uygulama tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmet odaklı bir uygulama tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 4adf7e759d4475d0bb9b3aa0abe8dbdc5e57edd3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879899"
---
# <a name="designing-a-microservice-oriented-application"></a>Mikro hizmet odaklı bir uygulama tasarlama

Bu bölüm, bir kuramsal sunucu tarafı Kurumsal uygulama geliştirmeye odaklanır.

## <a name="application-specifications"></a>Uygulama özellikleri

Kuramsal bir uygulamanın iş mantığı yürütme veritabanlarına erişme ve ardından HTML, JSON veya XML yanıtlar döndüren isteklerini işler. Uygulama istemciler, tek sayfa uygulamaları (Spa'lar), geleneksel web uygulamaları, mobil web uygulamaları ve yerel mobil uygulamalar çalıştıran masaüstü tarayıcıları dahil olmak üzere çeşitli desteklemelidir dediğimiz. Uygulama, üçüncü tarafların kullanmak için bir API de doğurabilir. Böylece yaklaşım dayanıklılığı kısmi hatası durumunda mikro yardımcı olur, ayrıca, mikro hizmetler veya dış uygulama, zaman uyumsuz olarak tümleştirebilir olmalıdır.

Uygulama bileşenlerinin bu tür oluşur:

-   Sunu bileşenleri. Bu, UI işleme ve uzak Hizmetleri tüketen sorumludur.

-   Etki alanı veya iş mantığı. Uygulama etki alanı mantığı budur.

-   Veritabanı erişim mantığı. Bu, veri erişim bileşenleri (SQL veya NoSQL) veritabanları erişmekten sorumlu oluşur.

-   Uygulama Tümleştirme mantığı. Bu, çoğunlukla ileti aracıları üzerinde tabanlı bir Mesajlaşma kanalı içerir.

Uygulamanın yüksek ölçeklenebilirlik, otonom olarak, ölçeği genişletme, dikey alt sistemlerin belirli alt sistemlerin diğerlerinden daha fazla ölçeklenebilirlik gerekir çünkü verirken gerektirir.

Uygulama birden çok altyapı ortamlarda (birden çok genel bulutlarda ve şirket içi) dağıtılması gereken ve ideal olmalıdır platformlar arası ve Linux'taki Windows (veya tersi) bir kolayca geçiş yapabilirsiniz.

## <a name="development-team-context"></a>Geliştirme ekibi bağlamı

Ayrıca uygulama geliştirme süreci hakkında aşağıdakileri varsayılır:

-   Birden çok geliştirme ekipleri uygulamanın farklı işletme alanlarına odaklanan var.

-   Yeni takım üyelerine hızlı şekilde üretken olmaya gerekir ve uygulama anlamak ve değiştirilmesi kolay olmalıdır.

-   Uygulamanın, uzun vadeli gelişimi ve durmaksızın değişen iş kuralları gerekir.

-   Çeviklik, diğer alt sistemler üzerinde minimum etkiyle birden çok alt sistemin güncelleştiremezsiniz olmanın yanı sıra gelecekte yeni değişiklikler uygulanırken olması anlamına gelir iyi uzun süreli bakım ihtiyacınız vardır.

-   Uygulama sürekli tümleştirme ve sürekli dağıtım uygulamanın istediğiniz.

-   Yeni çıkan teknolojiler (çerçeveleri, programlama dilleri, vb.) yararlanmak uygulama hızla gelişirken diğer yandan istediğiniz. İçinde yüksek maliyetlere neden ve uygulamanın kararlılığını ve tahmin edilebilirliğini etkiler çünkü yeni teknolojileri için taşırken uygulamanın tam geçiş yapmak istiyor musunuz.

## <a name="choosing-an-architecture"></a>Bir mimari seçme

Hangi uygulama dağıtım mimarisi olması gerekiyor mu? Geliştirme bağlam yanı sıra uygulama belirtimleri kesin, birlikte çalışan mikro hizmetler ve kapsayıcılar, biçiminde otonom alt sistemleri içine bir mikro hizmet burada parçalama tarafından uygulamanın mimari önerin bir kapsayıcıdır.

Bu yaklaşımda, her bir hizmet (kapsayıcı) bağlı ve sayısı azalacağından ilgili işlevler bir dizi uygular. Örneğin, bir uygulama Kataloğu hizmeti sıralama hizmeti, sepet hizmeti, kullanıcı profili hizmeti, vb. gibi hizmetleri oluşabilir.

Mikro hizmet iletişim protokolleri tür olarak HTTP (REST), ancak ayrıca zaman uyumsuz olarak kullanarak (örneğin, AMQP kullanarak) mümkün olduğunda, özellikle zaman yayma güncelleştirmeleri ile tümleştirme olayları.

Mikro hizmetler geliştirilen ve birbirinden kapsayıcıları olarak dağıtılabilir. Bu, bir geliştirme ekibi kullanılabilir geliştirmeye ve diğer alt sistemlerin etkilemeden belirli bir mikro hizmet dağıtımı, anlamına gelir.

Her mikro hizmet, diğer mikro Hizmetleri tam olarak ölçeklendirilebilmeleri izin veren, kendi veritabanı vardır. Gerektiğinde, veritabanlarından farklı mikro hizmetler arasında tutarlılık (aracılığıyla bir mantıksal olay veri yolu), uygulama düzeyinde tümleştirme olayları kullanılarak komut ve sorgu sorumluluğu ayrımı (CQRS) işlenmiş olarak sağlanır. Bu nedenle iş kısıtlamalarını nihai tutarlılık arasında birden fazla mikro hizmetin yaklaşımını benimseyin gerekir ve ilgili veritabanları.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>Hizmetine: .NET Core ve kapsayıcılar kullanılarak dağıtılmış mikro hizmetler için bir başvuru uygulaması

Böylece bilmiyor bir hypothetic iş etki alanı düşünmek yerine teknolojileri ve mimari odaklanabilirsiniz iyi bilinen iş etki alanı seçmiş olduğunuz — yani, bir katalog sunar bir Basitleştirilmiş e-ticaret (e-Atölye) uygulama ürünler, işle ilgili diğer işlevleri gerçekleştiren müşterilerden siparişleri alır ve envanter doğrular. Bu kapsayıcı tabanlı uygulama kaynak kodunu kullanılabilir [hizmetine](https://aka.ms/MicroservicesArchitecture) GitHub deposu.

Uygulamayı birkaç depolama UI ön uçlar (bir Web uygulaması ve yerel bir mobil uygulama) yanı sıra arka uç mikro hizmetler ve kapsayıcılar için gerekli tüm sunucu tarafı işlemleri dahil olmak üzere birden çok alt sistemin oluşur. Şekil 8-1, başvuru uygulaması mimarisi gösterilmektedir.

![](./media/image1.png)

**Şekil 8-1**. Bir doğrudan istemci-mikro hizmet iletişimi ve olay veri yolu gösteren uygulama hizmetine başvuru

**Barındırma ortamı**. Şekil 8-1'de, tek bir Docker konağı içinde dağıtılan birden fazla kapsayıcı görürsünüz. Bu olacak durum docker ile tek bir Docker konağı için dağıtırken-compose komutu. Ancak, eğer kullanarak bir orchestrator veya kapsayıcı kümesi, her kapsayıcı farklı bir konağa (node) çalışıyor olabilir ve biz mimarisi bölümünde daha önce açıklandığı gibi herhangi bir düğümü kapsayıcılar, herhangi bir sayıda çalışıyor olabilir.

**İletişim mimarisi**. Hizmetine uygulama (güncelleştirmeler ve işlemleri karşı sorgular) işlevsel eylem türünü bağlı olarak iki iletişim türlerini kullanır:

-   Doğrudan istemci-mikro hizmet iletişimi. Bu sorguları ve güncelleştirme veya istemci uygulamalarından işlem komutları kabul ederken kullanılır.

-   Zaman uyumsuz olay tabanlı iletişim. Mikro hizmetler güncelleştirmeler yayılması veya dış uygulamalarla tümleştirmek için bir olay veri yolu üzerinden gerçekleşir. Olay veri yolu, RabbitMQ veya Azure Service Bus, NServiceBus, MassTransit veya Brighter gibi daha üst düzey hizmet yolları kullanarak gibi herhangi bir Mesajlaşma Aracısı altyapı teknolojisi ile uygulanabilir.

Uygulama kapsayıcıları biçiminde mikro hizmetler kümesi olarak dağıtılır. İstemci uygulamaları bu kapsayıcılarla iletişim yapabilir mikro Hizmetler iletişim. Belirtildiği gibi bu ilk mimari bir istemci uygulamanın istekleri her mikro Hizmetleri doğrudan yapabileceğini anlamına gelir. bir doğrudan istemci-mikro hizmet iletişimi mimarisi kullanır. Her mikro hizmet gibi genel bir uç nokta sahip https://servicename.applicationname.companyname. Gerekirse, her bir mikro hizmetin farklı bir TCP bağlantı noktası kullanabilirsiniz. URL mikro Hizmetleri yük dengeleyici ile eşleyin üretim, hangi istekleri kullanılabilir mikro hizmet örnekleri arasında dağıtır.

**Önemli Not API ağ geçidi vs üzerinde. Doğrudan iletişim hizmetine.** Büyük ve karmaşık mikro hizmet tabanlı bir uygulama oluştururken bu kılavuzun mimarisi bölümünde açıklandığı gibi doğrudan istemci-mikro hizmet iletişimi mimarisi dezavantajları olabilir. Ancak hizmetine uygulama olduğu hedef bir basit sağlamaya odaklanın, Docker kapsayıcı tabanlı uygulama çalışmaya ve tek tek parça API etkileyebilecek ağ geçidi oluşturmak istemedik gibi küçük bir uygulama için yeterince iyi olabilir mikro hizmetler geliştirme bağımsız çalışma sınırı.

Ancak mikro hizmetler onlarca ile büyük bir mikro hizmet tabanlı uygulama tasarlamak için kullanacaksanız, biz mimarisi bölümünde açıklandığı gibi API ağ geçidi desenini düşünün öneririz.
Bu mimari kararı uzak istemciler için üretime hazır uygulamalar ve özel olarak yapılan cepheleri hakkında düşünmek sonra düzenlenmeye. İstemci uygulamaları form faktörü bağlı olarak özel birden çok API ağ geçitleri olan istemci uygulaması başına farklı veri toplama in regard to avantajları sağlayabilir Ayrıca iç mikro hizmetler veya API'leri için istemci uygulamaları Gizle ve bu tek katmanda yetkilendirin. 

Ancak ve bahsedildiği gibi büyük ve tek parça API, mikro hizmetler geliştirme otonomi KILL, ağ geçitleri karşı dikkatli olun.

### <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri hakimiyeti

Örnek uygulamada, her bir mikro hizmet kendi veritabanını veya veri kaynağı ve her veritabanı sahibi veya veri kaynağı başka bir kapsayıcı olarak dağıtılır. Bu tasarım kararına, yalnızca bir geliştiricinin kodunu Github'dan alma, kopyalayın ve Visual Studio veya Visual Studio Code içinde açmak kolaylaştıran yapıldı. Veya alternatif olarak, .NET Core CLI ve Docker CLI'yı kullanarak özel Docker görüntülerini derleme ve dağıtma ve bunları bir Docker geliştirme ortamında çalıştırmak kolaylaştırır. Her iki durumda da geliştiriciler oluşturun ve harici bir veritabanına veya (Bulut veya şirket içi) altyapı sabit bağımlılıkları olan başka bir veri kaynağı sağlamak zorunda kalmadan birkaç dakika içinde dağıtma sağlar kapsayıcıları için verileri kullanarak kaynakları.

Gerçek bir üretim ortamında, ölçeklenebilirlik ve yüksek kullanılabilirlik için veritabanları veritabanı sunucularında bulutta veya şirket içi, ancak kapsayıcıları bağlı olmalıdır.

Bu nedenle, mikro hizmetler için (ve bu uygulamada veritabanları için bile) dağıtım birimlerinin Docker kapsayıcıları ve mikro hizmetler ilkeleri benimsediğini çok kapsayıcılı bir uygulama başvuru uygulaması olduğundan.

### <a name="additional-resources"></a>Ek kaynaklar

-   **GitHub deposunu hizmetine. Başvuru uygulaması için kaynak kodu**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözüm avantajları

Bir mikro hizmet tabanlı çözümü bu gibi birçok avantaj vardır:

**Her mikro hizmet göreceli olarak küçüktür — yönetmek ve geliştirmek kolay**. Özellikle:

-   Anlama ve iyi üretkenliği hızlı bir şekilde kullanmaya başlamak bir geliştirici kolaydır.

-   Kapsayıcıları, geliştiricilerin daha üretken yapar Hızlı Başlat.

-   Visual Studio gibi bir IDE, geliştiricilerin daha üretken hale getirme hızlı, daha küçük projeleri yükleyebilirsiniz.

-   Her mikro hizmet, geliştirilen ve çeviklik, mikro hizmetler, yeni sürümler sık dağıtmak daha kolay olduğundan sağlayan diğer mikro hizmetler bağımsız olarak, dağıtılan tasarlanmıştır.

**Bireysel alanları uygulamanın ölçeğini filtrelenebilir**. Örneğin, katalog hizmeti veya sepet hizmeti, ancak sıralama sürecin ölçeği gerekebilir. Bir mikro hizmet altyapısı dışarı monolitik bir mimari olandan ölçeklendirme kullanılan kaynakları ile ilgili çok daha verimli olacaktır.

**Birden çok ekipler arasında geliştirme iş bölebilirsiniz**. Her hizmet tek bir geliştirme ekibi tarafından ait olabilir. Her takım yönetmek, geliştirin, dağıtın ve takımlar geri kalanı bağımsız olarak, hizmet ölçeklendirin.

**Sorunları daha yalıtılmış**. Bir hizmette bir sorun varsa, yalnızca bu hizmet, başlangıçta (yanlış tasarımı, mikro hizmetler arasında doğrudan bağımlılıklarla kullanılmadığı sürece) etkilenir ve diğer hizmetleri istekleri işlemeye devam edebilir. Buna karşılık, özellikle bir bellek sızıntısı gibi kaynakları gerektirdiğinde monolitik dağıtım mimarisi düzgün çalışmayan bir bileşeni tüm sistemin çökmesine getirebilirsiniz. Ayrıca, bir mikro hizmet içinde bir sorun çözüldüğünde, yalnızca etkilenen mikro hizmet uygulama geri kalanı etkilemeden dağıtabilirsiniz.

**En son teknolojileri kullanabilirsiniz**. Hizmetler bağımsız olarak geliştirmeye başlayın ve yan yana (kapsayıcılar ve .NET Core sayesinde) çalıştırmak için en son teknolojileri ve çerçeveleri expediently daha eski bir yığın veya tüm framework takılması yerine kullanmaya başlayabilirsiniz uygulama.

## <a name="downsides-of-a-microservice-based-solution"></a>Bir mikro hizmet tabanlı çözümün downsides

Böyle bir mikro hizmet tabanlı çözümü, ayrıca bazı dezavantajları vardır:

**Dağıtılmış bir uygulama**. Tasarlama ve oluşturma hizmetleri uygulaması dağıtma geliştiriciler için karmaşıklık ekler. Örneğin, geliştiriciler, HTTP veya test etmek ve özel durum işleme için karmaşıklık ekleyen AMPQ gibi protokolleri kullanılarak hizmetin iletişim uygulamalıdır. Ayrıca sisteme gecikme süresi ekler.

**Dağıtım karmaşıklığı**. Mikro hizmetler türleri onlarca ve (Bu hizmet başına çok sayıda örnekleri oluşturmak ve bu hizmetlerin çok konak genelinde dengelemek gerekir), yüksek ölçeklenebilirlik gereken bir uygulama, BT operasyon ve yönetimi için yüksek derecede dağıtım karmaşıklık anlamına gelir. Bir mikro hizmet odaklı altyapısı (orchestrator ve Zamanlayıcı gibi) kullanmıyorsanız, bu karmaşıklık iş uygulaması daha çok daha fazla geliştirme çalışmalarını gerektirebilir.

**Atomik işlemler**. Atomik işlemler genellikle birden çok mikro hizmetler arasında mümkün değildir. İş gereksinimlerini birden fazla mikro hizmetler arasında nihai tutarlılık yaklaşımını benimseyin gerekir.

**Genel kaynak gereksinimlerini artırılmış** (toplam bellek, sürücüler ve sunucular veya ana bilgisayar için ağ kaynaklarına). Bir mikro hizmetler yaklaşımı ile tek parça bir uygulamayı değiştirdiğinizde çoğu durumda, yeni mikro hizmet tabanlı uygulama için gerekli olan genel kaynaklar miktarını özgün tek parça uygulamanın Altyapı gereksinimlerini büyük olacaktır. Daha ileri düzeyde ayrıntı düzeyi ve dağıtılmış hizmetlerin daha genel kaynaklar gerektirdiğinden budur. Ancak, düşük maliyetli genel ve yalnızca belirli alanları tek parçalı uygulamalarla gelişen, uzun vadeli maliyet karşılaştırıldığında uygulamanın ölçeğini genişletmek işaretleyebilmesine avantajı kaynakları göz önünde bulundurulduğunda, artan kaynaklar için genellikle iyi bir denge kullanımıdır büyük uzun vadeli uygulamalar.

**Doğrudan client‑to‑microservice iletişimle ilgili sorunlar**. Uygulama, mikro hizmetler onlarca ile büyük olduğunda, zorlukları ve sınırlamalar vardır uygulama doğrudan istemci-mikro hizmet iletişimi gerekiyorsa. İstemci gereksinimlerini ve her bir mikro hizmetler tarafından sunulan API'lerde arasında olası uyuşmazlık bir sorundur. Bazı durumlarda, istemci uygulaması, birçok ayrı istekler Internet üzerinden verimsiz olabilir ve bir mobil ağ üzerinden pratik kullanıcı Arabirimi oluşturmak için yapmanız gerekebilir. Bu nedenle, istemci uygulaması arka uç sistemine gelen istekleri en aza.

Doğrudan istemci-mikro hizmet iletişimi ile başka bir sorun, bazı mikro hizmetler Web dostu olmayan protokolleri kullanabilecek olmasıdır. AMQP ileti başka bir hizmet kullanırken bir hizmeti bir ikili protokolünü kullanıyor olabilir. Bu protokoller firewall‑friendly değildir ve en iyi dahili olarak kullanılır. Genellikle, bir uygulama güvenlik duvarı dışında iletişim için HTTP ve WebSockets gibi protokoller kullanmanız gerekir.

Henüz bu doğrudan client‑to‑service yaklaşım ile başka bir dezavantajı, bu anlaşmalar Bu mikro hizmetlere yönelik yeniden düzenlenmesi zor yapmasıdır. Zaman içinde geliştiricilere, Sistem Hizmetleri içine nasıl bölümlenmiş değiştirmek isteyebilirsiniz. Örneğin, bunlar iki hizmet birleştirme veya bir hizmeti iki veya daha fazla hizmetlerine bölün. İstemciler Hizmetleri ile doğrudan iletişim kurar, ancak bu tür yeniden düzenleme gerçekleştirme istemci uygulamaları ile uyumluluğu bozabilir.

Tasarlama ve üzerinde mikro hizmet tabanlı karmaşık bir uygulama oluştururken mimari bölümünde bahsedildiği gibi basit bir doğrudan client‑to‑microservice iletişim yaklaşım yerine ayrıntılı birden çok API ağ geçitleri kullanımını göz önünde bulundurabilirsiniz.

**Mikro hizmet bölümleme**. Son olarak, göz önüne almanız, mikro hizmet mimarisi için hangi yaklaşımın ne olursa olsun, bir diğer zorluk nasıl ayıracağınız birden fazla mikro hizmetlerin uçtan uca uygulamaya karar vermektir. Kılavuzu mimarisi bölümünde belirtildiği gibi çeşitli teknikler ve uygulayabileceğiniz bir yaklaşım vardır. Temel olarak, uygulamanın diğer bölümler birbirinden ayrılmıştır ve sabit bağımlılıkları az sayıda olan alanları belirlemek gerekir. Çoğu durumda, bu hizmetleri bölümleme için kullanım örneği tarafından hizalanır. Örneğin, e-Atölye uygulamamız sipariş işleme ilgili tüm iş mantığı sorumlu olan bir sıralama hizmeti sahibiz. Ayrıca katalog hizmeti ve diğer özellikleri uygulayan sepet hizmeti sahibiz. İdeal olarak, her hizmetin sorumlulukları küçük bir dizi olmalıdır. Bu, bir sınıf yalnızca değiştirmek için bir neden olması gerektiğini bildiren sınıfa uygulanan tek sorumluluk ilkeye (SRP) benzer. Ancak bu durumda, kapsamı tek bir sınıf büyük olacak şekilde mikro hizmetler hakkında değildir. En önemlisi, bir mikro hizmet tamamen otonom, uçtan uca sorumluluk kendi veri kaynakları için de dahil olmak üzere olmak zorundadır.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Dış ve iç mimari ve tasarım desenleri

Bu kılavuz mimarisi kısmında tanımlanan ilkeler uygulayarak birden çok hizmet tarafından oluşan mikro hizmet mimarisi dış mimaridir. Ancak, her mikro hizmet ve üst düzey bir mikro hizmet mimarisi seçtiğiniz bağımsız olarak yapısı, bağlı olarak ortak ve farklı iç mimarileri için bazen önerilir, her için farklı eğilimlere bağlı farklı mikro hizmetler. Mikro hizmetler, hatta farklı teknolojiler ve programlama dilini kullanabilirsiniz. Şekil 8-2 Bu seviyelerine gösterilir.

![](./media/image2.png)

**Şekil 8-2**. Dış ve iç mimari ve tasarım

Örneğin, bizim *hizmetine* basit örnek, katalog, sepet ve kullanıcı profili mikro hizmetler (temel, alt sistemlerin CRUD). Bu nedenle, kendi iç mimari ve tasarım basit. Ancak, diğer mikro hizmetler gibi daha karmaşıktır ve durmaksızın değişen iş kuralları ile etki alanı karmaşıklık yüksek derecede temsil eder. sıralama mikro olabilir. Bu gibi durumlarda, biz yapıyor olarak etki alanı Odaklı Tasarım (DDD) yaklaşımı ile tanımlanmış olanlar gibi belirli bir mikro hizmet içinde daha gelişmiş desenler uygulamak isteyebilirsiniz *hizmetine* sıralama mikro hizmet. (Şimdi bu DDD deseni uygulaması açıklayan bölümde daha sonra gözden *hizmetine* mikro hizmet sıralama.)

Mikro hizmet başına farklı bir teknoloji başka bir nedenle, her bir mikro hizmetin niteliği olabilir. Örneğin, F gibi işlevsel bir programlama dili kullanmak daha iyi olabilir\#, hatta bir dil R gibi yapay ZEKA ve makine öğrenimi C gibi daha fazla nesne yönelimli programlama dili yerine etki alanları hedefliyorsanız\#.

Alt çizgi, her bir mikro hizmetin farklı tasarım düzenlerini esas alarak farklı bir iç mimari sahip olabilmeleridir. Bunları aşırı mühendislik çünkü tüm mikro Hizmetleri, Gelişmiş DDD deseni kullanılarak uygulanmalıdır. Benzer şekilde, karmaşık mikro hizmetler durmaksızın değişen iş mantığına sahip CRUD bileşenleri uygulanmamalıdır veya düşük kaliteli kodlar kalabilirsiniz.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Yeni Dünya: birden çok mimari desenleri ve çok yönlü mikro hizmetler

Yazılım mimarları ve geliştiricileri tarafından kullanılan birçok mimari desenleri vardır. Birkaçı verilmiştir (Mimari stilleri ile mimarisi desenleri karıştırma):

-   Basit CRUD, tek katmanlı tek katmanlı.

-   [Geleneksel N katmanlı](https://msdn.microsoft.com/library/ee658109.aspx#Layers).

-   [Etki alanı tasarım N katmanlı odaklı](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Mimari Temizleme](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (ile kullanılan [eShopOnWeb](https://aka.ms/WebAppArchitecture))

-   [Komut ve sorgu sorumluluğu ayrımı](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Olay denetimli mimari](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Ayrıca, birçok teknolojiler ve ASP.NET Core Web API, NancyFx, ASP.NET Core SignalR (.NET Core 2 ile kullanılabilir), F gibi dilleri ile mikro hizmetler oluşturabilirsiniz\#, Node.js, Python, Java, C++, GoLang ve daha fazlası.

Herhangi bir belirli mimari desen veya stil ya da belirli bir teknoloji tüm durumlar için doğru olduğunu önemli noktasıdır. (Değil herhangi bir sırada belirli rağmen) Şekil 8-3 gösteren bazı yaklaşımları ve teknolojileri farklı mikro Hizmetleri kullanılabilir.

![](./media/image3.png)

**Şekil 8-3**. Birden çok mimari desenleri ve çok yönlü mikro hizmetler world

Gösterildiği gibi Şekil 8-3, uygulamaların birçok mikro hizmetler (sınırlanmış her bir mikro hizmetin farklı bir şekilde uygulayabilir kapsamları etki alanı Odaklı Tasarım terminolojisi ya da sadece "alt" otonom mikro hizmetler olarak) oluşur. Her farklı mimari deseni sahip olabileceğiniz ve farklı dilleri ve veritabanlarını uygulama yapısı, iş gereksinimlerini ve öncelikler bağlı olarak kullanın. Bazı durumlarda, mikro hizmetler benzer olabilir. Ancak, her alt sisteminin içerik sınırı ve gereksinimleri genellikle farklı olduğundan, genellikle, geçerli değildir.

Örneğin, için basit bir CRUD bakım uygulama, bu tasarlamak ve DDD desenlerini uygulama için anlamlı olmayabilir. Ancak temel etki alanı veya çekirdek iş için durmaksızın değişen iş kuralları ile iş karmaşıklığını gidermek için daha gelişmiş desenleri uygulamak gerekebilir.

Özellikle, birden çok alt sistemi tarafından oluşturulan büyük uygulamalar ile dağıttığınızda, bir tek mimari deseni temel alınarak tek bir üst düzey mimari geçerli. Örneğin, CQRS tüm uygulama için üst düzey bir mimari olarak uygulanmamalıdır, ancak belirli bir hizmetler kümesi için yararlı olabilir.

Gümüş madde işareti yok veya verilen her durum için doğru mimari desen yoktur. "Hepsini yönetmek için bir mimari deseni." sahip olamaz Her mikro hizmet öncelikler bağlı olarak, farklı bir yaklaşım her biri için aşağıdaki bölümlerde açıklandığı gibi seçmeniz gerekir.


>[!div class="step-by-step"]
[Önceki](index.md)
[İleri](data-driven-crud-microservice.md)
