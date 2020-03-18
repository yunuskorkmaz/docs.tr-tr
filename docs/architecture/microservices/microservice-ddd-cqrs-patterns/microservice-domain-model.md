---
title: Mikro hizmet etki alan modeli tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD yönelimli etki alanı modeli tasarlarken temel kavramları anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: 628fb5c76362ec8f48367b3d69d16ea6ebd24f09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502328"
---
# <a name="design-a-microservice-domain-model"></a>Microservice etki alanı modeli tasarla

*Her iş microservice veya Sınırlı Bağlam için bir zengin etki alanı modeli tanımlayın.*

Amacınız, her iş microservice veya Bounded Context (BC) için tek bir uyumlu etki alanı modeli oluşturmaktır. Ancak, bir BC veya iş microservice bazen tek bir etki alanı modeli paylaşan birkaç fiziksel hizmetlerden oluşabileceğini unutmayın. Etki alanı modeli, temsil ettiği tek Sınırlı Bağlam'ın veya iş mikro hizmetinin kurallarını, davranışını, iş dilini ve kısıtlamalarını yakalamalıdır.

## <a name="the-domain-entity-pattern"></a>Etki Alanı Varlık deseni

Varlıklar etki alanı nesnelerini temsil eder ve öncelikle kimlikleri, süreklilikleri ve zaman içinde kalıcılıkları ile tanımlanırlar ve yalnızca onları oluşturan özniteliklerle değil. Eric Evans'ın dediği gibi, "öncelikle kimliğiyle tanımlanan bir nesneye Varlık denir." Varlıklar etki alanı modelinde çok önemlidir, çünkü bir modelin temelini onlardır. Bu nedenle, bunları dikkatle tanımlamalı ve tasarlamanız gerekir.

*Bir varlığın kimliği birden çok mikro hizmeti veya Sınırlı Bağlamları geçebilir.*

Aynı kimlik (yani aynı `Id` değer, belki aynı etki alanı varlığı olmasa da) birden çok Bağlı Bağlamveya mikro hizmetler arasında modellenebilir. Ancak, bu aynı varlık, aynı öznitelikleri ve mantığı ile birden çok Bağlı Bağlamlarda uygulanacağı anlamına gelmez. Bunun yerine, her Bağlı Bağlam'daki varlıklar özniteliklerini ve davranışlarını bu Bağlı Bağlam'ın etki alanında gerekli olanlarla sınırlandırın.

Örneğin, alıcı varlık, kimlik de dahil olmak üzere profil veya kimlik mikrohizmetinde kullanıcı varlığında tanımlanan bir kişinin özniteliklerinin çoğuna sahip olabilir. Ancak, yalnızca belirli alıcı verileri sipariş işlemiyle ilgili olduğundan, sipariş mikrohizmetindeki alıcı varlığı daha az özniteliklere sahip olabilir. Her microservice veya Bounded Context bağlamı etki alanı modelini etkiler.

*Etki alanı varlıkları, veri özniteliklerini uygulamaya ek olarak davranışı uygulamalıdır.*

DDD'deki bir etki alanı varlığı, varlık verileriyle (bellekte erişilen nesne) etki alanı mantığını veya davranışını uygulamalıdır. Örneğin, bir sipariş varlık sınıfının bir parçası olarak, sipariş öğesi, veri doğrulaması ve toplam hesaplama ekleme gibi görevler için yöntem olarak uygulanan iş mantığı ve işlemleri olmalıdır. Varlığın yöntemleri, bu kuralların uygulama katmanına yayılması yerine varlığın değişmezleri ve kurallarıyla ilgilenir.

Şekil 7-8, yalnızca veri özniteliklerini değil, ilgili etki alanı mantığına sahip işlemleri veya yöntemleri uygulayan bir etki alanı varlığını gösterir.

![Etki Alanı Varlığı deseni gösteren diyagram.](./media/microservice-domain-model/domain-entity-pattern.png)

**Şekil 7-8**. Veri artı davranışı uygulayan bir etki alanı varlık tasarımı örneği

Etki alanı modeli varlık yöntemleri ile davranışları uygular, yani bir "anemik" model değil. Tabii ki, bazen varlık sınıfının bir parçası olarak herhangi bir mantık uygulamayan varlıklar olabilir. Mantığın çoğu toplam kökünde tanımlandığı için, alt varlığın özel bir mantığı yoksa, bu durum bir toplam içindeki alt varlıklarda gerçekleşebilir. Etki alanı varlıkları yerine hizmet sınıflarında uygulanan çok fazla mantığa sahip karmaşık bir mikro hizmetiniz varsa, aşağıdaki bölümde açıklanan anemik etki alanı modeline düşebilirsiniz.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Anemik etki alanı modeline karşı zengin etki alanı modeli

Onun sonrası [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)olarak, Martin Fowler bu şekilde bir anemik etki alanı modeli açıklar:

Bir Anemik Etki Alanı Modeli temel belirtisi ilk allık gerçek bir şey gibi görünüyor olmasıdır. Birçok nesne, etki alanı içinde isimler sonra adlandırılmış ve bu nesnelerin zengin ilişkiler ve gerçek etki alanı modelleri sahip yapısı ile bağlı. Bu davranışa baktığınızda, ve bu nesnelerde neredeyse hiç davranış olmadığını fark ettiğinizde, onları buli ve ayarlayıcı torbalarından biraz daha fazlası haline getirirsiniz.

Tabii ki, bir anemik etki alanı modeli kullandığınızda, bu veri modelleri tüm etki alanı veya iş mantığı yakalamak hizmet nesneleri kümesi (geleneksel olarak adlandırılan *iş katmanı)* kullanılacaktır. İş katmanı veri modelinin üstüne oturur ve veri modelini veri gibi kullanır.

Anemik etki alanı modeli sadece bir prosedür tarzı tasarımdır. Anemik varlık nesneleri, davranış (yöntem) eksikliği nden dolayı gerçek nesneler değildir. Bunlar yalnızca veri özelliklerine sahiptir ve bu nedenle nesne yönelimli tasarım değildir. Tüm davranışları hizmet nesnelerine (iş katmanına) koyarak aslında [spagetti kodu](https://en.wikipedia.org/wiki/Spaghetti_code) veya [işlem komut dosyalarıyla](https://martinfowler.com/eaaCatalog/transactionScript.html)sonuçlanır ve bu nedenle etki alanı modelinin sağladığı avantajları kaybedersiniz.

Ne olursa olsun, microservice veya Bounded Context çok basit (CRUD hizmeti), sadece veri özellikleri ile varlık nesneleri şeklinde anemik etki alanı modeli yeterince iyi olabilir ve daha karmaşık DDD desenleri uygulamaya değer olmayabilir. Bu durumda, kasıtlı olarak CRUD amaçları için yalnızca veri içeren bir varlık oluşturduğunuziçin, bu yalnızca bir kalıcılık modeli olacaktır.

Bu nedenle mikrohizmet mimarileri, her Sınırlı İçerime bağlı olarak çok mimari bir yaklaşım için mükemmeldir. Örneğin, eShopOnContainers, sipariş microservice DDD desenleri uygular, ancak basit bir CRUD hizmeti olan katalog microservice, değil.

Bazı insanlar anemik etki alanı modeli bir anti-desen olduğunu söylüyorlar. Gerçekten ne uyguladığınıza bağlıdır. Oluşturduğunuz microservice yeterince basit ise (örneğin, bir CRUD hizmeti), anemik etki alanı modelini takip bir anti-desen değildir. Ancak, sürekli değişen iş kuralları bir yeri olan bir microservice etki alanı karmaşıklığı mücadele etmek gerekiyorsa, anemik etki alanı modeli bu microservice veya Bounded Context için bir anti-desen olabilir. Bu durumda, veri artı davranış içeren varlıklar ile zengin bir model olarak tasarlanması yanı sıra ek DDD desenleri (agregalar, değer nesneleri, vb) uygulanması gibi bir mikrohizmetin uzun vadeli başarısı için büyük faydalar olabilir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **DevIQ mı? Etki Alanı Varlığı** \
  <https://deviq.com/entity/>

- **Martin Fowler' ı. Etki Alanı Modeli** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowler' ı. Anemik Etki Alanı Modeli** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Değer Nesnesi deseni

Eric Evans'ın belirttiği gibi, "Birçok nesne kavramsal bir kimliğe sahip değildir. Bu nesneler bir şeyin belirli özelliklerini tanımlar."

Bir varlık bir kimlik gerektirir, ancak değer nesnesi deseni gibi bir sistemde olmayan birçok nesne vardır. Değer nesnesi, etki alanı yönünü açıklayan kavramsal kimliği olmayan bir nesnedir. Bunlar, yalnızca sizi geçici olarak ilgilendiren tasarım öğelerini temsil etmek için anlık olarak yaptığınız nesnelerdir. *Ne* olduklarını önemsiyorsun, *kim* olduklarını değil. Örnekler sayılar ve dizeleri içerir, ancak öznitelik grupları gibi üst düzey kavramlar da olabilir.

Bir mikro hizmetteki bir varlık başka bir microservice'teki bir varlık olmayabilir, çünkü ikinci durumda, Bağlı Bağlam farklı bir anlama sahip olabilir. Örneğin, bir e-ticaret uygulamasındaki bir adresin kimliği hiç olmayabilir, çünkü yalnızca bir kişi veya şirket için müşterinin profilinin öznitelikleri grubunu temsil edebilir. Bu durumda, adres bir değer nesnesi olarak sınıflandırılmalıdır. Ancak, bir elektrik elektrik şirketi için bir uygulamada, müşteri adresi iş etki alanı için önemli olabilir. Bu nedenle, faturalandırma sisteminin doğrudan adrese bağlanabilmesi için adresin bir kimliği olmalıdır. Bu durumda, bir adres etki alanı varlığı olarak sınıflandırılmalıdır.

Ad ve soyad taşıyan bir kişi, ad ve soyad başka bir değer kümesiyle çakışsa bile, bu ad ve soyadı farklı bir kişi için de atıfta bulunuyorsa, bir kişinin kimliği olduğundan genellikle bir varlıktır.

Değer nesnelerinin varlık çerçevesi (EF) gibi ilişkisel veritabanlarında ve ORM'larda yönetilmesi zorken, belge yönelimli veritabanlarında uygulanması ve kullanılması daha kolaydır.

EF Core 2.0 ve sonraki sürümler, daha sonra ayrıntılı olarak göreceğimiz gibi değer nesnelerinin işlemesini kolaylaştıran [Sahip olunan Varlıklar](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) özelliğini içerir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler' ı. Değer Nesnesi deseni** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Değer Nesnesi** \
  <https://deviq.com/value-object/>

- **Test Odaklı Geliştirmede Değer Nesneleri** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde Karmaşıklıkla Mücadele.** (Kitap; değer nesnelerinin bir tartışma içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Agrega deseni

Etki alanı modeli, sipariş yerine getirme veya envanter gibi önemli bir işlevsellik alanını denetlenebilen farklı veri varlıkları ve işlem kümeleri içerir. Daha ince taneli DDD birimi, bir kümeyi veya karma birim olarak kabul edilebilen varlık ve davranış grubunu açıklayan toplamdır.

Genellikle gereksinim duyduğunuz hareketleri temel alan bir toplam tanımlarsınız. Klasik bir örnek, sipariş öğelerinin listesini de içeren bir sipariştir. Bir sipariş öğesi genellikle bir varlık olacaktır. Ancak, genellikle toplu kök olarak adlandırılan, kök varlığı olarak sipariş varlığını da içerecek olan sipariş toplamı içinde bir alt varlık olacaktır.

Agregaları tanımlamak zor olabilir. Toplam, birlikte tutarlı olması gereken bir nesne grubudur, ancak bir nesne grubunu seçip bunları bir toplu olarak etiketleyemezsiniz. Bir etki alanı kavramıyla başlamalı ve bu kavramla ilgili en yaygın işlemlerde kullanılan varlıkları düşünmelisiniz. İşlemsel olarak tutarlı olması gereken varlıklar, bir toplamı oluşturan varlıklardır. İşlem işlemleri hakkında düşünme, muhtemelen toplamları tanımlamanın en iyi yoludur.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Toplam Kök veya Kök Varlık deseni

Bir toplam en az bir varlıktan oluşur: kök varlık veya birincil varlık olarak da adlandırılan toplam kök. Ayrıca, gerekli davranış ve hareketleri uygulamak için tüm varlıklar ve nesneler birlikte çalışan birden çok alt varlıklar ve değer nesneleri olabilir.

Bir toplam kökün amacı, agreganın tutarlılığını sağlamaktır; bu toplam kök sınıfında yöntemler veya işlemler yoluyla toplam güncelleştirmeleri için tek giriş noktası olmalıdır. Yalnızca toplam kökü üzerinden toplam içindeki varlıklarda değişiklik yapmalısınız. Toplu olarak uymanız gerekebilecek tüm değişmezleri ve tutarlılık kurallarını göz önünde bulundurarak, toplamın tutarlılık koruyucusudur. Bir alt varlığı veya değer nesnesini bağımsız olarak değiştirirseniz, toplam kök, toplamın geçerli bir durumda olduğundan emin olamaz. Gevşek bacaklı bir masa gibi olurdu. Tutarlılığı korumak, toplam kökün temel amacıdır.

Şekil 7-9'da, tek bir varlık (toplam kök Alıcı) içeren alıcı toplamı gibi örnek agregaları görebilirsiniz. Sipariş toplamı birden çok varlık ve bir değer nesnesi içerir.

![Alıcı toplamı ve sipariş toplamına karşılaştırıldığında diyagram.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Şekil 7-9**. Birden fazla veya tek tüzel kişilikli agrega örneği

Bir DDD etki alanı modeli agregalardan oluşur, bir agrega yalnızca bir varlık veya daha fazla olabilir ve değer nesneleri de içerebilir. EShopOnContainers başvuru uygulamasında sipariş mikroservice yaptığı gibi Alıcı toplu, etki alanıbağlı olarak ek alt varlıklar olabilir unutmayın. Şekil 7-9 yalnızca toplam kök içeren bir toplam örneği olarak, alıcının tek bir varlığa sahip olduğu bir durumu göstermektedir.

Agregaların ayrılığını korumak ve aralarındaki sınırları korumak için, ddd etki alanı modelinde, agregalar arasında doğrudan gezinmeye izin vermemek ve eShopOnContainers'daki [Sipariş mikrohizmet etki alanı modelinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) uygulandığı gibi yalnızca yabancı anahtar (FK) alanına sahip olmak iyi bir uygulamadır. Sipariş varlığı yalnızca alıcı için bir FK alanına sahiptir, ancak aşağıdaki kodda gösterildiği gibi bir EF Core navigasyon özelliği ne değildir:

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

Agregaların tanımlanması ve çalışılması araştırma ve deneyim gerektirir. Daha fazla bilgi için aşağıdaki Ek kaynaklar listesine bakın.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Vaughn Vernon' u. Etkili Agrega Tasarımı - Bölüm I: Tek Bir Agreganın Modelleilmesi** (from) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon' u. Etkili Agrega Tasarımı - Bölüm II: Agregaların Birlikte Çalışmasını Sağlama** (from) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon' u. Etkili Toplam Tasarım - Bölüm III: Discovery through Insight Kazanma** (dan) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergey Grybniak. DDD Taktik Tasarım Desenleri** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson' ı. Agregaları Kullanarak İşlemsel Mikro Hizmetler Geliştirme** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ mı? Agrega deseni** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Önceki](ddd-oriented-microservice.md)
>[Sonraki](net-core-microservice-domain-model.md)
