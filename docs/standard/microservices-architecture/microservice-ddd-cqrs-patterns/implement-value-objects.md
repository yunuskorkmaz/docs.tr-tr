---
title: Değer nesnelerini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Değer nesnelerini uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 4ba2e48e742e580a1c96743fa89e413c488b8dc7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106729"
---
# <a name="implementing-value-objects"></a><span data-ttu-id="90515-103">Değer nesnelerini uygulama</span><span class="sxs-lookup"><span data-stu-id="90515-103">Implementing value objects</span></span>

<span data-ttu-id="90515-104">Varlıklar ve toplamalar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temel önemdedir.</span><span class="sxs-lookup"><span data-stu-id="90515-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="90515-105">Ancak, yoktur çok sayıda nesne ve veri öğelerini bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistem.</span><span class="sxs-lookup"><span data-stu-id="90515-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="90515-106">Bir değer nesnesi diğer varlıklar başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="90515-106">A value object can reference other entities.</span></span> <span data-ttu-id="90515-107">Örneğin, bir noktadan diğerine almayı açıklar bir rota oluşturan bir uygulamada bu rota bir değer nesnesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="90515-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="90515-108">Özel bir rota noktalarında görüntüsünü olacaktır, ancak dahili Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yol bir kimlik sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="90515-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="90515-109">Şekil 9-13 sipariş toplama içinde adresi değer nesnesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="90515-109">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="90515-110">**Şekil 9-13**.</span><span class="sxs-lookup"><span data-stu-id="90515-110">**Figure 9-13**.</span></span> <span data-ttu-id="90515-111">Değer nesnesi sipariş toplama içinde adres</span><span class="sxs-lookup"><span data-stu-id="90515-111">Address value object within the Order aggregate</span></span>

<span data-ttu-id="90515-112">Şekil 9-13'te gösterildiği gibi bir varlığın genellikle birden çok özniteliklerini oluşur.</span><span class="sxs-lookup"><span data-stu-id="90515-112">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="90515-113">Örneğin, `Order` varlığı kimliğe sahip bir varlık olarak modellenir ve dahili olarak OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca karmaşık bir değer adresi ülke, posta, vb. Şehir oluşur ve bu etki alanında yok kimliği vardır, modellenir ve gerekir bir değer nesnesi olarak kabul.</span><span class="sxs-lookup"><span data-stu-id="90515-113">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. and has no identity in this domain,  must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="90515-114">Değer nesnelerin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="90515-114">Important characteristics of value objects</span></span>

<span data-ttu-id="90515-115">Değer nesneleri için iki ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="90515-115">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="90515-116">Hiçbir kimlik sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="90515-116">They have no identity.</span></span>

-   <span data-ttu-id="90515-117">Bunlar değişmez.</span><span class="sxs-lookup"><span data-stu-id="90515-117">They are immutable.</span></span>

<span data-ttu-id="90515-118">İlk özelliği zaten açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="90515-118">The first characteristic was already discussed.</span></span> <span data-ttu-id="90515-119">Girişi önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="90515-119">Immutability is an important requirement.</span></span> <span data-ttu-id="90515-120">Nesne oluşturulduktan sonra bir değer nesnesinin değerlerin sabit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="90515-120">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="90515-121">Bu nedenle, nesne oluşturulduğunda, gerekli değerleri de sağlamanız gerekir, ancak nesnenin ömrü boyunca değiştirmeye izin vermeniz değil.</span><span class="sxs-lookup"><span data-stu-id="90515-121">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="90515-122">Değer nesnelerini değişmez yapılarına sayesinde performans için belirli püf noktaları işlemleri yapmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="90515-122">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="90515-123">Sistemlerinde özellikle geçerlidir nesne örneklerini değeri binlerce olabilir; Burada, birçok aynı değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="90515-123">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="90515-124">Değişmez yapılarına yeniden almalarını sağlar; değerlerine aynıdır ve hiçbir kimliğe sahip olduğundan bunlar birbirinin yerine nesneler olabilir.</span><span class="sxs-lookup"><span data-stu-id="90515-124">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="90515-125">Bu tür bir en iyi duruma getirme bazen yavaş çalışan yazılım ve iyi bir performans yazılımıyla arasında bir fark yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90515-125">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="90515-126">Elbette, tüm bu durumlarda, uygulama ortamı ve dağıtım bağlam bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="90515-126">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="90515-127">Değer nesnesi uygulamasında C\#</span><span class="sxs-lookup"><span data-stu-id="90515-127">Value object implementation in C\#</span></span>

<span data-ttu-id="90515-128">Uygulama bakımından eşitlik karşılaştırması (bir değer nesnesi kimliği üzerinde temel almalıdır değil bu yana) tüm öznitelikler ve diğer temel özelliklere göre gibi temel yardımcı program yöntemleri olan bir değer nesnesi temel sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="90515-128">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="90515-129">Aşağıdaki örnek eShopOnContainers gelen sıralama mikro kullanılan bir değer nesnesi temel bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="90515-129">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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
    // Other utilility methods
}
```

<span data-ttu-id="90515-130">Aşağıdaki örnekte gösterilen adres nesnesiyle değer olarak, gerçek değer nesnesi uygularken Bu sınıf kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90515-130">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; }
    public String City { get; }
    public String State { get; }
    public String Country { get; }
    public String ZipCode { get; }

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

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="90515-131">Değer nesnelerini EF çekirdek 2.0 ile veritabanında kalıcı hale getirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="90515-131">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="90515-132">Yalnızca bir değer nesnesi, etki alanı modeli tanımlamak öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="90515-132">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="90515-133">Ancak nasıl, aslında, genellikle kimlik varlıklarıyla hedefler Entity Framework (EF) çekirdek aracılığıyla veritabanına kalıcı?</span><span class="sxs-lookup"><span data-stu-id="90515-133">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="90515-134">Arka plan ve eski yaklaşımlar EF çekirdek 1.1 kullanma</span><span class="sxs-lookup"><span data-stu-id="90515-134">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="90515-135">Arka plan olarak EF çekirdek 1.0 ve 1.1 kullanırken bir sınırlama, kullanamazsınız edildi [karmaşık türler](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) EF içinde tanımlanan geleneksel .NET Framework'teki 6.x.</span><span class="sxs-lookup"><span data-stu-id="90515-135">As background, a limitation when using EF Core 1.0 and 1.1 was that you cannot use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="90515-136">Bu nedenle, EF çekirdek 1.0 veya 1.1 kullanıyorsanız, kimlik alanı EF varlıkla olarak değer nesnesi depolamak gerekli.</span><span class="sxs-lookup"><span data-stu-id="90515-136">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="90515-137">Ardından, hiçbir kimliği ile bir değer nesnesi gibi daha fazla arama için değer nesne kimliğinin etki alanı modelinde önemli değildir netleştirmek için Kimliğini gizle.</span><span class="sxs-lookup"><span data-stu-id="90515-137">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="90515-138">Kimliği olarak kullanarak bu kimliği Gizle bir [gölge özelliği](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="90515-138">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="90515-139">Model kimliği gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeli için tür saydam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="90515-139">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="90515-140">EShopOnContainers (.NET Core 1.1) ilk sürümünde EF çekirdek altyapısı tarafından gerekli gizli kimliği DbContext düzeyi aşağıdaki yolla altyapı proje Fluent API kullanılarak uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="90515-140">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="90515-141">Bu nedenle, gizli açısından etki alanı modeli, ancak hala mevcut altyapısında kimliği.</span><span class="sxs-lookup"><span data-stu-id="90515-141">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="90515-142">Ancak, bu değer nesnesi Kalıcılık veritabanına farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="90515-142">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="90515-143">EF çekirdek 2.0 ile vardır yeni ve değer nesnelerini kalıcı hale getirmek için daha iyi yolu.</span><span class="sxs-lookup"><span data-stu-id="90515-143">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="90515-144">EF çekirdek 2.0 ait varlık türü olarak değer nesnelerini Sürdür</span><span class="sxs-lookup"><span data-stu-id="90515-144">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="90515-145">Bile bazı boşluklu DDD kurallı değer nesne modelinde EF çekirdek ait varlık türünde arasındaki, bunu şu anda EF çekirdek 2.0 değeri nesneleriyle kalıcı hale getirmek için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="90515-145">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="90515-146">Bu bölümün sonunda sınırlamaları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90515-146">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="90515-147">Ait varlık türü özelliği EF çekirdek 2.0 sürümünden bu yana eklendi.</span><span class="sxs-lookup"><span data-stu-id="90515-147">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="90515-148">Bir ait varlık türü, etki alanı model içinde tanımlanan kendi kimlik explicitely sahip değil ve varlıklarınızı hiçbirini içinde bir değer nesnesi gibi özellikleri olarak kullanılan türleri eşlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="90515-148">An owned entity type allows you to map types that do not have their own identity explicitely defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="90515-149">Bir ait varlık türünün CLR türü aynı başka bir varlık türü ile paylaşır.</span><span class="sxs-lookup"><span data-stu-id="90515-149">An owned entity type shares the same CLR type with another entity type.</span></span> <span data-ttu-id="90515-150">Tanımlayan gezinmeyi içeren varlık sahibi varlıktır.</span><span class="sxs-lookup"><span data-stu-id="90515-150">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="90515-151">Sahibi sorgulanırken ait türleri varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="90515-151">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="90515-152">Tüm kimlik sahip değil yalnızca etki alanı modeli bakarak ait türü görülüyor.</span><span class="sxs-lookup"><span data-stu-id="90515-152">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span>
<span data-ttu-id="90515-153">Kapak altında ait türleri kimliğe sahip, ancak, sahibi gezinti özelliği bu kimliğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="90515-153">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="90515-154">Kendi türlerin örnekleri kimliğini tamamen değil, kendi.</span><span class="sxs-lookup"><span data-stu-id="90515-154">The identity of instances of own types is not completely their own.</span></span> <span data-ttu-id="90515-155">Üç bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="90515-155">It consists of three components:</span></span>

- <span data-ttu-id="90515-156">Sahibinin kimliği</span><span class="sxs-lookup"><span data-stu-id="90515-156">The identity of the owner</span></span>

- <span data-ttu-id="90515-157">İşaret eden gezinti özelliği</span><span class="sxs-lookup"><span data-stu-id="90515-157">The navigation property pointing to them</span></span>

- <span data-ttu-id="90515-158">Söz konusu olduğunda koleksiyonları ait türlerinin bir bağımsız bileşeni (henüz EF çekirdek 2. 0'da desteklenir).</span><span class="sxs-lookup"><span data-stu-id="90515-158">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0).</span></span>

<span data-ttu-id="90515-159">Örneğin, sipariş varlık, bir parçası olarak eShopOnContainers sıralama etki alanı modeli adresi değer nesnesi sipariş varlık sahibi varlık içindeki ait varlık türü olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="90515-159">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="90515-160">Bir etki alanı modelde tanımlı hiçbir kimlik özelliği türüyle adresidir.</span><span class="sxs-lookup"><span data-stu-id="90515-160">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="90515-161">Sipariş türünde bir özellik, belirli bir sıraya sevkiyat adresini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90515-161">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="90515-162">Kural tarafından gölge birincil anahtar ait türü için oluşturulur ve onu sahibi olarak aynı tabloya tablo bölme kullanarak eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="90515-162">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="90515-163">Bunun yapılması sağlar nasıl karmaşık türler EF6 geleneksel .NET Framework'te kullanılan ait kullanım benzer şekilde türleri.</span><span class="sxs-lookup"><span data-stu-id="90515-163">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="90515-164">Bunları açıkça bildirmeniz gerekir böylece türleri hiçbir zaman EF çekirdek, kural tarafından bulunan ait dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="90515-164">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="90515-165">EShopOnContainers içinde OnModelCreating() yöntemi içindeki OrderingContext.cs adresindeki var. uygulanan birden çok altyapısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="90515-165">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="90515-166">Bunlardan birini sipariş varlığa ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="90515-166">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="90515-167">Aşağıdaki kodda sipariş varlık için Kalıcılık altyapı tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="90515-167">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="90515-168">Önceki kod `orderConfiguration.OwnsOne(o => o.Address)` yöntemini belirtir `Address` özelliktir ait bir varlığın `Order` türü.</span><span class="sxs-lookup"><span data-stu-id="90515-168">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="90515-169">Varsayılan olarak, ait varlık türü olarak özelliklerini veritabanı sütunlarını EF çekirdek kuralları ad `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="90515-169">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="90515-170">Bu nedenle, iç özelliklerini `Address` görünür `Orders` tablo adları ile `Address_Street`, `Address_City` (vb. için `State`, `Country` ve `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="90515-170">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="90515-171">Ekleyebilirsiniz `Property().HasColumnName()` bu sütunları yeniden adlandırmak için fluent yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90515-171">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="90515-172">Durumda burada `Address` ortak özellik eşlemeleri şu şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="90515-172">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="90515-173">Zinciri mümkündür `OwnsOne` fluent eşlemeye yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90515-173">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="90515-174">Aşağıdaki örnekte kuramsal, `OrderDetails` sahibi `BillingAddress` ve `ShippingAddress`, her ikisi de olduğu `Address` türleri.</span><span class="sxs-lookup"><span data-stu-id="90515-174">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="90515-175">Ardından `OrderDetails` tarafından sahip olunan `Order` türü.</span><span class="sxs-lookup"><span data-stu-id="90515-175">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="90515-176">Ait varlık türleri hakkında daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="90515-176">Additional details on owned entity types</span></span>

<span data-ttu-id="90515-177">• Türlerine ait OwnsOne fluent API kullanarak belirli bir türde bir gezinti özelliğine yapılandırdığınızda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="90515-177">•   Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

<span data-ttu-id="90515-178">• Bizim meta veri modelindeki ait bir tür tanımını olan bir bileşimi: sahip türü, gezinti özelliği ve ait türünün CLR türü.</span><span class="sxs-lookup"><span data-stu-id="90515-178">•   The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

<span data-ttu-id="90515-179">• Ait türü örneğini bizim yığınında kimliğini (anahtar) sahip türü kimliğini ve ait türü tanımını bileşimi ' dir.</span><span class="sxs-lookup"><span data-stu-id="90515-179">•   The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="90515-180">Varlık özellikleri ait:</span><span class="sxs-lookup"><span data-stu-id="90515-180">Owned entities capabilities:</span></span>

<span data-ttu-id="90515-181">Türü ya da ait diğer varlıklar (iç içe geçmiş ait türleri) başvuruda bulunabilir ait veya ait olmayan • (diğer varlıklar için normal başvuru Gezinti özellikleri).</span><span class="sxs-lookup"><span data-stu-id="90515-181">•   Owned type can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

<span data-ttu-id="90515-182">• Aynı eşleyebilirsiniz CLR farklı ait ayrı Gezinti özellikleri aracılığıyla aynı sahibi varlık türü olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="90515-182">•   You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

<span data-ttu-id="90515-183">• Tablo bölme Kurulum kural tarafından olmakla birlikte, ToTable kullanarak farklı bir tabloya ait türü eşleme tarafından iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="90515-183">•   Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

<span data-ttu-id="90515-184">• İstekli yükleme ait türleri, yani sorguya dayalı Include() çağrısı gerekli otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="90515-184">•   Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="90515-185">Ait varlıkları sınırlamaları:</span><span class="sxs-lookup"><span data-stu-id="90515-185">Owned entities limitations:</span></span>

<span data-ttu-id="90515-186">• Bir DbSet oluşturamıyor<T> (tarafından tasarım) ait bir türde.</span><span class="sxs-lookup"><span data-stu-id="90515-186">•   You cannot create a DbSet<T> of an owned type (by design).</span></span>

<span data-ttu-id="90515-187">• ModelBuilder.Entity çağrılamıyor<T>() ait türleri (şu anda tasarıma göre).</span><span class="sxs-lookup"><span data-stu-id="90515-187">•   You cannot call ModelBuilder.Entity<T>() on owned types (currently by design).</span></span>

<span data-ttu-id="90515-188">Henüz türleri • hiçbir koleksiyonları ait (ancak bunlar sürümlerde EF çekirdek 2.0 sonra desteklenen).</span><span class="sxs-lookup"><span data-stu-id="90515-188">•   No collections of owned types yet (but they will be supported in versions after EF Core 2.0).</span></span>

<span data-ttu-id="90515-189">• Bir öznitelik yapılandırma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="90515-189">•   No support for configuring them via an attribute.</span></span>

<span data-ttu-id="90515-190">• Aynı tablodaki sahibi olan eşlenen isteğe bağlı (yani boş değer atanabilir) ait türleri için destek yok (yani tablo bölme kullanarak).</span><span class="sxs-lookup"><span data-stu-id="90515-190">•   No support for optional (i.e. nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="90515-191">Bu durum, biz null için ayrı bir sentinel yoktur çünkü.</span><span class="sxs-lookup"><span data-stu-id="90515-191">This is because we don't have a separate sentinel for the null.</span></span>

<span data-ttu-id="90515-192">• Devralma eşleme desteği ait türleri, ancak aynı devralma hiyerarşileri ait farklı olarak iki yaprak türünü eşlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="90515-192">•   No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="90515-193">EF çekirdek aynı hiyerarşiye parçası olan olgu hakkında neden değil.</span><span class="sxs-lookup"><span data-stu-id="90515-193">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="90515-194">EF6'ın karmaşık türleri ile temel farklar</span><span class="sxs-lookup"><span data-stu-id="90515-194">Main differences with EF6's complex types</span></span>

<span data-ttu-id="90515-195">• Tablo bölme isteğe bağlıdır, yani isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve hala türlerine ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="90515-195">•   Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

<span data-ttu-id="90515-196">• (Örn. Bunlar bağımlı diğer ait olmayan türlere ilişkileri tarafında üstlenebilir) diğer varlıklar başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="90515-196">•   They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>


## <a name="additional-resources"></a><span data-ttu-id="90515-197">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="90515-197">Additional resources</span></span>

-   <span data-ttu-id="90515-198">**Martin Fowler. ValueObject deseni**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="90515-198">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="90515-199">**Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling.**</span><span class="sxs-lookup"><span data-stu-id="90515-199">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="90515-200">(Kitap; değer nesnelerini tartışması içerir) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="90515-200">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="90515-201">**Vaughn Vernon. Etki alanı tabanlı tasarımı uygulama.**</span><span class="sxs-lookup"><span data-stu-id="90515-201">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="90515-202">(Kitap; değer nesnelerini tartışması içerir) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="90515-202">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="90515-203">**Gölge Özellikleri**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="90515-203">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="90515-204">**Karmaşık türler ve/veya değer nesnelerini**.</span><span class="sxs-lookup"><span data-stu-id="90515-204">**Complex types and/or value objects**.</span></span> <span data-ttu-id="90515-205">EF çekirdek GitHub deposuna (sorunları sekmesi) tartışma [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="90515-205">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="90515-206">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="90515-206">**ValueObject.cs.**</span></span> <span data-ttu-id="90515-207">Nesne sınıfında eShopOnContainers taban değeri.</span><span class="sxs-lookup"><span data-stu-id="90515-207">Base value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="90515-208">**Sınıf adres.**</span><span class="sxs-lookup"><span data-stu-id="90515-208">**Address class.**</span></span> <span data-ttu-id="90515-209">Örnek değer nesne sınıfında eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="90515-209">Sample value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
<span data-ttu-id="90515-210">[Önceki](seedwork-domain-model-base-classes-interfaces.md)
[sonraki](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="90515-210">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
