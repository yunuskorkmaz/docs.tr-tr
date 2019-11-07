---
title: DDD odaklı bir mikro hizmet tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD-odaklı sıralama mikro hizmetinin ve uygulama katmanlarının tasarımını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: c5ac55978ca979a3ae055d9b0cd2d3c6b3187b4e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739968"
---
# <a name="design-a-ddd-oriented-microservice"></a>DDD-odaklı mikro hizmet tasarlama

Etki alanı odaklı tasarım (DDD) kullanım durumlarınızla ilgili olarak iş gerçekliği temelinde modelleme. Uygulama oluşturma bağlamında, DDD, etki alanları olarak sorunlar hakkında konuşur. Bağımsız sorun bölgelerini sınırlanmış bağlamlar (her bir mikro hizmetle ilişkili olan her sınırlı bağlam) ile açıklar ve bu sorunlar hakkında konuşmak için ortak bir dili vurgular. Ayrıca, iç uygulamayı desteklemek için zengin modellere sahip etki alanı varlıkları ( [anemik-Domain model](https://martinfowler.com/bliki/AnemicDomainModel.html)), değer nesneleri, Toplamalar ve toplama kökü (veya kök varlık) kuralları gibi birçok teknik kavram ve desen de önerir. Bu bölüm, bu iç desenlerin tasarımını ve uygulanmasını tanıtır.

Bazen bu ddd teknik kuralları ve desenleri, ddd yaklaşımının uygulanması için bir içerse öğrenme eğrisi olan belirlenen engelleri aşmak olarak algılanır. Ancak önemli bir bölüm desenlerin kendileri değildir, ancak kod, iş sorunlarına göre hizalanmak ve aynı iş koşulları (ubititous dili) kullanılarak düzenlenmez. Ayrıca, DDD yaklaşımları yalnızca önemli iş kurallarıyla karmaşık mikro hizmetler uyguladığınızda uygulanmalıdır. CRUD hizmeti gibi daha basit sorumluluklar daha basit yaklaşımlar ile yönetilebilir.

Sınırları nerede çizeceğiniz, mikro hizmet tasarlarken ve tanımlarken anahtar görevdir. DDD desenleri, etki alanındaki karmaşıklığı anlamanıza yardımcı olur. Her sınırlanmış bağlam için etki alanı modelinde, etki alanınızı modellemeye yönelik varlıkları, değer nesnelerini ve toplamaları tanımlar ve tanımlarsınız. Bağlamını tanımlayan bir sınır içinde bulunan bir etki alanı modeli oluşturur ve daraltın. Bu, mikro hizmet biçiminde çok açık olur. Bu sınırların içindeki bileşenler mikro hizmetlerinize göre sona erdir, ancak bazı durumlarda bir BC veya iş mikro hizmetleri çeşitli fiziksel hizmetlerden bulunabilir. DDD, sınırlardır ve mikro hizmetlerdir.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Mikro hizmet bağlamı sınırlarını nispeten küçük tutun

Sınırlanmış bağlamlar arasında sınırların nereye yerleştirileceğini belirlemek iki rekabet hedefini dengeler. İlk olarak, mümkün olan en küçük mikro hizmetleri oluşturmak, ancak ana sürücü olmamalıdır; birlikte kullanılması gereken nesnelerin etrafında bir sınır oluşturmalısınız. İkincisi, mikro hizmetler arasındaki geveze iletişimlerine engel olmak istiyorsunuz. Bu hedefler birbiriyle çelişme edebilir. Yeni bir sınırlanmış bağlamı ayırma ile ilgili her bir ek deneyle, iletişim sınırlarını hızlı bir şekilde büyüene kadar birçok küçük mikro hizmet olarak bunları dengeleyerek dengeleyebilirsiniz. Cohema, tek bir sınırlanmış bağlam içindeki anahtardır.

Sınıfları uygularken [uygunsuz kullanım kodu kokusu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) ile benzerdir. İki mikro hizmetin birbirleriyle çok fazla işbirliği yapması gerekiyorsa, büyük olasılıkla aynı mikro hizmet olmalıdır.

Bu şekilde bağımsız çalışma sınırı. Bir mikro hizmetin bir isteğe doğrudan hizmet vermek için başka bir hizmete bağlı olması gerekiyorsa, gerçekten otonom değildir.

## <a name="layers-in-ddd-microservices"></a>DDD mikro hizmetlerindeki Katmanlar

Önemli iş ve teknik karmaşıklık düzeyine sahip kurumsal uygulamaların çoğu birden fazla katman tarafından tanımlanır. Katmanlar bir mantıksal yapıtıdır ve hizmetin dağıtımıyla ilgili değildir. Bunlar, geliştiricilerin koddaki karmaşıklığı yönetmesine yardımcı olmaları için mevcuttur. Farklı katmanlar (örneğin, etki alanı modeli katmanı, sunum katmanı, vb.) farklı türlerde olabilir ve bu türler arasında çevirileri zorunlu kılabilir.

Örneğin, veritabanından bir varlık yüklenebilir. Daha sonra bu bilgilerin bir kısmı veya diğer varlıklardan ek veriler dahil bir bilgi toplama, istemci kullanıcı arabirimine bir REST Web API 'SI aracılığıyla gönderilebilir. Buradaki nokta, etki alanı varlığının etki alanı model katmanında yer aldığı ve sunum katmanı gibi, ait olmadığı diğer alanlara yayılmamalıdır.

Ayrıca, toplam köklerle (kök varlıklar) denetlenen her zaman geçerli varlıklara ( [etki alanı model katmanı bölümünde doğrulamaları tasarlama](domain-model-layer-validations.md) bölümüne bakın) sahip olmanız gerekir. Bu nedenle, Kullanıcı arabirimi düzeyinde bazı veriler hala doğrulanmamış olabileceğinden, varlıkların istemci görünümlerine bağlanmamalıdır. Bu, ViewModel için olduğu şeydir. ViewModel yalnızca sunum katmanı ihtiyaçlarına yönelik bir veri modelidir. Etki alanı varlıkları doğrudan ViewModel 'e ait değildir. Bunun yerine, Viewmodeller ve etki alanı varlıkları arasında çeviri yapmanız ve tam tersi de yapmanız gerekir.

Bu karmaşıklıktan dolayı, bu varlık grubuyla ilgili (toplama) tüm ınvaryantlar ve kuralların toplam bir giriş noktası veya kapısı aracılığıyla gerçekleştirildiğinden emin olmak için toplam köklere göre denetlenen bir etki alanı modeli olması önemlidir.

Şekil 7-5 ' de, bir katmanlı tasarımın eShopOnContainers uygulamasında nasıl uygulandığı gösterilmektedir.

![Etki alanı odaklı tasarım mikro hizmetindeki katmanların gösterildiği diyagram.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Şekil 7-5**. EShopOnContainers 'da sıralama mikro hizmetindeki DDD katmanları

Bir DDD mikro hizmetindeki sıralama gibi üç katman. Her katman bir VS projem: uygulama katmanı sıralama. API, etki alanı katmanı sıralama. etki alanı ve altyapı katmanı sıralama. altyapısıdır. Her katmanın yalnızca belirli diğer katmanlarla iletişim kurduğu şekilde sistemi tasarlamak istiyorsunuz. Kitaplıkların farklı sınıf kitaplıkları olarak uygulanıp uygulanmadığı, kitaplıklar arasında hangi bağımlılıkların ayarlandığını açıkça belirleyebileceğinize olanak tanımak daha kolay olabilir. Örneğin, etki alanı model katmanı başka bir katmana bağımlılık alamaz (etki alanı model sınıfları, düz eski CLR nesneleri veya [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), sınıflar olmalıdır). Şekil 7-6 ' de gösterildiği gibi, **sıralama. Domain** katman kitaplığı yalnızca .NET Core kitaplıklarında veya NuGet paketlerinde bağımlılıklara sahiptir, ancak veri kitaplığı veya kalıcılık kitaplığı gibi özel bir kitaplıkta değildir.

![Sıralama. etki alanı bağımlılıklarını ekran görüntüsü.](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Şekil 7-6**. Kitaplıklar olarak uygulanan katmanlar Katmanlar arasındaki bağımlılıklara daha iyi denetim sağlar

### <a name="the-domain-model-layer"></a>Etki alanı model katmanı

Eric Evans 'ın mükemmel kitap [etki alanı odaklı tasarımı](https://domainlanguage.com/ddd/) , etki alanı modeli katmanı ve uygulama katmanı hakkında aşağıdakileri söyler.

**Etki alanı modeli katmanı**: işletmenin kavramlarını, iş durumu hakkında bilgileri ve iş kurallarını temsil eden sorumludur. İş durumunu yansıtan eyalet, bu altyapıyı depolamanın teknik ayrıntıları altyapıya atanmış olsa bile burada kontrol edilir ve burada kullanılır. Bu katman, iş yazılımının kalbidir.

Etki alanı modeli katmanı, işletmenin ifade edildiği yerdir. .NET ' te bir mikro hizmet etki alanı model katmanı uyguladığınızda, bu katman veri ve davranışı (Logic ile Yöntemler) yakalayan etki alanı varlıklarını içeren bir sınıf kitaplığı olarak kodlanır.

[Kalıcılık Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerine göre, bu katmanın veri kalıcılığı ayrıntılarını tamamen yoksayması gerekir. Bu Kalıcılık görevleri altyapı katmanı tarafından gerçekleştirilmelidir. Bu nedenle, bu katmanın altyapı üzerinde doğrudan bağımlılıkları olmaması gerekir. Bu, önemli bir kuralın, etki alanı modeli varlık sınıflarınızın [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)'lar olması gerektiği anlamına gelir.

Etki alanı varlıklarının, Entity Framework veya Nhazırda bekleme gibi herhangi bir veri erişim altyapısı çerçevesinde doğrudan bağımlılığı (taban sınıftan türeme gibi) olmaması gerekir. İdeal olarak, etki alanı varlıklarınız herhangi bir altyapı çerçevesinde tanımlı herhangi bir türden türetilmemelidir veya uygulamamalıdır.

Entity Framework Core benzer modern ORM çerçeveleri bu yaklaşıma izin veriyor, böylece etki alanı model sınıflarınız altyapıyla birlikte kullanılamaz. Ancak, Azure Service Fabric aktörler ve güvenilir Koleksiyonlar gibi belirli NoSQL veritabanları ve çerçeveleri kullanılırken POCO varlıklarının bulunması her zaman mümkün değildir.

Etki alanı modelinize yönelik kalıcılık Ignorance ilkesini izlemek önemli olduğunda bile, kalıcılık sorunlarını yoksaymamalıdır. Fiziksel veri modelini ve varlık nesne modelinize nasıl eşlendiğini anlamak hala çok önemlidir. Aksi takdirde, imkansız tasarımlar oluşturabilirsiniz.

Ayrıca, bu, ilişkisel veritabanı için tasarlanmış bir modeli alıp bir NoSQL veya belge odaklı veritabanına doğrudan taşıyabilmeniz anlamına gelmez. Bazı varlık modellerinde model uygun olabilir, ancak genellikle bu değildir. Varlık modelinizin, her ikisi de depolama teknolojisine ve ORM teknolojisine bağlı olarak uyması gereken kısıtlamalar vardır.

### <a name="the-application-layer"></a>Uygulama katmanı

Uygulama katmanına geçiş yaparken, Eric Evans 'ın [etki alanı odaklı tasarımını](https://domainlanguage.com/ddd/)daha iyi bir şekilde ayırıyoruz:

**Uygulama katmanı:** Yazılımın yapması beklenen işleri tanımlar ve ifade eden etki alanı nesnelerini, sorunları gidermek için yönlendirir. Bu katmanın sorumlu olduğu görevler işletmeye göre anlamlıdır veya diğer sistemlerin uygulama katmanlarıyla etkileşim için gereklidir. Bu katman ince tutulur. İş kuralları veya bilgi içermez, ancak yalnızca sonraki katmandaki etki alanı nesnelerinin işbirliği yaptığı görevleri ve temsilcileri koordine eder. İş durumunu yansıtan bir durumu yoktur, ancak kullanıcı veya program için bir görevin ilerlemesini yansıtan bir durum olabilir.

.NET 'teki bir mikro hizmetin uygulama katmanı genellikle ASP.NET Core Web API projesi olarak kodlanır. Proje, mikro hizmetin etkileşimini, uzak ağ erişimini ve kullanıcı arabiriminden veya istemci uygulamalarından kullanılan dış Web API 'Lerini uygular. CQRS yaklaşımını, mikro hizmet tarafından kabul edilen komutları ve hatta mikro hizmetler arasındaki olay odaklı iletişimi (Tümleştirme olayları) kullanarak sorgular içerir. Uygulama katmanını temsil eden ASP.NET Core Web API 'SI, iş kuralları veya etki alanı bilgisi içermemelidir (özellikle işlemler veya güncelleştirmeler için etki alanı kuralları); Bunlar, etki alanı modeli sınıf kitaplığına ait olmalıdır. Uygulama katmanının yalnızca görevleri koordine ve herhangi bir etki alanı durumu (etki alanı modeli) tutmamalıdır veya tanımlamamalıdır. İş kurallarının yürütülmesini, etki alanı modeli sınıflarının kendilerine (Toplam kökler ve etki alanı varlıkları) yürütmesini devreder ve bu da bu etki alanı varlıklarındaki verileri son olarak güncelleştirir.

Temel olarak uygulama mantığı, belirli bir ön uca bağlı olan tüm kullanım durumlarını uyguladığınız yerdir. Örneğin, bir Web API hizmeti ile ilgili uygulama.

Amaç, etki alanı modeli katmanındaki etki alanı mantığının, ınvaryantlar, veri modeli ve ilgili iş kurallarının, sunum ve uygulama katmanlarından tamamen bağımsız olması gerekir. Çoğu, etki alanı modeli katmanının herhangi bir altyapı çerçevesine doğrudan bağlı olmaması gerekir.

### <a name="the-infrastructure-layer"></a>Altyapı katmanı

Altyapı katmanı, ilk olarak etki alanı varlıklarında (bellekte) tutulan verilerin veritabanlarında veya başka bir kalıcı depoda kalıcı olarak nasıl sürdürümğidir. Bir örnek, verileri ilişkisel bir veritabanında kalıcı hale getirmek için DBContext kullanan depo model sınıflarını uygulamak üzere Entity Framework Core kodu kullanmaktır.

Daha önce bahsedilen [Kalıcılık](https://deviq.com/persistence-ignorance/) kaldırma ve [altyapı](https://ayende.com/blog/3137/infrastructure-ignorance) kaldırma ilkelerine uygun olarak, altyapı katmanının etki alanı modeli katmanını "kirmini" olmaması gerekir. Çerçeveler üzerinde sabit bağımlılıklar olmaksızın, verileri (EF veya diğer herhangi bir çerçeve) sürdürmek için kullandığınız altyapıdan, etki alanı modeli varlık sınıflarını agntik tutmanız gerekir. Etki alanı modeli katman sınıfı kitaplığınızın yalnızca etki alanı kodunuz olmalıdır, yalnızca yazılımınızın temelini oluşturan ve altyapı teknolojisinden tamamen ayrılmış bir [poco](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) varlık sınıfları olmalıdır.

Bu nedenle, Şekil 7-7 ' de gösterildiği gibi, katmanlarınızın veya sınıf kitaplıklarınızın ve projelerinizin sonunda etki alanı model katmanına (kitaplık) bağlı olması gerekir.

![DDD hizmet katmanları arasında var olan bağımlılıkları gösteren diyagram.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Şekil 7-7**. DDD içindeki Katmanlar arasındaki bağımlılıklar

Bir DDD hizmetindeki bağımlılıklar, uygulama katmanı etki alanı ve altyapıya bağlıdır ve altyapı etki alanına bağlıdır, ancak etki alanı herhangi bir katmana bağlı değildir. Bu katman tasarımı her mikro hizmet için bağımsız olmalıdır. Daha önce belirtildiği gibi, daha basit bir şekilde veri odaklı mikro hizmetleri (tek bir katmanda basit CRUD) daha kolay bir şekilde uygularken, DDD desenlerini izleyen en karmaşık mikro hizmetleri de uygulayabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Sapq. Kalıcılık Ignorance ilkesi** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Altyapı Ignorance** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Anlek Lopez. Etki alanı odaklı tasarım \ katmanlı mimari**
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Önceki](cqrs-microservice-reads.md)
>[İleri](microservice-domain-model.md)
