---
title: DDD odaklı mikro tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | DDD odaklı mikro tasarlama
keywords: Docker, mikro, ASP.NET, kapsayıcı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d2d07abe55f30e0b12a7f0cba937abd1b7e32629
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="designing-a-ddd-oriented-microservice"></a>DDD odaklı mikro tasarlama

Etki alanı Odaklı Tasarım (DDD) kullanım durumları için ilgili olarak iş gerçekte dayalı modelleme savunan. Uygulamaları derleme bağlamında, etki alanı olarak sorunlar hakkında DDD alınmaktadır. Sınırlanmış bağlamları olarak bağımsız sorunlu alanları açıklar (her ilişkisindeki bağlam karşılık gelen bir mikro hizmet) ve bu sorunları hakkında anlaşmak için ortak bir dil vurgular. Birçok teknik kavramlar ve etki alanı varlıkları zengin modellerle gibi düzenleri de öneren (hiçbir [anemic etki alanı modeli](https://martinfowler.com/bliki/AnemicDomainModel.html)), değeri nesneleri, toplamları ve birleşik kök (veya kök varlık) kuralları iç uygulamasını desteklemek için. Bu bölümde, tasarım ve uygulama bu dahili desenlerinin tanıtır.

Bazen bu DDD teknik kuralları ve desenler DDD yaklaşımlar uygulamak için yüksek bir öğrenme eğrisi engellerini algılanır. Ancak, önemli değil desenlerini kendilerini, ancak iş sorunlarını hizalanır şekilde kod düzenleme ve aynı iş koşullarını (bulunabilen dili) kullanarak bir parçasıdır. Ayrıca, yalnızca önemli iş kuralları ile karmaşık mikro uyguluyorsanız DDD yaklaşımlar uygulanmalıdır. CRUD hizmeti gibi basit sorumlulukları daha basit yaklaşımlardan ile yönetilebilir.

Kenarlıkları çizmek tasarlama ve bir mikro hizmet tanımlama anahtar görev yerdir. DDD desenleri etki alanındaki karmaşıklık anlamanıza yardımcı. Etki alanı modeli ilişkisindeki her bağlam için için belirlemek ve varlıkları, değer nesnelerini ve etki alanınızı model toplamalar tanımlayın. Derleme ve içeriğiniz tanımlayan bir sınırı içinde bulunan bir etki alanı modeli daraltın. Ve bir mikro hizmet formunda çok açık. End BC bir bazı durumlarda rağmen bu sınırlar içinde bileşenleri, mikro olan yukarı veya iş mikro birkaç fiziksel hizmetinden birleştirilebilir. DDD sınırları hakkında ve bu nedenle mikro.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Mikro Hizmet bağlamı sınırları görece küçük tutun

Sınırlanmış bağlamları arasındaki sınırları nereye yerleştireceğinizi belirleme iki rakip hedefleri dengeler. İlk olarak, ana sürücü olmamalıdır rağmen başlangıçta en küçük olası mikro oluşturmak istediğiniz; cohesion gereken şeyleri sınırlarından oluşturmanız gerekir. İkinci olarak, mikro arasındaki chatty iletişim önlemek istiyor. Bu hedefleri birbiriyle çelişen. Bunları hızla yeni bir sınırlanmış bağlamı ayırmak için ek denemesine büyüyen iletişimi sınırları görene kadar mümkün olduğu kadar küçük mikro içine sistem ayırma dengelemeniz. Cohesion tek bir sınırlanmış bağlam içinde bir anahtardır.

Aşağıdakine benzer [uygunsuz samimiyet duyguları kod kokusu](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) sınıfları uygulanırken. İki mikro çok birbirleri ile işbirliği gerekiyorsa, bunlar büyük olasılıkla aynı mikro hizmet olmalıdır.

Şu anda aramak için başka bir otonomisi yoludur. Bir mikro hizmet isteği doğrudan hizmet vermek için başka bir hizmete gerekir kullanıyorsa, gerçekten otonom değil.

## <a name="layers-in-ddd-microservices"></a>DDD mikro katmanları

Önemli iş ve teknik karmaşıklık çoğu kuruluş uygulamalarıyla birden çok katman tarafından tanımlanır. Katmanları olan bir mantıksal yapı ve biri hizmet dağıtımı için ilişkili değildir. Geliştiriciler kodda karmaşıklığını yönetmenize yardımcı olmak için mevcut. Farklı katmanlar (örneğin, etki alanı modeli katmanı karşı sunu katmanı, vb.), bu türleri arasındaki çevirileri olması zorunlu tutulmuştur farklı olabilir.

Örneğin, bir varlık veritabanından yüklenemedi. Ardından, bu bilgileri veya diğer varlıklar ek verileri dahil olmak üzere bilgilerinin bir toplama parçası UI REST Web API'si aracılığıyla istemciye gönderilebilir. Burada etki alanı varlığı etki alanı modeli katman içinde yer alır ve bunu, gibi sunu katmanı ait diğer alanlara yayılan değil noktasıdır.

Ayrıca, her zaman geçerli varlıkları olması gerekir (bkz [etki alanı modeli katmanda doğrulamaları tasarlama](#designing-validations-in-the-domain-model-layer) bölüm) toplama kökleri (kök varlıklar) tarafından denetlenen. UI düzeyinde bazı veriler hala değil doğrulanması çünkü bu nedenle, varlıkları istemci görünümlerine bağlanmalıdır değil. ViewModel içindir budur. ViewModel, sunu katmanı ihtiyaçları için özel olarak bir veri modelidir. Etki alanı varlıkları doğrudan ViewModel ait değil. Bunun yerine, ViewModels ve etki alanı varlıklar arasındaki veya tam tersine çevirmek gerekir.

Kuruluşlarda karmaşıklık tüm invariants ve kurallar için ilişkili emin olun toplama kökleri tarafından denetlenen bir etki alanı modeline sahip önemli olduğu durumlarda varlıkları (toplama) grubu gerçekleştirilir tek giriş noktası veya ağ geçidi, toplama kök ile.

Şekil 9-5, katmanlı bir tasarım eShopOnContainers uygulamada nasıl uygulandığını gösterir.

![](./media/image6.png)

**Şekil 9-5**. Sıralama mikro hizmet eShopOnContainers içinde DDD katmanları

Her katman yalnızca belirli diğer katmanlar ile iletişim kurar sistemde tasarlamak istersiniz. Farklı sınıf kitaplıkları Katmanlar uygulanırsa, hangi bağımlılıkların kitaplıkları ayarlandığından açıkça tanımlayabilirsiniz çünkü zorlamak daha kolay olabilir. Örneğin, etki alanı modeli katmanı bağımlılık başka bir katmanında almamalıdır (etki alanı modeli sınıflarını eski düz CLR nesnelerini olmalıdır veya [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), sınıflar). Şekil 9-6'da gösterildiği gibi **Ordering.Domain** Katmanı kitaplığı, yalnızca .NET Core kitaplıkları veya NuGet paketleri, aynı olmayan tüm diğer özel kitaplığı veri kitaplığı ya da kalıcılığı kitaplığı gibi bağımlılıklar vardır.

![](./media/image7.PNG)

**Şekil 9-6**. Kitaplıkları katmanları arasındaki bağımlılıkları daha iyi denetlemesine izin ver olarak uygulanan katmanları

### <a name="the-domain-model-layer"></a>Etki alanı modeli katmanı

Eric Evans'ın mükemmel kitap [etki alanı tabanlı tasarım](https://domainlanguage.com/ddd/) etki alanı modeli katmanı ve uygulama katmanı hakkında aşağıdaki söyler.

**Etki alanı modeli katmanı**: iş, iş durumu ve iş kuralları hakkında bilgi kavramlarını temsil eden sorumlu. İş durumu yansıtır durumu denetlenen ve onu Depolama Teknik Ayrıntılar için altyapı temsilci olsa bile burada kullanılır. İş yazılım Kalp katmanıdır.

Etki alanı modeli iş yeri ifade katmanıdır. Mikro hizmet etki alanı modeli katmanı .NET uyguladığınızda, o katmanın bir sınıf kitaplığı verilerin yanı sıra davranışları (yöntemleri mantığı ile) yakalama etki alanı varlıklarla olarak kodlanmıştır.

Aşağıdaki [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeleri, bu katman veri kalıcılığı ayrıntıları tamamen yoksay gerekir. Bu Kalıcılık görevleri altyapı katmanı tarafından gerçekleştirilmelidir. Bu nedenle, bu katman doğrudan bağımlılıklarını önemli bir kuralı, etki alanı modeli varlık sınıfları olması gerektiğini anlamına gelir altyapısı üzerinde almamalıdır [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Etki alanı varlıkları (örneğin, bir taban sınıftan türetilen) doğrudan bağımlılıkları tüm veri erişim altyapı çerçevesi Entity Framework veya NHibernate gibi olmalıdır. İdeal olarak, etki alanı varlıklarınızı öğesinden türetilen veya gerekir tüm altyapı çerçevesinde tanımlanan herhangi bir tür.

Böylece, etki alanı model sınıflarınızı altyapısına eşleşmiş değil Entity Framework Çekirdek gibi birçok modern ORM çerçeveler bu yaklaşım izin verir. Ancak, POCO varlıklar sahip her zaman belirli NoSQL veritabanları ve aktörler ve Azure Service Fabric güvenilir koleksiyonlarda gibi çerçeveleri kullanırken mümkün değildir.

Bile, etki alanı modeli Kalıcılık kullanmayan ilkesini izlemek önemli olduğu durumlarda, Kalıcılık sorunları göz ardı etmelidir değil. Hala fiziksel veri modeli ve nasıl varlık nesnesi modelinizi eşlendiğini anlamak çok önemlidir. Aksi takdirde imkansız tasarımı oluşturabilirsiniz.

Ayrıca, bu bir ilişkisel veritabanı için tasarlanmış bir modeli alabilir ve doğrudan taşımak için bir NoSQL veya belge yönelimli veritabanı anlamına gelmez. Bazı varlık modelleri model uygun, ancak genellikle yok. Hala varlık modeli, hem depolama teknolojisi ve ORM teknolojisi tabanlı uymalıdır kısıtlamaları vardır.

### <a name="the-application-layer"></a>Uygulama katmanı

Taşıma uygulama katmanına biz yeniden alınıyor Eric Evans'ın kitap [etki alanı tabanlı tasarım](https://domainlanguage.com/ddd/):

**Uygulama katmanı:** yazılım yapmak için olması ve sorunlarını çözmek için açıklayıcı bir etki alanı nesnelerini yönlendirir işleri tanımlar. Bu katman sorumlu olduğu görevleri iş anlamlı veya diğer sistemler uygulama katmanları ile etkileşim için gerekli. Bu katman ince tutulur. İş kurallarını veya bilgi içermiyor, ancak yalnızca koordinatları görevleri ve temsilciler için etki alanı nesnelerinin sonraki katmanı işbirliğini aşağı çalışır. İş durumu yansıtma durumu yok, ancak kullanıcı veya program için bir görev ilerlemesini gösteren durum olabilir.

.NET uygulama katmanında bir mikro 's genellikle bir ASP.NET çekirdek Web API projesi olarak kodlanmıştır. Proje mikro 's etkileşim, uzaktan ağ erişimi ve kullanıcı Arabirimi veya istemci uygulamalardan kullanılan dış Web API'leri uygular. Bir CQRS kullanarak yaklaşmak, mikro hizmet ve hatta olay denetimli arasındaki iletişimi mikro (tümleştirme olayları) tarafından kabul edilen komutlar sorguları içerir. Uygulama katmanı temsil eden ASP.NET çekirdek Web API iş kurallarını veya etki alanı bilgi (özellikle etki alanı için kuralları işlemleri veya güncelleştirmeler); içermemelidir. Bu etki alanı modeli sınıf kitaplığı tarafından sahibi olmalıdır. Uygulama katmanı olmalıdır yalnızca koordinat görevleri ve gerekir değil tutun veya herhangi bir etki alanı durumu (etki alanı modeli) tanımlayın. Sonuç olarak bu etki alanı varlıkların içinde verileri güncelleştirecek etki alanı modeli sınıflarını kendilerini (Birleşik kökleri ve etki alanı varlıkları), iş kurallarının yürütülmesi atar.

Temel olarak, uygulama mantığını burada verilen ön ucunda bağlı tüm kullanım durumları uygulamak olur. Örneğin, bir Web API hizmeti ile ilgili uygulaması.

Etki alanı modeli katmanı, kendi invariants, veri modeli ve ilgili iş kuralları etki alanı mantığı sunu ve uygulama katmanları tamamen bağımsız hedeftir. En önemlisi, etki alanı modeli katmanı doğrudan üzerinde herhangi bir altyapı framework bağımlı olmamalıdır.

### <a name="the-infrastructure-layer"></a>Altyapı katmanı

Başlangıçta (bellekte) etki alanı varlıklardaki tutulan verileri veritabanı veya başka bir kalıcı deposunda nasıl kalıcı altyapı katmanıdır. Bir örnek, ilişkisel bir veritabanındaki verilere kalıcı hale getirmek için bir DBContext kullanmak depo düzeni sınıflarını uygulamak için Entity Framework Çekirdek kodu kullanmaktır.

Yukarıda açıklanan uygun [Kalıcılık kullanmayan](http://deviq.com/persistence-ignorance/) ve [altyapı kullanmayan](https://ayende.com/blog/3137/infrastructure-ignorance) ilkeler, altyapı katmanı olmalıdır değil "zarar verme" etki alanı modeli katmanı. Sabit bağımlılıkları çerçevesinde gerçekleştirerek değil (EF veya diğer framework) verilerini sürdürülmesi için kullandığınız altyapısından etki alanı modeli varlık sınıfları belirsiz tutmanız gerekir. Etki alanı model katmanı sınıf kitaplığı yalnızca, etki alanı kodu yalnızca olması gerektiğini [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) varlık sınıfları yazılımınızı Kalp uygulama ve altyapı teknolojilerinden tamamen ayrılmış.

Bu nedenle, Katmanlar veya sınıf kitaplıkları ve projeleri sonuçta etki alanı modeli katmanda (kitaplık) bağımlı tersi geçerli değildir, Şekil 9-7'de gösterildiği gibi.

![](./media/image8.png)

**Şekil 9-7**. DDD Katmanlar arasındaki bağımlılıkları

Bu katman tasarım her mikro hizmet için bağımsız olması gerekir. Daha önce belirtildiği gibi en karmaşık mikro uygulayabileceğiniz DDD desenleri verilere daha basit uygulama çalışırken aşağıdaki mikro (tek bir katmanda basit CRUD) daha basit bir şekilde.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **DevIQ. Kalıcılık kullanmayan İlkesi**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini. Altyapı kullanmayan**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Melek Lopez. Etki alanı tabanlı tasarım katmanlı mimarisi**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Önceki] (cqrs-mikro hizmet-reads.md) [sonraki] (mikro hizmet-etki-model.md)
