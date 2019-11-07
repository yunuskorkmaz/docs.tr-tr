---
title: Mikro hizmet etki alan modeli tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD-yönelimli bir etki alanı modeli tasarlarken temel kavramları anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 3a02059064305ca148b7909923e2f51e60ee54d5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737466"
---
# <a name="design-a-microservice-domain-model"></a>Mikro hizmet etki alanı modeli tasarlama

*Her bir iş mikro hizmeti veya sınırlanmış bağlam için bir zengin etki alanı modeli tanımlayın.*

Amacınız, her bir iş mikro hizmeti veya sınırlı bağlam (BC) için tek bir ortak etki alanı modeli oluşturmaktır. Ancak, bir BC veya iş mikro hizmetinin bazen tek bir etki alanı modelini paylaşan birkaç fiziksel hizmetten oluşmayabileceğini aklınızda bulundurun. Etki alanı modeli, temsil edilen tek sınırlanmış bağlamın veya iş mikro hizmetinin kurallarını, davranışını, iş dilini ve kısıtlamalarını yakalamalıdır.

## <a name="the-domain-entity-pattern"></a>Etki alanı varlık deseninin

Varlıklar, etki alanı nesnelerini temsil eder ve öncelikle kimlik, sürekliliği ve zaman içinde kalıcı olarak tanımlanır ve yalnızca bunları oluşturan özniteliklere göre değil. Eric Evans olarak, "kimliği tarafından birincil olarak tanımlanan bir nesne bir varlık olarak adlandırılır." Varlıklar, bir modelin temeli olduklarından, etki alanı modelinde çok önemlidir. Bu nedenle, bunları dikkatle belirleyip tasarlamanız gerekir.

*Bir varlığın kimliği birden fazla mikro hizmet veya sınırlı bağlamlara çapraz olabilir.*

Aynı kimlik (diğer bir deyişle, aynı etki alanı varlığı olmasa da aynı `Id` değeri, birden çok sınırlanmış bağlam veya mikro hizmet arasında modellenebilir. Ancak, aynı özniteliğe ve mantığa sahip aynı varlığın birden çok sınırlanmış bağlamda uygulandığını göstermez. Bunun yerine, her sınırlı bağlamdaki varlıklar, özniteliklerini ve davranışlarını Bu sınırlanmış bağlamın etki alanında gerekli olanlarla sınırlar.

Örneğin, alıcı varlığı, kimlik dahil olmak üzere profil veya kimlik mikro hizmetindeki Kullanıcı varlığında tanımlanmış bir kişi özniteliklerinin çoğuna sahip olabilir. Ancak, yalnızca belirli alıcı verileri sipariş sürecleriyle ilişkili olduğundan sıralama mikro hizmetindeki alıcı varlığı daha az özniteliğe sahip olabilir. Her mikro hizmet veya sınırlı bağlamın bağlamı, etki alanı modelini etkiler.

*Etki alanı varlıklarının, veri özniteliklerini uygulamaya ek olarak davranış uygulaması gerekir.*

DDD alanındaki bir etki alanı varlığı, varlık verileriyle ilgili etki alanı mantığını veya davranışını uygulamalıdır (bellekte erişilen nesne). Örneğin, bir sipariş varlığı sınıfının bir parçası olarak, bir sipariş öğesi, veri doğrulama ve toplam hesaplama gibi görevler için yöntemler olarak uygulanan iş mantığı ve işlemler olmalıdır. Varlığın yöntemleri, bu kuralların uygulama katmanında yayılmasını yerine varlığın ıntürevlerini ve kurallarını ele alır.

Şekil 7-8, yalnızca veri öznitelikleri değil, işlemler veya ilgili etki alanı mantığına sahip Yöntemler uygulayan bir etki alanı varlığını gösterir.

![Bir etki alanı varlığının deseninin gösterildiği diyagram.](./media/microservice-domain-model/domain-entity-pattern.png)

**Şekil 7-8**. Veri ve davranış uygulayan bir etki alanı varlığı tasarımı örneği

Bir etki alanı modeli varlığı, davranışları yöntemler aracılığıyla uygular, yani bir "anemik" modeli değildir. Kuşkusuz, bazen varlık sınıfının bir parçası olarak herhangi bir mantık uygulamayan varlıklara sahip olabilirsiniz. Bu, bir toplama içindeki alt varlıklarda, mantığın büyük çoğunluğu toplam kökte tanımlanmış olduğu için özel bir mantık yoksa meydana gelebilir. Etki alanı varlıkları yerine hizmet sınıflarında çok fazla mantığı uygulanmış karmaşık bir mikro hizmetiniz varsa, aşağıdaki bölümde açıklanan anemik etki alanı modeline düşeceksiniz.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Zengin etki alanı modeline karşı, anemik etki alanı modeli

Post [Anemicdomainmodel](https://martinfowler.com/bliki/AnemicDomainModel.html)içinde, Marwler bu şekilde bir anemik etki alanı modeli tanımlar:

Anemik etki alanı modelinin temel belirtisi, ilk lavanta 'de gerçek bir şey gibi görünüyor. Etki alanı alanındaki isimler sonrasında birçok adlandırılmış nesne vardır ve bu nesneler, doğru etki alanı modellerinin sahip olduğu zengin ilişkilerle ve yapıyla bağlanır. Bu, davranışa baktığınızda ve bu nesneler üzerinde herhangi bir davranışın sağlam olduğunu fark etmekle birlikte, daha fazla sayıda

Tabii ki, bir anemik etki alanı modeli kullandığınızda, bu veri modelleri, tüm etki alanı veya iş mantığını yakalayan bir hizmet nesneleri kümesinden (geleneksel olarak *iş katmanı*olarak adlandırılır) kullanılacaktır. İş katmanı, veri modeli üzerinde bulunur ve veri modelini yalnızca veri olarak kullanır.

Anemik etki alanı modeli yalnızca bir yordamsal stil tasarımdır. Anemik varlık nesneleri, davranış yetersizliğinden (metotlar) gerçek nesneler değildir. Yalnızca veri özelliklerini tutar ve bu nedenle nesne odaklı tasarım değildir. Tüm davranışı, aslında [spaghfeti kodu](https://en.wikipedia.org/wiki/Spaghetti_code) veya [işlem betikleri](https://martinfowler.com/eaaCatalog/transactionScript.html)ile sona erdirmek için, bir etki alanı modelinin sağladığı avantajları kaybedersiniz.

Mikro hizmetiniz veya sınırlı Içeriğiniz çok basittir (bir CRUD hizmeti), yalnızca veri özelliklerine sahip varlık nesneleri biçimindeki anemik etki alanı modeli yeterince iyi olabilir ve bu da daha karmaşık DDD desenlerinin uygulanması için değer olmayabilir. Bu durumda, özellikle CRUD amacıyla yalnızca verileri olan bir varlık oluşturmuş olduğunuzdan, tek bir Kalıcılık modeli olacaktır.

Mikro hizmet mimarilerinin her sınırlanmış Içeriğe bağlı olarak çok mimarili bir yaklaşım için mükemmel olmasının nedeni budur. Örneğin, eShopOnContainers 'da, sıralama mikro hizmeti DDD desenlerini uygular, ancak basit bir CRUD hizmeti olan Katalog mikro hizmeti desteklemez.

Bazı kişiler, anemik etki alanı modelinin bir anti-model olduğunu söylüyor. Bu, sizin uygulamadığınıza bağlıdır. Oluşturmakta olduğunuz mikro hizmet yeterince basittir (örneğin, bir CRUD hizmeti), anemik etki alanı modelini izleyerek bir anti-model değildir. Ancak, çok sayıda sürekli değişen iş kuralına sahip bir mikro hizmet etki alanının karmaşıklığının üstesinden gelmeniz gerekiyorsa, anemik etki alanı modeli söz konusu mikro hizmet veya sınırlanmış bağlam için bir anti-model olabilir. Bu durumda, veri ve davranış içeren varlıklar içeren zengin bir model olarak tasarlamak ve ek DDD desenleri (toplamalar, değer nesneleri vb.) uygulamak, bu tür bir mikro hizmetin uzun süreli başarısı için büyük avantajlardan yararlanmaktadır.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Sapq. Etki alanı varlığı** \
  <https://deviq.com/entity/>

- **Marwler. Etki alanı modeli** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Marwler. Anemik etki alanı modeli** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Değer nesne deseninin

Eric Evans, "birçok nesnenin kavramsal kimliği yoktur. Bu nesneler bir şeyi belirli özelliklerini anlatmaktadır. "

Bir varlık bir kimlik gerektirir, ancak bir sistemde, değer nesne düzeniyle benzer birçok nesne vardır. Değer nesnesi, bir etki alanı alanını açıklayan kavramsal kimlik olmayan bir nesnedir. Bunlar, yalnızca geçici olarak sizi ilgilendiren tasarım öğelerini göstermek için örneğini oluşturduğunuz nesnelerdir. Ne olduklarını, *kim* olduğunu değil, bunların *ne* olduğunu size özen gösterin. Sayılar ve dizeler verilebilir, ancak öznitelik grupları gibi daha üst düzey kavramlar da olabilir.

Mikro hizmetteki bir varlık başka bir mikro hizmette varlık olmayabilir, çünkü ikinci durumda, sınırlanmış bağlamın farklı bir anlamı olabilir. Örneğin, bir e-ticaret uygulamasındaki bir adresin hiç bir kimliği olmayabilir, çünkü yalnızca bir kişi veya şirket için müşterinin profilinin bir öznitelik grubunu temsil edebilir. Bu durumda, adres bir değer nesnesi olarak sınıflandırılmalıdır. Ancak, elektrik güç yardımcı programı şirketi için bir uygulamada, müşteri adresi iş etki alanı için önemli olabilir. Bu nedenle, fatura sisteminin doğrudan adresle bağlantılı olması için adreste bir kimlik olması gerekir. Bu durumda, bir adres bir etki alanı varlığı olarak sınıflandırılmalıdır.

Adı ve soyadı olan bir kişi genellikle bir varlıktır, çünkü ad ve soyadı başka bir değer kümesiyle aynı olsa da, bu adlar farklı bir kişiye başvuruyor olabilir.

Değer nesneleri, ilişkisel veritabanlarında ve ORMs 'nin aynı şekilde yönetilmesi zor olduğundan, belge odaklı veritabanlarında uygulama ve kullanım daha kolay olur.

EF Core 2,0, daha sonra ayrıntılı olarak göreceğiniz için değer nesnelerinin daha kolay işlemesini sağlayan [varlık](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) özelliğini içerir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Marwler. Değer nesne deseninin** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Değer nesnesi** \
  <https://deviq.com/value-object/>

- **Test odaklı geliştirme \ değer nesneleri**
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Etki alanı odaklı tasarım: yazılım Kalbunda karmaşıklık karmaşıklığı.** (Kitap; değer nesnelerinin bir tartışmasını içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Toplam model

Bir etki alanı modeli, sipariş tamamlama veya stok gibi önemli bir işlev alanını denetleyebilmek için farklı veri varlıklarının ve işlemlerin kümelerini içerir. Daha hassas bir birim birimi, bir küme veya bir varlık grubunu ve bir arada bulunan bir birim olarak kabul edilebilir davranışları tanımlayan topladır.

Genellikle ihtiyacınız olan işlemlere göre bir toplama tanımlarsınız. Klasik bir örnek, sipariş öğelerinin bir listesini de içeren bir sıradır. Bir sipariş öğesi genellikle bir varlık olur. Ancak, sıra toplama içinde bir alt varlık olur ve bu da, genellikle toplam kök olarak adlandırılan kök varlık olarak sıra varlığını içerir.

Toplamaları tanımlama zor olabilir. Toplama, birlikte tutarlı olması gereken bir nesne grubudur, ancak bir nesne grubunu seçip bunları bir toplama etiketlenemez. Bir etki alanı kavramıyla başlamalı ve bu kavram ile ilgili en yaygın işlemlerde kullanılan varlıkları düşünmeniz gerekir. İşlemsel olarak tutarlı olması gereken varlıklar, bir toplama oluşturan şeydir. İşlem işlemleri hakkında düşünce, büyük olasılıkla toplamaları belirlemenin en iyi yoludur.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Toplam kök veya kök varlık deseninin

Toplama, en az bir varlıktan oluşur: kök varlık veya birincil varlık olarak da adlandırılan toplam kök. Ayrıca, gerekli davranış ve işlemleri uygulamak için birlikte çalışan tüm varlıklar ve nesneler ile birden çok alt varlık ve değer nesnesi olabilir.

Toplama kökünün amacı, toplamanın tutarlılığını sağlamaktır; Toplam kök sınıfında Yöntemler veya işlemler aracılığıyla toplanacak güncelleştirmelerin tek giriş noktası olması gerekir. Toplama içindeki varlıklarda yalnızca toplama köküyle değişiklik yapmanız gerekir. Toplamanız için gerekli olan tüm ınvaryantlar ve tutarlılık kurallarını dikkate alarak, toplamanın tutarlılık koruyucusu vardır. Bir alt varlık veya değer nesnesini bağımsız olarak değiştirirseniz, toplam kök, toplamanın geçerli bir durumda olduğundan emin olamaz. Bu, boştaki bir baya sahip bir tablo gibi olacaktır. Tutarlılığı korumak, toplam kökünün ana amacı olur.

Şekil 7-9 ' de, tek bir varlık (Toplam kök alıcı) içeren alıcı toplaması gibi örnek toplamalar görebilirsiniz. Sıra toplaması birden çok varlık ve bir değer nesnesi içerir.

![Bir alıcı toplamasını ve bir sıra toplamasını karşılaştıran diyagram.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Şekil 7-9**. Birden çok veya tek varlık içeren toplamalar örneği

DDD etki alanı modeli toplamalarda oluşur, bir toplama yalnızca bir varlık veya daha fazla olabilir ve değer nesneleri de içerebilir. Alıcı toplamanın, etki alanına bağlı olarak, eShopOnContainers başvuru uygulamasındaki mikro hizmette sıralama yaptığı gibi ek alt varlıklara sahip olabileceğini unutmayın. Şekil 7-9 yalnızca Birleşik bir kök içeren bir toplama örneği olarak, alıcının tek bir varlığa sahip olduğu bir durumu gösterir.

Toplamaların ayrılmasını sürdürmek ve aralarında Temizleme sınırları tutmak için, bir DDD etki alanı modelinde, toplamalar arasında doğrudan gezinmeye izin vermemek ve sıralamada uygulandığı gibi yalnızca yabancı anahtar (FK) alanına sahip olmak için iyi bir uygulamadır [ eShopOnContainers içindeki mikro hizmet etki alanı modeli](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) . Sipariş varlığı, alıcı için yalnızca bir FK alanına sahiptir, ancak aşağıdaki kodda gösterildiği gibi EF Core gezinti özelliği değildir:

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

Toplamaları tanımlama ve bunlarla çalışma için araştırma ve deneyim gerekir. Daha fazla bilgi için aşağıdaki ek kaynaklar listesine bakın.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Vaughn versuz. Geçerli toplama tasarımı-Bölüm ı: tek bir toplama modelleme** (<http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn versuz. Geçerli toplama tasarımı-Bölüm II: toplamalar birlikte çalışır hale getirme** (<http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn versuz. Etkili toplu tasarım-Bölüm III: bulma yoluyla öngörü elde etme** (<http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergey Gryıbniak. DDD Politiktasarım desenleri** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Toplamaları kullanarak Işlem mikro hizmetleri geliştirme** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **Sapq. Toplam model** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Önceki](ddd-oriented-microservice.md)
>[İleri](net-core-microservice-domain-model.md)
