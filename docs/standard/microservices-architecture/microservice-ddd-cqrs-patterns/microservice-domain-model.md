---
title: Mikro hizmet etki alanı model tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet etki alanı model tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: 2776412b96d4ed141f48814d19d2deaa1a71520d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="designing-a-microservice-domain-model"></a>Mikro hizmet etki alanı model tasarlama

*Her iş mikro hizmet ya da ilişkisindeki bağlamı için bir zengin etki alanı modeli tanımlayın*

Amacınız, her iş mikro hizmet ya da ilişkisindeki bağlam (BC) için tek bağlı etki alanı modeli oluşturmaktır. Ancak bu unutmayın bir BC veya iş mikro hizmet bazen oluşan bir tek etki alanı modeli paylaşan birden fazla fiziksel Hizmetleri. Etki alanı modeli kuralları, davranışı, iş dili ve tek ilişkisindeki bağlamı veya temsil ettiği iş mikro hizmet kısıtlamaları yakalama gerekir.

## <a name="the-domain-entity-pattern"></a>Etki alanı varlığı düzeni

Varlıklar etki alanı nesnelerini temsil eder ve temelde yalnızca bunları oluşturan öznitelikleri ve bunların kimlik, sürekliliği ve zaman içinde Kalıcılık tarafından tanımlanır. Eric Evans diyor gibi "öncelikle kimliğini tarafından tanımlanan bir nesne bir varlık çağrılır." Bir model için temel olduğundan varlıklar etki alanı modelinde çok önemlidir. Bu nedenle, belirleyin ve dikkatli bir şekilde tasarlayın.

*Bir varlığın kimliğini birden fazla mikro veya sınırlanmış bağlamları çapraz.*

Aynı kimliğe (değil aynı varlık rağmen) birden çok ilişkisindeki bağlamları veya mikro modellenebilir. Ancak, aynı öznitelikleri ve mantığı ile aynı varlık birden çok ilişkisindeki bağlamlarda uygulanan anlamına gelmez. Bunun yerine, kendi öznitelikleri ve bu gerekli için davranışlar bu ilişkisindeki bağlamın etki alanındaki her ilişkisindeki bağlamındaki varlıkları sınırlayın.

Örneğin, alıcı varlık kimliğini de dahil olmak üzere profil veya kimlik mikro kullanıcı varlıkta tanımlanan bir kişinin öznitelikleri çoğunu olabilir. Ancak yalnızca belirli alıcı verileri sipariş işlemle ilişkili olduğundan alıcı varlıkta sıralama mikro hizmet daha az sayıda öznitelik olabilir. Her mikro Hizmet bağlamı veya sınırlanmış bağlamı kendi etki alanı modeli etkiler.

*Etki alanı varlıkları veri öznitelikleri uygulama yanı sıra davranışı uygulamalıdır*

Bir etki alanı varlığı GGG, etki alanı mantığı ya da varlık verilerini (bellekte erişilen nesne) ilgili davranışı uygulamalıdır. Örneğin, bir siparişi varlık sınıfı bir parçası olarak iş mantığı ve bir sipariş öğesi, veri doğrulama ve toplam hesaplaması ekleme gibi görevler için yöntemleri olarak uygulanan işlemler olmalıdır. Varlığın yöntemleri invariants ve uygulama katmanı yayılan bu kurallarına sahip yerine varlık kurallar dikkatli olun.

Şekil 9-8 yalnızca veri öznitelikleri ancak operations veya yöntemleri ile ilgili etki alanının mantığını uygulayan bir etki alanı varlığı gösterir.

![](./media/image9.png)

**Şekil 9-8**. Verilerin yanı sıra davranışı uygulama etki alanı varlığı tasarım örneği

Elbette, bazen varlık sınıfı bir parçası olarak herhangi bir mantık uygulamaz varlıklar sahip olabilir. Alt varlık mantığı çoğunu tanımlanmış çünkü toplama kök dizininde özel bir mantık yoksa bir toplama alt varlıkları oluşabilir. Çok sayıda etki alanı varlıkları yerine hizmet sınıflarını uygulanan mantığı içeren karmaşık bir mikro hizmet varsa, aşağıdaki bölümde açıklanan anemic etki alanı modeline dönmeden.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Zengin etki alanı modeli anemic etki alanı modeli karşılaştırması

Kendi postasında [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler bu şekilde bir anemic etki alanı modeli açıklanmaktadır:

Temel Anemic bir etki alanı modeli blush en önce gerçek bir şey gibi görünüyor, belirtisidir. Nesne, birçok etki alanı içinde isimleri sonra adlı ve bu nesneler zengin ilişkileri ve doğru etki alanı modelleri sahip yapısı ile bağlı. Yakalama davranış arayın ve, bu nesneler üzerinde tümcesi herhangi davranış olduğunu paketler alıcılar ve ayarlayıcılar, biraz daha yapmadan farkında olun gelir.

Bir anemic etki alanı modeli kullandığınızda, doğal olarak, bu veri modelleri hizmet nesneleri kümesinden kullanılacak (Geleneksel olarak adlandırılmış *iş katmanı*) tüm etki alanı veya iş mantığı yakalayın. İş katmanı veri modeli üstünde bulunur ve yalnızca veri veri modelini kullanır.

Yalnızca bir yordam stil tasarımı anemic etki alanı modelidir. Davranışları (yöntemleri) bulunmadığından anemic varlık nesnesi gerçek nesneler değildir. Bunlar yalnızca veri özellikleri basılı tutun ve böylece nesne odaklı tasarım değildir. Tüm davranışı out (iş katmanı) hizmeti nesnelerine koyarak, aslında şunun [spaghetti kod](https://en.wikipedia.org/wiki/Spaghetti_code) veya [işlem betikleri](https://martinfowler.com/eaaCatalog/transactionScript.html), ve bu nedenle, avantajları, kaybetmeniz etki alanı modeli sağlar.

Mikro hizmet veya sınırlanmış bağlam çok basit ise bakılmaksızın (bir CRUD hizmeti), yalnızca veri özellikleri varlık nesneleriyle biçiminde anemic etki alanı modeli yeterince iyi olabilir ve daha karmaşık DDD desenleri uygulama değerinde olmayabilir. Bu durumda, yalnızca verileri CRUD amacıyla sahip bir varlık bilerek oluşturdunuz çünkü Kalıcılık model yalnızca olacaktır.

Mikro mimarileri ilişkisindeki her bağlam bağlı olarak çok mimari bir yaklaşım için mükemmel bir nedeni budur. Örneğin, eShopOnContainers, sıralama mikro hizmet DDD desenleri uygular, ancak bir basit CRUD hizmetidir, katalog mikro hizmet yok.

Bazı kişiler anemic etki alanı modeli karşı bir düzeni olduğunu varsayalım. Gerçekten neler, uyguluyorsanız üzerinde bağlıdır. Oluşturmakta mikro hizmet ise bir koruma desen değil anemic etki alanı modeli izleyen basit yeterince (örneğin, bir CRUD hizmeti). Ancak, çok sayıda sürekli değişen iş kuralları olan bir mikro 's etki karmaşıklığını üstesinden gelmek gerekiyorsa, anemic etki alanı modeli mikro hizmet veya sınırlanmış bağlamı için bir koruma desen olabilir. Bu durumda, bir zengin tasarlama veri artı davranışı içeren yanı sıra ek DDD desenleri (toplamalar, değer nesneleri, vb.) uygulama varlıkları modeliyle böyle bir mikro hizmet uzun vadeli başarısı için çok büyük yararları olabilir.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **DevIQ. Etki alanı varlığı**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler. Etki alanı modeli**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. Anemic etki alanı modeli**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Değer nesnesi düzeni

Eric Evans belirtildiği gibi bu "çok sayıda nesne kavramsal kimliğe sahip değil. Bu nesneler belirli bir şey özelliklerini tanımlar."

Bir varlık Kimlikteki gerektiriyor, ancak bulunmayan bir sistemde birçok nesne yok değer nesnesi düzeni ister. Bir değer nesnesi, bir etki alanı en boy açıklar ve kavramsal bir kimliği olan bir nesnedir. Bu, yalnızca geçici olarak ilgilendiren tasarım öğeleri göstermek için örneği nesneleridir. İlgilendiğiniz *ne* bunlar değil, *kimin* oldukları. Örnekler sayılara hem de dizelere içerir, ancak özniteliklerin grupları gibi daha üst düzey kavramlarını da olabilir.

İkinci durumda, sınırlanmış bağlamı farklı bir anlama sahip çünkü bir mikro hizmet varlık benzer bir varlık başka bir mikro olmayabilir. Yalnızca bir grup kişi veya şirket için Müşteri'nin profili özniteliklerini temsil edebilir beri Örneğin, bir e-ticaret uygulamada bir adresi Kimlikteki hiç sahip olmayabilir. Bu durumda, adresi bir değer nesnesi sınıflandırılmış. Ancak, bir elektrik güç yardımcı şirket için bir uygulamada, müşteri adresi iş etki alanı için önemli olabilir. Bu nedenle, fatura sistemiyle adresine doğrudan bağlanabilir şekilde adresi bir kimlik olmalıdır. Bu durumda, bir adresi bir etki alanı varlığı sınıflandırılmış.

Bir ad ve Soyadı kişiyle genellikle bir varlıktır adı ve Soyadı başka bir değer kümesiyle çakıştığı olsa bile bir kişinin kimliğini olduğundan, eğer gibi bu adlar da başvuruyor farklı bir kişiye.

Değer belgede uygulamak ve kullanmak daha kolay veritabanlarına yönelik ancak ilişkisel veritabanları ve ORMs EF gibi yönetmek sabit nesneleridir.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. Değer nesnesi düzeni**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Değer nesnesi**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **Değer Test-Driven geliştirme nesneleri**
    [*https://leanpub.com/tdd-ebook/read\#leanpub otomatik değeri nesneleri*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling.** (Kitap; değer nesnelerini tartışması içerir) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>Toplama düzeni

Bir etki alanı modeli farklı veri varlıkları ve sipariş fulfilment veya envanter gibi işlevleri önemli bir bölümünü denetleyebilirsiniz işlemleri kümelerini içerir. Bir daha hassas DDD bir küme veya grup varlıkları ve bağlı bir birim olarak kabul davranışları açıklanmaktadır toplama birimdir.

Gereksinim duyduğunuz hareketlerini temel alarak bir toplama genellikle tanımlarsınız. Klasik bir örnek de sipariş öğelerinin bir listesini içeren bir sırasıdır. Bir sipariş öğesi, genellikle bir varlık olacaktır. Ancak bir alt varlık sipariş varlık genellikle bir toplama kök adı verilen kendi kök varlık olarak da içerecek sipariş toplama içinde görüntülenir.

Toplamalar tanımlayan zor olabilir. Bir toplama bir gruptur nesnelerin araya tutarlı olmalıdır, ancak yalnızca bir grup seçin olamaz ve bir toplama etiket. Bir etki alanı kavramı ile başlamalı ve konusu kavrama ilgili yaygın işlemlerde kullanılan varlıkları düşünün. İşlemsel olarak tutarlı olması gereken bu ne toplama forms varlıklardır. İşlem işlemleri hakkında düşünmeye büyük olasılıkla toplamalar tanımlamak için en iyi yoludur.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Birleşik kök veya kök varlık düzeni

Bir toplama en az bir varlık oluşur: Birleşik kök, kök varlık veya birincil varlık olarak da bilinir. Ayrıca, birden çok alt varlıkları ve tüm varlıkları ve gerekli davranışı ve işlemleri uygulamak üzere birlikte çalışan nesnelerle değeri nesneler olabilir.

Toplama tutarlılığını sağlamak için bir toplama kök amacı.; Yalnızca giriş noktası için toplama yöntemleri aracılığıyla güncelleştirmeleri olmalı veya işlemleri toplama sınıfı kök. Yalnızca toplama kök üzerinden toplama varlıkları değişiklik. Tüm invariants ve toplam olarak uymak için gerekebilecek tutarlık kuralları dikkate alarak toplama 's tutarlılık koruyucu olur. Alt varlık veya değer nesne bağımsız olarak değiştirirseniz, toplama kök toplama işlevinde geçerli bir durumda olduğundan emin olun olamaz. Gevşek bir bacağı içeren bir tablo gibi olacaktır. Bakımı tutarlılık toplama kök ana amacı budur.

Şekil 9-9'da, toplama, tek bir varlık (Birleşik kök alıcı) içeren alıcı gibi örnek toplamalar görebilirsiniz. Sipariş toplama birden çok varlık ve bir değer nesnesini içerir.

![](./media/image10.png)

**Şekil 9-9**. Toplamalar birden çok örneği ya da tek varlıklar

Sıralama mikro hizmet eShopOnContainers başvuru uygulamada içinde yaptığı gibi alıcı toplama etki alanınız bağlı olarak, ek alt varlıkları olabilir unutmayın. Şekil 9-9 yalnızca alıcı tek bir varlık birleşik bir kök içeren bir toplama örneği bulunduğu bir durumu gösterir.

Toplamlar ve yalnızca yabancı anahtar (FK) alanı sahip arasında doğrudan Gezinti içinde uygulandığı şekilde izin vermeyecek şekilde DDD etki alanı modeli iyi bir uygulama olmasından Toplamaların birbirinden ayırmaya ve bunlar arasında NET sınırları tutmak için [ Mikro hizmet etki alanı modeli sıralama](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) eShopOnContainers içinde. Sipariş varlığın yalnızca FK alan alıcı ancak olmayan bir EF çekirdek gezinti özelliği, aşağıdaki kodda gösterildiği gibi vardır:

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

Tanımlama ve toplamalar ile çalışma araştırma ve deneyimi gerektirir. Daha fazla bilgi için aşağıdaki ek kaynaklar listesine bakın.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Vaughn Vernon. Etkin Toplama tasarımı - bölümü I: tek bir toplama modelleme**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_TOPLULUK\_özellik\_TOPLAMALAR\_bölümü \_1. pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Etkin Toplama tasarımı - Bölüm II: Yapma toplamalar iş birlikte**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *

-   **Vaughn Vernon. Etkili toplama tasarım - bölüm III: Bulma aracılığıyla sağlamasını Insight**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *

-   **Sergey Grybniak. DDD Taktik tasarım desenleri**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Uludağ. İşlem mikro toplamalar kullanarak geliştirme**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. Toplama düzeni**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[Önceki] (bbb-yönelimli-microservice.md) [sonraki] (net-core-mikro hizmet-etki-model.md)
