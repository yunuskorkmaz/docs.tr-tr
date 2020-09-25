---
title: Mikro hizmet odaklı bir uygulama tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmet odaklı bir uygulamanın avantajlarını ve altlarını anlayın ve bu sayede bilinçli bir karar alabilirsiniz.
ms.date: 10/02/2018
ms.openlocfilehash: 11aa6327a8d870a1ff6356b88695b693c27f99a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172345"
---
# <a name="design-a-microservice-oriented-application"></a>Mikro hizmet odaklı bir uygulama tasarlama

Bu bölüm, kuramsal bir sunucu tarafı kurumsal uygulama geliştirmeye odaklanmaktadır.

## <a name="application-specifications"></a>Uygulama belirtimleri

Kuramsal uygulama, iş mantığını yürüterek, veritabanlarına erişerek ve sonra HTML, JSON veya XML yanıtlarını döndürerek istekleri işler. Uygulamanın tek sayfalı uygulamalar (maça 'Lar), geleneksel web uygulamaları, mobil web uygulamaları ve yerel mobil uygulamalar çalıştıran masaüstü tarayıcıları gibi çeşitli istemcileri desteklemesi gerektiğini söyliyoruz. Uygulama, üçüncü tarafların kullanması için bir API de sunabilir. Ayrıca, mikro hizmetlerini veya dış uygulamaları zaman uyumsuz olarak tümleştirmede, bu yaklaşım kısmi hatalarda mikro hizmetlerin dayanıklılığını sağlamaya yardımcı olur.

Uygulama, bu tür bileşenlerden oluşur:

- Sunu bileşenleri. Bunlar, Kullanıcı arabirimini işlemekten ve uzak Hizmetleri tüketen sorumludur.

- Etki alanı veya iş mantığı. Bu, uygulamanın etki alanı mantığdır.

- Veritabanı erişim mantığı. Bu, veritabanlarına erişmekten sorumlu veri erişim bileşenlerinden oluşur (SQL veya NoSQL).

- Uygulama tümleştirme mantığı. Bu, temel olarak ileti aracılarına dayalı bir mesajlaşma kanalı içerir.

Bazı alt sistemler diğerlerinden daha fazla ölçeklenebilirlik gerektirdiğinden, uygulama yüksek ölçeklenebilirlik gerektirir.

Uygulamanın birden çok altyapı ortamında (birden çok genel bulut ve şirket içi) dağıtılması ve ideal olması, Linux 'tan Windows 'a (veya tam tersi) kolayca geçiş yapabilmesi için platformlar arası olmalıdır.

## <a name="development-team-context"></a>Geliştirme ekibi bağlamı

Ayrıca, uygulamanın geliştirme süreci hakkında aşağıdakileri de varsaydık:

- Uygulamanın farklı iş alanlarında odaklanan birden çok geliştirme takımı var.

- Yeni takım üyeleri hızla üretken hale gelmelidir ve uygulamanın anlaşılması ve değiştirilmesi kolay olmalıdır.

- Uygulamanın uzun süreli bir evrimi ve sürekli değişen iş kuralları olacaktır.

- Daha sonra, diğer alt sistemlerde en düşük etkiyle birden çok alt sistemi güncelleştirebilirken, gelecekte yeni değişiklikler uygularken çeviklik sağlamak için iyi bir uzun süreli bakım yapmanız gerekir.

- Sürekli tümleştirme ve uygulamanın sürekli dağıtımı için alıştırma yapmak istiyorsunuz.

- Uygulamayı gelişirken, gelişen teknolojiden (çerçeveler, programlama dilleri vb.) yararlanmak istiyorsunuz. Yeni teknolojilere geçiş yaparken uygulamanın tam geçişini yapmak istemezsiniz çünkü bu, yüksek maliyetlere neden olur ve uygulamanın tahmin edilebilir ve kararlılığı etkiler.

## <a name="choosing-an-architecture"></a>Mimari seçme

Uygulama dağıtım mimarisi ne olmalıdır? Geliştirme bağlamıyla birlikte uygulamanın belirtimleri, bir mikro hizmetin bir kapsayıcı olduğu, mikro hizmetler ve kapsayıcılar için ortak çalışan mikro hizmet ve kapsayıcı biçiminde parçalanarak uygulamayı mimaride oluşturmayı kesinlikle öneririz.

Bu yaklaşımda, her hizmet (kapsayıcı) bir dizi ortak ve dar ilgili işlev uygular. Örneğin, bir uygulama katalog hizmeti, sipariş hizmeti, sepet hizmeti, Kullanıcı profili hizmeti vb. gibi hizmetlerden oluşabilir.

Mikro hizmetler HTTP (REST) gibi protokolleri kullanarak iletişim kurar, ancak özellikle de güncelleştirmeler tümleştirme olaylarıyla yayılırken zaman uyumsuz olarak (örneğin AMQP kullanma).

Mikro hizmetler birbiriyle bağımsız kapsayıcı olarak geliştirilir ve dağıtılır. Bu, bir geliştirme ekibinin diğer alt sistemleri etkilemeden belirli bir mikro hizmeti geliştirip dağıtabileceği anlamına gelir.

Her mikro hizmet kendi veritabanına sahiptir ve bunun diğer mikro hizmetlerden tamamen ayırt edilebilir olmasını sağlar. Gerektiğinde, farklı mikro hizmetlerden veritabanları arasındaki tutarlılık, Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) ' de işlendiği gibi uygulama düzeyi tümleştirme olayları (mantıksal bir olay veri yolu aracılığıyla) kullanılarak elde edilir. Bu nedenle, iş kısıtlamaları birden çok mikro hizmet ve ilgili veritabanları arasında son tutarlılığı benimsemelidir.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers: kapsayıcılar kullanılarak dağıtılan .NET Core ve mikro hizmetler için başvuru uygulaması

Bildiğiniz bir kuramsal iş etki alanı hakkında düşünmek yerine mimaride ve teknolojilerine odaklanabilmeniz için, bir ürünün kataloğunu sunan, müşterilerin siparişlerini doğrulayan, stoku doğrulayan ve diğer iş işlevlerini gerçekleştiren, iyi bilinen bir iş etki alanı (örneğin, Basitleştirilmiş bir e-ticaret (e-alışveriş) uygulaması seçtik. Bu kapsayıcı tabanlı uygulama kaynak kodu [Eshoponcontainers](https://aka.ms/MicroservicesArchitecture) GitHub deposunda mevcuttur.

Uygulama, iç mikro hizmetlere birleştirilmiş giriş noktaları olarak birkaç API ağ geçidine sahip tüm gerekli sunucu tarafı işlemleri için arka uç mikro hizmetleri ve kapsayıcıları dahil olmak üzere birden çok alt sistemi (bir Web uygulaması ve yerel bir mobil uygulama) içerir. Şekil 6-1, başvuru uygulamasının mimarisini gösterir.

![Tek bir Docker konağında eShopOnContainers kullanan istemci uygulamalarının diyagramı.](./media/microservice-application-design/eshoponcontainers-reference-application-architecture.png)

**Şekil 6-1**. Geliştirme ortamı için eShopOnContainers başvuru uygulama mimarisi

Yukarıdaki diyagramda, mobil ve SPA istemcilerinin tek API ağ geçidi uç noktalarına iletişim kurduğu ve bu da mikro hizmetlerle iletişim kurduğu gösterilmektedir. Geleneksel Web istemcileri, API ağ geçidi aracılığıyla mikro hizmetlere iletişim kuran MVC mikro hizmeti ile iletişim kurar.

**Barındırma ortamı**. Şekil 6-1 ' de, tek bir Docker ana bilgisayarı içinde dağıtılan birkaç kapsayıcı görürsünüz. Bu durum, Docker-Compose up komutuyla tek bir Docker konağına dağıtım yaparken de olur. Ancak, bir Orchestrator ya da kapsayıcı kümesi kullanıyorsanız, her kapsayıcı farklı bir konakta (node) çalışıyor olabilir ve herhangi bir düğüm, mimari bölümünde daha önce anlatıldığı gibi herhangi bir sayıda kapsayıcı çalıştırıyor olabilir.

**İletişim mimarisi**. EShopOnContainers uygulaması, işlevsel eylemin türüne (sorgular ve işlemler ve sorgular) bağlı olarak iki iletişim türü kullanır:

- API ağ geçitleri aracılığıyla http istemciden mikro hizmet iletişimi. Bu, sorgular için ve istemci uygulamalarından güncelleştirme veya işlem komutları kabul edildiğinde kullanılır. API ağ geçitlerini kullanma yaklaşımı, sonraki bölümlerde ayrıntılı olarak açıklanmıştır.

- Zaman uyumsuz olay tabanlı iletişim. Bu durum, güncelleştirmeleri mikro hizmetlere yaymak veya dış uygulamalarla bütünleştirmek için bir olay veri yolundan oluşur. Olay veri yolu, kbbitmq gibi herhangi bir mesajlaşma Aracısı altyapı teknolojisiyle veya Azure Service Bus, NServiceBus, Masstransıya ya da daha parlak gibi daha yüksek düzey (soyutlama düzeyi) hizmet veri yolları kullanarak uygulanabilir.

Uygulama, kapsayıcılar biçiminde bir mikro hizmet kümesi olarak dağıtılır. İstemci uygulamaları, API ağ geçitleri tarafından Yayınlanan Genel URL 'Ler aracılığıyla kapsayıcı olarak çalışan mikro hizmetlerle iletişim kurabilir.

### <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri hakimiyeti

Örnek uygulamada, her mikro hizmet kendi veritabanı veya veri kaynağına sahiptir, ancak tüm SQL Server veritabanları tek bir kapsayıcı olarak dağıtılır. Bu tasarım kararı, bir geliştiricinin kodu GitHub 'dan almasını, klonlamasını ve Visual Studio 'da veya Visual Studio Code açmasını kolaylaştırmak için yapılmıştır. Alternatif olarak, .NET Core CLI ve Docker CLı kullanarak özel Docker görüntülerini derlemeyi kolaylaştırır ve sonra bunları bir Docker geliştirme ortamında dağıtıp çalıştırın. Her iki durumda da veri kaynakları için kapsayıcıları kullanmak, geliştiricilerin bir dış veritabanı veya altyapıda (bulut ya da şirket içi) sabit bağımlılıklara sahip başka bir veri kaynağı sağlamaya gerek kalmadan dakikalar içinde derleme ve dağıtım yapmasına olanak sağlar.

Gerçek bir üretim ortamında, yüksek kullanılabilirlik ve ölçeklenebilirlik için veritabanları bulutta veya şirket içinde veritabanı sunucularını temel almalıdır, ancak kapsayıcılarda değil.

Bu nedenle, mikro hizmetler (ve bu uygulamadaki veritabanları için de) dağıtım birimleri Docker kapsayıcılarıdır ve başvuru uygulaması, mikro hizmet ilkelerini kullanan çok kapsayıcılı bir uygulamadır.

### <a name="additional-resources"></a>Ek kaynaklar

- **eShopOnContainers GitHub deposu. Başvuru uygulaması için kaynak kodu** \
  <https://aka.ms/eShopOnContainers/>

## <a name="benefits-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözümün avantajları

Bunun gibi mikro hizmet tabanlı bir çözümün birçok avantajı vardır:

**Her mikro hizmet görece küçük, kolayca yönetiyoruz ve gelişme**. Özellikle:

- Geliştiricilerin iyi bir üretkenlik ile hızla anlaması ve kullanmaya başlamak kolaydır.

- Kapsayıcılar hızlı başlar ve geliştiricilerin daha üretken olmasını sağlar.

- Visual Studio gibi bir IDE, daha küçük projeler yükleyebilir ve geliştiricilerin üretken olmasını sağlayabilir.

- Her mikro hizmet, diğer mikro hizmetlerden bağımsız olarak tasarlanabilir, geliştirilebilir ve dağıtılabilir ve bu da mikro hizmetlerin yeni sürümlerini sıklıkla dağıtmak daha kolay olduğundan çeviklik sağlar.

**Uygulamanın bireysel alanlarının ölçeğini genişletmek mümkündür**. Örneğin, katalog hizmeti veya sepet hizmeti, sıralama işlemini değil, genişleme için de genişletilebilir. Bir mikro hizmet altyapısı, tek parçalı bir mimarinin ölçeklendirilmesi sırasında kullanılan kaynaklarla ilgili olarak çok daha etkili olacaktır.

**Geliştirme işini birden çok takım arasında bölebilirsiniz**. Her hizmet tek bir geliştirme ekibine ait olabilir. Her bir ekip, takımlarının geri kalanından bağımsız olarak kendi hizmetini yönetebilir, geliştirebilir, dağıtabilir ve ölçeklendirebilirler.

**Sorunlar daha yalıtılmıştır**. Bir hizmette sorun varsa, yalnızca bu hizmet başlangıçta etkilendi (yanlış tasarımın kullanıldığı, mikro hizmetler arasındaki doğrudan bağımlılıklarla birlikte) ve diğer hizmetler istekleri işlemeye devam edebilir. Buna karşılık, tek parçalı bir dağıtım mimarisinde hatalı çalışan bir bileşen, özellikle de bellek sızıntısı gibi kaynaklar içeriyorsa sistemin tamamını getirebilir. Ayrıca, mikro hizmette bir sorun çözüldüğünde, uygulamanın geri kalanını etkilemeden yalnızca etkilenen mikro Hizmeti dağıtabilirsiniz.

**En son teknolojileri kullanabilirsiniz**. Hizmetleri bağımsız olarak geliştirmeye başlayabilmeniz ve yan yana (kapsayıcılar ve .NET Core sayesinde) çalıştırabilmeniz için, tüm uygulama için daha eski bir yığında veya çerçevede takılmak yerine en son teknolojileri ve çerçeveleri kullanmaya başlayabilirsiniz.

## <a name="downsides-of-a-microservice-based-solution"></a>Mikro hizmet tabanlı bir çözümün aşağı yönleri

Bunun gibi mikro hizmet tabanlı bir çözüm de bazı dezavantajları vardır:

**Dağıtılmış uygulama**. Uygulamayı dağıtmak, Hizmetleri tasarlarken ve oluştururken geliştiriciler için karmaşıklık ekler. Örneğin, geliştiriciler, test ve özel durum işleme için karmaşıklık ekleyen HTTP veya AMPQ gibi protokolleri kullanarak hizmet dışı iletişim uygulamalıdır. Ayrıca sisteme gecikme süresi ekler.

**Dağıtım karmaşıklığı**. Onlarca mikro hizmet türüne sahip ve yüksek ölçeklenebilirlik gerektiren bir uygulama (hizmet başına çok sayıda örnek oluşturamayacak ve bu hizmetlerin birçok konakta dengelenmesi gerekir), BT işlemleri ve yönetimi için yüksek düzeyde dağıtım karmaşıklığı anlamına gelir. Mikro hizmet odaklı bir altyapı (Orchestrator ve Scheduler gibi) kullanmıyorsanız, bu ek karmaşıklık iş uygulamasının kendisinden daha fazla geliştirme çabasına gerek duyar.

**Atomik işlemler**. Birden çok mikro hizmet arasındaki Atomik işlemler genellikle mümkün değildir. İş gereksinimlerinin birden fazla mikro hizmet arasında nihai tutarlılığı benimseme gereksinimi vardır.

**Artırılan küresel kaynak ihtiyaçları** (tüm sunucular veya konaklar için toplam bellek, sürücü ve ağ kaynağı). Birçok durumda, tek parçalı bir uygulamayı mikro hizmetler yaklaşımıyla değiştirdiğinizde, yeni mikro hizmet tabanlı uygulama için gereken ilk genel kaynak miktarı, orijinal monoparçalı uygulamanın altyapı ihtiyaçlarına daha büyük olacaktır. Bunun nedeni, daha yüksek düzeyde ayrıntı düzeyi ve dağıtılmış hizmetlerin daha fazla genel kaynak gerektirmesidir. Ancak, genel olarak kaynakların düşük maliyetli olması ve tek parçalı uygulamalar gelişmede uzun süreli maliyetlere kıyasla uygulamanın yalnızca belirli bir alanını ölçeklendirebilmenin avantajına göre, kaynakların daha fazla kullanımı genellikle büyük ve uzun süreli uygulamalar için iyi bir zorunluluğunu getirir.

**Doğrudan istemciden mikro hizmet Iletişimi sorunları**. Uygulama büyükse, onlarca mikro hizmetle, uygulamanın doğrudan istemciden mikro hizmet iletişimleri gerektirip gerektirmediğini sorun ve sınırlamalar vardır. Bir sorun, istemci ihtiyaçları ve mikro hizmetlerin her biri tarafından kullanıma sunulan API 'Ler arasında olası bir uyumsuzluktan biridir. Belirli durumlarda, istemci uygulamasının Kullanıcı arabirimini oluşturmak için çok sayıda ayrı istek yapması gerekebilir ve bu, Internet üzerinden verimsiz olabilir ve bir mobil ağ üzerinde pratik olabilir. Bu nedenle, istemci uygulamasından arka uç sistemine yapılan isteklerin küçültülmüş olması gerekir.

Doğrudan istemciden mikro hizmet iletişimleriyle ilgili başka bir sorun, bazı mikro hizmetlerin Web 'e yönelik olmayan protokolleri kullanıyor olması olabilir. Bir hizmet ikili protokol kullanabilir, ancak başka bir hizmet AMQP mesajlaşma kullanabilir. Bu protokoller güvenlik duvarı dostu değildir ve en iyi şekilde dahili olarak kullanılır. Genellikle, bir uygulamanın güvenlik duvarının dışında iletişim için HTTP ve WebSockets gibi protokolleri kullanması gerekir.

Bu doğrudan istemci-hizmet yaklaşımının başka bir sakıncası, bu mikro hizmetlere ait sözleşmelerin yeniden düzenlenmesi zor hale gelir. Zaman içinde geliştiricilerin, sistemin hizmetlere nasıl bölümlendiği hakkında değiştirmek isteyebilir. Örneğin, iki hizmeti birleştirebilir veya bir hizmeti iki veya daha fazla hizmete bölebilir. Ancak, istemciler hizmetlerle doğrudan iletişim kurduklarında, bu tür bir yeniden düzenleme gerçekleştirildiğinde istemci uygulamalarıyla uyumluluk kesilebilir.

Mimari bölümünde belirtildiği gibi, mikro hizmetlere dayalı karmaşık bir uygulama tasarlarken ve oluştururken, daha basit doğrudan istemciden mikro hizmet iletişim yaklaşımı yerine birden çok hassas API ağ geçidinin kullanımını göz önünde bulundurmayabilirsiniz.

**Mikro hizmetler bölümleniyor**. Son olarak, mikro hizmet mimariniz için hangi yaklaşımdan bağımsız olarak başka bir zorluk, uçtan uca bir uygulamanın birden fazla mikro hizmete nasıl bölümleyeceğinize karar vermektir. Kılavuzun mimari bölümünde belirtildiği gibi, gerçekleştirebileceğiniz birkaç teknik ve yaklaşım vardır. Temel olarak, uygulamanın diğer alanlardan ayrılmış ve az sayıda sabit bağımlılığı olan olan bölgelerini belirlemeniz gerekir. Çoğu durumda bu, Hizmetleri kullanım örneğine göre bölümlendirme ile hizalanır. Örneğin, e-ticaret uygulamamızda, sipariş işlemiyle ilgili tüm iş mantığından sorumlu bir sıralama hizmeti sunuyoruz. Ayrıca, diğer özellikleri uygulayan katalog hizmeti ve sepet hizmeti de vardır. İdeal olarak, her hizmetin yalnızca küçük bir sorumluluk kümesi olmalıdır. Bu, sınıflara uygulanan tek sorumluluk ilkesine (SRP) benzer, bu da bir sınıfın yalnızca bir nedeni olması gerektiğini belirtir. Ancak bu, mikro hizmetler ile ilgilidir, bu nedenle kapsam tek bir sınıftan daha büyük olur. Çoğu bir mikro hizmet, kendi veri kaynakları için sorumluluk dahil olmak üzere tamamen otonom ve uçtan uca olmalıdır.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Dış ve dahili mimari ve tasarım desenleri

Dış mimari, bu kılavuzun mimari bölümünde açıklanan ilkeleri izleyerek birden çok hizmet tarafından oluşturulan Mikro hizmet mimarisidir. Ancak, her bir mikro hizmetin yapısına ve seçtiğiniz yüksek düzeyli mikro hizmet mimarisinden bağımsız olarak, her biri farklı bir mikro hizmet için farklı desenleri temel alan farklı iç mimarilerin olması önerilir. Mikro hizmetler, farklı teknolojiler ve programlama dillerini de kullanabilir. Şekil 6-2 bu çeşitliliğe sahiptir.

![Dış ve iç mimari desenlerini karşılaştıran diyagram.](./media/microservice-application-design/external-versus-internal-architecture.png)

**Şekil 6-2**. Harici ve dahili mimari ve tasarım

Örneğin, *Eshoponcontainers* örneğimizde Katalog, sepet ve Kullanıcı profili mikro hizmetleri basittir (temelde, CRUD alt sistemleri). Bu nedenle, iç mimarisi ve tasarımı basittir. Ancak, sıralama mikro hizmeti gibi daha karmaşık olan ve çok sayıda etki alanı karmaşıklığıyla sürekli değişen iş kurallarını temsil eden diğer mikro hizmetlerinize sahip olabilirsiniz. Bunlar gibi durumlarda, *Eshoponcontainers* sıralama mikro hizmetinde yaptığımız gibi, belirli bir mikro hizmet için etki alanı odaklı TASARıM (DDD) yaklaşımlarıyla tanımlananlara benzer şekilde daha gelişmiş desenler uygulamak isteyebilirsiniz. (Bu DDD desenlerinin ilerleyen bölümlerinde, *Eshoponcontainers* sıralama mikro hizmeti 'nin uygulanmasını anlatan daha sonra gözden geçiğiz.)

Mikro hizmet başına farklı bir teknolojinin başka bir nedeni de her mikro hizmetin doğası olabilir. Örneğin, F gibi işlevsel bir programlama dilinin kullanılması daha iyi olabilir, C gibi \# daha fazla nesne odaklı programlama dili yerıne AI ve makine öğrenimi etki alanlarını hedefliyorsanız R gibi bir dil de kullanabilirsiniz \# .

En alttaki satır, her mikro hizmetin farklı tasarım düzenlerine göre farklı bir iç mimariye sahip olmasını sağlayabilir. Tüm mikro hizmetler, gelişmiş DDD desenleri kullanılarak uygulanmamalıdır çünkü bu, bunlar üzerinde aşırı mühendislik uygulanırlar. Benzer şekilde, sürekli değişen iş mantığı olan karmaşık mikro hizmetler, CRUD bileşenleri olarak uygulanmamalıdır ya da düşük kaliteli kodla bitemez.

## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Yeni Dünya: birden çok mimari deseni ve çok yönlü mikro hizmeti

Yazılım mimarları ve geliştiriciler tarafından kullanılan birçok mimari deseni vardır. Aşağıda birkaç (karıştırma mimarisi stilleri ve mimari desenleri) verilmiştir:

- Basit CRUD, tek katmanlı, tek katmanlı.

- [Geleneksel N katmanlı](/previous-versions/msp-n-p/ee658109(v=pandp.10)).

- [Etki alanı odaklı tasarım N katmanlı](https://devblogs.microsoft.com/cesardelatorre/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

- [Temizleme mimarisi](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) ( [Eshoponweb](https://aka.ms/WebAppArchitecture)ile kullanıldığı gibi)

- [Komut ve sorgu sorumluluklarının ayrılığı](https://martinfowler.com/bliki/CQRS.html) (CQRS).

- [Olay odaklı mimari](https://en.wikipedia.org/wiki/Event-driven_architecture) (Eda).

Ayrıca, ASP.NET Core Web API 'Leri, NancyFx, ASP.NET Core SignalR (.NET Core 2 ile kullanılabilir), F \# , Node.js, Python, Java, C++, GoLang gibi birçok teknoloji ve dilde mikro hizmetler de oluşturabilirsiniz.

Önemli nokta, belirli bir mimari deseninin veya stilin olmaması ya da herhangi bir teknolojinin tüm durumlar için doğru olması. Şekil 6-3, farklı mikro hizmetlerde kullanılabilecek bazı yaklaşımları ve teknolojileri (belirli bir sırada olmasa da) gösterir.

![Çok yönlü dünyadaki bir mimaride 12 karmaşık mikro hizmeti gösteren diyagram.](./media/microservice-application-design/multi-architectural-patterns-polyglot-microservices.png)

**Şekil 6-3**. Multi-mimari desenleri ve çok yönlü mikro hizmetleri dünyası

Multi-mimari model ve çok yönlü mikro hizmetleri, dilleri ve teknolojileri her bir mikro hizmetin ihtiyaçlarına göre karıştırabilmeniz ve eşleştirebilir ve yine de birbirleriyle iletişim kuran anlamına gelir. Şekil 6-3 ' de gösterildiği gibi, birçok mikro hizmetten oluşan uygulamalarda (etki alanı odaklı tasarım terminolojisinde sınırlı bağlamlarda veya otonom mikro hizmetler olarak yalnızca "alt sistemler"), her mikro hizmeti farklı bir şekilde uygulayabilirsiniz. Her birinin farklı bir mimari deseninin olması ve uygulamanın doğası, iş gereksinimleri ve önceliklerine bağlı olarak farklı diller ve veritabanları kullanması olabilir. Bazı durumlarda, mikro hizmetler benzer olabilir. Ancak genellikle bu durum değildir çünkü her alt sistemin bağlam sınırı ve gereksinimleri genellikle farklıdır.

Örneğin, basit bir CRUD bakım uygulaması için DDD desenleri tasarlamak ve uygulamak mantıklı olmayabilir. Ancak, çekirdek etki alanınız veya temel işletmeniz için, sürekli değişen iş kurallarıyla iş karmaşıklığını ortadan açmaya yönelik daha gelişmiş desenler uygulamanız gerekebilir.

Özellikle birden çok alt sistemi tarafından oluşturulan büyük uygulamalarla uğraşdığınızda, tek bir mimari deseninin temelinde tek bir üst düzey mimari uygulamamalısınız. Örneğin, CQRS, tüm uygulama için en üst düzey mimari olarak uygulanmamalıdır, ancak belirli bir hizmet kümesi için yararlı olabilir.

Her belirli durum için gümüş bir madde işareti veya sağ mimari model yoktur. "Tümünü kural için bir mimari deseninin" olması gerekmez. Her mikro hizmetin önceliklerine bağlı olarak, aşağıdaki bölümlerde açıklandığı gibi her biri için farklı bir yaklaşım seçmeniz gerekir.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](data-driven-crud-microservice.md)
