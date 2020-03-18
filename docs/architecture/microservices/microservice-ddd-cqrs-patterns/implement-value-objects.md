---
title: Değer nesneleri uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Yeni Varlık Çerçevesi özelliklerini kullanarak değer nesnelerini uygulamak için ayrıntılara ve seçeneklere bakın.
ms.date: 01/30/2020
ms.openlocfilehash: 4ace5c141b1cbd2dcfefb7ea7165a4006b130479
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502509"
---
# <a name="implement-value-objects"></a><span data-ttu-id="6c220-103">Değer nesnelerini uygulama</span><span class="sxs-lookup"><span data-stu-id="6c220-103">Implement value objects</span></span>

<span data-ttu-id="6c220-104">Varlıklar ve toplamlar hakkında önceki bölümlerde ele alındığı gibi, kimlik varlıklar için esastır.</span><span class="sxs-lookup"><span data-stu-id="6c220-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="6c220-105">Ancak, bir sistemde değer nesneleri gibi kimlik ve kimlik izleme gerektirmeyen birçok nesne ve veri öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="6c220-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="6c220-106">Bir değer nesnesi diğer varlıklara başvuruyapabilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-106">A value object can reference other entities.</span></span> <span data-ttu-id="6c220-107">Örneğin, bir noktadan diğerine nasıl alınacağını açıklayan bir rota oluşturan bir uygulamada, bu yol bir değer nesnesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6c220-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="6c220-108">Bu belirli bir rota üzerinde noktaların bir anlık görüntü olurdu, ancak bu önerilen rota bir kimlik olmazdı, dahili şehir, yol, vb gibi varlıklar atıfta bulunsa bile.</span><span class="sxs-lookup"><span data-stu-id="6c220-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="6c220-109">Şekil 7-13, Sipariş toplamıiçindeki Adres değeri nesnesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c220-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Sipariş Toplamı'nın içindeki Adres değeri nesnesini gösteren diyagram.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="6c220-111">**Şekil 7-13**.</span><span class="sxs-lookup"><span data-stu-id="6c220-111">**Figure 7-13**.</span></span> <span data-ttu-id="6c220-112">Sipariş toplamı içindeki adres değeri nesnesi</span><span class="sxs-lookup"><span data-stu-id="6c220-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="6c220-113">Şekil 7-13'te gösterildiği gibi, bir varlık genellikle birden çok özniteliklerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c220-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="6c220-114">Örneğin, `Order` varlık bir kimliğe sahip bir varlık olarak modellenebilir ve Sipariş Kimliği, OrderDate, OrderItems, vb. gibi öznitelikler kümesinden dahili olarak oluşturulabilir. Ancak, sadece ülke/bölge, sokak, şehir, vb. oluşan karmaşık bir değer olan ve bu etki alanında kimliği olmayan adres, modellenmeli ve bir değer nesnesi olarak ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="6c220-115">Değer nesnelerinin önemli özellikleri</span><span class="sxs-lookup"><span data-stu-id="6c220-115">Important characteristics of value objects</span></span>

<span data-ttu-id="6c220-116">Değer nesneleri için iki ana özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="6c220-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="6c220-117">Kimlikleri yok.</span><span class="sxs-lookup"><span data-stu-id="6c220-117">They have no identity.</span></span>

- <span data-ttu-id="6c220-118">Değişmezler.</span><span class="sxs-lookup"><span data-stu-id="6c220-118">They are immutable.</span></span>

<span data-ttu-id="6c220-119">İlk karakteristik zaten tartışıldı.</span><span class="sxs-lookup"><span data-stu-id="6c220-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="6c220-120">Değişmezlik önemli bir gerekliliktir.</span><span class="sxs-lookup"><span data-stu-id="6c220-120">Immutability is an important requirement.</span></span> <span data-ttu-id="6c220-121">Nesne oluşturulduktan sonra bir değer nesnesinin değerleri değişmez olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="6c220-122">Bu nedenle, nesne oluşturulduğunda, gerekli değerleri sağlamanız gerekir, ancak nesnenin ömrü boyunca bunların değişmesine izin vermemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="6c220-123">Değer nesneleri, değişmez doğası sayesinde performans için belirli hileler gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c220-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="6c220-124">Bu, özellikle, çoğu aynı değerlere sahip binlerce değer nesnesi örneği olabilecek sistemlerde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6c220-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="6c220-125">Değişmez doğaları yeniden kullanılmalarını sağlar; değerleri aynı olduğundan ve kimlikleri olmadığından değiştirilebilir nesneler olabilirler.</span><span class="sxs-lookup"><span data-stu-id="6c220-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="6c220-126">Bu tür optimizasyon bazen yavaş çalışan yazılım ve iyi performans ile yazılım arasında bir fark yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="6c220-127">Tabii ki, tüm bu durumlarda uygulama ortamı ve dağıtım bağlamında bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="6c220-128">C'de değer nesnesi uygulaması\#</span><span class="sxs-lookup"><span data-stu-id="6c220-128">Value object implementation in C\#</span></span>

<span data-ttu-id="6c220-129">Uygulama açısından, tüm öznitelikler (bir değer nesnesi kimliğe dayalı olmamalıdır) ve diğer temel özellikleri arasında karşılaştırma dayalı eşitlik gibi temel yardımcı program yöntemleri olan bir değer nesnesi taban sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="6c220-130">Aşağıdaki örnekte, eShopOnContainers'dan sipariş mikrohizmetinde kullanılan bir değer nesnesi taban sınıfı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c220-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="6c220-131">Aşağıdaki örnekte gösterilen Adres değeri nesnesinde olduğu gibi, gerçek değer nesnenizi uygularken bu sınıfı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6c220-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="6c220-132">Adres'in bu değer nesnesi uygulamasının nasıl bir kimliği olmadığını ve bu nedenle, Değer Nesnesi sınıfında bile Adres sınıfında kimlik alanı olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="6c220-133">Varlık Çerçevesi (EF) tarafından kullanılacak bir sınıfta kimlik alanı olmaması, kimliği olmayan daha iyi değer nesnelerinin uygulanmasına büyük ölçüde yardımcı olan EF Core 2.0'a kadar mümkün değildi.</span><span class="sxs-lookup"><span data-stu-id="6c220-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="6c220-134">Bu tam olarak bir sonraki bölümün açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="6c220-135">Bu değer nesneleri, değişmez olan, salt okunur olması gerektiğini iddia edilebilir (yani, sadece almak özellikleri var), ve bu gerçekten doğrudur.</span><span class="sxs-lookup"><span data-stu-id="6c220-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="6c220-136">Ancak, değer nesneleri genellikle ileti kuyrukları üzerinden gitmek için seri ve deserialized ve salt okunur değerleri atama deserializer durur, bu yüzden sadece pratik olması için yeterli okunur özel küme olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="6c220-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="6c220-137">EF Core 2.0 ve sonrası ile veritabanındaki değer nesneleri nasıl kalıcı</span><span class="sxs-lookup"><span data-stu-id="6c220-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="6c220-138">Etki alanı modelinizde bir değer nesnesini nasıl tanımladığınızı gördün.</span><span class="sxs-lookup"><span data-stu-id="6c220-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="6c220-139">Ama nasıl aslında veritabanında Genellikle kimlik ile varlıkları hedefleyen varlık Framework Core kullanarak veritabanında devam edebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="6c220-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="6c220-140">EF Core 1.1 kullanarak arka plan ve eski yaklaşımlar</span><span class="sxs-lookup"><span data-stu-id="6c220-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="6c220-141">Arka plan olarak, EF Core 1.0 ve 1.1 kullanırken bir sınırlama, geleneksel .NET Framework'de EF 6.x'te tanımlandığı gibi [karmaşık türleri](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) kullanamamanızdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="6c220-142">Bu nedenle, EF Core 1.0 veya 1.1 kullanıyorsanız, değer nesnenizi kimlik alanına sahip bir EF varlığı olarak depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c220-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="6c220-143">Daha sonra, daha çok kimliği olmayan bir değer nesnesine benzemektedir, böylece etki alanı modelinde bir değer nesnesinin kimliğinin önemli olmadığını açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="6c220-144">Kimliği [gölge özellik](https://docs.microsoft.com/ef/core/modeling/shadow-properties )olarak kullanarak bu kimliği gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="6c220-145">Modelde kimliği gizlemek için bu yapılandırma EF altyapı düzeyinde ayarlandığından, etki alanı modeli için saydam tür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6c220-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="6c220-146">eShopOnContainers'ın (.NET Core 1.1) ilk sürümünde, EF Core altyapısının ihtiyaç duyduğu gizli kimlik, altyapı projesinde Akıcı API kullanılarak DbContext düzeyinde aşağıdaki şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6c220-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="6c220-147">Bu nedenle, kimlik etki alanı modeli açısından gizliydi, ancak yine de altyapıda mevcuttu.</span><span class="sxs-lookup"><span data-stu-id="6c220-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="6c220-148">Ancak, bu değer nesnesinin veritabanına kalıcılığı farklı bir tablodaki normal bir varlık gibi gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="6c220-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="6c220-149">EF Core 2.0 ve sonraki ile değer nesnelerini kalıcı olarak sürdürmek için yeni ve daha iyi yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="6c220-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="6c220-150">EF Core 2.0 ve sonraki işlemlerde sahip olunan varlık türleri olarak değer nesnelerini kalıcı olarak</span><span class="sxs-lookup"><span data-stu-id="6c220-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="6c220-151">DDD'deki kanonik değer nesnesi deseni ile EF Core'daki sahip olunan varlık türü arasındaki bazı boşluklara rağmen, şu anda EF Core 2.0 ve sonraki değerlere sahip nesneleri kalıcı hale getirmek için en iyi yoldur.</span><span class="sxs-lookup"><span data-stu-id="6c220-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="6c220-152">Bu bölümün sonunda sınırlamaları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="6c220-153">Sahip olunan varlık türü özelliği, sürüm 2.0'dan beri EF Core'a eklendi.</span><span class="sxs-lookup"><span data-stu-id="6c220-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="6c220-154">Sahip olunan varlık türü, etki alanı modelinde açıkça tanımlanan kendi kimliği olmayan ve varlıklarınızdan herhangi birinde değer nesnesi gibi özellikler olarak kullanılan türleri eşlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6c220-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="6c220-155">Sahip olunan varlık türü, aynı CLR türünü başka bir varlık türüyle paylaşır (diğer bir şey, bu sadece normal bir sınıftır).</span><span class="sxs-lookup"><span data-stu-id="6c220-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="6c220-156">Tanımlayıcı gezintiyi içeren varlık sahibi varlıktır.</span><span class="sxs-lookup"><span data-stu-id="6c220-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="6c220-157">Sahibini sorgularken, sahip olunan türler varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="6c220-158">Sadece etki alanı modeline bakarak, sahip olunan bir tür herhangi bir kimliği yokmuş gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="6c220-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="6c220-159">Ancak, kapakları altında, sahip olunan türleri kimlik var, ancak sahibi navigasyon özelliği bu kimliğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c220-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="6c220-160">Sahip olunan türlerin örneklerinin kimliği tamamen kendilerine ait değildir.</span><span class="sxs-lookup"><span data-stu-id="6c220-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="6c220-161">Üç bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="6c220-161">It consists of three components:</span></span>

- <span data-ttu-id="6c220-162">Sahibinin kimliği</span><span class="sxs-lookup"><span data-stu-id="6c220-162">The identity of the owner</span></span>

- <span data-ttu-id="6c220-163">Onları gösteren navigasyon özelliği</span><span class="sxs-lookup"><span data-stu-id="6c220-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="6c220-164">Sahip olunan türlerin koleksiyonlarısöz konusu olduğunda, bağımsız bir bileşen (EF Core 2.2 ve sonrası olarak desteklenir).</span><span class="sxs-lookup"><span data-stu-id="6c220-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="6c220-165">Örneğin, eShopOnContainers'daki Sipariş etki alanı modelinde, Sipariş varlığının bir parçası olarak, Adres değeri nesnesi, Sipariş varlığı olan sahip varlık içinde sahip olunan varlık türü olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6c220-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="6c220-166">Adres, etki alanı modelinde tanımlı kimlik özelliği olmayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="6c220-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="6c220-167">Belirli bir siparişin sevkiyat adresini belirtmek için Sipariş türünün bir özelliği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c220-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="6c220-168">Kural olarak, sahip olunan tür için bir gölge birincil anahtar oluşturulur ve tablo bölme kullanılarak sahibi ile aynı tabloya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="6c220-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="6c220-169">Bu, sahip olunan türleri, geleneksel .NET Framework'de EF6'da karmaşık türlerin nasıl kullanıldığına benzer şekilde kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6c220-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="6c220-170">Sahip olunan türlerin EF Core'daki sözleşme tarafından hiçbir zaman keşfedilmeyişediğini, bu nedenle bunları açıkça beyan etmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c220-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="6c220-171">eShopOnContainers' da, OrderingContext.cs, OnModelCreating() yöntemi içinde birden çok altyapı yapılandırması uygulanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c220-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="6c220-172">Bunlardan biri Sipariş varlığı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="6c220-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="6c220-173">Aşağıdaki kodda, kalıcılık altyapısı Sipariş varlığı için tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="6c220-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="6c220-174">Önceki kodda, `orderConfiguration.OwnsOne(o => o.Address)` yöntem `Address` özelliğitin `Order` türünün sahip olduğu bir varlık olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c220-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="6c220-175">Varsayılan olarak, EF Core kuralları veritabanı sütunlarını sahip olunan `EntityProperty_OwnedEntityProperty`varlık türündeki özellikleri .</span><span class="sxs-lookup"><span data-stu-id="6c220-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="6c220-176">Bu nedenle, iç `Address` özellikleri adları `Orders` `Address_Street`ile tabloda `Address_City` görünür , `State`(ve benzeri için , `Country` ve `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="6c220-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="6c220-177">Bu sütunları `Property().HasColumnName()` yeniden adlandırmak için akıcı yöntemi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="6c220-178">Kamu malı `Address` olduğu durumlarda, haritalamalar aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="6c220-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="6c220-179">Yöntemi akıcı bir haritalamayla zincirlemek `OwnsOne` mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6c220-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="6c220-180">Aşağıdaki varsayımsal `OrderDetails` örnekte, sahip `BillingAddress` `ShippingAddress`ve , `Address` her ikisi de türü vardır.</span><span class="sxs-lookup"><span data-stu-id="6c220-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="6c220-181">Sonra `OrderDetails` türüne `Order` aittir.</span><span class="sxs-lookup"><span data-stu-id="6c220-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="6c220-182">Sahip olunan varlık türleri hakkında ek ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6c220-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="6c220-183">OwnsOne akıcı API'sini kullanarak bir gezinti özelliğini belirli bir türe yapılandırdığınızda sahip olunan türler tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6c220-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="6c220-184">Meta veri modelimizde sahip olunan bir türün tanımı bir bileşimidir: sahip türü, gezinti özelliği ve sahip olunan türün CLR türü.</span><span class="sxs-lookup"><span data-stu-id="6c220-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="6c220-185">Yığınımızdaki sahipolunan bir tür örneğinin kimliği (anahtarı), sahip türünün kimliğinin ve sahip olunan türün tanımının bir bileşimidir.</span><span class="sxs-lookup"><span data-stu-id="6c220-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="6c220-186">Sahip olunan varlıklar yetenekleri</span><span class="sxs-lookup"><span data-stu-id="6c220-186">Owned entities capabilities</span></span>

- <span data-ttu-id="6c220-187">Sahip olunan türler, sahip olunan (iç içe sahip olunan türler) veya sahip olunmayan (diğer varlıklara düzenli başvuru gezinme özellikleri) diğer varlıklara başvurur.</span><span class="sxs-lookup"><span data-stu-id="6c220-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="6c220-188">Ayrı gezinti özellikleri aracılığıyla aynı sahip varlığında farklı sahip olunan türler olarak aynı CLR türünü eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="6c220-189">Tablo bölme kuralına göre kurulumdur, ancak Sahip olunan türü ToTable kullanarak farklı bir tabloyla eşleyerek devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="6c220-190">İstekli yükleme, sahip olunan türlerde otomatik olarak gerçekleştirilir, `.Include()` yani sorguyu çağırmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c220-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="6c220-191">EF Core 2.1 `[Owned]`ve sonrası kullanılarak öznitelik ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="6c220-192">Sahip olunan türlerin koleksiyonlarını işleyebilir (sürüm 2.2 ve sonraki sürümleri kullanarak).</span><span class="sxs-lookup"><span data-stu-id="6c220-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="6c220-193">Sahip olunan varlıklar sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="6c220-193">Owned entities limitations</span></span>

- <span data-ttu-id="6c220-194">Sahip olunan bir `DbSet<T>` tür (tasarım gereği) oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6c220-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="6c220-195">Sahip olunan `ModelBuilder.Entity<T>()` türleri (şu anda tasarımgereği) arayamayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="6c220-196">Aynı tabloda sahibiyle eşlenen isteğe bağlı (yani geçersiz kılınabilir) sahip olunan türler için destek yok (diğer bir deyişle, tablo bölmeyi kullanarak).</span><span class="sxs-lookup"><span data-stu-id="6c220-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="6c220-197">Bunun nedeni, haritalama nın her özellik için yapılmasıdır, null karmaşık değeri bir bütün olarak ayrı bir sentinel imiz yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c220-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="6c220-198">Sahip olunan türler için devralma eşleme desteği yok, ancak aynı devralma hiyerarşilerinin iki yaprak türünü farklı sahip olunan türler olarak eşlenebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6c220-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="6c220-199">EF Core, aynı hiyerarşinin bir parçası oldukları gerçeğini düşünmez.</span><span class="sxs-lookup"><span data-stu-id="6c220-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="6c220-200">EF6'nın karmaşık tipleri ile temel farklılıklar</span><span class="sxs-lookup"><span data-stu-id="6c220-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="6c220-201">Tablo bölme isteğe bağlıdır, diğer bir süre sonra isteğe bağlı olarak ayrı bir tabloya eşlenebilir ve yine de sahip olunabilir.</span><span class="sxs-lookup"><span data-stu-id="6c220-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="6c220-202">Diğer varlıklara başvuruda bulunabilirler (diğer varlıklar, sahip olunmayan diğer türlerle ilişkilerde bağımlı taraf olarak hareket edebilirler).</span><span class="sxs-lookup"><span data-stu-id="6c220-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6c220-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6c220-203">Additional resources</span></span>

- <span data-ttu-id="6c220-204">**Martin Fowler' ı. ValueObject deseni** </span><span class="sxs-lookup"><span data-stu-id="6c220-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="6c220-205">**Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde Karmaşıklıkla Mücadele.**</span><span class="sxs-lookup"><span data-stu-id="6c220-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="6c220-206">(Kitap; değer nesnelerinin bir tartışma içerir) </span><span class="sxs-lookup"><span data-stu-id="6c220-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="6c220-207">**Vaughn Vernon' u. Etki Alanı Odaklı Tasarımın Uygulanması.**</span><span class="sxs-lookup"><span data-stu-id="6c220-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="6c220-208">(Kitap; değer nesnelerinin bir tartışma içerir) </span><span class="sxs-lookup"><span data-stu-id="6c220-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="6c220-209">**Sahip olunan Varlık Türleri** </span><span class="sxs-lookup"><span data-stu-id="6c220-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="6c220-210">**Gölge Özellikleri** </span><span class="sxs-lookup"><span data-stu-id="6c220-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="6c220-211">**Karmaşık türleri ve/veya değer nesneleri.**</span><span class="sxs-lookup"><span data-stu-id="6c220-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="6c220-212">EF Core GitHub repo (Sorunlar sekmesinde) </span><span class="sxs-lookup"><span data-stu-id="6c220-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="6c220-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="6c220-213">**ValueObject.cs.**</span></span> <span data-ttu-id="6c220-214">eShopOnContainers'da temel değer nesne sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c220-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="6c220-215">**Adres sınıfı.**</span><span class="sxs-lookup"><span data-stu-id="6c220-215">**Address class.**</span></span> <span data-ttu-id="6c220-216">eShopOnContainers örnek değer nesne sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c220-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="6c220-217">[Önceki](seedwork-domain-model-base-classes-interfaces.md)
> [Sonraki](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="6c220-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
