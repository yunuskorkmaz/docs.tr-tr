---
title: DDD odaklı bir mikro hizmet tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD odaklı sipariş mikrohizmetinin ve uygulama katmanlarının tasarımını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: c5ac55978ca979a3ae055d9b0cd2d3c6b3187b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401699"
---
# <a name="design-a-ddd-oriented-microservice"></a>DDD odaklı bir microservice tasarla

Etki alanına dayalı tasarım (DDD), kullanım durumlarınıza ilişkin olarak işletmenin gerçekliğine dayalı modellemeyi savunur. Yapı uygulamaları bağlamında, DDD etki alanı olarak sorunlar hakkında konuşuyor. Bağımsız sorunlu alanları Sınırlı Bağlamlar olarak tanımlar (her Sınırlı Bağlam bir mikro hizmetle ilişkilidir) ve bu sorunlar hakkında konuşmak için ortak bir dili vurgular. Ayrıca, iç uygulamayı desteklemek için zengin modellere [(anemik etki alanı modeli](https://martinfowler.com/bliki/AnemicDomainModel.html)olmayan), nesneleri değerlendiren ve toplu kök (veya kök varlık) kurallarına sahip etki alanı varlıkları gibi birçok teknik kavram ve desen önerir. Bu bölümde, bu iç desenlerin tasarımı ve uygulanması tanıtıştır.

Bazen bu DDD teknik kurallar ve desenler DDD yaklaşımları uygulamak için dik bir öğrenme eğrisi var engeller olarak algılanmaktadır. Ama önemli kısmı desenler kendilerini değil, iş sorunları hizalanmış böylece kodu organize ve aynı iş terimleri (her yerde dil) kullanarak. Buna ek olarak, DDD yaklaşımları yalnızca önemli iş kurallarıile karmaşık mikro hizmetler uyguluyorsanız uygulanmalıdır. CRUD hizmeti gibi daha basit sorumluluklar, daha basit yaklaşımlarla yönetilebilir.

Bir mikro hizmet tasarlarken ve tanımlarken sınırların çizilmesi gereken temel görevdir. DDD desenleri etki alanında karmaşıklığı anlamanıza yardımcı olur. Her Bağlı Bağlam için etki alanı modeli için, etki alanınızı modelleyen varlıkları, değer nesnelerini ve toplamlarını tanımlar ve tanımlarsınız. Bağlamınızı tanımlayan bir sınır içinde bulunan bir etki alanı modeli oluşturur ve ayrıntısına kadar zorlarsınız. Ve bu çok bir mikrohizmet şeklinde açıktır. Bazı durumlarda bir BC veya iş mikro hizmetleri çeşitli fiziksel hizmetlerden oluşabilse de, bu sınırlar içindeki bileşenler sizin mikro hizmetleriniz olarak sona erer. DDD sınırları hakkında ve bu yüzden mikro hizmetler vardır.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Mikrohizmet bağlamı sınırlarını nispeten küçük tutun

Bağlı Bağlamlar arasında sınırların nereye yerleştirilen belirlenmesi, rakip iki hedefi dengeler. İlk olarak, ana sürücü olmasa da, başlangıçta mümkün olan en küçük mikro hizmetleri oluşturmak istiyorsunuz; uyum alabilen şeylerin etrafında bir sınır oluşturmalısınız. İkinci olarak, mikro hizmetler arasında geveze iletişimi önlemek istiyorum. Bu hedefler birbiriyle çelişebilir. Yeni bir Sınırlı Bağlam'ı ayırmak için yapılan her ek girişimle iletişim sınırlarının hızla büyüdüğünü görene kadar sistemi olabildiğince küçük mikro hizmetlere ayırarak bunları dengelemeniz gerekir. Uyum tek bir sınırlı bağlam içinde anahtardır.

Bu sınıfları uygularken [Uygunsuz Samimiyet kodu kokusu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) benzer. Eğer iki mikro hizmetin birbiriyle çok işbirliği yapması gerekiyorsa, muhtemelen aynı mikro servis olmalıdır.

Buna bakmanın bir başka yolu da özerkliktir. Bir microservice doğrudan bir istek hizmet için başka bir hizmet güvenmek gerekiyorsa, gerçekten özerk değildir.

## <a name="layers-in-ddd-microservices"></a>DDD mikrohizmetlerdeki katmanlar

Önemli iş ve teknik karmaşıklığa sahip çoğu kurumsal uygulama birden çok katmanla tanımlanır. Katmanlar mantıksal bir yapıdır ve hizmetin dağıtımıyla ilgili değildir. Geliştiricilerin koddaki karmaşıklığı yönetmesine yardımcı olmak için bulunurlar. Farklı katmanlar (sunu katmanına karşı etki alanı modeli katmanı gibi, vb. farklı türlerde olabilir ve bu türler arasındaki çevirileri zorunlu kılabilir.

Örneğin, bir varlık veritabanından yüklenebilir. Daha sonra bu bilgilerin bir kısmı veya diğer varlıklardan gelen ek veriler de dahil olmak üzere bir bilgi toplama, bir REST Web API aracılığıyla istemci Kullanıcı Arama Birimi'ne gönderilebilir. Burada önemli nokta, etki alanı varlığının etki alanı modeli katmanı içinde yer alması ve sunu katmanı gibi ait olmadığı diğer alanlara yayılmaması gerektiğidir.

Ayrıca, her zaman geçerli olan varlıklara sahip olmanız gerekir [(bkz. etki alanı modeli katmanı bölümündeki tasarım doğrulamaları)](domain-model-layer-validations.md) toplu kökler (kök varlıklar) tarafından denetler. Bu nedenle, ui düzeyinde bazı veriler hala doğrulanamayabilir, çünkü varlıklar istemci görünümleri bağlı olmamalıdır. ViewModel bunun içindir. ViewModel, yalnızca sunum katmanı gereksinimleri için bir veri modelidir. Etki alanı varlıkları doğrudan ViewModel'e ait değildir. Bunun yerine, ViewModels ve etki alanı varlıkları arasında çeviri yapmanız gerekir ve bunun tersi de vardır.

Karmaşıklıkla mücadele ederken, bu varlık grubuyla (toplam) ilgili tüm değişmezlerin ve kuralların toplam kök olan tek bir giriş noktası veya geçit üzerinden gerçekleştirildiğinden emin olan bir etki alanı modelinin toplu kökler tarafından denetlenir olması önemlidir.

Şekil 7-5, katmanlı tasarımın eShopOnContainers uygulamasında nasıl uygulandığını gösterir.

![Etki alanına dayalı bir tasarım mikrohizmetindeki katmanları gösteren diyagram.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Şekil 7-5**. eShopOnContainers sipariş microservice DDD katmanları

Sipariş gibi bir DDD microservice üç katmanları. Her katman bir VS projesidir: Uygulama katmanı Ordering.API, Etki Alanı katmanı Ordering.Domain ve Altyapı katmanı Ordering.Infrastructure'dır. Sistemi, her katmanyalnızca diğer katmanlarla iletişim kuracak şekilde tasarlamak istiyorsunuz. Katmanlar farklı sınıf kitaplıkları olarak uygulanıyorsa, kitaplıklar arasında hangi bağımlılıkların ayarlanacağını açıkça belirleyebileceğinizden, bunu uygulamak daha kolay olabilir. Örneğin, etki alanı modeli katmanı başka bir katmana bağımlılık yapmamalıdır (etki alanı modeli sınıfları Düz Eski CLR Nesneleri veya [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), sınıflar olmalıdır). Şekil 7-6'da gösterildiği gibi, **Ordering.Domain** katmanı kitaplığı yalnızca .NET Core kitaplıklarına veya NuGet paketlerine bağlıdır, ancak veri kitaplığı veya kalıcılık kitaplığı gibi başka özel kitaplıklarda yoktur.

![Ordering.Domain bağımlılıklarının ekran görüntüsü.](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Şekil 7-6**. Kitaplıklar olarak uygulanan katmanlar, katmanlar arasındaki bağımlılıkların daha iyi kontrol edilmesine olanak sağlar

### <a name="the-domain-model-layer"></a>Etki alanı modeli katmanı

Eric Evans mükemmel kitap [Domain Driven Tasarım](https://domainlanguage.com/ddd/) etki alanı modeli katmanı ve uygulama katmanı hakkında aşağıdaki diyor.

**Etki Alanı Modeli Katmanı**: İşletmenin kavramlarını, iş durumu hakkında bilgileri ve iş kurallarını temsil eden sorumludur. İş durumunu yansıtan devlet, depolamanın teknik detayları altyapıya devredilse de burada kontrol edilir ve kullanılır. Bu katman iş yazılımlarının kalbidir.

Etki alanı modeli katmanı, işletmenin ifade edildiği yerdir. .NET'te bir microservice etki alanı modeli katmanı uyguladığınızda, bu katman, veri artı davranışı (mantık lı yöntemler) yakalayan etki alanı varlıklarıyla sınıf kitaplığı olarak kodlanır.

[Kalıcılık Cehalet](https://deviq.com/persistence-ignorance/) ve [Altyapı Cehalet](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerini izleyerek, bu katman tamamen veri kalıcılık ayrıntıları göz ardı etmelidir. Bu kalıcılık görevleri altyapı katmanı tarafından gerçekleştirilmelidir. Bu nedenle, bu katman altyapıya doğrudan bağımlılık lar almamalıdır, bu da önemli bir kuralın etki alanı modeli varlık sınıflarınızın [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s olması gerektiği anlamına gelir.

Etki alanı varlıkları, Entity Framework veya NHibernate gibi herhangi bir veri erişim altyapısı çerçevesinde doğrudan bağımlılığa (taban sınıftan türemiş gibi) sahip olmamalıdır. İdeal olarak, etki alanı varlıklarınız herhangi bir altyapı çerçevesinde tanımlanan herhangi bir türden türememeli veya uygulamamalıdır.

Entity Framework Core gibi çoğu modern ORM çerçevesi bu yaklaşıma izin verir, böylece etki alanı modeli sınıflarınızın altyapıyla birleştiğinde değildir. Ancak, Azure Hizmet Dokusunda Aktörler ve Güvenilir Koleksiyonlar gibi belirli NoSQL veritabanlarını ve çerçevelerini kullanırken POCO varlıklarına sahip olmak her zaman mümkün değildir.

Etki Alanı modeli niz için Kalıcılık Cehalet ilkesini izlemek önemli olsa bile, kalıcılık endişelerini göz ardı etmemelisiniz. Fiziksel veri modelini ve varlık nesnesi modeliyle nasıl eşleşiş olduğunu anlamak yine de çok önemlidir. Aksi takdirde imkansız tasarımlar oluşturabilirsiniz.

Ayrıca, bu ilişkisel bir veritabanı için tasarlanmış bir model alabilir ve doğrudan bir NoSQL veya belge yönelimli veritabanına taşıyabilirsiniz anlamına gelmez. Bazı varlık modellerinde, model sığabilir, ancak genellikle sığmaz. Hem depolama teknolojisine hem de ORM teknolojisine dayalı olarak varlık modelinizin uyması gereken kısıtlamalar hala vardır.

### <a name="the-application-layer"></a>Uygulama katmanı

Uygulama katmanına geçmeden, yine Eric Evans'ın Domain [Driven Design](https://domainlanguage.com/ddd/)adlı kitabından bahsedebiliriz:

**Uygulama Katmanı:** Yazılımın yapması gereken işleri tanımlar ve etkileyici etki alanı nesnelerini sorunları çözmesi için yönlendirir. Bu katmanın sorumlu olduğu görevler işletme için anlamlıdır veya diğer sistemlerin uygulama katmanlarıyla etkileşim için gereklidir. Bu tabaka ince tutulur. İş kuralları veya bilgi içermez, ancak yalnızca görevleri ve temsilcileri bir sonraki katmanda etki alanı nesnelerinin işbirlikleri için çalışır koordine eder. İş durumunu yansıtan bir durum yoktur, ancak kullanıcı veya program için bir görevin ilerlemesini yansıtan bir durum olabilir.

Bir microservice'in .NET'teki uygulama katmanı genellikle ASP.NET Core Web API projesi olarak kodlanır. Proje, mikro hizmetin etkileşimini, uzak ağ erişimini ve ui veya istemci uygulamalarından kullanılan harici Web API'lerini uygular. CQRS yaklaşımı kullanıyorsanız sorguları, microservice tarafından kabul edilen komutları ve hatta mikro hizmetler (tümleştirme olayları) arasındaki olay odaklı iletişimi içerir. Uygulama katmanını temsil eden ASP.NET Core Web API'si iş kuralları veya etki alanı bilgisi içermemelidir (özellikle hareketler veya güncelleştirmeler için etki alanı kuralları); bunlar etki alanı modeli sınıf kitaplığı tarafından sahip olunmalıdır. Uygulama katmanı yalnızca görevleri koordine etmeli ve herhangi bir etki alanı durumunu (etki alanı modeli) tutmamalı veya tanımlamamalıdır. İş kurallarının yürütülmesini etki alanı modeli sınıflarına (toplu kökler ve etki alanı varlıkları) devreder ve sonuçta bu etki alanı varlıkları içindeki verileri günceller.

Temel olarak, uygulama mantığı, belirli bir ön uça bağlı olan tüm kullanım durumlarını uyguladığınız yerdir. Örneğin, bir Web API hizmetiyle ilgili uygulama.

Amaç, etki alanı modeli katmanındaki etki alanı mantığının, değişmezlerinin, veri modelinin ve ilgili iş kurallarının sunu ve uygulama katmanlarından tamamen bağımsız olması gerektiğidir. Hepsinden önemlisi, etki alanı modeli katmanı doğrudan herhangi bir altyapı çerçevesine bağlı olmamalıdır.

### <a name="the-infrastructure-layer"></a>Altyapı katmanı

Altyapı katmanı, başlangıçta etki alanı varlıklarında (bellekte) tutulan verilerin veritabanlarında veya başka bir kalıcı depoda nasıl kalıcı olarak kalıcı olarak kalıcı olarak kalıcı olarak kalıcı olarak bekletildiğidir. Bir örnek, İlişkisel bir veritabanındaki verileri kalıcı olarak sürdürmek için DBContext kullanan Depo desen sınıflarını uygulamak için Varlık Framework Core kodunu kullanmaktır.

Daha önce bahsedilen [Kalıcılık Cehalet](https://deviq.com/persistence-ignorance/) ve [Altyapı Cehalet](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri uyarınca, altyapı katmanı etki alanı modeli katmanı "kontamine" olmamalıdır. Çerçevelere sıkı bağımlılıklar yapmayarak, verileri (EF veya başka bir çerçeve) kalıcı tutmak için kullandığınız altyapıdan etki alanı modeli varlık sınıflarını agnostik tutmanız gerekir. Etki alanı modeli katmanı sınıf kitaplığınız yalnızca etki alanı kodunuza sahip olmalıdır, yalnızca yazılımınızın kalbini uygulayan ve altyapı teknolojilerinden tamamen ayrılmış [OLAN POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) varlık sınıfları olmalıdır.

Bu nedenle, katmanlarınız veya sınıf kitaplıklarınız ve projeleriniz, Şekil 7-7'de gösterildiği gibi, tam tersi değil, etki alanı modeli katmanınıza (kitaplığı) bağlı olmalıdır.

![DDD hizmet katmanları arasında var olan bağımlılıkları gösteren diyagram.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Şekil 7-7**. DDD'deki katmanlar arasındaki bağımlılıklar

DDD Hizmetindeki bağımlılıklar, Uygulama katmanı Etki Alanına ve Altyapıya bağlıdır ve Altyapı Etki Alanına bağlıdır, ancak Etki Alanı herhangi bir katmana bağlı değildir. Bu katman tasarımı her microservice için bağımsız olmalıdır. Daha önce de belirtildiği gibi, DDD desenlerini takip eden en karmaşık mikro hizmetleri uygulayabilir ve daha basit bir şekilde daha basit veri odaklı mikro hizmetler (tek bir katmanda basit CRUD) uygulayabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

- **DevIQ mı? Sebat Cehalet ilkesi** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Altyapı Cehalet** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Melek Lopez. Etki Alanı Odaklı Tasarımda Katmanlı Mimari** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Önceki](cqrs-microservice-reads.md)
>[Sonraki](microservice-domain-model.md)
