---
title: DDD odaklı bir mikro hizmet tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | DDD odaklı sıralama mikro hizmet ve uygulama katmanları tasarımını anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 65a1a58d0c70c7e788aea420006c1ad617628f93
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145614"
---
# <a name="design-a-ddd-oriented-microservice"></a>DDD odaklı bir mikro hizmet tasarlama

Etki alanı Odaklı Tasarım (DDD), kullanım örnekleri ile ilgili olarak iş gerçeğe dayalı modelleme sorunlarınızda. Uygulamaları oluşturma, bağlamında DDD etki alanı adı sorunlar hakkında konuşuyor. Sınırlanmış Bağlamlar olarak bağımsız sorunlu alanları açıklar (her sınırlanmış bağlam karşılık gelen bir mikro hizmet için) ve bu sorunları hakkında konuşmak için ortak bir dil vurgular. Ayrıca birçok teknik kavramlar ve desenleri, etki alanı varlıklarla zengin modeller gibi önerir (hiçbir [anemic etki alanı modeli](https://martinfowler.com/bliki/AnemicDomainModel.html)), değeri nesneleri, toplamlar ve toplama kök (veya kök varlık) kuralları iç uygulama desteklemek için. Bu bölüm, tasarım ve uygulama bu iç desenlerinin tanıtır.

Bazen bu DDD teknik kuralları ve desenleri DDD yaklaşımları uygulamak için zorlu öğrenme süreçlerine sahip engellerini algılanır. Ancak, önemli değil desenleri kendilerini, ancak iş sorunlarına hizalanacağı şekilde kod düzenleme ve aynı iş terimlerini (bulunabilen dili) kullanarak bir parçasıdır. Ayrıca, önemli iş kuralları ile karmaşık mikro hizmetler uyguluyorsanız DDD yaklaşımları uygulanmalıdır. Bir CRUD hizmeti gibi basit sorumlulukları daha basit bir yaklaşım ile yönetilebilir.

Sınırları nerede tasarlarken ve bir mikro hizmet tanımlama anahtar görevdir. DDD deseni etki alanındaki karmaşıklığı anlamanıza yardımcı olur. Etki alanı modeli için sınırlanmış her bağlam için belirleyin ve varlıkları, değer nesneleri ve, etki alanı model toplamalar tanımlayın. Derleme ve Bağlamınızı tanımlayan bir sınırları içinde yer alan bir etki alanı modeli daraltın. Ve bir mikro hizmet biçiminde çok açık. Son BC bir bazı durumlarda olsa da bu sınırlar içinde bileşenleri, mikro hizmetler, olan yukarı veya iş mikro hizmetler birçok fiziksel hizmetlerini oluşabilir. DDD sınırları hakkında ve bu nedenle mikro hizmetler.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Mikro hizmet bağlam sınırlarını görece küçük tutun

Sınırlanmış Bağlamlar arasında sınırları yerleştirileceği yeri belirleme iki rakip hedefleri dengeler. İlk olarak, ana sürücüsü olmamalıdır olsa da başlangıçta en küçük olası mikro hizmetler oluşturmak istiyorsunuz; Uyuma gereken şeyleri etrafında bir sınır oluşturmanız gerekir. İkinci olarak, mikro hizmetler arasında geveze iletişim engellemek istiyorsanız. Bu hedefleri birbiriyle çelişebilir. Yeni bir sınırlanmış bağlam ayırmak için her ek denemesi ile hızla büyüyen iletişim sınırları görene kadar olabildiğince çok küçük mikro hizmetler halinde sistemin parçalama bunları dengelemek. Uyuma tek bir sınırlanmış bağlam içinde bir anahtardır.

Benzer [uygunsuz samimiyet duyguları kod kokusu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) sınıfları uygulanırken. İki mikro hizmetler çok birbirleriyle işbirliği yapması gerekiyorsa, bunlar büyük olasılıkla aynı mikro hizmet olmalıdır.

Şu anda aramak için başka bir bağımsız çalışma sınırı yoludur. Bir mikro hizmet doğrudan bir isteğe hizmet vermek için başka bir hizmetten yararlanın gerekir, gerçek anlamda otonom değil.

## <a name="layers-in-ddd-microservices"></a>DDD mikro hizmet katmanları

Çoğu kurumsal uygulamalar önemli işletme ve teknik karmaşıklığı ile birden çok katman tarafından tanımlanır. Katmanları olan mantıksal bir yapıt ve hizmeti dağıtımına ilişkili değildir. Geliştiricilerin kod karmaşıklığını yönetmenize yardımcı olmak için mevcut. (Etki alanı model katmanında ve bir sunu katmanı, vb. gibi) farklı katmanlara hangi bu türler arasında çevirileri taahhütlerin farklı olabilir.

Örneğin, bir varlığın veritabanından yüklenemedi. Ardından bu bilgileri veya diğer varlıklar, ek verileri dahil olmak üzere bilgi toplamını bölümü bir REST Web API'si aracılığıyla kullanıcı Arabirimi istemciye gönderilebilir. Burada etki alanı varlığı içinde etki alanı model katmanında yer alır ve bunu, gibi sunu katmanına ait değil. diğer alanlarına yayılır değil noktasıdır.

Ayrıca, her zaman geçerli varlıkları olması gerekir (bkz [etki alanı model katmanında doğrulamaları tasarlama](domain-model-layer-validations.md) bölümü) toplama kökleri (kök varlıklar) tarafından denetlenir. UI düzeyinde bazı veriler hala geçerliliğinin doğrulanması çünkü bu nedenle, varlıklar istemci görünümlerine bağlanmalıdır değil. ViewModel içindir budur. ViewModel, sunu katmanı ihtiyaçları için özel bir veri modelidir. Etki alanı varlıklarının ViewModel için doğrudan ait değil. Bunun yerine, Viewmodel'lar ve etki alanı varlıklar arasında ve çevirme gerekir.

Kuruluşlarda karmaşıklığı okuduğunuzda ve kuralları için ilgili emin toplama kökleri tarafından denetlenen bir etki alanı modeli için önemli olduğunda, varlıkları (toplama) grubu gerçekleştirilir tek giriş noktası veya ağ geçidi, toplama kök ile.

Şekil 7-5 katmanlı bir tasarım hizmetine uygulamada nasıl uygulandığını göstermektedir.

![Bir DDD mikro hizmet üç katmanda sıralama ister. Her katman, bir VS projesine ise: Uygulama katmanı Ordering.API Ordering.Domain etki alanı katmanıdır ve altyapı katmanını Ordering.Infrastructure'dür.](./media/image6.png)

**Şekil 7-5**. Sıralama mikro hizmetine DDD katmanları

Her katman yalnızca belirli diğer katmanlarla ile iletişim kurar. böylece sistemi tasarlamak istiyorsunuz. Kitaplıklar arasında hangi bağımlılıkların ayarlandığından NET bir şekilde tespit edebilirsiniz çünkü katmanları farklı sınıf kitaplıkları uygulanırsa zorlamak daha kolay olabilir. Örneğin, etki alanı model katmanında bir bağımlılık başka bir katmanda almamalıdır (düz eski CLR nesnelerini, etki alanı model sınıfları olmalıdır veya [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), sınıflar). Şekil 7-6'da gösterildiği gibi **Ordering.Domain** Katmanı kitaplığı, yalnızca .NET Core kitaplıkları veya NuGet paketlerini, ancak tüm diğer özel bir kitaplık, verileri kitaplığı veya Kalıcılık kitaplığı gibi bağımlılıkları vardır.

![Çözüm Gezgini görünümü Ordering.Domain bağımlılıklarının göstermeyi .NET Core kitaplıkları'nı yalnızca bağlıdır.](./media/image7.png)

**Şekil 7-6**. Kitaplıkları Katmanlar arasındaki bağımlılıkları daha iyi Denetimi'ne izin ver olarak uygulanan katmanları

### <a name="the-domain-model-layer"></a>Etki alanı model katmanında

Eric Evans'ın mükemmel kitap [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/) etki alanı model katmanında ve uygulama katmanı hakkında aşağıdaki söyler.

**Etki alanı Model katmanında**: İş kuralları ve iş durumu hakkındaki bilgileri, iş kavramlarını göstermek için sorumlu. İş durumu yansıtır durumu denetlenir ve teknik ayrıntılarını depolamadan altyapıya izin verilmiş olsa da burada kullanılan. Bu katman, Kurumsal Yazılım kalbidir.

Etki alanı model katmanında, iş yeri ifade edilir ' dir. . NET'te bir mikro hizmet etki alanı model katmanında uyguladığınızda, o katmanın verilerin yanı sıra davranışı (mantıksal yöntemleriyle) yakalama etki alanı varlıklarının ile bir sınıf kitaplığı olarak kodlanmıştır.

Aşağıdaki [Kalıcılık Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri, bu katman veri kalıcılığı ayrıntıları tamamen yoksay gerekir. Bu süreklilik görevleri altyapı katmanı tarafından gerçekleştirilmelidir. Bu nedenle, bu katmanda doğrudan bağımlılıkları önemli bir kuralı, etki alanı modeli varlık sınıfları olmalıdır, yani etkin altyapısında almamalıdır [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Etki alanı varlıklarının Entity Framework veya NHibernate gibi tüm veri erişim altyapı Framework (örneğin, bir taban sınıftan türetme) doğrudan hiçbir bağımlılık olmamalıdır. İdeal olarak, etki alanı varlıklarınızı türetmek veya gerekir tüm altyapı Framework'te tanımlanan herhangi bir tür.

Etki alanı model sınıflarınızı altyapıya bağlı değil, bu yaklaşım, Entity Framework Core gibi birçok modern ORM çerçeveleri sağlar. Ancak, POCO varlık sahip her zaman belirli bir NoSQL veritabanları ve aktörler ve Azure Service fabric'te güvenilir koleksiyonlar gibi çerçeveleri kullanarak mümkün değildir.

Etki alanı modeliniz için Kalıcılık Ignorance ilkesini izlemek önemli olsa bile, Kalıcılık kaygıları sayılmalıdır değil. Yine de fiziksel veri modeli ve varlığı nesne modeli eşlemelerini nasıl anlamak çok önemlidir. Aksi takdirde, mümkün olmayan tasarımı oluşturabilirsiniz.

Ayrıca, bu, ilişkisel bir veritabanı için tasarlanmış bir model alabilir ve doğrudan taşımak için bir NoSQL veya belge yönelimli veritabanı anlamına gelmez. Bazı varlık modelleri modeline uyacak, ancak genellikle yok. Yine de, varlık modeli, hem depolama teknolojisi ve teknolojisi ORM tabanlı uymalıdır kısıtlamaları da vardır.

### <a name="the-application-layer"></a>Uygulama katmanı

Taşıma için uygulama katmanı, biz yeniden alınıyor Eric Evans'ın kitap [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/):

**Uygulama katmanı:** Yazılım yapmak için gereken ve sorunlarını çalışmaya ifadesel bir etki alanı nesnelerini yönlendirir işleri tanımlar. Bu katman sorumlu olduğu iş anlamlı veya diğer sistemlere uygulama katmanları ile etkileşim için gerekli görevlerdir. Bu katman, ölçülü kaynak tutulur. İş kuralları veya bilgi içermiyor, ancak yalnızca koordinatları görevleri ve temsilciler için etki alanı nesnelerini sonraki katmanında işbirliğini aşağı çalışır. İş durumu yansıtma durumu yok, ancak kullanıcı veya program için bir görev ilerlemesini gösteren bir durum olabilir.

.NET mikro hizmet ait uygulama katmanında, genellikle bir ASP.NET Core Web API projesi kodlanmıştır. Mikro hizmet'ın etkileşim, uzak ağ erişimi ve kullanıcı Arabirimi veya istemci uygulamalardan kullanılan dış Web API projesi uygular. Mikro hizmet ve mikro hizmetler (tümleştirme olayları) arasında bile olay temelli iletişim tarafından kabul edilen komutlar kullanılarak bir CQRS yaklaşımı, sorguları içerir. Uygulama katmanı temsil eden ASP.NET Core Web API'si, iş kuralları veya etki alanı bilgilerini (özellikle etki alanı kuralları için işlemleri veya güncelleştirmeler); içermemelidir Bu etki alanı modeli sınıfı kitaplığı tarafından ait. Uygulama katmanı yalnızca gereken koordinat görevleri ve gerekir değil basılı tutun veya herhangi bir etki alanı durumu (etki alanı modeli) tanımlayın. Bu, iş kuralları, bu etki alanı varlıklarının içinde verilerin nihai olarak güncelleştirir etki alanı model sınıflarına kendilerini (toplama kökler ve etki alanı varlıklarının) yürütülmesini atar.

Uygulama mantığı temel olarak, belirli bir ön uç üzerinde bağımlı tüm kullanım örnekleri burada uygulamanız olur. Örneğin, bir Web API'si hizmeti için ilgili uygulama.

Etki alanı model katmanında, kendi okuduğunuzda, veri modeli ve ilgili iş kuralları etki alanı mantığı sunu ve uygulama katmanları tamamen bağımsız hedeftir. En önemlisi, etki alanı model katmanında doğrudan herhangi bir altyapı çerçeveyi bağımlı olmamalıdır.

### <a name="the-infrastructure-layer"></a>Altyapı katmanını

Veritabanları veya başka bir kalıcı depoya (bellekte) etki alanı varlıklarının başlangıçta tutulan verilerin kalıcı nasıl altyapı katmanıdır. Örnek, bir ilişkisel veritabanındaki verileri kalıcı hale getirmek için bir DBContext kullanın depo düzeni sınıfları uygulamak için Entity Framework Core kod kullanıyor.

Daha önce bahsedilen uygun olarak [Kalıcılık Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri, altyapı katmanını gerekir değil "zarar verme" etki alanı model katmanında. Etki alanı modeli varlık sınıfları belirsiz sabit bağımlılıkları çerçevelerini temel alarak değil (EF veya diğer herhangi bir çerçeveyi) verileri kalıcı hale getirmek için kullandığınız altyapıdan tutmanız gerekir. Etki alanı modeli katmanı sınıf kitaplığı yalnızca, etki alanı kodu yalnızca olması gerektiğini [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) varlık sınıfları yazılımınızı 'un uygulama ve altyapı teknolojiden tamamen ayrılmış.

Bu nedenle, katmanları veya sınıf kitaplıkları ve projeleri Sonuçta, etki alanı model katmanında (kitaplık) bağımlı tam tersi gerekmiyor, Şekil 7-7'de gösterildiği gibi.

![Etki alanı ve altyapı, bağımlılıkları DDD hizmetinde, uygulama katmanına bağlıdır ve altyapı etki alanına bağlıdır, ancak etki alanı herhangi bir katmanda bağımlı değildir.](./media/image8.png)

**Şekil 7-7**. DDD Katmanlar arasındaki bağımlılıkları

Bu katman tasarım için her bir mikro hizmetin bağımsız olmalıdır. Daha önce belirtildiği gibi en karmaşık mikro hizmetler uygulayabileceğiniz DDD deseni, veri odaklı basit uygulama çalışırken aşağıdaki mikro hizmetler (tek bir katmanda basit CRUD) daha basit bir şekilde.

#### <a name="additional-resources"></a>Ek kaynaklar

- **DevIQ. Kalıcılık Ignorance İlkesi** \
  [*https://deviq.com/persistence-ignorance/*](https://deviq.com/persistence-ignorance/)

- **Oren Eini. Altyapı Ignorance** \
  [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

- **Melek Lopez. Etki alanı Odaklı Tasarım katmanlı mimaride** \
  [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)

>[!div class="step-by-step"]
>[Önceki](cqrs-microservice-reads.md)
>[İleri](microservice-domain-model.md)