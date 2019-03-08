---
title: Değer nesneleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Ayrıntıları ve Entity Framework yenilikleri kullanarak değer nesneleri uygulama seçenekleri alın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 28f5a5148b39b60d69fecc8bf1273445ebad4953
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675023"
---
# <a name="implement-value-objects"></a><span data-ttu-id="dd0b3-103">Değer nesneleri uygulama</span><span class="sxs-lookup"><span data-stu-id="dd0b3-103">Implement value objects</span></span>

<span data-ttu-id="dd0b3-104">Varlıklar ve toplamlar hakkında önceki bölümlerde açıklandığı gibi kimlik varlıklar için temeldir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="dd0b3-105">Ancak, vardır birçok nesneleri ve veri öğeleri bir kimlik ve kimlik, değer nesneleri gibi izleme gerektirmeyen bir sistemde.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="dd0b3-106">Bir değer nesnesi diğer varlıkların başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-106">A value object can reference other entities.</span></span> <span data-ttu-id="dd0b3-107">Örneğin, bir noktasından diğerine alma açıklayan bir yol oluşturur bir uygulamada yönlendiren bir değer nesnesi olur.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="dd0b3-108">Belirli bir yol noktalarında anlık görüntüsünü olacaktır, ancak dahili olarak Şehir, yol, vb. gibi varlıkları belirtebilir olsa bile bu önerilen yolu bir kimlik sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="dd0b3-109">Şekil 7-13 adresi değer nesnesini sipariş toplama içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Adresi değeri-nesne sipariş toplama içinde.](./media/image14.png)

<span data-ttu-id="dd0b3-111">**Şekil 7-13**.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-111">**Figure 7-13**.</span></span> <span data-ttu-id="dd0b3-112">İçindeki sırası toplam değer nesnesi adresi</span><span class="sxs-lookup"><span data-stu-id="dd0b3-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="dd0b3-113">Şekil 7-13'te gösterildiği gibi bir varlık, genellikle birden çok özniteliklerini oluşur.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="dd0b3-114">Örneğin, `Order` varlığı kimliğe sahip bir varlık olarak modellenir ve dahili olarak OrderID, OrderDate, OrderItems vb. gibi öznitelikleri kümesi oluşur. Ancak yalnızca bir karmaşık değerli adresi, ülke, posta, şehir, vb. oluşur ve kimliksiz bu etki alanında var, gerekir modellenir ve bir değer nesnesi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="dd0b3-115">Değer nesnelerin önemli özellikler</span><span class="sxs-lookup"><span data-stu-id="dd0b3-115">Important characteristics of value objects</span></span>

<span data-ttu-id="dd0b3-116">Değer nesneleri için iki ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="dd0b3-117">Hiçbir kimlik sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-117">They have no identity.</span></span>

- <span data-ttu-id="dd0b3-118">Bunlar sabittir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-118">They are immutable.</span></span>

<span data-ttu-id="dd0b3-119">İlk özelliği zaten açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="dd0b3-120">Değiştirilemezlik önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-120">Immutability is an important requirement.</span></span> <span data-ttu-id="dd0b3-121">Nesne oluşturulduktan sonra bir değer nesnesini değerini sabit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="dd0b3-122">Bu nedenle, bir nesne oluşturulduğunda, gerekli değerler sağlamanız gerekir ancak, bunları nesne ömrü boyunca değiştirmek izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="dd0b3-123">Değeri nesneler performans için sabit doğasını sayesinde belirli püf noktaları işlemleri yapmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="dd0b3-124">Bu sistemlerde özellikle doğrudur nesne örneklerini değer binlerce olabilir Burada, çoğu aynı değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="dd0b3-125">Sabit doğasını yeniden olanak sağlar; birbirinin yerine nesneleri değerlerine aynıdır ve bunlar herhangi bir kimliğe sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="dd0b3-126">Bu tür bir en iyi duruma getirme, bazen yavaş çalışan yazılım ve iyi performans yazılım arasında bir fark yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="dd0b3-127">Elbette, tüm bu durumlarda, uygulama ortamı ve dağıtım bağlam bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="dd0b3-128">C'de değeri nesne uygulama\#</span><span class="sxs-lookup"><span data-stu-id="dd0b3-128">Value object implementation in C\#</span></span>

<span data-ttu-id="dd0b3-129">Uygulama açısından eşitlik karşılaştırması bu yana (bir değer nesnesi kimliğini dayanması değil) tüm öznitelikler ve diğer temel özelliklerine göre gibi temel yardımcı program yöntemleri sahip bir değer nesnesi temel sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="dd0b3-130">Aşağıdaki örnek, sıralama mikro hizmetine gelen kullanılan değer nesnesi temel bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="dd0b3-131">Aşağıdaki örnekte gösterilen adresi değer nesnesini gibi ile gerçek değer nesnenizin uygularken Bu sınıf kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="dd0b3-132">Kimlik ve bu nedenle, hiçbir Kimliği alanı ne adresi sınıfı bile ValueObject sınıfı, bu adresi değer nesnesini uygulaması nasıl sahip olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="dd0b3-133">EF Core 2.0, önemli ölçüde daha iyi değeri uygulamak için yardımcı olan herhangi bir kimliğe sahip nesneleri kadar hiçbir Kimliği alanı Entity Framework tarafından kullanılacak bir sınıf olması mümkün değildi</span><span class="sxs-lookup"><span data-stu-id="dd0b3-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="dd0b3-134">Tam olarak bir sonraki bölüm açıklaması olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="dd0b3-135">Değer nesneleri, sabit, olan salt okunur (yani salt alma Özellikler) olması gerektiğini tartışılabilir ve gerçekten de true.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="dd0b3-136">Ancak, değer nesneler genellikle serileştirilmiş ve ileti kuyrukları gitmek için seri durumdan ve salt okunur olan, böylece biz yalnızca bunları kullanışlı olması için salt okunur yeterince özel ayarlı bırakın gelen değerler, atama seri durumdan çıkarıcının durdurur.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="dd0b3-137">Değer EF Core 2.0 ile veritabanı nesnelerini kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="dd0b3-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="dd0b3-138">Yalnızca, etki alanı modeli içinde bir değer nesnesini tanımlamak öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="dd0b3-139">Ancak, nasıl, aslında Bu kimliğe sahip varlıklar genellikle hedefleyen Entity Framework (EF) çekirdek aracılığıyla veritabanına kalıcı hale getirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="dd0b3-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="dd0b3-140">Arka plan ve EF Core 1.1 kullanarak eski yaklaşımları</span><span class="sxs-lookup"><span data-stu-id="dd0b3-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="dd0b3-141">Arka planı olarak değil kullanabilirsiniz, EF Core 1.0 ve 1.1 kullanırken bir sınırlama olan [karmaşık türler](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) EF tanımlandığı gibi geleneksel .NET Framework 6.x.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="dd0b3-142">Bu nedenle, EF Core 1.0 veya 1.1 kullanıyorsanız, değer nesnesi Kimliği alanı ile EF varlık olarak depolamak gerekli.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="dd0b3-143">Ardından, hiçbir kimlik ile bir değer nesnesi gibi daha fazla görünüyordu için bir değer nesnesi kimliğini etki alanı modeli içinde önemli olduğunu netleştirmek için Kimliğine gizle.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="dd0b3-144">Kimliği'ni kullanarak bu kimliği gizlemek bir [gölge özelliği](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="dd0b3-145">Modeli Kimliğini gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeliniz için tür saydam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="dd0b3-146">Hizmetine (.NET Core 1.1) ilk sürümünde, EF Core altyapısı tarafından gereken gizli kimliği şu şekilde DbContext düzeyinde altyapı proje Fluent API'sini kullanarak uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="dd0b3-147">Bu nedenle, etki alanı modeli açısından gizli ancak hala mevcut altyapı kimliği.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="dd0b3-148">Ancak, bu değer nesnesi bir Kalıcılık veritabanına gibi farklı bir tablo normal bir varlıkta gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="dd0b3-149">EF Core 2.0 ile vardır yeni ve değer nesnelerini kalıcı hale getirmek için daha iyi yollar.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="dd0b3-150">Değer nesneleri olarak sahip olunan varlık türleri EF Core 2.0 Sürdür</span><span class="sxs-lookup"><span data-stu-id="dd0b3-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="dd0b3-151">Hatta bazı aralıklı olarak sahip olunan varlık türünde EF Core DDD kurallı değer nesne modelinde arasındaki, bunu şu anda değer nesneleri EF Core 2.0 ile kalıcı hale getirmek için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="dd0b3-152">Bu bölümün sonunda sınırlamaları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="dd0b3-153">Sahip olunan varlık türü özelliği EF Core 2.0 sürümünden itibaren eklendi.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="dd0b3-154">Sahip olunan varlık türü kendi kimlik etki alanı modeli içinde açıkça tanımlanmış yoksa ve tüm varlıklarınızı içinde bir değer nesnesi gibi bir özellik olarak kullanılan türler eşlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="dd0b3-155">Sahip olunan varlık türü başka bir varlık türü ile aynı CLR türüne paylaşımları (diğer bir deyişle, bu normal bir sınıfın'dir).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="dd0b3-156">Tanımlama Gezinti içeren varlık sahibi varlıktır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="dd0b3-157">Sahibi sorgularken, sahip olunan türleri varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="dd0b3-158">Herhangi bir kimliğe sahip değil yalnızca etki alanı modeli bakarak sahibi bir türü görülüyor.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="dd0b3-159">Ancak, kapsar ait türleri kimliğe sahip, ancak sahip gezinme özelliği bu kimliğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="dd0b3-160">Sahip olunan türlerin örneklerini kimliğini tamamen değil, kendi.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="dd0b3-161">Bu üç bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-161">It consists of three components:</span></span>

- <span data-ttu-id="dd0b3-162">Sahibi kimliği</span><span class="sxs-lookup"><span data-stu-id="dd0b3-162">The identity of the owner</span></span>

- <span data-ttu-id="dd0b3-163">İşaret eden gezinti özelliği</span><span class="sxs-lookup"><span data-stu-id="dd0b3-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="dd0b3-164">Söz konusu olduğunda koleksiyon sahibi türlerinin bir bağımsız bileşeni (henüz 2.2 yakında EF Core 2.0 desteklenmiyor).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="dd0b3-165">Örneğin, sipariş varlığı bir parçası olarak hizmetine sıralama etki alanı modeli içinde adresi değer nesnesini bir sipariş varlık sahibi varlık içindeki sahip olunan varlık türü olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="dd0b3-166">Etki alanı modeli içinde tanımlanan hiçbir kimlik özelliğini türüyle adresidir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="dd0b3-167">Sipariş türünde bir özellik, belirli bir siparişi teslimat adresini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="dd0b3-168">Kural olarak, sahip olunan türü için gölge birincil anahtar oluşturulur ve onu aynı tablonun sahibi olarak tablo bölmeyi kullanarak eşleneceğini.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="dd0b3-169">Bu olanak EF6 geleneksel .NET Framework içinde nasıl karmaşık türler için kullanılan ait kullanım benzer şekilde türleri.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="dd0b3-170">Bunları bildirdiğinizde açıkça zorunda türleri hiçbir zaman EF Core kuralı tarafından bulunan ait dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="dd0b3-171">Hizmetine OnModelCreating() metodundaki OrderingContext.cs adresindeki var. uygulanan birden çok altyapısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd0b3-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="dd0b3-172">Bunlardan biri, sipariş varlığı için ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="dd0b3-173">Aşağıdaki kodda sipariş varlığı için Kalıcılık altyapısı olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="dd0b3-174">Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntemini belirtir `Address` özelliğidir, sahip olunan varlık `Order` türü.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="dd0b3-175">Varsayılan sahip olunan varlık türünün özelliklerini veritabanı sütunlarını EF Core kuralları ad `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="dd0b3-176">Bu nedenle, iç özelliklerini `Address` görünür `Orders` tablo adları ile `Address_Street`, `Address_City` (vb. için `State`, `Country` ve `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="dd0b3-177">Ekleyebilirsiniz `Property().HasColumnName()` bu sütunları yeniden adlandırma için fluent yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="dd0b3-178">Durumda burada `Address` ortak bir özellik eşlemeleri aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="dd0b3-179">Zincire mümkündür `OwnsOne` fluent eşlemesinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="dd0b3-180">Aşağıdaki örnekte kuramsal, `OrderDetails` sahibi `BillingAddress` ve `ShippingAddress`, her ikisi de olduğu `Address` türleri.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="dd0b3-181">Ardından `OrderDetails` tarafından sahip olunan `Order` türü.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="dd0b3-182">Sahip olunan varlık türleri hakkında daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="dd0b3-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="dd0b3-183">Sahip olunan türleri OwnsOne fluent API'sini kullanarak belirli bir tür için bir gezinti özelliği yapılandırdığınızda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="dd0b3-184">Sahip olunan bir meta veri modelimizi türünün bileşik bir tanımıdır: sahip türü, gezinme özelliğini ve şirkete ait türünün CLR türü.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="dd0b3-185">(Anahtar) bizim yığınında ait türü örneği bir bileşik sahip türünün kimliği ve sahip olduğu türü tanımı kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="dd0b3-186">Sahip olunan varlık özellikleri:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="dd0b3-187">Türleri ya da ait diğer varlıklar (iç içe geçmiş türler sahip olunan) başvurabilir ait veya sahibi olmayan (normal başvuru Gezinti özellikleri diğer varlıklar için).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="dd0b3-188">Şirkete ait farklı ayrı Gezinti özellikleri aracılığıyla aynı sahibi varlıktaki aynı CLR türü eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="dd0b3-189">Tablo bölme kural tarafından Kurulum olmakla birlikte, farklı bir tabloya ToTable kullanarak eşleme tarafından sahip olunan türü geri çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="dd0b3-190">İstekli yükleme otomatik olarak sahip olunan türlerinde Include() üzerindeki sorgu çağırmaya yani gerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="dd0b3-191">Özniteliği ile yapılandırılabilir \[ait\], EF Core 2.1 gibi</span><span class="sxs-lookup"><span data-stu-id="dd0b3-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="dd0b3-192">Sahip olunan varlık sınırlamaları:</span><span class="sxs-lookup"><span data-stu-id="dd0b3-192">Owned entities limitations:</span></span>

- <span data-ttu-id="dd0b3-193">Bir olan DB oluşturulamıyor\<T\> (Tasarım tarafından) sahip olunan bir türü.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="dd0b3-194">ModelBuilder.Entity çağrılamıyor\<T\>((şu anda tasarıma) ait türlerinde).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="dd0b3-195">Koleksiyon sahibi türleri henüz (itibarıyla EF Core 2.1 ancak 2.2 içinde desteklenecek).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="dd0b3-196">Desteği isteğe bağlı (diğer bir deyişle, boş değer atanabilir) sahibiyle aynı tablodaki eşlenen türlerine ait (yani tablo bölmeyi kullanarak).</span><span class="sxs-lookup"><span data-stu-id="dd0b3-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="dd0b3-197">Eşleme için her bir özellik yapıldığı için bu, biz null karmaşık değer için ayrı bir sentinel olarak yoksa tüm.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="dd0b3-198">Devralma eşleme desteği türlerine sahip olduğu, ancak iki yaprak şirkete ait farklı olarak aynı devralma hiyerarşilerini eşleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="dd0b3-199">EF Core aynı hiyerarşiye bir parçası olduğundan olgu hakkında neden değil.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="dd0b3-200">EF6'ın karmaşık türleri ile temel farklar</span><span class="sxs-lookup"><span data-stu-id="dd0b3-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="dd0b3-201">Tablo bölme isteğe bağlıdır, yani bunlar isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve hala türlerine ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="dd0b3-202">Bunlar, diğer varlıklara (yani bunlar diğer ait olmayan türlere ilişkileri bağımlı tarafında üstlenebilir) başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dd0b3-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dd0b3-203">Additional resources</span></span>

- <span data-ttu-id="dd0b3-204">**Martin Fowler. ValueObject düzeni** \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-204">**Martin Fowler. ValueObject pattern** \\</span></span>
  [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

- <span data-ttu-id="dd0b3-205">**Eric Evans. Etki alanı Odaklı Tasarım: Kuruluşlarda karmaşık yazılım kalbidir.**</span><span class="sxs-lookup"><span data-stu-id="dd0b3-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="dd0b3-206">(Kitap; değer nesneleri hakkında ayrıntılı bilgi içerir) \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-206">(Book; includes a discussion of value objects) \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- <span data-ttu-id="dd0b3-207">**Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım.**</span><span class="sxs-lookup"><span data-stu-id="dd0b3-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="dd0b3-208">(Kitap; değer nesneleri hakkında ayrıntılı bilgi içerir) \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-208">(Book; includes a discussion of value objects) \\</span></span>
  [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- <span data-ttu-id="dd0b3-209">**Gölge Özellikler** \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-209">**Shadow Properties** \\</span></span>
  [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

- <span data-ttu-id="dd0b3-210">**Karmaşık türler ve/veya değer nesneleri**.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="dd0b3-211">EF Core GitHub deposunda (sorunlar sekmesinden) tartışma \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-211">Discussion in the EF Core GitHub repo (Issues tab) \\</span></span>
  [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

- <span data-ttu-id="dd0b3-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="dd0b3-212">**ValueObject.cs.**</span></span> <span data-ttu-id="dd0b3-213">Temel değer nesne sınıfında eShopOnContainers.* * \\</span><span class="sxs-lookup"><span data-stu-id="dd0b3-213">Base value object class in eShopOnContainers.**  \\</span></span>
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

- <span data-ttu-id="dd0b3-214">**Sınıf adresi.**</span><span class="sxs-lookup"><span data-stu-id="dd0b3-214">**Address class.**</span></span> <span data-ttu-id="dd0b3-215">Örnek değer hizmetine nesne sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dd0b3-215">Sample value object class in eShopOnContainers.</span></span> \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)

> [!div class="step-by-step"]
> <span data-ttu-id="dd0b3-216">[Önceki](seedwork-domain-model-base-classes-interfaces.md)
> [İleri](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="dd0b3-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
