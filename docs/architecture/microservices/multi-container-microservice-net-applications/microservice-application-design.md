---
title: Mikro hizmet odaklı bir uygulama tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Mikro hizmet odaklı bir uygulamanın faydalarını ve dezavantajlarını anlayın, böylece bilinçli bir karar alabilirsiniz.
ms.date: 10/02/2018
ms.openlocfilehash: 619440c02c1a82e05adb2cec9ddba933cd3e0a65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76965769"
---
# <a name="design-a-microservice-oriented-application"></a>Mikro hizmet odaklı bir uygulama tasarla

Bu bölümde varsayımsal bir sunucu tarafı kurumsal uygulama geliştirmeye odaklanın.

## <a name="application-specifications"></a>Uygulama özellikleri

Varsayımsal uygulama, iş mantığı çalıştırarak, veritabanlarına erişerek ve ardından HTML, JSON veya XML yanıtlarını döndürerek istekleri işler. Uygulamanın, Tek Sayfa uygulamaları (SPA'lar), geleneksel web uygulamaları, mobil web uygulamaları ve yerel mobil uygulamalar çalıştıran masaüstü tarayıcıları da dahil olmak üzere çeşitli istemcileri desteklemesi gerektiğini söyleyeceğiz. Uygulama, üçüncü tarafların tüketebileceği bir API'yi de ortaya çıkarabilir. Ayrıca, mikro hizmetlerini veya harici uygulamalarını eşit olarak entegre edebilmelidir, böylece bu yaklaşım kısmi arızalarda mikro hizmetlerin esnekliğine yardımcı olacaktır.

Uygulama bu tür bileşenlerden oluşacaktır:

- Sunum bileşenleri. Bunlar, ui'yi işlemekten ve uzak hizmetleri tüketmekten sorumludur.

- Etki alanı veya iş mantığı. Bu, uygulamanın etki alanı mantığıdır.

- Veritabanı erişim mantığı. Bu, veritabanlarına (SQL veya NoSQL) erişmekle sorumlu veri erişim bileşenlerinden oluşur.

- Uygulama tümleştirme mantığı. Bu, çoğunlukla ileti aracılarına dayalı bir mesajlaşma kanalLarını içerir.

Uygulama yüksek ölçeklenebilirlik gerektirir, dikey alt sistemlerinin bağımsız olarak ölçeklendirmesine izin verirken, çünkü bazı alt sistemler diğerlerinden daha fazla ölçeklenebilirlik gerektirir.

Uygulama birden çok altyapı ortamlarında (birden çok genel bulut ve şirket içi) dağıtılabilmeli ve ideal olarak çapraz platform olmalıdır, Linux'tan Windows'a (veya tam tersi) kolayca geçebilmeli.

## <a name="development-team-context"></a>Geliştirme ekibi bağlamı

Ayrıca uygulama için geliştirme süreci hakkında aşağıdakileri varsayıyoruz:

- Uygulamanın farklı iş alanlarına odaklanan birden çok geliştirme ekibiniz var.

- Yeni ekip üyeleri hızlı bir şekilde üretken olmalıdır ve uygulama nın anlaşılması ve değiştirilmesi kolay olmalıdır.

- Uygulama uzun vadeli bir evrim ve sürekli değişen iş kuralları olacaktır.

- Diğer alt sistemler üzerinde en az etkiye sahip birden çok alt sistemi güncelleştirebilme de gelecekte yeni değişiklikleri uygularken çevikliğe sahip olmak anlamına gelir, iyi uzun vadeli bakım gerekir.

- Sürekli tümleştirme ve uygulamanın sürekli dağıtım uygulama istiyorum.

- Uygulamayı geliştirirken gelişen teknolojilerden (çerçeveler, programlama dilleri, vb.) yararlanmak istiyorsunuz. Yeni teknolojilere geçerken uygulamanın tam geçişlerini yapmak istemezsinüz, çünkü bu yüksek maliyetlere neden olur ve uygulamanın öngörülebilirliğini ve kararlılığını etkiler.

## <a name="choosing-an-architecture"></a>Mimari seçme

Uygulama dağıtım mimarisi ne olmalıdır? Uygulamanın özellikleri, geliştirme bağlamı ile birlikte, bir mikro hizmetin bir mikro hizmetin bulunduğu, işbirliği yapan mikro hizmetler ve kapsayıcılar şeklinde özerk alt sistemlere ayrıştırarak uygulamayı mimarlamanızı kuvvetle önerir. bir konteynerdir.

Bu yaklaşımda, her hizmet (kapsayıcı) uyumlu ve dar ilişkili işlevleri bir dizi uygular. Örneğin, bir uygulama katalog hizmeti, sipariş hizmeti, sepet hizmeti, kullanıcı profili hizmeti gibi hizmetlerden oluşabilir.

Mikro hizmetler, http (REST) gibi protokolleri kullanarak, aynı zamanda eş senkronize (örneğin, MÜMKÜN olduğunda AMQP kullanarak) kullanarak, özellikle tümleştirme olayları ile güncelleştirmeleri yaymak.

Mikro hizmetler birbirinden bağımsız olarak konteyner olarak geliştirilir ve dağıtılır. Bu, geliştirme ekibinin diğer alt sistemleri etkilemeden belirli bir mikro hizmeti geliştirebileceği ve dağıtabileceği anlamına gelir.

Her microservice tamamen diğer microservices ayrılmış olmasını sağlayan kendi veritabanı vardır. Gerektiğinde, komut ve sorgu sorumluluğu ayrımında (CQRS) ele alınan uygulama düzeyindetümleştirme olayları (mantıksal bir olay veri meseni aracılığıyla) kullanılarak farklı mikro hizmetlerden veritabanları arasında tutarlılık sağlanır. Bu nedenle, iş kısıtlamaları birden çok mikro hizmetler ve ilgili veritabanları arasında nihai tutarlılık kucaklamak gerekir.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: .NET Core ve konteynerler kullanılarak dağıtılan mikro hizmetler için bir referans uygulaması

Bilmediğiniz varsayımsal bir iş alanı hakkında düşünmek yerine mimari ve teknolojilere odaklanabilmeniz için, tanınmış bir iş alanı seçtik, yani katalog sunan basitleştirilmiş bir e-ticaret (e-shop) uygulaması ürünlerin, müşterilerden sipariş alır, envanteri doğrular ve diğer iş işlevlerini gerçekleştirir. Bu konteyner tabanlı uygulama kaynak kodu [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) GitHub repo mevcuttur.

Uygulama, birkaç mağaza Kullanıcı Arabirimi ön uçları (Web uygulaması ve yerel bir mobil uygulama) dahil olmak üzere birden fazla alt sistemden oluşur ve arka uç mikrohizmetleri ve konteynerleri ile birkaç API Ağ Geçidi ile gerekli tüm sunucu tarafı işlemleri için iç mikrohizmetlere konsolide giriş noktaları. Şekil 6-1 başvuru uygulamasının mimarisini gösterir.

![Tek bir Docker ana bilgisayarda eShopOnContainers kullanarak istemci uygulamaları diyagramı.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Şekil 6-1**. Geliştirme ortamı için eShopOnContainers başvuru uygulama mimarisi

Yukarıdaki diyagram, Mobil ve SPA istemcilerinin tek API ağ geçidi uç noktalarıyla iletişim kurduğunu ve daha sonra mikro hizmetlere iletişim kurduğunu gösterir. Geleneksel web istemcileri, API ağ geçidi aracılığıyla mikro hizmetlere iletişim sağlayan MVC microservice ile iletişim kurar.

**Barındırma ortamı.** Şekil 6-1'de, tek bir Docker ana bilgisayar içinde dağıtılan birkaç kapsayıcı görürsünüz. Docker-comto komutu ile tek bir Docker ana bilgisayara dağıtım yaparken bu durumda olacaktır. Ancak, bir orchestrator veya kapsayıcı kümesi kullanıyorsanız, her kapsayıcı farklı bir ana bilgisayarda (düğüm) çalışıyor olabilir ve herhangi bir düğüm, daha önce mimari bölümünde açıklandığı gibi herhangi bir sayıda kapsayıcı çalışıyor olabilir.

**İletişim mimarisi**. eShopOnContainers uygulaması işlevsel eylem türüne bağlı olarak iki iletişim türü kullanır (güncelleştirmeler ve işlemler karşı sorgular):

- API Ağ Geçitleri üzerinden http istemciden mikrohizmet iletişimine. Bu, sorgular için ve istemci uygulamalarından güncelleştirme veya işlem komutları kabul ederken kullanılır. API Ağ Geçitleri'ni kullanan yaklaşım daha sonraki bölümlerde ayrıntılı olarak açıklanmıştır.

- Asynchronous olay tabanlı iletişim. Bu, güncellemeleri mikro hizmetler arasında yaymak veya harici uygulamalarla tümleştirmek için bir olay veri mesuliaracılığıyla gerçekleşir. Etkinlik veri neşrisi RabbitMQ gibi herhangi bir mesajlaşma aracısı altyapı teknolojisiyle veya Azure Servis Veri, NServiceBus, MassTransit veya Brighter gibi üst düzey (soyutlama düzeyi) servis veri neşrleri kullanılarak uygulanabilir.

Uygulama kapsayıcılar şeklinde mikro hizmetler kümesi olarak dağıtılır. İstemci uygulamaları, API Ağ Geçitleri tarafından yayınlanan genel URL'ler aracılığıyla kapsayıcı olarak çalışan bu mikro hizmetlerle iletişim kurabilir.

### <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri hakimiyeti

Örnek uygulamada, tüm SQL Server veritabanları tek bir kapsayıcı olarak dağıtılsa da, her microservice kendi veritabanına veya veri kaynağına sahip. Bu tasarım kararı yalnızca bir geliştiricinin kodu GitHub'dan alıp klonlamasını ve Visual Studio veya Visual Studio Code'da açmasını kolaylaştırmak için alındı. Veya alternatif olarak, .NET Core CLI ve Docker CLI'yi kullanarak özel Docker görüntülerini derlemeyi ve ardından docker geliştirme ortamında dağıtmayı ve çalıştırmayı kolaylaştırır. Her iki durumda da, veri kaynakları için kapsayıcılar kullanmak, geliştiricilerin harici bir veritabanı veya altyapıya (bulut veya şirket içi) sıkı bağımlılıkları olan başka bir veri kaynağı sağlamak zorunda kalmadan birkaç dakika içinde oluşturmalarına ve dağıtmalarına olanak tanır.

Gerçek bir üretim ortamında, yüksek kullanılabilirlik ve ölçeklenebilirlik için, veritabanları bulutveya şirket içi veritabanı sunucularını temel almalıdır, ancak kapsayıcılarda değil.

Bu nedenle, mikro hizmetler için dağıtım birimleri (ve bu uygulamadaki veritabanları için bile) Docker kapsayıcılarıdır ve başvuru uygulaması mikro hizmetler ilkelerini benimseyen çok kapsayıcılı bir uygulamadır.

### <a name="additional-resources"></a>Ek kaynaklar

- **eShopOnContainers GitHub repo. Başvuru uygulaması için kaynak kodu** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözümün faydaları

Bunun gibi mikrohizmet tabanlı bir çözümün birçok faydası vardır:

**Her microservice nispeten küçük-yönetmek ve geliştirmek kolaydır.** Daha ayrıntılı şekilde belirtmek gerekirse:

- Bir geliştiricinin iyi bir üretkenlikle hızlı bir şekilde anlaması ve başlaması kolaydır.

- Kapsayıcılar hızlı başlar, bu da geliştiricileri daha üretken yapar.

- Visual Studio gibi bir IDE, geliştiricileri üretken hale getirerek daha küçük projeleri hızlı bir şekilde yükleyebilir.

- Her microservice, mikro hizmetlerin yeni sürümlerini sık sık dağıtmak daha kolay olduğundan çeviklik sağlayan diğer mikro hizmetlerden bağımsız olarak tasarlanabilir, geliştirilebilir ve dağıtılabilir.

**Uygulamanın tek tek alanlarını ölçeklendirmek mümkündür.** Örneğin, katalog hizmetinin veya sepet hizmetinin ölçeklenmesi gerekebilir, ancak sipariş işlemi gerekmeyebilir. Bir mikrohizmet altyapısı, ölçekleme yaparken kullanılan kaynaklar açısından yekpare bir mimarinin olabileceğinden çok daha verimli olacaktır.

**Geliştirme çalışmasını birden çok takım arasında bölebilirsiniz.** Her hizmet tek bir geliştirme ekibine ait olabilir. Her takım, hizmetlerini diğer takımlardan bağımsız olarak yönetebilir, geliştirebilir, dağıtabilir ve ölçeklendirebilir.

**Sorunlar daha yalıtılmış.** Bir hizmette bir sorun varsa, yalnızca bu hizmet başlangıçta etkilenir (mikro hizmetler arasında doğrudan bağımlılıklar olan yanlış tasarımın kullanıldığı durumlar hariç) ve diğer hizmetler istekleri işlemeye devam edebilir. Buna karşılık, yekpare dağıtım mimarisindeki arızalı bir bileşen, özellikle bellek sızıntısı gibi kaynaklar içeriyorsa, tüm sistemi çökertebilir. Ayrıca, bir mikro hizmetteki bir sorun çözüldüğünde, uygulamanın geri kalanını etkilemeden etkilenen microservice'i dağıtabilirsiniz.

**En son teknolojileri kullanabilirsiniz.** Hizmetleri bağımsız olarak geliştirmeye başlayıp yan yana çalıştırabileceğinizden (kapsayıcılar ve .NET Core sayesinde), tüm için eski bir yığın veya çerçevede sıkışıp kalmak yerine en son teknolojileri ve çerçeveleri hızlı bir şekilde kullanmaya başlayabilirsiniz Uygulama.

## <a name="downsides-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözümün dezavantajları

Bunun gibi mikrohizmet tabanlı bir çözümün de bazı dezavantajları vardır:

**Dağıtılmış uygulama**. Uygulamanın dağıtılması, hizmetleri tasarlarken ve inşa ederken geliştiriciler için karmaşıklık ekler. Örneğin, geliştiricilerin, test ve özel durum işleme için karmaşıklık ekleyen HTTP veya AMPQ gibi protokolleri kullanarak servisler arası iletişim ilerler. Ayrıca sisteme gecikme ekleniyor.

**Dağıtım karmaşıklığı.** Düzinelerce mikro hizmet türüne sahip olan ve yüksek ölçeklenebilirlik gerektiren bir uygulama (hizmet başına birçok örnek oluşturabilmesi ve bu hizmetleri birçok ana bilgisayar da dengelemesi gerekir) BT işlemleri ve yönetimi için yüksek derecede dağıtım karmaşıklığı anlamına gelir. Mikrohizmet odaklı bir altyapı (bir orkestratör ve zamanlayıcı gibi) kullanmıyorsanız, bu ek karmaşıklık iş uygulamasının kendisinden çok daha fazla geliştirme çabası gerektirebilir.

**Atomik işlemler**. Birden çok mikro hizmet arasındaki atomik işlemler genellikle mümkün değildir. İş gereksinimleri birden fazla mikro hizmetler arasında nihai tutarlılık kucaklamak zorunda.

**Artırılmış genel kaynak gereksinimleri** (tüm sunucular veya ana bilgisayarlar için toplam bellek, sürücüler ve ağ kaynakları). Çoğu durumda, yekpare bir uygulamayı mikro hizmet yaklaşımıyla değiştirdiğinizde, yeni mikrohizmet tabanlı uygulamanın ihtiyaç duyduğu ilk küresel kaynak miktarı orijinal monolitik uygulamanın altyapı gereksinimlerinden daha büyük olacaktır. Bunun nedeni, daha yüksek parçalı lık ve dağıtılmış hizmetlerin daha fazla küresel kaynak gerektirmesidir. Ancak, genel olarak kaynakların düşük maliyeti ve monolitik uygulamalar gelişirken uzun vadeli maliyetler ile karşılaştırıldığında uygulamanın sadece belirli alanları ölçeklendirmek mümkün olmanın yararı göz önüne alındığında, kaynakların artan kullanımı genellikle büyük için iyi bir tradeoff olduğunu, uzun vadeli uygulamalar.

**Doğrudan istemciden mikrohizmete iletişim ile ilgili sorunlar.** Uygulama, düzinelerce mikro hizmetle büyük olduğunda, uygulama doğrudan istemciden mikrohizmete iletişim gerektiriyorsa zorluklar ve sınırlamalar vardır. Bir sorun istemcinin ihtiyaçları ve API'ler her mikro hizmetlerin maruz arasındaki potansiyel bir uyumsuzluk olduğunu. Bazı durumlarda, istemci uygulamasının Internet üzerinden verimsiz olabilecek ve mobil ağ üzerinden kullanışsız olabilecek Kullanıcı Aracı'nı oluşturmak için birçok ayrı istekte bulunması gerekebilir. Bu nedenle, istemci uygulamasından arka uç sistemine gelen istekler en aza indirilmelidir.

Doğrudan istemciden mikrohizmete iletişimle ilgili bir diğer sorun da, bazı mikro hizmetlerin Web dostu olmayan protokolleri kullanıyor olmasıdır. Bir hizmet ikili iletişim kuralı kullanabilirken, başka bir hizmet AMQP iletisi kullanabilir. Bu protokoller güvenlik duvarı dostu değildir ve en iyi dahili olarak kullanılır. Genellikle, bir uygulama güvenlik duvarı dışında iletişim için HTTP ve WebSockets gibi protokolleri kullanmalıdır.

Bu doğrudan istemciden hizmete yaklaşımın bir diğer dezavantajı da, bu mikro hizmetlerin sözleşmelerini yeniden düzenlemeyi zorlaştırır. Zamanla geliştiriciler sistemin hizmetlere nasıl bölümleneceğini değiştirmek isteyebilir. Örneğin, iki hizmeti birbirleştirmeye veya bir hizmeti iki veya daha fazla hizmete bölebilirler. Ancak, istemciler hizmetlerle doğrudan iletişim kuruyorsa, bu tür yeniden düzenleme yapmak istemci uygulamalarıyla uyumluluğu bozabilir.

Mimari bölümünde belirtildiği gibi, mikro hizmetlere dayalı karmaşık bir uygulama tasarlarken ve inşa ederken, daha basit doğrudan istemciden mikrohizmete iletişim yaklaşımı yerine birden çok ince taneli API Ağ Geçidi kullanımını düşünebilirsiniz.

**Mikro hizmetlerin bölümlemi.** Son olarak, mikrohizmet mimariniz için hangi yaklaşımı kullanırsanız ele alırsanız alın, başka bir zorluk da uçdan uca bir uygulamayı birden çok mikro hizmete nasıl bölümlere ayırabileceğinize karar vermektir. Kılavuzun mimari bölümünde belirtildiği gibi, alabileceğiniz çeşitli teknikler ve yaklaşımlar vardır. Temel olarak, uygulamanın diğer alanlardan ayrılan ve sabit bağımlılıksayısı düşük olan alanları belirlemeniz gerekir. Çoğu durumda, bu kullanım örneği tarafından bölümleme hizmetleri hizalanır. Örneğin, e-mağaza uygulamamızda, sipariş süreciyle ilgili tüm iş mantığından sorumlu bir sipariş hizmetimiz bulunmaktadır. Ayrıca katalog hizmeti ve diğer yetenekleri uygulayan sepet hizmeti var. İdeal olarak, her hizmetin yalnızca küçük bir sorumluluk kümesi olmalıdır. Bu, sınıflara uygulanan ve bir sınıfın yalnızca bir değiştirmesi için tek bir nedeni olması gerektiğini belirten tek sorumluluk ilkesine (SRP) benzer. Ama bu durumda, bu mikro hizmetler hakkında, bu nedenle kapsamı tek bir sınıf daha büyük olacaktır. Hepsinden önemlisi, bir microservice tamamen özerk olmalı, sonuna kadar, kendi veri kaynakları için sorumluluk da dahil olmak üzere.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Dış ve iç mimari ve tasarım desenleri

Dış mimari, bu kılavuzun mimari bölümünde açıklanan ilkeleri izleyerek birden fazla hizmet tarafından oluşturulan mikrohizmet mimarisidir. Ancak, her microservice doğasına bağlı olarak ve seçtiğiniz üst düzey microservice mimarisi bağımsız olarak, yaygın ve bazen farklı desenleri dayalı farklı iç mimarileri olması tavsiye edilir, farklı için mikro hizmetler. Mikro hizmetler farklı teknolojileri ve programlama dillerini bile kullanabilir. Şekil 6-2 bu çeşitliliği göstermektedir.

![Dış ve iç mimari desenleri karşılaştıran diyagram.](./media/microservice-application-design/external-versus-internal-architecture.png)

**Şekil 6-2**. Dış ve iç mimari ve tasarım

Örneğin, bizim *eShopOnContainers* örnek, katalog, sepet ve kullanıcı profili microservices basit (temelde, CRUD alt sistemleri). Bu nedenle, iç mimarisi ve tasarımı basittir. Ancak, daha karmaşık olan ve yüksek etki alanı karmaşıklığıyla sürekli değişen iş kurallarını temsil eden sipariş mikrohizmeti gibi başka mikro hizmetleriniz de olabilir. Bu gibi durumlarda, biz microservice sipariş *eShopOnContainers* yapıyoruz gibi, etki alanı odaklı tasarım (DDD) yaklaşımları ile tanımlanan olanlar gibi, belirli bir microservice içinde daha gelişmiş desenler uygulamak isteyebilirsiniz. (Biz mikrohizmet sipariş *eShopOnContainers* uygulanması açıklar bölümünde daha sonra bu DDD desenleri gözden geçirecektir.)

Mikrohizmet başına farklı bir teknoloji nin bir diğer nedeni de her microservice doğası olabilir. Örneğin, C\#gibi daha nesne yönelimli bir\#programlama dili yerine, AI ve makine öğrenimi etki alanlarını hedefliyorsanız, F gibi işlevsel bir programlama dili, hatta R gibi bir dil kullanmak daha iyi olabilir.

Alt satırda her microservice farklı tasarım desenleri dayalı farklı bir iç mimari olabilir. Tüm mikro hizmetler gelişmiş DDD desenleri kullanılarak uygulanmamalıdır, çünkü bu onları aşırı mühendislik olacaktır. Benzer şekilde, sürekli değişen iş mantığına sahip karmaşık mikro hizmetler CRUD bileşenleri olarak uygulanmamalıdır veya düşük kaliteli kodla başa çıkabilirsiniz.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Yeni dünya: birden fazla mimari desen ve polyglot microservices

Yazılım mimarları ve geliştiricileri tarafından kullanılan birçok mimari desenler vardır. Aşağıdaki (mimari stilleri ve mimari desenleri karıştırma):

- Basit CRUD, tek katmanlı, tek katmanlı.

- [Geleneksel N Katmanlı](https://docs.microsoft.com/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Etki Alanı Odaklı Tasarım N katmanlı.](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/)

- [Temiz Mimari](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) [(eShopOnWeb](https://aka.ms/WebAppArchitecture)ile birlikte kullanılır)

- [Komut ve Sorgu Sorumluluk Ayrımı](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Olay Odaklı Mimari](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Ayrıca, ASP.NET Core Web API'leri, NancyFx, ASP.NET Core SignalR (.NET Core 2), F,\#Node.js, Python, Java, C++, GoLang ve daha fazlası gibi birçok teknoloji ve dilde mikro hizmetler oluşturabilirsiniz.

Önemli nokta, hiçbir mimari desen veya stil, ne de belirli bir teknoloji, tüm durumlar için doğru olmasıdır. Şekil 6-3, farklı mikro hizmetlerde kullanılabilecek bazı yaklaşımları ve teknolojileri (belirli bir sırada olmasa da) göstermektedir.

![Polyglot dünya mimarisinde 12 karmaşık mikro hizmeti gösteren diyagram.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Şekil 6-3**. Çok mimari desenler ve polyglot microservices dünya

Çok mimari desen ve çok dilli mikrohizmetler, dilleri ve teknolojileri her mikro hizmetin gereksinimleriyle karıştırıp eşleştirebileceğiniz ve hala birbirleriyle konuşmalarını sağlayabilirsiniz. Şekil 6-3'te gösterildiği gibi, birçok mikrohizmet (etki alanı odaklı tasarım terminolojisinde Sınırlı Bağlamlar veya sadece "alt sistemler" özerk mikrohizmetler olarak oluşturulan uygulamalarda), her mikro hizmeti farklı bir şekilde uygulayabilirsiniz. Her biri farklı bir mimari deseni olabilir ve uygulamanın yapısına, iş gereksinimlerine ve önceliklerine bağlı olarak farklı diller ivedilik ve veritabanları kullanabilir. Bazı durumlarda, mikro hizmetler benzer olabilir. Ancak her alt sistemin bağlam sınırı ve gereksinimleri genellikle farklı olduğundan, genellikle durum böyle değildir.

Örneğin, basit bir CRUD bakım uygulaması için DDD desenleri tasarlamak ve uygulamak mantıklı olmayabilir. Ancak, temel etki alanınız veya temel işletmeniz için, sürekli değişen iş kurallarıyla iş karmaşıklığını gidermek için daha gelişmiş kalıplar uygulamanız gerekebilir.

Özellikle birden çok alt sistem tarafından oluşturulan büyük uygulamalarla uğraşırken, tek bir mimari deseni temel alan tek bir üst düzey mimari uygulamamalısınız. Örneğin, CQRS tüm uygulama için üst düzey bir mimari olarak uygulanmamalıdır, ancak belirli bir hizmet kümesi için yararlı olabilir.

Her durumda gümüş mermi veya doğru mimari desen yoktur. "Hepsini yönetmek için tek bir mimari desen" olamaz. Her microservice önceliklerine bağlı olarak, aşağıdaki bölümlerde açıklandığı gibi, her biri için farklı bir yaklaşım seçmeniz gerekir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](data-driven-crud-microservice.md)
