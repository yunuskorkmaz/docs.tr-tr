---
title: Değer nesneleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Ayrıntıları ve Entity Framework yenilikleri kullanarak değer nesneleri uygulama seçenekleri alın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: bd165ac2511476a5041e7d09126647546c632ba6
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063079"
---
# <a name="implement-value-objects"></a>Değer nesneleri uygulama

Varlıklar ve toplamlar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temeldir. Ancak, vardır birçok nesneleri ve veri öğeleri bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistemde.

Bir değer nesnesi diğer varlıkların başvurabilirsiniz. Örneğin, bir noktasından diğerine alma açıklayan bir yol oluşturur bir uygulamada yönlendiren bir değer nesnesi olur. Belirli bir yol noktalarında anlık görüntüsünü olacaktır, ancak dahili olarak Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yolu bir kimlik sahip olmaz.

Şekil 7-13 adresi değer nesnesini sipariş toplama içinde gösterir.

![Adresi değeri-nesne sipariş toplama içinde.](./media/image14.png)

**Şekil 7-13**. İçindeki sırası toplam değer nesnesi adresi

Şekil 7-13'te gösterildiği gibi bir varlık, genellikle birden çok özniteliklerini oluşur. Örneğin, `Order` varlığı kimliğe sahip bir varlık olarak modellenir ve dahili olarak OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca bir karmaşık değerli adresi, ülke, posta, şehir, vb. oluşur ve kimliksiz bu etki alanında var, gerekir modellenir ve bir değer nesnesi olarak kabul edilir.

## <a name="important-characteristics-of-value-objects"></a>Değer nesnelerin önemli özellikler

Değer nesneleri için iki ana özellikleri şunlardır:

- Hiçbir kimlik sahiptirler.

- Bunlar sabittir.

İlk özelliği zaten açıklanmıştır. Değiştirilemezlik önemli bir gereksinimdir. Nesne oluşturulduktan sonra bir değer nesnesini değerini sabit olmalıdır. Bu nedenle, bir nesne oluşturulduğunda, gerekli değerler sağlamanız gerekir ancak, bunları nesne ömrü boyunca değiştirmek izin gerekir.

Değeri nesneler performans için sabit doğasını sayesinde belirli püf noktaları işlemleri yapmanıza olanak verir. Bu sistemlerde özellikle doğrudur nesne örneklerini değer binlerce olabilir Burada, çoğu aynı değerlere sahip. Sabit doğasını yeniden olanak sağlar; birbirinin yerine nesneleri değerlerine aynıdır ve bunlar herhangi bir kimliğe sahip olabilirler. Bu tür bir en iyi duruma getirme, bazen yavaş çalışan yazılım ve iyi performans yazılım arasında bir fark yapabilirsiniz. Elbette, tüm bu durumlarda, uygulama ortamı ve dağıtım bağlam bağlıdır.

## <a name="value-object-implementation-in-c"></a>C'de değeri nesne uygulama\#

Uygulama açısından eşitlik karşılaştırması bu yana (bir değer nesnesi kimliğini dayanması değil) tüm öznitelikler ve diğer temel özelliklerine göre gibi temel yardımcı program yöntemleri sahip bir değer nesnesi temel sınıf olabilir. Aşağıdaki örnek, sıralama mikro hizmetine gelen kullanılan değer nesnesi temel bir sınıfı gösterir.

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

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

Aşağıdaki örnekte gösterilen adresi değer nesnesini gibi ile gerçek değer nesnenizin uygularken Bu sınıf kullanabilirsiniz:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
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

Kimlik ve bu nedenle, hiçbir Kimliği alanı ne adresi sınıfı bile ValueObject sınıfı, bu adresi değer nesnesini uygulaması nasıl sahip olduğunu görebilirsiniz.

EF Core 2.0, önemli ölçüde daha iyi değeri uygulamak için yardımcı olan herhangi bir kimliğe sahip nesneleri kadar hiçbir Kimliği alanı Entity Framework tarafından kullanılacak bir sınıf olması mümkün değildi Tam olarak bir sonraki bölüm açıklaması olmasıdır.

Değer nesneleri, sabit, olan salt okunur (yani salt alma Özellikler) olması gerektiğini tartışılabilir ve gerçekten de true. Ancak, değer nesneler genellikle serileştirilmiş ve ileti kuyrukları gitmek için seri durumdan ve salt okunur olan, böylece biz yalnızca bunları kullanışlı olması için salt okunur yeterince özel ayarlı bırakın gelen değerler, atama seri durumdan çıkarıcının durdurur.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Değer EF Core 2.0 ile veritabanı nesnelerini kalıcı yapma

Yalnızca, etki alanı modeli içinde bir değer nesnesini tanımlamak öğrendiniz. Ancak, nasıl, aslında Bu kimliğe sahip varlıklar genellikle hedefleyen Entity Framework (EF) çekirdek aracılığıyla veritabanına kalıcı hale getirebilirsiniz?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Arka plan ve EF Core 1.1 kullanarak eski yaklaşımları

Arka planı olarak değil kullanabilirsiniz, EF Core 1.0 ve 1.1 kullanırken bir sınırlama olan [karmaşık türler](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) EF tanımlandığı gibi geleneksel .NET Framework 6.x. Bu nedenle, EF Core 1.0 veya 1.1 kullanıyorsanız, değer nesnesi Kimliği alanı ile EF varlık olarak depolamak gerekli. Ardından, hiçbir kimlik ile bir değer nesnesi gibi daha fazla görünüyordu için bir değer nesnesi kimliğini etki alanı modeli içinde önemli olduğunu netleştirmek için Kimliğine gizle. Kimliği'ni kullanarak bu kimliği gizlemek bir [gölge özelliği](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Modeli Kimliğini gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeliniz için tür saydam olacaktır.

Hizmetine (.NET Core 1.1) ilk sürümünde, EF Core altyapısı tarafından gereken gizli kimliği şu şekilde DbContext düzeyinde altyapı proje Fluent API'sini kullanarak uygulanmıştır. Bu nedenle, etki alanı modeli açısından gizli ancak hala mevcut altyapı kimliği.

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

Ancak, bu değer nesnesi bir Kalıcılık veritabanına gibi farklı bir tablo normal bir varlıkta gerçekleştirildi.

EF Core 2.0 ile vardır yeni ve değer nesnelerini kalıcı hale getirmek için daha iyi yollar.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Değer nesneleri olarak sahip olunan varlık türleri EF Core 2.0 Sürdür

Hatta bazı aralıklı olarak sahip olunan varlık türünde EF Core DDD kurallı değer nesne modelinde arasındaki, bunu şu anda değer nesneleri EF Core 2.0 ile kalıcı hale getirmek için en iyi yoludur. Bu bölümün sonunda sınırlamaları görebilirsiniz.

Sahip olunan varlık türü özelliği EF Core 2.0 sürümünden itibaren eklendi.

Sahip olunan varlık türü kendi kimlik etki alanı modeli içinde açıkça tanımlanmış yoksa ve tüm varlıklarınızı içinde bir değer nesnesi gibi bir özellik olarak kullanılan türler eşlemenizi sağlar. Sahip olunan varlık türü başka bir varlık türü ile aynı CLR türüne paylaşımları (diğer bir deyişle, bu normal bir sınıfın'dir). Tanımlama Gezinti içeren varlık sahibi varlıktır. Sahibi sorgularken, sahip olunan türleri varsayılan olarak dahil edilir.

Herhangi bir kimliğe sahip değil yalnızca etki alanı modeli bakarak sahibi bir türü görülüyor. Ancak, kapsar ait türleri kimliğe sahip, ancak sahip gezinme özelliği bu kimliğin bir parçasıdır.

Sahip olunan türlerin örneklerini kimliğini tamamen değil, kendi. Bu üç bileşenden oluşur:

- Sahibi kimliği

- İşaret eden gezinti özelliği

- Söz konusu olduğunda koleksiyon sahibi türlerinin bir bağımsız bileşeni (henüz 2.2 yakında EF Core 2.0 desteklenmiyor).

Örneğin, sipariş varlığı bir parçası olarak hizmetine sıralama etki alanı modeli içinde adresi değer nesnesini bir sipariş varlık sahibi varlık içindeki sahip olunan varlık türü olarak uygulanır. Etki alanı modeli içinde tanımlanan hiçbir kimlik özelliğini türüyle adresidir. Sipariş türünde bir özellik, belirli bir siparişi teslimat adresini belirtmek için kullanılır.

Kural olarak, sahip olunan türü için gölge birincil anahtar oluşturulur ve onu aynı tablonun sahibi olarak tablo bölmeyi kullanarak eşleneceğini. Bu olanak EF6 geleneksel .NET Framework içinde nasıl karmaşık türler için kullanılan ait kullanım benzer şekilde türleri.

Bunları bildirdiğinizde açıkça zorunda türleri hiçbir zaman EF Core kuralı tarafından bulunan ait dikkat edin önemlidir.

Hizmetine OnModelCreating() metodundaki OrderingContext.cs adresindeki var. uygulanan birden çok altyapısını yapılandırma Bunlardan biri, sipariş varlığı için ilişkilidir.

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

Aşağıdaki kodda sipariş varlığı için Kalıcılık altyapısı olarak tanımlanır:

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

Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntemini belirtir `Address` özelliğidir, sahip olunan varlık `Order` türü.

Varsayılan sahip olunan varlık türünün özelliklerini veritabanı sütunlarını EF Core kuralları ad `EntityProperty_OwnedEntityProperty`. Bu nedenle, iç özelliklerini `Address` görünür `Orders` tablo adları ile `Address_Street`, `Address_City` (vb. için `State`, `Country` ve `ZipCode`).

Ekleyebilirsiniz `Property().HasColumnName()` bu sütunları yeniden adlandırma için fluent yöntemi. Durumda burada `Address` ortak bir özellik eşlemeleri aşağıdaki gibi olur:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Zincire mümkündür `OwnsOne` fluent eşlemesinde yöntemi. Aşağıdaki örnekte kuramsal, `OrderDetails` sahibi `BillingAddress` ve `ShippingAddress`, her ikisi de olduğu `Address` türleri. Ardından `OrderDetails` tarafından sahip olunan `Order` türü.

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

### <a name="additional-details-on-owned-entity-types"></a>Sahip olunan varlık türleri hakkında daha fazla ayrıntı

- Sahip olunan türleri OwnsOne fluent API'sini kullanarak belirli bir tür için bir gezinti özelliği yapılandırdığınızda tanımlanır.

- Sahip olunan bir meta veri modelimizi türünün bileşik bir tanımıdır: sahip türü, gezinme özelliğini ve şirkete ait türünün CLR türü.

- (Anahtar) bizim yığınında ait türü örneği bir bileşik sahip türünün kimliği ve sahip olduğu türü tanımı kimliğidir.

#### <a name="owned-entities-capabilities"></a>Sahip olunan varlık özellikleri:

- Türleri ya da ait diğer varlıklar (iç içe geçmiş türler sahip olunan) başvurabilir ait veya sahibi olmayan (normal başvuru Gezinti özellikleri diğer varlıklar için).

- Şirkete ait farklı ayrı Gezinti özellikleri aracılığıyla aynı sahibi varlıktaki aynı CLR türü eşleyebilirsiniz.

- Tablo bölme kural tarafından Kurulum olmakla birlikte, farklı bir tabloya ToTable kullanarak eşleme tarafından sahip olunan türü geri çevirebilirsiniz.

- İstekli yükleme otomatik olarak sahip olunan türlerinde Include() üzerindeki sorgu çağırmaya yani gerek gerçekleştirilir.

- Özniteliği ile yapılandırılabilir \[ait\], EF Core 2.1 gibi

#### <a name="owned-entities-limitations"></a>Sahip olunan varlık sınırlamaları:

- Bir olan DB oluşturulamıyor\<T\> (Tasarım tarafından) sahip olunan bir türü.

- ModelBuilder.Entity çağrılamıyor\<T\>((şu anda tasarıma) ait türlerinde).

- Koleksiyon sahibi türleri henüz (itibarıyla EF Core 2.1 ancak 2.2 içinde desteklenecek).

- Desteği isteğe bağlı (diğer bir deyişle, boş değer atanabilir) sahibiyle aynı tablodaki eşlenen türlerine ait (yani tablo bölmeyi kullanarak). Eşleme için her bir özellik yapıldığı için bu, biz null karmaşık değer için ayrı bir sentinel olarak yoksa tüm.

- Devralma eşleme desteği türlerine sahip olduğu, ancak iki yaprak şirkete ait farklı olarak aynı devralma hiyerarşilerini eşleme olmalıdır. EF Core aynı hiyerarşiye bir parçası olduğundan olgu hakkında neden değil.

#### <a name="main-differences-with-ef6s-complex-types"></a>EF6'ın karmaşık türleri ile temel farklar

- Tablo bölme isteğe bağlıdır, yani bunlar isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve hala türlerine ait olabilir.

- Bunlar, diğer varlıklara (yani bunlar diğer ait olmayan türlere ilişkileri bağımlı tarafında üstlenebilir) başvuruda bulunabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler. ValueObject düzeni** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Etki alanı Odaklı Tasarım: Kuruluşlarda karmaşık yazılım kalbidir.** (Kitap; değer nesneleri hakkında ayrıntılı bilgi içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım.** (Kitap; değer nesneleri hakkında ayrıntılı bilgi içerir) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Gölge Özellikler** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Karmaşık türler ve/veya değer nesneleri**. EF Core GitHub deposunda (sorunlar sekmesinden) tartışma \
  <https://github.com/aspnet/EntityFramework/issues/246>

- **ValueObject.cs.** Temel değerin nesne sınıfı hizmetine. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Sınıf adresi.** Örnek değer hizmetine nesne sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Önceki](seedwork-domain-model-base-classes-interfaces.md)
> [İleri](enumeration-classes-over-enum-types.md)
