---
title: Değer nesneleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Yeni Entity Framework özelliklerini kullanarak değer nesneleri uygulamak için Ayrıntılar ve seçeneklere ulaşın.
ms.date: 08/21/2020
ms.openlocfilehash: 1cb7ce04b3ab2f6da25f398e016baf60b863fb6b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169212"
---
# <a name="implement-value-objects"></a>Değer nesneleri uygulama

Varlıklar ve toplamalar hakkında daha önceki bölümlerde açıklandığı gibi, varlıklar için de kimlik temel alınmıştır. Ancak, bir sistemde, değer nesneleri gibi kimlik ve kimlik izleme gerektirmeyen birçok nesne ve veri öğesi vardır.

Bir değer nesnesi, diğer varlıklara başvurabilir. Örneğin, bir noktadan diğerine nasıl alınacağını açıklayan bir yol oluşturan bir uygulamada, bu yol bir değer nesnesi olur. Bu, belirli bir rotadaki noktaların anlık görüntüsü olacaktır, ancak bu önerilen yolun, dahili olarak şehir, yol vb. varlıklara başvurabileceği bir kimliğe sahip olmaması gerekir.

Şekil 7-13, düzen toplama içindeki adres değeri nesnesini gösterir.

![Düzen toplama içindeki adres değeri-nesnesi gösteren diyagram.](./media/implement-value-objects/value-object-within-aggregate.png)

**Şekil 7-13**. Sıra toplaması içindeki adres değeri nesnesi

Şekil 7-13 ' de gösterildiği gibi, bir varlık genellikle birden çok öznitelikten oluşur. Örneğin, `Order` varlık kimliği olan bir varlık olarak modellenebilir ve OrderID, OrderDate, OrderItems vb. gibi bir öznitelik kümesinin dahili olarak oluşturulmuş olabilir. Ancak, ülke/bölge, cadde, şehir, vb. gibi karmaşık bir değer olan ve bu etki alanında hiçbir kimliği olmayan adresin, modellenmesi ve değer nesnesi olarak kabul edilmesinin gerekir.

## <a name="important-characteristics-of-value-objects"></a>Değer nesnelerinin önemli özellikleri

Değer nesneleri için iki ana özellik vardır:

- Hiçbir kimliği yoktur.

- Bunlar sabittir.

İlk özellik zaten tartılandı. Dengeszlik kullanılabilirliği önemli bir gereksinimdir. Nesne oluşturulduktan sonra bir değer nesnesinin değerleri sabit olmalıdır. Bu nedenle, nesne oluşturulduğunda gerekli değerleri sağlamanız gerekir, ancak nesnenin ömrü boyunca değişmelerine izin vermeniz gerekir.

Değer nesneleri, belirli püf noktalarını, gerçek sabit doğası sayesinde performans için gerçekleştirmenize olanak tanır. Bu, özellikle de aynı değere sahip binlerce değer nesne örneği olabilen sistemlerde geçerlidir. Sabit doğası, bunların yeniden kullanılmasını sağlar; değerleri aynı olduğundan ve kimlik olmadığından, bunlar değiştirilebilir nesneler olabilir. Bu tür iyileştirme, bazen yavaş çalışan yazılımlar ve iyi performansa sahip yazılımlar arasında farklılık yapabilirler. Tabii ki, tüm bu durumlar uygulama ortamına ve dağıtım bağlamına bağlıdır.

## <a name="value-object-implementation-in-c"></a>C 'de değer nesnesi uygulama\#

Uygulama açısından, tüm öznitelikler arasındaki karşılaştırmaya göre (bir değer nesnesi kimlik tabanlı olmaması gerektiğinden) ve diğer temel özelliklerle eşitlik gibi temel yardımcı yöntemlere sahip bir değer nesnesi taban sınıfına sahip olabilirsiniz. Aşağıdaki örnek, eShopOnContainers 'dan sıralama mikro hizmetinde kullanılan bir değer nesnesi temel sınıfını gösterir.

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return this.GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Select(x => x != null ? x.GetHashCode() : 0)
            .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

Aşağıdaki örnekte gösterilen adres değeri nesnesi gibi gerçek değer nesneniz uygularken bu sınıfı kullanabilirsiniz:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetEqualityComponents()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

Bu değerin nesne uygulamasının bir kimlik olmadığını ve bu nedenle, hiçbir kimlik alanı olmadığını, hiçbir ID alanını ve ne zaman ValueObject sınıfında bile olmadığını görebilirsiniz.

Entity Framework (EF) tarafından kullanılmak üzere bir sınıfta ID alanı olmadığından, KIMLIK olmayan daha iyi değer nesnelerini uygulama konusunda büyük ölçüde yardımcı olan EF Core 2,0 'e kadar mümkün değildir. Bu, bir sonraki bölümün tam olarak bir açıklaması olur.

Değer nesnelerinin sabit olması, salt okunurdur (yani salt al özelliklerine sahip) ve gerçekten doğru olması gerekir. Ancak, değer nesneleri genellikle serileştirilmiş ve seri durumdan çıkarılmış ve ileti kuyruklarıyla birlikte kaldırılacak ve Salt okunabilir hale getirilemez, bu yüzden yalnızca `private set` , pratik olması gereken salt okunurdur.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a>EF Core 2,0 ve üzeri ile veritabanında değer nesnelerini kalıcı hale getirme

Yalnızca etki alanı modelinizde bir değer nesnesinin nasıl tanımlanacağını gördünüz. Ancak, genellikle kimliği olan varlıkları hedeflediğinden bu Entity Framework Core kullanarak veritabanını veritabanına nasıl kalıcı hale getirebilirsiniz?

### <a name="background-and-older-approaches-using-ef-core-11"></a>EF Core 1,1 kullanarak arka plan ve eski yaklaşımlar

Arka plan olarak, 1,0 ve 1,1 EF Core kullanılırken, geleneksel .NET Framework EF 6. x bölümünde tanımlandığı gibi [karmaşık türleri](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) kullanmadığınıza ilişkin bir sınırlama vardır. Bu nedenle, 1,0 veya 1,1 EF Core kullanıyorsanız, değer nesnenizin kimliğini kimlik alanı olan bir EF varlığı olarak depolamanız gerekir. Daha sonra, kimliği olmayan bir değer nesnesi gibi daha fazla baktığı için, bir değer nesnesinin kimliğinin etki alanı modelinde önemli olmadığını net hale getirmek için KIMLIĞINI gizleyebilirsiniz. KIMLIĞI bir [Gölge Özellik](/ef/core/modeling/shadow-properties)olarak kullanarak bu kimliği gizleyebilirsiniz. Modeldeki KIMLIĞI gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modelinize yönelik bir tür saydam olacaktır.

EShopOnContainers 'un ilk sürümünde (.NET Core 1,1), EF Core altyapısı tarafından gereken gizli KIMLIK, altyapı projesinde akıcı API kullanılarak, DbContext düzeyinde aşağıdaki şekilde uygulanmıştır. Bu nedenle, KIMLIK, görünümün etki alanı model noktasından gizlendi, ancak hala altyapıda var.

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

Ancak, bu değer nesnesinin veritabanına kalıcılığı, farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.

EF Core 2,0 ve üzeri sürümlerde, değer nesnelerini kalıcı hale getirmek için yeni ve daha iyi yollar vardır.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a>Değer nesnelerini EF Core 2,0 ve sonraki sürümlerde sahip olan varlık türleri olarak kalıcı hale getirme

DDD 'daki kurallı değer nesne deseninin yanı sıra EF Core sahip olan varlık türü arasında bazı boşluklar olsa da, EF Core 2,0 ve üzeri ile değer nesnelerini kalıcı hale getirmenin en iyi yolu vardır. Bu bölümün sonundaki sınırlamalara bakabilirsiniz.

Sahip olan varlık türü özelliği 2,0 sürümünden bu yana EF Core eklenmiştir.

Sahip olunan bir varlık türü, kendi kimliğine sahip olmayan türleri etki alanı modelinde açıkça tanımlamış ve varlıklarınızda bir değer nesnesi gibi özellikler olarak kullanılan türleri eşlemenizi sağlar. Sahip olan bir varlık türü, başka bir varlık türüyle aynı CLR türünü paylaşır (yani, yalnızca normal bir sınıftır). Tanımlama gezintisini içeren varlık, sahip varlıktır. Sahibi sorgulanırken, sahip olan türler varsayılan olarak dahil edilir.

Yalnızca etki alanı modeline bakarak, sahip olunan bir tür herhangi bir kimliğe sahip değil gibi görünür. Bununla birlikte, sahip olunan türlerin altında kimlik vardır ancak sahip gezinti özelliği bu kimliğin bir parçasıdır.

Sahip olunan türlerin örneklerinin kimliği tamamen kendi kendine değil. Üç bileşenden oluşur:

- Sahibin kimliği

- İşaret eden gezinti özelliği

- Sahip olunan türlerin koleksiyonları durumunda bağımsız bir bileşen (EF Core 2,2 ve üzeri sürümlerde desteklenir).

Örneğin, eShopOnContainers 'daki sıralama etki alanı modelinde, sipariş varlığının bir parçası olarak, adres değeri nesnesi, sahip varlığı içinde, sipariş varlığı olan bir sahip varlık türü olarak uygulanır. `Address` , etki alanı modelinde tanımlanmış Identity özelliği olmayan bir türdür. Bu, belirli bir siparişin sevkiyat adresini belirtmek için sipariş türünün bir özelliği olarak kullanılır.

Kurala göre, sahip olunan tür için bir gölge birincil anahtar oluşturulur ve tablo bölme kullanılarak aynı tabloyla aynı tabloyla eşleştirilir. Bu, sahip oldukları türlerin geleneksel .NET Framework EF6 içinde nasıl kullanıldığı hakkında benzer şekilde kullanılmasına olanak tanır.

Sahip oldukları EF Core hiçbir kurala göre hiçbir şekilde bulunamadığına dikkat etmeniz önemlidir, bu nedenle bunları açıkça bildirmeniz gerekir.

EShopOnContainers içinde, OrderingContext.cs dosyasında, yöntemi içinde, `OnModelCreating()` birden çok altyapı yapılandırması uygulanır. Bunlardan biri sipariş varlığıyla ilgilidir.

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
//
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

Aşağıdaki kodda, sıra varlığı için kalıcılık altyapısı tanımlanmıştır:

```csharp
// Part of the OrderEntityTypeConfiguration.cs class
//
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();

    //...Additional validations, constraints and code...
    //...
}
```

Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntemi, `Address` özelliğin türün sahip olduğu bir varlık olduğunu belirtir `Order` .

Varsayılan olarak EF Core kurallar, sahip olduğu varlık türünün özelliklerinin veritabanı sütunlarını olarak adlandırın `EntityProperty_OwnedEntityProperty` . Bu nedenle, iç özellikleri, `Address` `Orders` `Address_Street` `Address_City` (ve için,, ve için) adlarına sahip tabloda görüntülenir `State` `Country` `ZipCode` .

`Property().HasColumnName()`Bu sütunları yeniden adlandırmak için floent metodunu ekleyebilirsiniz. Ortak özellik olduğu durumlarda `Address` , eşlemeler aşağıdakine benzer olacaktır:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

`OwnsOne`Yöntemi akıcı bir eşlemede zincirlemek mümkündür. Aşağıdaki kuramsal örnekte, ve olan `OrderDetails` `BillingAddress` ve `ShippingAddress` her iki tür olan `Address` . Daha sonra `OrderDetails` `Order` türüne aittir.

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a>Sahip olunan varlık türleri hakkında ek ayrıntılar

- Sahip olan türler, OwnsOne Fluent API kullanarak belirli bir türe bir gezinti özelliği yapılandırdığınızda tanımlanmıştır.

- Meta veri modelinizdeki sahip olunan bir türün tanımı, bir bileşiminin türü, gezinti özelliği ve sahip olunan türün CLR türü.

- Yığınımızda sahip olan bir tür örneğinin kimliği (anahtarı), sahip türünün kimliğinin ve sahip olunan türün tanımının bir bileşiminin bir örneğidir.

#### <a name="owned-entities-capabilities"></a>Sahip olunan varlıkların özellikleri

- Sahip olunan türler, sahip olunan (iç içe geçmiş türler) veya sahip olmayan (diğer varlıklara ait normal başvuru gezinti özellikleri) diğer varlıklara başvurabilir.

- Aynı CLR türünü, ayrı gezinti özellikleri aracılığıyla aynı sahip varlıktaki farklı sahip türlerle eşleyebilirsiniz.

- Tablo bölme kurala göre ayarlanır, ancak ait türü ToTable kullanarak farklı bir tabloyla eşleyerek bu seçeneği kullanabilirsiniz.

- Eager yüklemesi, sahip olunan türler üzerinde otomatik olarak gerçekleştirilir, yani sorgu üzerinde çağrı yapmanız gerekmez `.Include()` .

- `[Owned]`EF Core 2,1 ve üzeri kullanılarak özniteliğiyle yapılandırılabilir.

- , Sahip olunan türlerin koleksiyonlarını işleyebilir (sürüm 2,2 ve üzeri kullanarak).

#### <a name="owned-entities-limitations"></a>Sahip olunan varlıkların sınırlamaları

- `DbSet<T>`Sahip olunan bir tür (tasarıma göre) oluşturamazsınız.

- `ModelBuilder.Entity<T>()`Sahip olunan türler üzerinde çağrılamaz (Şu anda tasarım kaynaklı).

- Aynı tablodaki (yani, tablo bölme kullanılarak) sahip ile eşlenmiş isteğe bağlı (null yapılabilir) türler desteklenmez. Bunun nedeni her bir özellik için eşlemenin yapıldığından, null karmaşık değer için bir bütün olarak ayrı bir Sentinel yoktur.

- Sahip olunan türler için devralma-eşleme desteği yoktur, ancak aynı devralma hiyerarşilerindeki iki yaprak türünü farklı sahipli türlerle eşleyemezsiniz. EF Core, aynı hiyerarşinin bir parçası oldukları gerçeğiyle ilgili bir neden olmayacaktır.

#### <a name="main-differences-with-ef6s-complex-types"></a>EF6's karmaşık türlerle ana farklılıklar

- Tablo bölme isteğe bağlıdır, diğer bir deyişle, isteğe bağlı olarak ayrı bir tabloyla eşleştirilebilir ve sahip oldukları türler de vardır.

- Diğer varlıklara başvurabilir (diğer bir deyişle, bağımlı olan diğer türlere ilişkilerle ilgili olarak görev yapabilir).

## <a name="additional-resources"></a>Ek kaynaklar

- **Marwler. ValueObject kalıbı** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Etki alanı odaklı tasarım: yazılım Kalbunda karmaşıklık karmaşıklığı.** (Kitap; değer nesnelerinin bir tartışmasını içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn versuz. Etki alanı odaklı tasarım uygulama.** (Kitap; değer nesnelerinin bir tartışmasını içerir) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Sahip olan varlık türleri** \
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- **Gölge özellikleri** \
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- **Karmaşık türler ve/veya değer nesneleri**. EF Core GitHub deposu 'nda tartışma (sorunlar sekmesi) \
  <https://github.com/dotnet/efcore/issues/246>

- **ValueObject.cs.** EShopOnContainers içindeki temel değer nesne sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Adres sınıfı.** EShopOnContainers içinde örnek değer nesne sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Önceki](seedwork-domain-model-base-classes-interfaces.md) 
>  [Sonraki](enumeration-classes-over-enum-types.md)
