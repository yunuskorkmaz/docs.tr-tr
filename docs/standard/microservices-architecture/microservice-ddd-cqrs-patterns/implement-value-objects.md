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
# <a name="implementing-value-objects"></a><span data-ttu-id="8efe7-104">Değer nesnelerini uygulama</span><span class="sxs-lookup"><span data-stu-id="8efe7-104">Implementing value objects</span></span>

<span data-ttu-id="8efe7-105">Varlıklar ve toplamalar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temel önemdedir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="8efe7-106">Ancak, yoktur çok sayıda nesne ve veri öğelerini bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistem.</span><span class="sxs-lookup"><span data-stu-id="8efe7-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="8efe7-107">Bir değer nesnesi diğer varlıklar başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-107">A value object can reference other entities.</span></span> <span data-ttu-id="8efe7-108">Örneğin, bir noktadan diğerine almayı açıklar bir rota oluşturan bir uygulamada bu rota bir değer nesnesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8efe7-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="8efe7-109">Özel bir rota noktalarında görüntüsünü olacaktır, ancak dahili Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yol bir kimlik sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="8efe7-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="8efe7-110">Şekil 9-13 sipariş toplama içinde adresi değer nesnesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="8efe7-111">**Şekil 9-13**.</span><span class="sxs-lookup"><span data-stu-id="8efe7-111">**Figure 9-13**.</span></span> <span data-ttu-id="8efe7-112">Değer nesnesi sipariş toplama içinde adres</span><span class="sxs-lookup"><span data-stu-id="8efe7-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="8efe7-113">Şekil 9-13'te gösterildiği gibi bir varlığın genellikle birden çok özniteliklerini oluşur.</span><span class="sxs-lookup"><span data-stu-id="8efe7-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="8efe7-114">Örneğin, sipariş kimliğe sahip bir varlık olarak modellenir ve değiştirebilirsiniz dahili OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca karmaşık bir değer adresi ülke, posta, şehir oluşur, vb. modellenir ve bir değer nesnesi kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="8efe7-115">Değer nesnelerin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="8efe7-115">Important characteristics of value objects</span></span>

<span data-ttu-id="8efe7-116">Değer nesneleri için iki ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8efe7-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="8efe7-117">Hiçbir kimlik sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="8efe7-117">They have no identity.</span></span>

-   <span data-ttu-id="8efe7-118">Bunlar değişmez.</span><span class="sxs-lookup"><span data-stu-id="8efe7-118">They are immutable.</span></span>

<span data-ttu-id="8efe7-119">İlk özelliği zaten açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8efe7-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="8efe7-120">Girişi önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-120">Immutability is an important requirement.</span></span> <span data-ttu-id="8efe7-121">Nesne oluşturulduktan sonra bir değer nesnesinin değerlerin sabit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="8efe7-122">Bu nedenle, nesne oluşturulduğunda, gerekli değerleri de sağlamanız gerekir, ancak nesnenin ömrü boyunca değiştirmeye izin vermeniz değil.</span><span class="sxs-lookup"><span data-stu-id="8efe7-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="8efe7-123">Değer nesnelerini değişmez yapılarına sayesinde performans için belirli püf noktaları işlemleri yapmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="8efe7-124">Sistemlerinde özellikle geçerlidir nesne örneklerini değeri binlerce olabilir; Burada, birçok aynı değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="8efe7-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="8efe7-125">Değişmez yapılarına yeniden almalarını sağlar; değerlerine aynıdır ve hiçbir kimliğe sahip olduğundan bunlar birbirinin yerine nesneler olabilir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="8efe7-126">Bu tür bir en iyi duruma getirme bazen yavaş çalışan yazılım ve iyi bir performans yazılımıyla arasında bir fark yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8efe7-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="8efe7-127">Elbette, tüm bu durumlarda, uygulama ortamı ve dağıtım bağlam bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8efe7-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="8efe7-128">Değer nesnesi uygulamasında C\#</span><span class="sxs-lookup"><span data-stu-id="8efe7-128">Value object implementation in C\#</span></span>

<span data-ttu-id="8efe7-129">Uygulama bakımından eşitlik karşılaştırması (bir değer nesnesi kimliği üzerinde temel almalıdır değil bu yana) tüm öznitelikler ve diğer temel özelliklere göre gibi temel yardımcı program yöntemleri olan bir değer nesnesi temel sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="8efe7-130">Aşağıdaki örnek eShopOnContainers gelen sıralama mikro kullanılan bir değer nesnesi temel bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="8efe7-131">Aşağıdaki örnekte gösterilen adres nesnesiyle değer olarak, gerçek değer nesnesi uygularken Bu sınıf kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8efe7-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="8efe7-132">Kimlik özelliğini EF Çekirdek değer nesnelerini kalıcı hale getirmek için kullanılırken gizleme</span><span class="sxs-lookup"><span data-stu-id="8efe7-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="8efe7-133">EF çekirdeği kullanmak, kendi geçerli sürümde (EF çekirdek 1.1) kullanamazsınız olduğunda bir sınırlama [karmaşık türler](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) EF içinde tanımlanan 6.x.</span><span class="sxs-lookup"><span data-stu-id="8efe7-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="8efe7-134">Bu nedenle, değer nesnesi EF varlık olarak depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="8efe7-135">Ancak, kimlik değer nesnesinin bir parçası olan modelde önemli değil netleştirmek için Kimliğini gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8efe7-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="8efe7-136">Kimliği Gizle kimliği gölge özelliği olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8efe7-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="8efe7-137">Model kimliği gizlemek için bu yapılandırma bir altyapı düzeyinde ayarlandığından için etki alanı modelinizin saydam ve altyapı uygulaması gelecekte değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8efe7-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="8efe7-138">EShopOnContainers içinde EF çekirdek altyapısı tarafından gerekli gizli kimliği DbContext düzeyini aşağıdaki şekilde altyapı proje Fluent API kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8efe7-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

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

<span data-ttu-id="8efe7-139">Bu nedenle, etki alanı modeli açısından bakıldığında kimliği gizlidir ve gelecekte değer nesnesi altyapı da karmaşık bir tür veya başka bir yolu olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8efe7-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8efe7-140">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8efe7-140">Additional resources</span></span>

-   <span data-ttu-id="8efe7-141">**Martin Fowler. ValueObject deseni**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="8efe7-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="8efe7-142">**Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling.**</span><span class="sxs-lookup"><span data-stu-id="8efe7-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="8efe7-143">(Kitap; değer nesnelerini tartışması içerir) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="8efe7-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="8efe7-144">**Vaughn Vernon. Etki alanı tabanlı tasarımı uygulama.**</span><span class="sxs-lookup"><span data-stu-id="8efe7-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="8efe7-145">(Kitap; değer nesnelerini tartışması içerir) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="8efe7-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="8efe7-146">**Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="8efe7-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="8efe7-147">**Karmaşık türler ve/veya değer nesnelerini**.</span><span class="sxs-lookup"><span data-stu-id="8efe7-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="8efe7-148">EF çekirdek GitHub deposuna (sorunları sekmesi) tartışmada [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="8efe7-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="8efe7-149">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="8efe7-149">**ValueObject.cs.**</span></span> <span data-ttu-id="8efe7-150">Nesne sınıfında eShopOnContainers taban değeri.</span><span class="sxs-lookup"><span data-stu-id="8efe7-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="8efe7-151">*https://github.com/dotnet/eShopOnContainers/BLOB/master/src/Services/Ordering/Ordering.domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="8efe7-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="8efe7-152">**Sınıf adres.**</span><span class="sxs-lookup"><span data-stu-id="8efe7-152">**Address class.**</span></span> <span data-ttu-id="8efe7-153">Örnek değer nesne sınıfında eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8efe7-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="8efe7-154">*https://github.com/dotnet/eShopOnContainers/BLOB/master/src/Services/Ordering/Ordering.domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="8efe7-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="8efe7-155">[Önceki] (seedwork-domain-model-base-classes-interfaces.md) [sonraki] (numaralandırması-sınıfları-üzerinden-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="8efe7-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
