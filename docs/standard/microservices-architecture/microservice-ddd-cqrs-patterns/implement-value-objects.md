---
title: "Değer nesnelerini uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Değer nesnelerini uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a>Değer nesnelerini uygulama

Varlıklar ve toplamalar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temel önemdedir. Ancak, yoktur çok sayıda nesne ve veri öğelerini bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistem.

Bir değer nesnesi diğer varlıklar başvuruda bulunabilir. Örneğin, bir noktadan diğerine almayı açıklar bir rota oluşturan bir uygulamada bu rota bir değer nesnesi olacaktır. Özel bir rota noktalarında görüntüsünü olacaktır, ancak dahili Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yol bir kimlik sahip olmaz.

Şekil 9-13 sipariş toplama içinde adresi değer nesnesi gösterir.

![](./media/image14.png)

**Şekil 9-13**. Değer nesnesi sipariş toplama içinde adres

Şekil 9-13'te gösterildiği gibi bir varlığın genellikle birden çok özniteliklerini oluşur. Örneğin, sipariş kimliğe sahip bir varlık olarak modellenir ve değiştirebilirsiniz dahili OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca karmaşık bir değer adresi ülke, posta, şehir oluşur, vb. modellenir ve bir değer nesnesi kabul edilir.

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

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>Kimlik özelliğini EF Çekirdek değer nesnelerini kalıcı hale getirmek için kullanılırken gizleme

EF çekirdeği kullanmak, kendi geçerli sürümde (EF çekirdek 1.1) kullanamazsınız olduğunda bir sınırlama [karmaşık türler](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) EF içinde tanımlanan 6.x. Bu nedenle, değer nesnesi EF varlık olarak depolamanız gerekir. Ancak, kimlik değer nesnesinin bir parçası olan modelde önemli değil netleştirmek için Kimliğini gizleyebilirsiniz. Kimliği Gizle kimliği gölge özelliği olarak kullanmaktır. Model kimliği gizlemek için bu yapılandırma bir altyapı düzeyinde ayarlandığından için etki alanı modelinizin saydam ve altyapı uygulaması gelecekte değiştirebilirsiniz.

EShopOnContainers içinde EF çekirdek altyapısı tarafından gerekli gizli kimliği DbContext düzeyini aşağıdaki şekilde altyapı proje Fluent API kullanılarak uygulanır.

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

Bu nedenle, etki alanı modeli açısından bakıldığında kimliği gizlidir ve gelecekte değer nesnesi altyapı da karmaşık bir tür veya başka bir yolu olarak uygulanabilir.

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
