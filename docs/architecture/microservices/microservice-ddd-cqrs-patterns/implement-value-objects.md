---
title: Değer nesneleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Yeni Entity Framework özelliklerini kullanarak değer nesneleri uygulamak için Ayrıntılar ve seçeneklere ulaşın.
ms.date: 08/21/2020
ms.openlocfilehash: 02eed7baaa364c62aa2df599f1d8b0e700dd215f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811125"
---
# <a name="implement-value-objects"></a><span data-ttu-id="e175c-103">Değer nesneleri uygulama</span><span class="sxs-lookup"><span data-stu-id="e175c-103">Implement value objects</span></span>

<span data-ttu-id="e175c-104">Varlıklar ve toplamalar hakkında daha önceki bölümlerde açıklandığı gibi, varlıklar için de kimlik temel alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="e175c-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="e175c-105">Ancak, bir sistemde, değer nesneleri gibi kimlik ve kimlik izleme gerektirmeyen birçok nesne ve veri öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="e175c-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="e175c-106">Bir değer nesnesi, diğer varlıklara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-106">A value object can reference other entities.</span></span> <span data-ttu-id="e175c-107">Örneğin, bir noktadan diğerine nasıl alınacağını açıklayan bir yol oluşturan bir uygulamada, bu yol bir değer nesnesi olur.</span><span class="sxs-lookup"><span data-stu-id="e175c-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="e175c-108">Bu, belirli bir rotadaki noktaların anlık görüntüsü olacaktır, ancak bu önerilen yolun, dahili olarak şehir, yol vb. varlıklara başvurabileceği bir kimliğe sahip olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="e175c-109">Şekil 7-13, düzen toplama içindeki adres değeri nesnesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e175c-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Düzen toplama içindeki adres değeri-nesnesi gösteren diyagram.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="e175c-111">**Şekil 7-13**.</span><span class="sxs-lookup"><span data-stu-id="e175c-111">**Figure 7-13**.</span></span> <span data-ttu-id="e175c-112">Sıra toplaması içindeki adres değeri nesnesi</span><span class="sxs-lookup"><span data-stu-id="e175c-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="e175c-113">Şekil 7-13 ' de gösterildiği gibi, bir varlık genellikle birden çok öznitelikten oluşur.</span><span class="sxs-lookup"><span data-stu-id="e175c-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="e175c-114">Örneğin, `Order` varlık kimliği olan bir varlık olarak modellenebilir ve OrderID, OrderDate, OrderItems vb. gibi bir öznitelik kümesinin dahili olarak oluşturulmuş olabilir. Ancak, ülke/bölge, cadde, şehir, vb. gibi karmaşık bir değer olan ve bu etki alanında hiçbir kimliği olmayan adresin, modellenmesi ve değer nesnesi olarak kabul edilmesinin gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="e175c-115">Değer nesnelerinin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="e175c-115">Important characteristics of value objects</span></span>

<span data-ttu-id="e175c-116">Değer nesneleri için iki ana özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="e175c-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="e175c-117">Hiçbir kimliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e175c-117">They have no identity.</span></span>

- <span data-ttu-id="e175c-118">Bunlar sabittir.</span><span class="sxs-lookup"><span data-stu-id="e175c-118">They are immutable.</span></span>

<span data-ttu-id="e175c-119">İlk özellik zaten tartılandı.</span><span class="sxs-lookup"><span data-stu-id="e175c-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="e175c-120">Dengeszlik kullanılabilirliği önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="e175c-120">Immutability is an important requirement.</span></span> <span data-ttu-id="e175c-121">Nesne oluşturulduktan sonra bir değer nesnesinin değerleri sabit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e175c-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="e175c-122">Bu nedenle, nesne oluşturulduğunda gerekli değerleri sağlamanız gerekir, ancak nesnenin ömrü boyunca değişmelerine izin vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="e175c-123">Değer nesneleri, belirli püf noktalarını, gerçek sabit doğası sayesinde performans için gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e175c-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="e175c-124">Bu, özellikle de aynı değere sahip binlerce değer nesne örneği olabilen sistemlerde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e175c-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="e175c-125">Sabit doğası, bunların yeniden kullanılmasını sağlar; değerleri aynı olduğundan ve kimlik olmadığından, bunlar değiştirilebilir nesneler olabilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="e175c-126">Bu tür iyileştirme, bazen yavaş çalışan yazılımlar ve iyi performansa sahip yazılımlar arasında farklılık yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="e175c-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="e175c-127">Tabii ki, tüm bu durumlar uygulama ortamına ve dağıtım bağlamına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e175c-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="e175c-128">C 'de değer nesnesi uygulama\#</span><span class="sxs-lookup"><span data-stu-id="e175c-128">Value object implementation in C\#</span></span>

<span data-ttu-id="e175c-129">Uygulama açısından, tüm öznitelikler arasındaki karşılaştırmaya göre (bir değer nesnesi kimlik tabanlı olmaması gerektiğinden) ve diğer temel özelliklerle eşitlik gibi temel yardımcı yöntemlere sahip bir değer nesnesi taban sınıfına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on the comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="e175c-130">Aşağıdaki örnek, eShopOnContainers 'dan sıralama mikro hizmetinde kullanılan bir değer nesnesi temel sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e175c-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="e175c-131">Aşağıdaki örnekte gösterilen adres değeri nesnesi gibi gerçek değer nesneniz uygularken bu sınıfı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e175c-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="e175c-132">Bu değerin nesne uygulamasının bir kimlik olmadığını ve bu nedenle, hiçbir kimlik alanı olmadığını, hiçbir ID alanını ve ne zaman ValueObject sınıfında bile olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="e175c-133">Entity Framework (EF) tarafından kullanılmak üzere bir sınıfta ID alanı olmadığından, KIMLIK olmayan daha iyi değer nesnelerini uygulama konusunda büyük ölçüde yardımcı olan EF Core 2,0 'e kadar mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="e175c-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="e175c-134">Bu, bir sonraki bölümün tam olarak bir açıklaması olur.</span><span class="sxs-lookup"><span data-stu-id="e175c-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="e175c-135">Değer nesnelerinin sabit olması, salt okunurdur (yani salt al özelliklerine sahip) ve gerçekten doğru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="e175c-136">Ancak, değer nesneleri genellikle serileştirilmiş ve seri durumdan çıkarılmış ve ileti kuyruklarıyla birlikte kaldırılacak ve Salt okunabilir hale getirilemez, bu yüzden yalnızca `private set` , pratik olması gereken salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="e175c-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so you just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="e175c-137">EF Core 2,0 ve üzeri ile veritabanında değer nesnelerini kalıcı hale getirme</span><span class="sxs-lookup"><span data-stu-id="e175c-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="e175c-138">Yalnızca etki alanı modelinizde bir değer nesnesinin nasıl tanımlanacağını gördünüz.</span><span class="sxs-lookup"><span data-stu-id="e175c-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="e175c-139">Ancak, genellikle kimliği olan varlıkları hedeflediğinden bu Entity Framework Core kullanarak veritabanını veritabanına nasıl kalıcı hale getirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="e175c-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="e175c-140">EF Core 1,1 kullanarak arka plan ve eski yaklaşımlar</span><span class="sxs-lookup"><span data-stu-id="e175c-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="e175c-141">Arka plan olarak, 1,0 ve 1,1 EF Core kullanılırken, geleneksel .NET Framework EF 6. x bölümünde tanımlandığı gibi [karmaşık türleri](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) kullanmadığınıza ilişkin bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="e175c-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="e175c-142">Bu nedenle, 1,0 veya 1,1 EF Core kullanıyorsanız, değer nesnenizin kimliğini kimlik alanı olan bir EF varlığı olarak depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="e175c-143">Daha sonra, kimliği olmayan bir değer nesnesi gibi daha fazla baktığı için, bir değer nesnesinin kimliğinin etki alanı modelinde önemli olmadığını net hale getirmek için KIMLIĞINI gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="e175c-144">KIMLIĞI bir [Gölge Özellik](https://docs.microsoft.com/ef/core/modeling/shadow-properties )olarak kullanarak bu kimliği gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="e175c-145">Modeldeki KIMLIĞI gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modelinize yönelik bir tür saydam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e175c-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="e175c-146">EShopOnContainers 'un ilk sürümünde (.NET Core 1,1), EF Core altyapısı tarafından gereken gizli KIMLIK, altyapı projesinde akıcı API kullanılarak, DbContext düzeyinde aşağıdaki şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e175c-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="e175c-147">Bu nedenle, KIMLIK, görünümün etki alanı model noktasından gizlendi, ancak hala altyapıda var.</span><span class="sxs-lookup"><span data-stu-id="e175c-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="e175c-148">Ancak, bu değer nesnesinin veritabanına kalıcılığı, farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="e175c-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="e175c-149">EF Core 2,0 ve üzeri sürümlerde, değer nesnelerini kalıcı hale getirmek için yeni ve daha iyi yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="e175c-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="e175c-150">Değer nesnelerini EF Core 2,0 ve sonraki sürümlerde sahip olan varlık türleri olarak kalıcı hale getirme</span><span class="sxs-lookup"><span data-stu-id="e175c-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="e175c-151">DDD 'daki kurallı değer nesne deseninin yanı sıra EF Core sahip olan varlık türü arasında bazı boşluklar olsa da, EF Core 2,0 ve üzeri ile değer nesnelerini kalıcı hale getirmenin en iyi yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e175c-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="e175c-152">Bu bölümün sonundaki sınırlamalara bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="e175c-153">Sahip olan varlık türü özelliği 2,0 sürümünden bu yana EF Core eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e175c-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="e175c-154">Sahip olunan bir varlık türü, kendi kimliğine sahip olmayan türleri etki alanı modelinde açıkça tanımlamış ve varlıklarınızda bir değer nesnesi gibi özellikler olarak kullanılan türleri eşlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e175c-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="e175c-155">Sahip olan bir varlık türü, başka bir varlık türüyle aynı CLR türünü paylaşır (yani, yalnızca normal bir sınıftır).</span><span class="sxs-lookup"><span data-stu-id="e175c-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="e175c-156">Tanımlama gezintisini içeren varlık, sahip varlıktır.</span><span class="sxs-lookup"><span data-stu-id="e175c-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="e175c-157">Sahibi sorgulanırken, sahip olan türler varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="e175c-158">Yalnızca etki alanı modeline bakarak, sahip olunan bir tür herhangi bir kimliğe sahip değil gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="e175c-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="e175c-159">Bununla birlikte, sahip olunan türlerin altında kimlik vardır ancak sahip gezinti özelliği bu kimliğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e175c-159">However, under the covers, owned types do have the identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="e175c-160">Sahip olunan türlerin örneklerinin kimliği tamamen kendi kendine değil.</span><span class="sxs-lookup"><span data-stu-id="e175c-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="e175c-161">Üç bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="e175c-161">It consists of three components:</span></span>

- <span data-ttu-id="e175c-162">Sahibin kimliği</span><span class="sxs-lookup"><span data-stu-id="e175c-162">The identity of the owner</span></span>

- <span data-ttu-id="e175c-163">İşaret eden gezinti özelliği</span><span class="sxs-lookup"><span data-stu-id="e175c-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="e175c-164">Sahip olunan türlerin koleksiyonları durumunda bağımsız bir bileşen (EF Core 2,2 ve üzeri sürümlerde desteklenir).</span><span class="sxs-lookup"><span data-stu-id="e175c-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="e175c-165">Örneğin, eShopOnContainers 'daki sıralama etki alanı modelinde, sipariş varlığının bir parçası olarak, adres değeri nesnesi, sahip varlığı içinde, sipariş varlığı olan bir sahip varlık türü olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e175c-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="e175c-166">`Address` , etki alanı modelinde tanımlanmış Identity özelliği olmayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="e175c-166">`Address` is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="e175c-167">Bu, belirli bir siparişin sevkiyat adresini belirtmek için sipariş türünün bir özelliği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e175c-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="e175c-168">Kurala göre, sahip olunan tür için bir gölge birincil anahtar oluşturulur ve tablo bölme kullanılarak aynı tabloyla aynı tabloyla eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="e175c-169">Bu, sahip oldukları türlerin geleneksel .NET Framework EF6 içinde nasıl kullanıldığı hakkında benzer şekilde kullanılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e175c-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="e175c-170">Sahip oldukları EF Core hiçbir kurala göre hiçbir şekilde bulunamadığına dikkat etmeniz önemlidir, bu nedenle bunları açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e175c-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="e175c-171">EShopOnContainers içinde, OrderingContext.cs dosyasında, yöntemi içinde, `OnModelCreating()` birden çok altyapı yapılandırması uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e175c-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="e175c-172">Bunlardan biri sipariş varlığıyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="e175c-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="e175c-173">Aşağıdaki kodda, sıra varlığı için kalıcılık altyapısı tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="e175c-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="e175c-174">Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntemi, `Address` özelliğin türün sahip olduğu bir varlık olduğunu belirtir `Order` .</span><span class="sxs-lookup"><span data-stu-id="e175c-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="e175c-175">Varsayılan olarak EF Core kurallar, sahip olduğu varlık türünün özelliklerinin veritabanı sütunlarını olarak adlandırın `EntityProperty_OwnedEntityProperty` .</span><span class="sxs-lookup"><span data-stu-id="e175c-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="e175c-176">Bu nedenle, iç özellikleri, `Address` `Orders` `Address_Street` `Address_City` (ve için,, ve için) adlarına sahip tabloda görüntülenir `State` `Country` `ZipCode` .</span><span class="sxs-lookup"><span data-stu-id="e175c-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="e175c-177">`Property().HasColumnName()`Bu sütunları yeniden adlandırmak için floent metodunu ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="e175c-178">Ortak özellik olduğu durumlarda `Address` , eşlemeler aşağıdakine benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="e175c-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="e175c-179">`OwnsOne`Yöntemi akıcı bir eşlemede zincirlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e175c-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="e175c-180">Aşağıdaki kuramsal örnekte, ve olan `OrderDetails` `BillingAddress` ve `ShippingAddress` her iki tür olan `Address` .</span><span class="sxs-lookup"><span data-stu-id="e175c-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="e175c-181">Daha sonra `OrderDetails` `Order` türüne aittir.</span><span class="sxs-lookup"><span data-stu-id="e175c-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="e175c-182">Sahip olunan varlık türleri hakkında ek ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e175c-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="e175c-183">Sahip olan türler, OwnsOne Fluent API kullanarak belirli bir türe bir gezinti özelliği yapılandırdığınızda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e175c-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="e175c-184">Meta veri modelinizdeki sahip olunan bir türün tanımı, bir bileşiminin türü, gezinti özelliği ve sahip olunan türün CLR türü.</span><span class="sxs-lookup"><span data-stu-id="e175c-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="e175c-185">Yığınımızda sahip olan bir tür örneğinin kimliği (anahtarı), sahip türünün kimliğinin ve sahip olunan türün tanımının bir bileşiminin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e175c-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="e175c-186">Sahip olunan varlıkların özellikleri</span><span class="sxs-lookup"><span data-stu-id="e175c-186">Owned entities capabilities</span></span>

- <span data-ttu-id="e175c-187">Sahip olunan türler, sahip olunan (iç içe geçmiş türler) veya sahip olmayan (diğer varlıklara ait normal başvuru gezinti özellikleri) diğer varlıklara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="e175c-188">Aynı CLR türünü, ayrı gezinti özellikleri aracılığıyla aynı sahip varlıktaki farklı sahip türlerle eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="e175c-189">Tablo bölme kurala göre ayarlanır, ancak ait türü ToTable kullanarak farklı bir tabloyla eşleyerek bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="e175c-190">Eager yüklemesi, sahip olunan türler üzerinde otomatik olarak gerçekleştirilir, yani sorgu üzerinde çağrı yapmanız gerekmez `.Include()` .</span><span class="sxs-lookup"><span data-stu-id="e175c-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="e175c-191">`[Owned]`EF Core 2,1 ve üzeri kullanılarak özniteliğiyle yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e175c-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="e175c-192">, Sahip olunan türlerin koleksiyonlarını işleyebilir (sürüm 2,2 ve üzeri kullanarak).</span><span class="sxs-lookup"><span data-stu-id="e175c-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="e175c-193">Sahip olunan varlıkların sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="e175c-193">Owned entities limitations</span></span>

- <span data-ttu-id="e175c-194">`DbSet<T>`Sahip olunan bir tür (tasarıma göre) oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e175c-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="e175c-195">`ModelBuilder.Entity<T>()`Sahip olunan türler üzerinde çağrılamaz (Şu anda tasarım kaynaklı).</span><span class="sxs-lookup"><span data-stu-id="e175c-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="e175c-196">Aynı tablodaki (yani, tablo bölme kullanılarak) sahip ile eşlenmiş isteğe bağlı (null yapılabilir) türler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e175c-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="e175c-197">Bunun nedeni her bir özellik için eşlemenin yapıldığından, null karmaşık değer için bir bütün olarak ayrı bir Sentinel yoktur.</span><span class="sxs-lookup"><span data-stu-id="e175c-197">This is because mapping is done for each property, there is no  separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="e175c-198">Sahip olunan türler için devralma-eşleme desteği yoktur, ancak aynı devralma hiyerarşilerindeki iki yaprak türünü farklı sahipli türlerle eşleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e175c-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="e175c-199">EF Core, aynı hiyerarşinin bir parçası oldukları gerçeğiyle ilgili bir neden olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e175c-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="e175c-200">EF6's karmaşık türlerle ana farklılıklar</span><span class="sxs-lookup"><span data-stu-id="e175c-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="e175c-201">Tablo bölme isteğe bağlıdır, diğer bir deyişle, isteğe bağlı olarak ayrı bir tabloyla eşleştirilebilir ve sahip oldukları türler de vardır.</span><span class="sxs-lookup"><span data-stu-id="e175c-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="e175c-202">Diğer varlıklara başvurabilir (diğer bir deyişle, bağımlı olan diğer türlere ilişkilerle ilgili olarak görev yapabilir).</span><span class="sxs-lookup"><span data-stu-id="e175c-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e175c-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e175c-203">Additional resources</span></span>

- <span data-ttu-id="e175c-204">**Marwler. ValueObject kalıbı** </span><span class="sxs-lookup"><span data-stu-id="e175c-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="e175c-205">**Eric Evans. Etki alanı odaklı tasarım: yazılım Kalbunda karmaşıklık karmaşıklığı.**</span><span class="sxs-lookup"><span data-stu-id="e175c-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="e175c-206">(Kitap; değer nesnelerinin bir tartışmasını içerir) </span><span class="sxs-lookup"><span data-stu-id="e175c-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="e175c-207">**Vaughn versuz. Etki alanı odaklı tasarım uygulama.**</span><span class="sxs-lookup"><span data-stu-id="e175c-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="e175c-208">(Kitap; değer nesnelerinin bir tartışmasını içerir) </span><span class="sxs-lookup"><span data-stu-id="e175c-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="e175c-209">**Sahip olan varlık türleri** </span><span class="sxs-lookup"><span data-stu-id="e175c-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="e175c-210">**Gölge özellikleri** </span><span class="sxs-lookup"><span data-stu-id="e175c-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="e175c-211">**Karmaşık türler ve/veya değer nesneleri**.</span><span class="sxs-lookup"><span data-stu-id="e175c-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="e175c-212">EF Core GitHub deposu 'nda tartışma (sorunlar sekmesi) </span><span class="sxs-lookup"><span data-stu-id="e175c-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="e175c-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="e175c-213">**ValueObject.cs.**</span></span> <span data-ttu-id="e175c-214">EShopOnContainers içindeki temel değer nesne sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e175c-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="e175c-215">**Adres sınıfı.**</span><span class="sxs-lookup"><span data-stu-id="e175c-215">**Address class.**</span></span> <span data-ttu-id="e175c-216">EShopOnContainers içinde örnek değer nesne sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e175c-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="e175c-217">[Önceki](seedwork-domain-model-base-classes-interfaces.md) 
>  [Sonraki](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="e175c-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
