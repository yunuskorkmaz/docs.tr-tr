---
title: Bir mikro hizmet etki alan modeli tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bir mikro hizmet etki alan modeli tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: 9a54679fc28bb2adf803a38fe5e43f67048a4cfd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048482"
---
# <a name="designing-a-microservice-domain-model"></a>Bir mikro hizmet etki alan modeli tasarlama

*Her bir iş mikro hizmet veya içerik sınırlanmış bir zengin etki alanı modeli tanımlayın*

Amacınız, her iş mikro hizmet ya da sınırlanmış bağlam (BC) için tek cohesive etki alanı modeli oluşturmaktır. Göz önünde tutun ancak bir BC veya iş mikro hizmet bazen hizmetlerden tek etki alanı modeli paylaşan birden fazla fiziksel oluşan. Etki alanı modeli, kuralları, davranışı, iş dil ve tek sınırlanmış bağlam veya temsil ettiği iş mikro hizmet kısıtlamaları yakalamalısınız.

## <a name="the-domain-entity-pattern"></a>Etki alanı varlığı deseni

Varlıklar etki alanı nesnelerini temsil eder ve öncelikle kendi kimlik, süreklilik ve Kalıcılık zaman içinde ve yalnızca bunları oluşturan öznitelikleri tarafından tanımlanır. Eric Evans yazılı olarak "öncelikle kendi kimliği tarafından tanımlanan bir nesne bir varlık olarak adlandırılır." Bir model için taban olduğundan varlıklar etki alanı modeli içinde çok önemlidir. Bu nedenle, tanımlamak ve dikkatlice tasarlayın.

*Bir varlığın kimliğini, birden çok mikro hizmette veya sınırlanmış Bağlamlar çapraz.*

Aynı kimliğe (değil aynı varlık rağmen) birden çok sınırlanmış Bağlamlar veya mikro hizmetler modellenir. Ancak, aynı özniteliklerle ve mantıksal aynı varlığın birden çok sınırlanmış bağlamlarda uygulanması anlamına gelmez. Bunun yerine, kendi öznitelikleri ve gerekli Bu davranış, sınırlanmış bağlamı'nın etki alanındaki her sınırlanmış bağlam varlıklarda sınırlayın.

Örneğin, alıcı varlık kimliği de dahil olmak üzere profil veya kimlik mikro hizmet, kullanıcı varlığında tanımlanan bir kişinin öznitelikleri çoğunu olabilir. Ancak yalnızca belirli alıcı veri sırası işlemle ilişkili olduğundan alıcı varlık sıralama mikro hizmet içinde daha az sayıda öznitelik olabilir. Her mikro Hizmet bağlamı veya içerik sınırlanmış kendi etki alanı modeli etkiler.

*Etki alanı varlıklarının yanı sıra veri öznitelikleri uygulama davranışını uygulamalıdır*

Bir etki alanı varlığı DDD, varlık verilerini (bellekte erişilen nesne) ilgili davranışı ve etki alanı mantığı uygulamalıdır. Örneğin, bir sipariş varlık sınıfı bir parçası olarak iş mantığı ve bir sipariş öğesi, verileri doğrulama ve toplam hesaplama ekleme gibi görevleri yöntemler olarak uygulanan işlemler olmalıdır. Varlığın metotları okuduğunuzda ve bu kurallar, uygulama katmanı arasında yaymak yerine varlık kurallar ilgileniriz.

Şekil 9-8, yalnızca veri öznitelikleri ancak işlemleri veya yöntemleriyle ilgili etki alanının mantığını uygulayan bir etki alanı varlığı gösterir.

![](./media/image9.png)

**Şekil 9-8**. Verilerin yanı sıra davranışı uygulayan bir etki alanı varlığı tasarım örneği

Elbette, bazen varlık sınıfı bir parçası olarak herhangi bir mantık uygulamaz varlıklar sahip olabilir. Alt varlık mantığı çoğunu tanımlı olduğundan toplama kök dizininde özel bir mantık yoksa bir toplama içinde alt varlıklar oluşabilir. Çok sayıda etki alanı varlıklarının yerine hizmet sınıflarını, uygulanan mantığı içeren karmaşık bir mikro hizmet varsa, aşağıdaki bölümde açıklanan anemic etki alanı modeline dönülüyor.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Zengin etki alanı modeli anemic etki alanı modeli karşılaştırması

Kendi gönderisinde [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler bu şekilde bir anemic etki alanı modeli açıklanmaktadır:

Temel Anemic bir etki alanı modeli blush en önce gerçek bir şey gibi görünüyor, belirtisidir. Nesneler, pek çok etki alanında isimleri sonra adlı ve bu nesneler zengin ilişkileri ve doğru etki alanı modelleri sahip yapısı ile bağlı. Yakalama davranışına arayın ve size gereken herhangi bir davranış bu nesneler üzerinde paketleri alıcılar ve ayarlayıcılar, biraz daha yönetilmelerini fark ettiniz gelir.

Bir anemic etki alanı modeli kullandığınız zaman, doğal olarak, bu veri modelleri hizmet nesneleri kümesinden kullanılacak (Geleneksel olarak adlandırılmış *iş katmanı*) tüm etki alanı veya iş mantığı yakalayın. İş katmanı, veri modelinde en üstünde yer alan ve veri modeline veri olarak kullanır.

Yalnızca bir yordam stil tasarımı anemic etki alanı modelidir. Bunlar davranışı (yöntem) bulunmadığından anemic varlık nesnesi gerçek nesneler değildir. Bunlar yalnızca veri özellikleri tutmak ve bu nedenle nesne yönelimli tasarım değildir. Tüm davranışı dışarı hizmet nesneleri (iş katmanı) koyarak temelde elde edersiniz [spaghetti kod](https://en.wikipedia.org/wiki/Spaghetti_code) veya [işlem betikleri](https://martinfowler.com/eaaCatalog/transactionScript.html), ve bu nedenle, avantajları, bir etki alanı modeli sağlar.

Fark etmeksizin, mikro hizmet veya içerik sınırlanmış çok basit olup olmadığını (bir CRUD hizmeti) veri özellikleri ile varlık nesnesi biçiminde anemic etki alanı modeli yeterince iyi ve daha karmaşık DDD desenlerini uygulamak değer olmayabilir. Bu durumda, yalnızca veri CRUD amacıyla sahip bir varlık kasıtlı olarak oluşturdunuz Kalıcılık modeli basitçe olmayacaktır.

Mikro hizmet mimarileri sınırlanmış her bağlam bağlı olarak çok mimari bir yaklaşım için mükemmel nedeni budur. Örneği için hizmetine, sıralama mikro hizmet DDD deseni uygular, ancak basit bir CRUD hizmet olan katalog mikro hizmet yok.

Bazı kişiler anemic etki alanı modeli önleyici bir düzeni olduğunu varsayalım. Bu, gerçekten ne uyguladığınız üzerinde bağlıdır. Oluşturmakta olduğunuz mikro hizmet ise önleyici bir desen değil anemic etki alanı modeli aşağıdaki basit yeterince (örneğin, bir CRUD hizmeti). Ancak, anemic etki alanı modeli durmaksızın değişen iş kuralları çok fazla olan bir mikro hizmet kişinin etki alanı karmaşıklığını gidermek gerekiyorsa, söz konusu mikro hizmet veya içerik sınırlanmış önleyici bir desen olabilir. Bu durumda, zengin tasarlarken verilerin yanı sıra ya da davranışı içeren yanı sıra ek DDD deseni (toplamalar, değer nesneleri, vb.) uygulama varlıkları modelde böyle bir mikro hizmet, uzun vadeli başarı için büyük avantajlar sahip olabilir.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **DevIQ. Etki alanı varlığı**
    [*https://deviq.com/entity/*](https://deviq.com/entity/)

-   **Martin Fowler. Etki alanı modeli**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. Anemic etki alanı modeli**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Değer nesnesinin düzeni

Eric Evans belirtildiği gibi "çok sayıda nesne kavramsal kimlik yok. Bu nesneler belirli bir şey özelliklerini açıklar."

Bir varlığın bir kimlik gerektirir, ancak bulunmayan bir sistemde birçok nesne yok değeri nesne düzeni ister. Bir değer nesnesi, bir etki alanı en boy açıklayan hiçbir kavramsal kimliği için kullanılan bir nesnedir. Bunlar yalnızca geçici olarak ilgili tasarım öğeleri göstermek için örneği nesnelerdir. Verdiğiniz *ne* bunlar değil, *kimin* oldukları. Örnekler, sayılar ve dizeler içerir, ancak öznitelik grupları gibi daha üst düzey kavramlarını da olabilir.

İkinci durumda, sınırlanmış bağlam farklı bir anlama sahip çünkü bir varlıkta bir mikro hizmet benzer başka bir mikro hizmet, bir varlıkta olmayabilir. Yalnızca öznitelikler, bir kişinin veya şirketin müşterinin profilinin bir grubu temsil edebilir beri gibi bir adresi bir e-ticaret uygulamasında bir kimlik hiç sahip olmayabilir. Bu durumda, bir değer nesnesi olarak adresi sınıflandırılmalıdır. Ancak, bir uygulamada bir enerjisi yardımcı şirket için müşteri adresi iş etki alanı için önemli olabilir. Bu nedenle, fatura sistemiyle adrese doğrudan bağlanabilir şekilde adresi bir kimlik olmalıdır. Bu durumda, bir adres bir etki alanı varlığı sınıflandırılmalıdır.

Bir ad ve Soyadı olan bir kişi genellikle bir varlık olan bir kişi adı ve Soyadı başka bir değer kümesiyle çakıştığı bile kimliği olduğundan, IF gibi bu adları da başvuruyor farklı bir kişiyle.

Değer belgede uygulamak ve kullanmak daha kolay oldukları veritabanlarına yönelik ancak ilişkisel veritabanı ve ORMs EF gibi yönetmek sabit nesnelerdir.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. Değer nesne düzeni**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Değer nesnesi**
    [*https://deviq.com/value-object/*](https://deviq.com/value-object/)

-   **Değer nesnelerini Test odaklı geliştirme**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi karmaşıklığı bağlayabileceğiniz.** (Kitap; değer nesneleri hakkında ayrıntılı bilgi içerir) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>Toplama düzeni

Bir etki alanı modeli farklı veri varlıkları ve sipariş işleminden veya sayım gibi işlevleri önemli bir bölümünü denetleyebilirsiniz işlemleri kümelerini içerir. Daha ayrıntılı DDD bir küme veya varlıkların birbirine bağlı bir birim olarak davranılıp davranışları ve grubu tanımlayan toplama birimidir.

İhtiyacınız olan işlemlerden yola çıkarak bir toplama genellikle tanımlarsınız. Klasik örnek sırası öğeleri listesini içeren bir sırasıdır. Sipariş öğesi, genellikle bir varlığın olacaktır. Ancak, sipariş varlığı genellikle bir toplama kök adı verilen kendi kök varlık olarak da içerecek sipariş toplama içinde bir alt varlık olacaktır.

Toplamlar belirlemek zor olabilir. Bir toplama birlikte tutarlı olması gereken nesneleri grubudur, ancak yalnızca bir grup seçin ve bunları bir toplama etiket. Bir etki alanı kavramı ile başlayın ve konusu kavrama ilgili en yaygın işlemlerde kullanılan varlıkları dikkat etmeniz gerekir. İşlemsel olarak tutarlı olması gereken bu ne toplama forms varlıklardır. İşlem işlemleri hakkında düşünmeye büyük olasılıkla toplamalar tanımlamak için en iyi yoludur.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Toplama kök veya kök varlık deseni

En az bir varlık bir toplama oluşur: toplama kök, kök varlık veya birincil varlık olarak da bilinir. Ayrıca, birden çok alt varlıklar ve tüm varlıklar ve gerekli davranışı ve işlemleri uygulamak için birlikte çalışan nesnelerin değeri nesneler olabilir.

Bir toplama kök amacı, toplamanın tutarlılık sağlamaktır; toplama yöntemleri aracılığıyla güncelleştirmeleri tek giriş noktası olmalıdır veya işlemleri ve toplam sınıfı kök. Yalnızca toplama kök aracılığıyla toplama varlıklarda değişiklik. Bu, tüm okuduğunuzda ve uymak için toplu halde ihtiyacınız olabilecek tutarlık kuralları dikkate alarak, toplam'ın tutarlılık koruyucu olur. Bir alt varlık veya değer nesnesi bağımsız olarak değiştirirseniz, toplama kök toplama işlevinde geçerli bir durumda olduğunu garanti edemez. Gevşek oluşturan içeren bir tablo gibi olacaktır. Tutarlılığı toplama kök ana amacı budur.

Şekil 9-9'da örnek toplamlar (toplam kök alıcı) tek bir varlık içeren alıcı toplama, gibi görebilirsiniz. Sipariş toplama, birden çok varlık ve bir değer nesnesini içerir.

![](./media/image10.png)

**Şekil 9-9**. Toplamalar birden çok örneği veya tek varlıklar

Sıralama mikro hizmetine başvuru uygulaması içinde çalıştığı gibi alıcı toplama etki alanınıza bağlı olarak ek alt varlıklar, olabilir unutmayın. Şekil 9-9, yalnızca alıcı tek bir varlık yalnızca bir toplama kök içeren bir toplama örneği bulunduğu bir durumu gösterir.

Toplamalarına ayrılığı koruma ve bunlar arasında NET sınırları tutmak için iyi bir uygulama içinde uygulandığı şekilde toplamlar ve yalnızca yabancı anahtar (FK) alanına sahip arasında doğrudan Gezinti izin vermeyecek şekilde DDD etki alanı modeli içinde olduğu [ Mikro hizmet etki alanı modeli sıralama](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) hizmetine. Siparişi varlığını yalnızca bir FK alan alıcı, ancak değil bir EF Core gezinti özelliği için aşağıdaki kodda gösterildiği gibi sahiptir:

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

Tanımlama ve toplamalar ile çalışma, araştırma ve deneyimi gerektirir. Daha fazla bilgi için aşağıdaki ek kaynaklar listesine bakın.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Vaughn Vernon. Etkili toplama tasarımı - bölümü ı: tek bir toplamada modelleme**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Etkili toplama tasarımı - Bölüm II: Birlikte yapma toplamalar çalışma**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf)

-   **Vaughn Vernon. Etkili toplama tasarımı - bölüm III: Öngörü elde aracılığıyla bulma**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf)

-   **Baş Grybniak. DDD Taktiksel tasarım desenleri**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Uludağ. Toplamlar kullanarak işlem mikro Hizmetleri Geliştirme**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. Toplama düzeni**
    [*https://deviq.com/aggregate-pattern/*](https://deviq.com/aggregate-pattern/)

>[!div class="step-by-step"]
[Önceki](ddd-oriented-microservice.md)
[İleri](net-core-microservice-domain-model.md)
