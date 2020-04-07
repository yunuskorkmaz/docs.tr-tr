---
title: Değer nesneleri uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Yeni Varlık Çerçevesi özelliklerini kullanarak değer nesnelerini uygulamak için ayrıntılara ve seçeneklere bakın.
ms.date: 01/30/2020
ms.openlocfilehash: 4a8a92a8dabcf09654ecd0e5dea2a7df25d7abf7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805742"
---
# <a name="implement-value-objects"></a>Değer nesnelerini uygulama

Varlıklar ve toplamlar hakkında önceki bölümlerde ele alındığı gibi, kimlik varlıklar için esastır. Ancak, bir sistemde değer nesneleri gibi kimlik ve kimlik izleme gerektirmeyen birçok nesne ve veri öğesi vardır.

Bir değer nesnesi diğer varlıklara başvuruyapabilir. Örneğin, bir noktadan diğerine nasıl alınacağını açıklayan bir rota oluşturan bir uygulamada, bu yol bir değer nesnesi olacaktır. Bu belirli bir rota üzerinde noktaların bir anlık görüntü olurdu, ancak bu önerilen rota bir kimlik olmazdı, dahili şehir, yol, vb gibi varlıklar atıfta bulunsa bile.

Şekil 7-13, Sipariş toplamıiçindeki Adres değeri nesnesini gösterir.

![Sipariş Toplamı'nın içindeki Adres değeri nesnesini gösteren diyagram.](./media/implement-value-objects/value-object-within-aggregate.png)

**Şekil 7-13**. Sipariş toplamı içindeki adres değeri nesnesi

Şekil 7-13'te gösterildiği gibi, bir varlık genellikle birden çok özniteliklerden oluşur. Örneğin, `Order` varlık bir kimliğe sahip bir varlık olarak modellenebilir ve Sipariş Kimliği, OrderDate, OrderItems, vb. gibi öznitelikler kümesinden dahili olarak oluşturulabilir. Ancak, sadece ülke/bölge, sokak, şehir, vb. oluşan karmaşık bir değer olan ve bu etki alanında kimliği olmayan adres, modellenmeli ve bir değer nesnesi olarak ele alınmalıdır.

## <a name="important-characteristics-of-value-objects"></a>Değer nesnelerinin önemli özellikleri

Değer nesneleri için iki ana özellik vardır:

- Kimlikleri yok.

- Değişmezler.

İlk karakteristik zaten tartışıldı. Değişmezlik önemli bir gerekliliktir. Nesne oluşturulduktan sonra bir değer nesnesinin değerleri değişmez olmalıdır. Bu nedenle, nesne oluşturulduğunda, gerekli değerleri sağlamanız gerekir, ancak nesnenin ömrü boyunca bunların değişmesine izin vermemelisiniz.

Değer nesneleri, değişmez doğası sayesinde performans için belirli hileler gerçekleştirmenize olanak sağlar. Bu, özellikle, çoğu aynı değerlere sahip binlerce değer nesnesi örneği olabilecek sistemlerde geçerlidir. Değişmez doğaları yeniden kullanılmalarını sağlar; değerleri aynı olduğundan ve kimlikleri olmadığından değiştirilebilir nesneler olabilirler. Bu tür optimizasyon bazen yavaş çalışan yazılım ve iyi performans ile yazılım arasında bir fark yaratabilir. Tabii ki, tüm bu durumlarda uygulama ortamı ve dağıtım bağlamında bağlıdır.

## <a name="value-object-implementation-in-c"></a>C'de değer nesnesi uygulaması\#

Uygulama açısından, tüm öznitelikler (bir değer nesnesi kimliğe dayalı olmamalıdır) ve diğer temel özellikleri arasında karşılaştırma dayalı eşitlik gibi temel yardımcı program yöntemleri olan bir değer nesnesi taban sınıf olabilir. Aşağıdaki örnekte, eShopOnContainers'dan sipariş mikrohizmetinde kullanılan bir değer nesnesi taban sınıfı gösterilmektedir.

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

Aşağıdaki örnekte gösterilen Adres değeri nesnesinde olduğu gibi, gerçek değer nesnenizi uygularken bu sınıfı kullanabilirsiniz:

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

Adres'in bu değer nesnesi uygulamasının nasıl bir kimliği olmadığını ve bu nedenle, Değer Nesnesi sınıfında bile Adres sınıfında kimlik alanı olmadığını görebilirsiniz.

Varlık Çerçevesi (EF) tarafından kullanılacak bir sınıfta kimlik alanı olmaması, kimliği olmayan daha iyi değer nesnelerinin uygulanmasına büyük ölçüde yardımcı olan EF Core 2.0'a kadar mümkün değildi. Bu tam olarak bir sonraki bölümün açıklamasıdır.

Bu değer nesneleri, değişmez olan, salt okunur olması gerektiğini iddia edilebilir (yani, sadece almak özellikleri var), ve bu gerçekten doğrudur. Ancak, değer nesneleri genellikle seri hale getirilir ve ileti kuyruklarından geçmek için deserialized ve salt okunur değerleri atama deserializer durur, bu yüzden sadece olarak `private set`bırakın , hangi pratik olması için sadece okunur.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a>EF Core 2.0 ve sonrası ile veritabanındaki değer nesneleri nasıl kalıcı

Etki alanı modelinizde bir değer nesnesini nasıl tanımladığınızı gördün. Ama nasıl aslında veritabanında Genellikle kimlik ile varlıkları hedefleyen varlık Framework Core kullanarak veritabanında devam edebilirsiniz?

### <a name="background-and-older-approaches-using-ef-core-11"></a>EF Core 1.1 kullanarak arka plan ve eski yaklaşımlar

Arka plan olarak, EF Core 1.0 ve 1.1 kullanırken bir sınırlama, geleneksel .NET Framework'de EF 6.x'te tanımlandığı gibi [karmaşık türleri](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) kullanamamanızdır. Bu nedenle, EF Core 1.0 veya 1.1 kullanıyorsanız, değer nesnenizi kimlik alanına sahip bir EF varlığı olarak depolamanız gerekir. Daha sonra, daha çok kimliği olmayan bir değer nesnesine benzemektedir, böylece etki alanı modelinde bir değer nesnesinin kimliğinin önemli olmadığını açıkça belirtebilirsiniz. Kimliği [gölge özellik](https://docs.microsoft.com/ef/core/modeling/shadow-properties )olarak kullanarak bu kimliği gizleyebilirsiniz. Modelde kimliği gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeli için saydam tür olacaktır.

eShopOnContainers'ın (.NET Core 1.1) ilk sürümünde, EF Core altyapısının ihtiyaç duyduğu gizli kimlik, altyapı projesinde Akıcı API kullanılarak DbContext düzeyinde aşağıdaki şekilde uygulanmıştır. Bu nedenle, kimlik etki alanı modeli açısından gizliydi, ancak yine de altyapıda mevcuttu.

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

Ancak, bu değer nesnesinin veritabanına kalıcılığı farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.

EF Core 2.0 ve sonraki ile değer nesnelerini kalıcı olarak sürdürmek için yeni ve daha iyi yollar vardır.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a>EF Core 2.0 ve sonraki işlemlerde sahip olunan varlık türleri olarak değer nesnelerini kalıcı olarak

DDD'deki kanonik değer nesnesi deseni ile EF Core'daki sahip olunan varlık türü arasındaki bazı boşluklara rağmen, şu anda EF Core 2.0 ve sonraki değerlere sahip nesneleri kalıcı hale getirmek için en iyi yoldur. Bu bölümün sonunda sınırlamaları görebilirsiniz.

Sahip olunan varlık türü özelliği, sürüm 2.0'dan beri EF Core'a eklendi.

Sahip olunan varlık türü, etki alanı modelinde açıkça tanımlanan kendi kimliği olmayan ve varlıklarınızdan herhangi birinde değer nesnesi gibi özellikler olarak kullanılan türleri eşlemenize olanak tanır. Sahip olunan varlık türü, aynı CLR türünü başka bir varlık türüyle paylaşır (diğer bir şey, bu sadece normal bir sınıftır). Tanımlayıcı gezintiyi içeren varlık sahibi varlıktır. Sahibini sorgularken, sahip olunan türler varsayılan olarak dahil edilir.

Sadece etki alanı modeline bakarak, sahip olunan bir tür herhangi bir kimliği yokmuş gibi görünür. Ancak, kapakları altında, sahip olunan türleri kimlik var, ancak sahibi navigasyon özelliği bu kimliğin bir parçasıdır.

Sahip olunan türlerin örneklerinin kimliği tamamen kendilerine ait değildir. Üç bileşenden oluşur:

- Sahibinin kimliği

- Onları gösteren navigasyon özelliği

- Sahip olunan türlerin koleksiyonlarısöz konusu olduğunda, bağımsız bir bileşen (EF Core 2.2 ve sonrası olarak desteklenir).

Örneğin, eShopOnContainers'daki Sipariş etki alanı modelinde, Sipariş varlığının bir parçası olarak, Adres değeri nesnesi, Sipariş varlığı olan sahip varlık içinde sahip olunan varlık türü olarak uygulanır. Adres, etki alanı modelinde tanımlı kimlik özelliği olmayan bir türdür. Belirli bir siparişin sevkiyat adresini belirtmek için Sipariş türünün bir özelliği olarak kullanılır.

Kural olarak, sahip olunan tür için bir gölge birincil anahtar oluşturulur ve tablo bölme kullanılarak sahibi ile aynı tabloya eşlenir. Bu, sahip olunan türleri, geleneksel .NET Framework'de EF6'da karmaşık türlerin nasıl kullanıldığına benzer şekilde kullanmanıza olanak tanır.

Sahip olunan türlerin EF Core'daki sözleşme tarafından hiçbir zaman keşfedilmeyişediğini, bu nedenle bunları açıkça beyan etmeniz gerektiğini unutmayın.

eShopOnContainers, OrderingContext.cs dosyasında, `OnModelCreating()` yöntem içinde, birden fazla altyapı yapılandırmaları uygulanır. Bunlardan biri Sipariş varlığı ile ilgilidir.

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

Aşağıdaki kodda, kalıcılık altyapısı Sipariş varlığı için tanımlanır:

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

Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntem `Address` özelliğitin `Order` türünün sahip olduğu bir varlık olduğunu belirtir.

Varsayılan olarak, EF Core kuralları veritabanı sütunlarını sahip olunan `EntityProperty_OwnedEntityProperty`varlık türündeki özellikleri . Bu nedenle, tabloda , `Orders` (ve benzeri `Address_Street` `Address_City` için `State`, `Country`, ve `ZipCode`) adlarıyla tabloda görünür. `Address`

Bu sütunları `Property().HasColumnName()` yeniden adlandırmak için akıcı yöntemi ekleyebilirsiniz. Kamu malı `Address` olduğu durumlarda, haritalamalar aşağıdaki gibi olacaktır:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Yöntemi akıcı bir haritalamayla zincirlemek `OwnsOne` mümkündür. Aşağıdaki varsayımsal `OrderDetails` örnekte, sahip `BillingAddress` `ShippingAddress`ve , `Address` her ikisi de türü vardır. Sonra `OrderDetails` türüne `Order` aittir.

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

- OwnsOne akıcı API'sini kullanarak bir gezinti özelliğini belirli bir türe yapılandırdığınızda sahip olunan türler tanımlanır.

- Meta veri modelimizde sahip olunan bir türün tanımı bir bileşimidir: sahip türü, gezinti özelliği ve sahip olunan türün CLR türü.

- Yığınımızdaki sahipolunan bir tür örneğinin kimliği (anahtarı), sahip türünün kimliğinin ve sahip olunan türün tanımının bir bileşimidir.

#### <a name="owned-entities-capabilities"></a>Sahip olunan varlıklar yetenekleri

- Sahip olunan türler, sahip olunan (iç içe sahip olunan türler) veya sahip olunmayan (diğer varlıklara düzenli başvuru gezinme özellikleri) diğer varlıklara başvurur.

- Ayrı gezinti özellikleri aracılığıyla aynı sahip varlığında farklı sahip olunan türler olarak aynı CLR türünü eşleyebilirsiniz.

- Tablo bölme kuralına göre ayarlanır, ancak ToTable'ı kullanarak sahip olunan türü farklı bir tabloyla eşleyerek devre dışı bırakabilirsiniz.

- İstekli yükleme, sahip olunan türlerde otomatik olarak gerçekleştirilir, `.Include()` yani sorguyu çağırmaya gerek yoktur.

- EF Core 2.1 `[Owned]`ve sonrası kullanılarak öznitelik ile yapılandırılabilir.

- Sahip olunan türlerin koleksiyonlarını işleyebilir (sürüm 2.2 ve sonraki sürümleri kullanarak).

#### <a name="owned-entities-limitations"></a>Sahip olunan varlıklar sınırlamaları

- Sahip olunan bir `DbSet<T>` tür (tasarım gereği) oluşturamazsınız.

- Sahip olunan `ModelBuilder.Entity<T>()` türleri (şu anda tasarımgereği) arayamayabilirsiniz.

- Aynı tabloda sahibiyle eşlenen isteğe bağlı (yani geçersiz kılınabilir) sahip olunan türler için destek yok (diğer bir deyişle, tablo bölmeyi kullanarak). Bunun nedeni, haritalama nın her özellik için yapılmasıdır, bir bütün olarak null karmaşık değeri için ayrı bir nöbetçimiz yoktur.

- Sahip olunan türler için devralma eşleme desteği yok, ancak aynı devralma hiyerarşilerinin iki yaprak türünü farklı sahip olunan türler olarak eşlenebilmelisiniz. EF Core, aynı hiyerarşinin bir parçası oldukları gerçeğini düşünmez.

#### <a name="main-differences-with-ef6s-complex-types"></a>EF6'nın karmaşık tipleri ile temel farklılıklar

- Tablo bölme isteğe bağlıdır, diğer bir süre sonra isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve yine de sahip olunabilir.

- Diğer varlıklara başvuruda bulunabilirler (diğer varlıklar, sahip olunmayan diğer türlerle ilişkilerde bağımlı taraf olarak hareket edebilirler).

## <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler' ı. ValueObject deseni** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde Karmaşıklıkla Mücadele.** (Kitap; değer nesnelerinin bir tartışma içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon' u. Etki Alanı Odaklı Tasarımın Uygulanması.** (Kitap; değer nesnelerinin bir tartışma içerir) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Sahip olunan Varlık Türleri** \
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- **Gölge Özellikleri** \
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- **Karmaşık türleri ve/veya değer nesneleri.** EF Core GitHub repo (Sorunlar sekmesinde) \
  <https://github.com/dotnet/efcore/issues/246>

- **ValueObject.cs.** eShopOnContainers'da temel değer nesne sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Adres sınıfı.** eShopOnContainers örnek değer nesne sınıfı. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Önceki](seedwork-domain-model-base-classes-interfaces.md)
> [Sonraki](enumeration-classes-over-enum-types.md)
