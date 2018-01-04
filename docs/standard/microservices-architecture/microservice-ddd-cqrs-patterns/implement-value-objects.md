---
title: "Değer nesnelerini uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Değer nesnelerini uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b7b85d2aa3c563fbd4c7cf89336827d25f22c0e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-value-objects"></a>Değer nesnelerini uygulama

Varlıklar ve toplamalar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temel önemdedir. Ancak, yoktur çok sayıda nesne ve veri öğelerini bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistem.

Bir değer nesnesi diğer varlıklar başvuruda bulunabilir. Örneğin, bir noktadan diğerine almayı açıklar bir rota oluşturan bir uygulamada bu rota bir değer nesnesi olacaktır. Özel bir rota noktalarında görüntüsünü olacaktır, ancak dahili Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yol bir kimlik sahip olmaz.

Şekil 9-13 sipariş toplama içinde adresi değer nesnesi gösterir.

![](./media/image14.png)

**Şekil 9-13**. Değer nesnesi sipariş toplama içinde adres

Şekil 9-13'te gösterildiği gibi bir varlığın genellikle birden çok özniteliklerini oluşur. Örneğin, `Order` varlığı kimliğe sahip bir varlık olarak modellenir ve dahili olarak OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca karmaşık bir değer adresi ülke, posta, vb. Şehir oluşur ve bu etki alanında yok kimliği vardır, modellenir ve gerekir bir değer nesnesi olarak kabul.

## <a name="important-characteristics-of-value-objects"></a>Değer nesnelerin önemli özellikleri

Değer nesneleri için iki ana özellikleri şunlardır:

-   Hiçbir kimlik sahiptirler.

-   Bunlar değişmez.

İlk özelliği zaten açıklanmıştır. Girişi önemli bir gereksinimdir. Nesne oluşturulduktan sonra bir değer nesnesinin değerlerin sabit olması gerekir. Bu nedenle, nesne oluşturulduğunda, gerekli değerleri de sağlamanız gerekir, ancak nesnenin ömrü boyunca değiştirmeye izin vermeniz değil.

Değer nesnelerini değişmez yapılarına sayesinde performans için belirli püf noktaları işlemleri yapmanıza olanak verir. Sistemlerinde özellikle geçerlidir nesne örneklerini değeri binlerce olabilir; Burada, birçok aynı değerlere sahip. Değişmez yapılarına yeniden almalarını sağlar; değerlerine aynıdır ve hiçbir kimliğe sahip olduğundan bunlar birbirinin yerine nesneler olabilir. Bu tür bir en iyi duruma getirme bazen yavaş çalışan yazılım ve iyi bir performans yazılımıyla arasında bir fark yapabilirsiniz. Elbette, tüm bu durumlarda, uygulama ortamı ve dağıtım bağlam bağlıdır.

## <a name="value-object-implementation-in-c"></a>Değer nesnesi uygulamasında C\#

Uygulama bakımından eşitlik karşılaştırması (bir değer nesnesi kimliği üzerinde temel almalıdır değil bu yana) tüm öznitelikler ve diğer temel özelliklere göre gibi temel yardımcı program yöntemleri olan bir değer nesnesi temel sınıfı olabilir. Aşağıdaki örnek eShopOnContainers gelen sıralama mikro kullanılan bir değer nesnesi temel bir sınıfı gösterir.

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
    // Other utilility methods
}
```

Aşağıdaki örnekte gösterilen adres nesnesiyle değer olarak, gerçek değer nesnesi uygularken Bu sınıf kullanabilirsiniz:

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

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Değer nesnelerini EF çekirdek 2.0 ile veritabanında kalıcı hale getirmek nasıl

Yalnızca bir değer nesnesi, etki alanı modeli tanımlamak öğrendiniz. Ancak nasıl, aslında, genellikle kimlik varlıklarıyla hedefler Entity Framework (EF) çekirdek aracılığıyla veritabanına kalıcı?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Arka plan ve eski yaklaşımlar EF çekirdek 1.1 kullanma

Arka plan olarak EF çekirdek 1.0 ve 1.1 kullanırken bir sınırlama, kullanamazsınız edildi [karmaşık türler](https://docs.microsoft.com/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) EF içinde tanımlanan geleneksel .NET Framework'teki 6.x. Bu nedenle, EF çekirdek 1.0 veya 1.1 kullanıyorsanız, kimlik alanı EF varlıkla olarak değer nesnesi depolamak gerekli. Ardından, hiçbir kimliği ile bir değer nesnesi gibi daha fazla arama için değer nesne kimliğinin etki alanı modelinde önemli değildir netleştirmek için Kimliğini gizle. Kimliği olarak kullanarak bu kimliği Gizle bir [gölge özelliği](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Model kimliği gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeli için tür saydam olacaktır.

EShopOnContainers (.NET Core 1.1) ilk sürümünde EF çekirdek altyapısı tarafından gerekli gizli kimliği DbContext düzeyi aşağıdaki yolla altyapı proje Fluent API kullanılarak uygulanmıştır. Bu nedenle, gizli açısından etki alanı modeli, ancak hala mevcut altyapısında kimliği.

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

Ancak, bu değer nesnesi Kalıcılık veritabanına farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.

EF çekirdek 2.0 ile vardır yeni ve değer nesnelerini kalıcı hale getirmek için daha iyi yolu.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>EF çekirdek 2.0 ait varlık türü olarak değer nesnelerini Sürdür

Bile bazı boşluklu DDD kurallı değer nesne modelinde EF çekirdek ait varlık türünde arasındaki, bunu şu anda EF çekirdek 2.0 değeri nesneleriyle kalıcı hale getirmek için en iyi yoludur. Bu bölümün sonunda sınırlamaları görebilirsiniz.

Ait varlık türü özelliği EF çekirdek 2.0 sürümünden bu yana eklendi.

Bir ait varlık türü, etki alanı model içinde tanımlanan kendi kimlik explicitely sahip değil ve varlıklarınızı hiçbirini içinde bir değer nesnesi gibi özellikleri olarak kullanılan türleri eşlemenizi sağlar. Bir ait varlık türünün CLR türü aynı başka bir varlık türü ile paylaşır. Tanımlayan gezinmeyi içeren varlık sahibi varlıktır. Sahibi sorgulanırken ait türleri varsayılan olarak dahil edilir.

Tüm kimlik sahip değil yalnızca etki alanı modeli bakarak ait türü görülüyor.
Kapak altında ait türleri kimliğe sahip, ancak, sahibi gezinti özelliği bu kimliğin bir parçasıdır.

Kendi türlerin örnekleri kimliğini tamamen değil, kendi. Üç bileşenden oluşur: 

- Sahibinin kimliği

- İşaret eden gezinti özelliği

- Söz konusu olduğunda koleksiyonları ait türlerinin bir bağımsız bileşeni (henüz EF çekirdek 2. 0'da desteklenir).

Örneğin, sipariş varlık, bir parçası olarak eShopOnContainers sıralama etki alanı modeli adresi değer nesnesi sipariş varlık sahibi varlık içindeki ait varlık türü olarak uygulanır. Bir etki alanı modelde tanımlı hiçbir kimlik özelliği türüyle adresidir. Sipariş türünde bir özellik, belirli bir sıraya sevkiyat adresini belirtmek için kullanılır.

Kural tarafından gölge birincil anahtar ait türü için oluşturulur ve onu sahibi olarak aynı tabloya tablo bölme kullanarak eşleşecektir. Bunun yapılması sağlar nasıl karmaşık türler EF6 geleneksel .NET Framework'te kullanılan ait kullanım benzer şekilde türleri.

Bunları açıkça bildirmeniz gerekir böylece türleri hiçbir zaman EF çekirdek, kural tarafından bulunan ait dikkate almak önemlidir.

EShopOnContainers içinde OnModelCreating() yöntemi içindeki OrderingContext.cs adresindeki var. uygulanan birden çok altyapısını yapılandırma Bunlardan birini sipariş varlığa ilişkilidir.

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

Aşağıdaki kodda sipariş varlık için Kalıcılık altyapı tanımlanır:

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

Önceki kod `orderConfiguration.OwnsOne(o => o.Address)` yöntemini belirtir `Address` özelliktir ait bir varlığın `Order` türü.

Varsayılan olarak, ait varlık türü olarak özelliklerini veritabanı sütunlarını EF çekirdek kuralları ad `EntityProperty_OwnedEntityProperty`. Bu nedenle, iç özelliklerini `Address` görünür `Orders` tablo adları ile `Address_Street`, `Address_City` (vb. için `State`, `Country` ve `ZipCode`).

Ekleyebilirsiniz `Property().HasColumnName()` bu sütunları yeniden adlandırmak için fluent yöntemi. Durumda burada `Address` ortak özellik eşlemeleri şu şekilde olacaktır:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Zinciri mümkündür `OwnsOne` fluent eşlemeye yöntemi. Aşağıdaki örnekte kuramsal, `OrderDetails` sahibi `BillingAddress` ve `ShippingAddress`, her ikisi de olduğu `Address` türleri. Ardından `OrderDetails` tarafından sahip olunan `Order` türü.

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
    public StreetAddress BillingAddress { get; set; }
    public StreetAddress ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a>Ait varlık türleri hakkında daha fazla ayrıntı

• Türlerine ait OwnsOne fluent API kullanarak belirli bir türde bir gezinti özelliğine yapılandırdığınızda tanımlanır.

• Bizim meta veri modelindeki ait bir tür tanımını olan bir bileşimi: sahip türü, gezinti özelliği ve ait türünün CLR türü.

• Ait türü örneğini bizim yığınında kimliğini (anahtar) sahip türü kimliğini ve ait türü tanımını bileşimi ' dir.

#### <a name="owned-entities-capabilities"></a>Varlık özellikleri ait:

Türü ya da ait diğer varlıklar (iç içe geçmiş ait türleri) başvuruda bulunabilir ait veya ait olmayan • (diğer varlıklar için normal başvuru Gezinti özellikleri).

• Aynı eşleyebilirsiniz CLR farklı ait ayrı Gezinti özellikleri aracılığıyla aynı sahibi varlık türü olarak yazın.

• Tablo bölme Kurulum kural tarafından olmakla birlikte, ToTable kullanarak farklı bir tabloya ait türü eşleme tarafından iptal edilebilir.

• İstekli yükleme ait türleri, yani sorguya dayalı Include() çağrısı gerekli otomatik olarak gerçekleştirilir.

#### <a name="owned-entities-limitations"></a>Ait varlıkları sınırlamaları:

• Bir DbSet oluşturamıyor<T> (tarafından tasarım) ait bir türde.

• ModelBuilder.Entity çağrılamıyor<T>() ait türleri (şu anda tasarıma göre).

Henüz türleri • hiçbir koleksiyonları ait (ancak bunlar sürümlerde EF çekirdek 2.0 sonra desteklenen).

• Bir öznitelik yapılandırma desteği yoktur.

• Aynı tablodaki sahibi olan eşlenen isteğe bağlı (yani boş değer atanabilir) ait türleri için destek yok (yani tablo bölme kullanarak). Bu durum, biz null için ayrı bir sentinel yoktur çünkü.

• Devralma eşleme desteği ait türleri, ancak aynı devralma hiyerarşileri ait farklı olarak iki yaprak türünü eşlemek gerekir. EF çekirdek aynı hiyerarşiye parçası olan olgu hakkında neden değil.

#### <a name="main-differences-with-ef6s-complex-types"></a>EF6'ın karmaşık türleri ile temel farklar

• Tablo bölme isteğe bağlıdır, yani isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve hala türlerine ait olabilir.

• (Örn. Bunlar bağımlı diğer ait olmayan türlere ilişkileri tarafında üstlenebilir) diğer varlıklar başvuruda bulunabilir.


## <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. ValueObject deseni**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling.** (Kitap; değer nesnelerini tartışması içerir) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Etki alanı tabanlı tasarımı uygulama.** (Kitap; değer nesnelerini tartışması içerir) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Karmaşık türler ve/veya değer nesnelerini**. EF çekirdek GitHub deposuna (sorunları sekmesi) tartışmada [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Nesne sınıfında eShopOnContainers taban değeri.
    [*https://github.com/dotnet/eShopOnContainers/BLOB/master/src/Services/Ordering/Ordering.domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Sınıf adres.** Örnek değer nesne sınıfında eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/BLOB/master/src/Services/Ordering/Ordering.domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
[Önceki] (seedwork-domain-model-base-classes-interfaces.md) [sonraki] (numaralandırması-sınıfları-üzerinden-enum-types.md)
