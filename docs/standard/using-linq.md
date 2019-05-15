---
title: LINQ (dil ile tümleşik sorgu)
description: Nasıl LINQ dil düzeyinde sorgulama özellikleri ve bir API C# ve VB için etkileyici ve bildirim temelli bir kod yazmak için bir yol sağladığını öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 941bfa624bfcc05457714b2f342054bbebfdf908
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557895"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="ba996-103">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="ba996-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="ba996-104">Nedir?</span><span class="sxs-lookup"><span data-stu-id="ba996-104">What is it?</span></span>

<span data-ttu-id="ba996-105">LINQ dil düzeyinde sorgulama özellikleri sağlar ve bir [yüksek sıralı işlev](https://en.wikipedia.org/wiki/Higher-order_function) C# ve VB ifadesel ve bildirim temelli bir kod yazmak için bir yol olarak API.</span><span class="sxs-lookup"><span data-stu-id="ba996-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="ba996-106">Dil düzeyi sorgu söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="ba996-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="ba996-107">Aynı örneği kullanarak `IEnumerable<T>` API:</span><span class="sxs-lookup"><span data-stu-id="ba996-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="ba996-108">LINQ Expressive olduğu</span><span class="sxs-lookup"><span data-stu-id="ba996-108">LINQ is Expressive</span></span>

<span data-ttu-id="ba996-109">Evcil Hayvanlar listesi vardır, ancak erişebileceğiniz bir evcil hayvan doğrudan göre bir sözlük içinde dönüştürmek istediğiniz Imagine kendi `RFID` değeri.</span><span class="sxs-lookup"><span data-stu-id="ba996-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="ba996-110">Geleneksel kesinlik temelli kod:</span><span class="sxs-lookup"><span data-stu-id="ba996-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="ba996-111">Yeni bir oluşturmamayı niyetini kod arkasında olan `Dictionary<int, Pet>` ve eklemek için bir döngü yoluyla olan mevcut bir listeyi sözlükteki dönüştürmek için!</span><span class="sxs-lookup"><span data-stu-id="ba996-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="ba996-112">Kesinlik temelli Kodun desteklemez LINQ niyetini korur.</span><span class="sxs-lookup"><span data-stu-id="ba996-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="ba996-113">Equivalent LINQ expression:</span><span class="sxs-lookup"><span data-stu-id="ba996-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="ba996-114">LINQ kullanarak kodu oyun alanını hedefi ile kod arasında bir programcısı akıl olduğunda evens için değerlidir.</span><span class="sxs-lookup"><span data-stu-id="ba996-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="ba996-115">Başka bir ödül kod kısaltma ' dir.</span><span class="sxs-lookup"><span data-stu-id="ba996-115">Another bonus is code brevity.</span></span> <span data-ttu-id="ba996-116">1/3 yukarıdaki gibi büyük bir kod temeli bölümlerini azaltmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ba996-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="ba996-117">Oldukça tatlı anlaşma, doğru?</span><span class="sxs-lookup"><span data-stu-id="ba996-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="ba996-118">LINQ sağlayıcıları veri erişimini basitleştirme</span><span class="sxs-lookup"><span data-stu-id="ba996-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="ba996-119">Out joker yazılım önemli bir öbek için her şeyi (veritabanları, JSON, XML, vb.) bir kaynaktan veri uğraşmanızı geçici olarak döner.</span><span class="sxs-lookup"><span data-stu-id="ba996-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="ba996-120">Genellikle bu sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenme içerir.</span><span class="sxs-lookup"><span data-stu-id="ba996-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="ba996-121">LINQ veri erişiminin ortak öğeler aynı hangi veri kaynağı ne olursa olsun, çekme görünen bir sorgu söz dizimi özetleyen tarafından basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba996-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="ba996-122">Aşağıdakileri dikkate alın: özel öznitelik değeri olan tüm XML öğeleri bulma.</span><span class="sxs-lookup"><span data-stu-id="ba996-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="ba996-123">Bu görevi gerçekleştirmek için XML belgesi el ile geçirmek için kod yazma, çok daha zor olurdu.</span><span class="sxs-lookup"><span data-stu-id="ba996-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="ba996-124">XML ile etkileşim LINQ sağlayıcıları ile yapmanız gereken tek şey değildir.</span><span class="sxs-lookup"><span data-stu-id="ba996-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="ba996-125">[LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) bir oldukça çıplak kemikler nesne-ilişkisel Eşleyici (ORM) bir MSSQL Server veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="ba996-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="ba996-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplık etkin JSON belgesinde geçişi LINQ aracılığıyla sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba996-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="ba996-127">Aradığınızı yapan bir kitaplık yoksa, ayrıca, ayrıca [kendi LINQ sağlayıcınızı yazma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="ba996-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="ba996-128">Sorgu söz dizimi neden kullanmalısınız?</span><span class="sxs-lookup"><span data-stu-id="ba996-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="ba996-129">Genellikle gelen bir soru budur.</span><span class="sxs-lookup"><span data-stu-id="ba996-129">This is a question which often comes up.</span></span> <span data-ttu-id="ba996-130">Sonra bu,</span><span class="sxs-lookup"><span data-stu-id="ba996-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="ba996-131">Bundan çok daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="ba996-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="ba996-132">API sözdizimi sorgu söz dizimi yapmak için yalnızca daha kısa bir yol değil mi?</span><span class="sxs-lookup"><span data-stu-id="ba996-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="ba996-133">Hayır.</span><span class="sxs-lookup"><span data-stu-id="ba996-133">No.</span></span> <span data-ttu-id="ba996-134">Sorgu söz dizimi için kullanılmasına **izin** tanıtır ve sonraki ifade parçalarını de kullanmayı ifadesi, kapsamı içinde bir değişken bağlamasına izin veren yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ba996-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="ba996-135">Aynı kodu yeniden oluştururken yalnızca API söz dizimi ile yapılabilir, ancak büyük olasılıkla okunması zor olan kodlara neden.</span><span class="sxs-lookup"><span data-stu-id="ba996-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="ba996-136">Soru sorun bu şekilde **yalnızca sorgu söz dizimi kullanmalısınız?**</span><span class="sxs-lookup"><span data-stu-id="ba996-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="ba996-137">Bu sorunun yanıtı **Evet** varsa...</span><span class="sxs-lookup"><span data-stu-id="ba996-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="ba996-138">Mevcut codebase zaten kullandığı sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba996-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="ba996-139">Sorgularınızın karmaşıklığı nedeniyle içinde kapsam değişkenleri gerekir</span><span class="sxs-lookup"><span data-stu-id="ba996-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="ba996-140">Tercih ettiğiniz sorgu söz dizimi ve kod temelinizde departmanınızı olmaz</span><span class="sxs-lookup"><span data-stu-id="ba996-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="ba996-141">Bu sorunun yanıtı **hiçbir** varsa...</span><span class="sxs-lookup"><span data-stu-id="ba996-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="ba996-142">Mevcut codebase zaten kullandığı API söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba996-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="ba996-143">İçinde sorgularınızı kapsam değişkenleri gerek sahip</span><span class="sxs-lookup"><span data-stu-id="ba996-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="ba996-144">Tercih ettiğiniz API söz dizimi ve kod temelinizde departmanınızı olmaz</span><span class="sxs-lookup"><span data-stu-id="ba996-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="ba996-145">Temel örnekler</span><span class="sxs-lookup"><span data-stu-id="ba996-145">Essential Samples</span></span>

<span data-ttu-id="ba996-146">LINQ örnekleri gerçekten kapsamlı bir listesi için ziyaret [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="ba996-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="ba996-147">Bazı önemli parçaları LINQ hızlı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba996-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="ba996-148">LINQ burada büyütmüş daha önemli ölçüde daha fazla işlevsellik sağladığından kapsamlı, hiçbir şekilde budur.</span><span class="sxs-lookup"><span data-stu-id="ba996-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="ba996-149">Ekmekler ve ezmesi - `Where`, `Select`, ve `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="ba996-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

* <span data-ttu-id="ba996-150">Bir liste düzleştirme:</span><span class="sxs-lookup"><span data-stu-id="ba996-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

* <span data-ttu-id="ba996-151">UNION (ile özel bir karşılaştırıcı) iki kümesi arasında:</span><span class="sxs-lookup"><span data-stu-id="ba996-151">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

* <span data-ttu-id="ba996-152">İki kesişimi:</span><span class="sxs-lookup"><span data-stu-id="ba996-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

* <span data-ttu-id="ba996-153">Sıralama:</span><span class="sxs-lookup"><span data-stu-id="ba996-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

* <span data-ttu-id="ba996-154">Son olarak, örnek daha gelişmiş: iki örneği aynı türdeki özelliklerin değerlerini eşit olup olmadığını belirleme (Borrowed ve gelen değiştirilmiş [StackOverflow yazıya](https://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="ba996-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }
    
    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

## <a name="plinq"></a><span data-ttu-id="ba996-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="ba996-155">PLINQ</span></span>

<span data-ttu-id="ba996-156">PLINQ ve paralel LINQ bir paralel yürütme için LINQ ifadelerini altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="ba996-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="ba996-157">Diğer bir deyişle, normal bir LINQ ifadesini basit bir şekilde herhangi bir iş parçacığı sayısı arasında paralel.</span><span class="sxs-lookup"><span data-stu-id="ba996-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="ba996-158">Bu bir çağrı aracılığıyla gerçekleştirilir `AsParallel()` önceki ifade.</span><span class="sxs-lookup"><span data-stu-id="ba996-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="ba996-159">Aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="ba996-159">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

<span data-ttu-id="ba996-160">Bu kod bölüm `facebookUsers` gerekirse, toplam beğenilerin paralel, her bir iş parçacığı üzerinde toplama sistem iş parçacıklarını arasında her iş parçacığı tarafından hesaplanan sonuçlarını toplamak ve bu sonucu güzel bir dizeye proje.</span><span class="sxs-lookup"><span data-stu-id="ba996-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="ba996-161">Diyagram formunda:</span><span class="sxs-lookup"><span data-stu-id="ba996-161">In diagram form:</span></span>

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="ba996-163">LINQ ile kolayca ifade edilebilir paralelleştirilebilir CPU bağımlı iş (diğer bir deyişle, saf işlevler ve yan etkileri) PLINQ için mükemmel bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="ba996-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="ba996-164">İşler, _yapmak_ bir yan etkisi, kullanmayı [görev paralel Kitaplığı](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="ba996-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="ba996-165">Ek kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="ba996-165">Further Resources:</span></span>

* [<span data-ttu-id="ba996-166">101 LINQ örneği</span><span class="sxs-lookup"><span data-stu-id="ba996-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="ba996-167">[Linqpad](https://www.linqpad.net/), oyun alanı ortamı ve veritabanını sorgulama altyapısı için C#/F#/VB</span><span class="sxs-lookup"><span data-stu-id="ba996-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
* <span data-ttu-id="ba996-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/),-LINQ nesnelerin nasıl gerçekleştirilir öğrenmek için kitap</span><span class="sxs-lookup"><span data-stu-id="ba996-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
