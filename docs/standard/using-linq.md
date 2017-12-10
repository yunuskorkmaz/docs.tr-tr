---
title: "LINQ (dil ile tümleşik sorgu)"
description: "Nasıl LINQ dil düzeyi sorgulama özellikleri ve bir API C# ve VB etkileyici, bildirim temelli kod yazmak için bir yol olarak sağladığını öğrenin."
keywords: .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: ae0fb23c3edb6488fd0c281b1b94548e1cb2d3bd
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="6dedd-104">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="6dedd-104">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="6dedd-105">Nedir o?</span><span class="sxs-lookup"><span data-stu-id="6dedd-105">What is it?</span></span>

<span data-ttu-id="6dedd-106">LINQ dil düzeyi sorgulama özellikleri sağlar ve bir [daha yüksek sıralı işlevi](https://en.wikipedia.org/wiki/Higher-order_function) C# ve VB etkileyici, bildirim temelli kod yazmak için bir yol olarak API.</span><span class="sxs-lookup"><span data-stu-id="6dedd-106">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and VB as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="6dedd-107">Dil düzeyi sorgu söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="6dedd-107">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

<span data-ttu-id="6dedd-108">Aynı örneği kullanarak `IEnumerable<T>` API'si:</span><span class="sxs-lookup"><span data-stu-id="6dedd-108">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a><span data-ttu-id="6dedd-109">LINQ Expressive olduğu</span><span class="sxs-lookup"><span data-stu-id="6dedd-109">LINQ is Expressive</span></span>

<span data-ttu-id="6dedd-110">Evcil Hayvanlar listesi sahip, ancak erişebileceğiniz bir evcil hayvan doğrudan göre sözlükteki dönüştürmek istediğiniz düşünün kendi `RFID` değeri.</span><span class="sxs-lookup"><span data-stu-id="6dedd-110">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="6dedd-111">Geleneksel kesinlik temelli kod:</span><span class="sxs-lookup"><span data-stu-id="6dedd-111">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

<span data-ttu-id="6dedd-112">Kod arkasında amacınıza yeni bir değil oluşturmaktır `Dictionary<int, Pet>` ve eklemek için bir döngü olan mevcut bir listeyi sözlükteki dönüştürmek için!</span><span class="sxs-lookup"><span data-stu-id="6dedd-112">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="6dedd-113">Kesinlik temelli kod'in almadığı LINQ amacınıza korur.</span><span class="sxs-lookup"><span data-stu-id="6dedd-113">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="6dedd-114">Eşdeğer LINQ ifadesi:</span><span class="sxs-lookup"><span data-stu-id="6dedd-114">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

<span data-ttu-id="6dedd-115">LINQ kullanarak kod Programcı olarak akıl zaman amacı kodu arasında oyun alanını evens için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="6dedd-115">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="6dedd-116">Başka bir avantaj kod kısaltma ' dir.</span><span class="sxs-lookup"><span data-stu-id="6dedd-116">Another bonus is code brevity.</span></span> <span data-ttu-id="6dedd-117">1/3 yukarıdaki gibi bir codebase büyük bölümünü azaltmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="6dedd-117">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="6dedd-118">Oldukça tatlı anlaşma, doğru?</span><span class="sxs-lookup"><span data-stu-id="6dedd-118">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="6dedd-119">Veri erişimi LINQ sağlayıcıları basitleştirin</span><span class="sxs-lookup"><span data-stu-id="6dedd-119">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="6dedd-120">Joker out yazılımda önemli bir öbek için her şeyi (veritabanları, JSON, XML, vb.), bazı kaynağından veri postalarla etrafında döner.</span><span class="sxs-lookup"><span data-stu-id="6dedd-120">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="6dedd-121">Genellikle bu can sıkıcı olabilir her veri kaynağı için yeni bir API öğrenme içerir.</span><span class="sxs-lookup"><span data-stu-id="6dedd-121">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="6dedd-122">LINQ bu veri erişimi ortak öğeler aynı veri kaynağını olsun, çekme görünen bir sorgu sözdizimi özetleyen tarafından basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="6dedd-122">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="6dedd-123">Aşağıdakileri dikkate alın: belirli öznitelik değeri olan tüm XML öğeleri bulma.</span><span class="sxs-lookup"><span data-stu-id="6dedd-123">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

<span data-ttu-id="6dedd-124">Bu görevi gerçekleştirmek için XML belgesi el ile geçiş için kod yazma, çok daha zor olurdu.</span><span class="sxs-lookup"><span data-stu-id="6dedd-124">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="6dedd-125">XML ile etkileşim LINQ sağlayıcıları ile yapabileceğiniz tek şey değil.</span><span class="sxs-lookup"><span data-stu-id="6dedd-125">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="6dedd-126">[LINQ-SQL](../../docs/framework/data/adonet/sql/linq/index.md) bir oldukça tam kemikler nesne ilişkisel Eşleyici (ORM) bir MSSQL sunucu için veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="6dedd-126">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="6dedd-127">[JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplığı LINQ aracılığıyla verimli JSON belgesi geçişi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6dedd-127">The [JSON.NET](http://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="6dedd-128">Gerekenler yapan bir kitaplık yoksa, ayrıca, şunları da yapabilirsiniz [kendi LINQ sağlayıcı yazma](https://msdn.microsoft.com/library/Bb546158.aspx)!</span><span class="sxs-lookup"><span data-stu-id="6dedd-128">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://msdn.microsoft.com/library/Bb546158.aspx)!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="6dedd-129">Sorgu sözdizimi neden kullanılır?</span><span class="sxs-lookup"><span data-stu-id="6dedd-129">Why Use the Query Syntax?</span></span>

<span data-ttu-id="6dedd-130">Genellikle gelen bir soru budur.</span><span class="sxs-lookup"><span data-stu-id="6dedd-130">This is a question which often comes up.</span></span> <span data-ttu-id="6dedd-131">Sonra bu,</span><span class="sxs-lookup"><span data-stu-id="6dedd-131">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

<span data-ttu-id="6dedd-132">Bu çok daha kısa aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6dedd-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

<span data-ttu-id="6dedd-133">API sözdizimi yalnızca sorgu sözdizimi yapmak için daha kısa yol değil mi?</span><span class="sxs-lookup"><span data-stu-id="6dedd-133">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="6dedd-134">Hayır.</span><span class="sxs-lookup"><span data-stu-id="6dedd-134">No.</span></span> <span data-ttu-id="6dedd-135">Sorgu sözdizimi için kullanımına izin verir **izin** getirir ve ifade sonraki parçalarını de kullanmayı ifadesi, kapsamı içinde bir değişken bağlamak izin veren yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6dedd-135">The query syntax allows for the use the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="6dedd-136">Aynı kodu yeniden yalnızca API sözdizimi ile yapılabilir, ancak büyük olasılıkla okunması zor olan kod çalıştırılmasına neden.</span><span class="sxs-lookup"><span data-stu-id="6dedd-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="6dedd-137">Bu soru begs şekilde **sorgu sözdizimi yalnızca kullanmalısınız?**</span><span class="sxs-lookup"><span data-stu-id="6dedd-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="6dedd-138">Bu soruya yanıt **Evet** varsa...</span><span class="sxs-lookup"><span data-stu-id="6dedd-138">The answer to this question is **yes** if...</span></span>

*   <span data-ttu-id="6dedd-139">Var olan codebase zaten kullanıyor sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6dedd-139">Your existing codebase already uses the query syntax</span></span>
*   <span data-ttu-id="6dedd-140">Sorgularınızın karmaşıklığı nedeniyle içinde kapsam değişkenlere gerekir</span><span class="sxs-lookup"><span data-stu-id="6dedd-140">You need to scope variables within your queries due to complexity</span></span>
*   <span data-ttu-id="6dedd-141">Sorgu sözdizimi tercih ve temelinizde gelen rahatsız olmaz</span><span class="sxs-lookup"><span data-stu-id="6dedd-141">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="6dedd-142">Bu soruya yanıt **hiçbir** varsa...</span><span class="sxs-lookup"><span data-stu-id="6dedd-142">The answer to this question is **no** if...</span></span>

*   <span data-ttu-id="6dedd-143">Var olan codebase zaten kullanıyor API sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dedd-143">Your existing codebase already uses the API syntax</span></span>
*   <span data-ttu-id="6dedd-144">Kapsam değişkenleri gerek sorgularınızı içinde sahip</span><span class="sxs-lookup"><span data-stu-id="6dedd-144">You have no need to scope variables within your queries</span></span>
*   <span data-ttu-id="6dedd-145">Tercih ettiğiniz API sözdizimi ve temelinizde gelen rahatsız olmaz</span><span class="sxs-lookup"><span data-stu-id="6dedd-145">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="6dedd-146">Temel örnekleri</span><span class="sxs-lookup"><span data-stu-id="6dedd-146">Essential Samples</span></span>

<span data-ttu-id="6dedd-147">LINQ örnekleri gerçekten kapsamlı bir listesi için ziyaret [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span><span class="sxs-lookup"><span data-stu-id="6dedd-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="6dedd-148">Bazı temel parçalar LINQ hızlı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6dedd-148">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="6dedd-149">LINQ burada showcased daha önemli ölçüde daha fazla işlevsellik sağlayan bu kapsamlı, hiçbir şekilde aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6dedd-149">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

*   <span data-ttu-id="6dedd-150">Ekmek ve ezmesi - `Where`, `Select`, ve `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="6dedd-150">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

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

// Summing then lengths of a set of strings
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

*   <span data-ttu-id="6dedd-151">Liste listesini düzleştirme:</span><span class="sxs-lookup"><span data-stu-id="6dedd-151">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   <span data-ttu-id="6dedd-152">UNION iki kümeleriyle (özel karşılaştırıcı) arasında:</span><span class="sxs-lookup"><span data-stu-id="6dedd-152">Union between two sets (with custom comparator):</span></span>

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
        return b.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

*   <span data-ttu-id="6dedd-153">İki küme arasındaki kesişimi:</span><span class="sxs-lookup"><span data-stu-id="6dedd-153">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   <span data-ttu-id="6dedd-154">Sıralama:</span><span class="sxs-lookup"><span data-stu-id="6dedd-154">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   <span data-ttu-id="6dedd-155">Son olarak, örnek daha gelişmiş: aynı türde iki örneği özelliklerinin değerleri eşit olup olmadığını belirleme (Borrowed ve gelen değiştirilmiş [bu StackOverflow post](http://stackoverflow.com/a/844855)):</span><span class="sxs-lookup"><span data-stu-id="6dedd-155">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](http://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self != null && to != null)
    {
        var type = typeof(T);
        var ignoreList = new List<string>(ignore);

        // Selects the properties which have unequal values into a sequence of those properties.
        var unequalProperties = from pi in type.GetProperties(BindingFlags.Public | BindingFlags.Instance)
                                where !ignoreList.Contains(pi.Name)
                                let selfValue = type.GetProperty(pi.Name).GetValue(self, null)
                                let toValue = type.GetProperty(pi.Name).GetValue(to, null)
                                where selfValue != toValue && (selfValue == null || !selfValue.Equals(toValue))
                                select new { Prop = pi.Name, selfValue, toValue };
        return !unequalProperties.Any();
    }

    return self == to;
}
```

## <a name="plinq"></a><span data-ttu-id="6dedd-156">PLINQ</span><span class="sxs-lookup"><span data-stu-id="6dedd-156">PLINQ</span></span>

<span data-ttu-id="6dedd-157">PLINQ ya da paralel LINQ bir paralel yürütme LINQ ifadeleri için altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="6dedd-157">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="6dedd-158">Diğer bir deyişle, normal bir LINQ ifadeleri trivially iş parçacıkları arasında herhangi bir sayı paralel birkaç ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="6dedd-158">In other words, a regular LINQ expressions can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="6dedd-159">Bu çağrı aracılığıyla gerçekleştirilir `AsParallel()` ifade önceki.</span><span class="sxs-lookup"><span data-stu-id="6dedd-159">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="6dedd-160">Aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6dedd-160">Consider the following:</span></span>

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

<span data-ttu-id="6dedd-161">Bu kod bölüm `facebookUsers` gerektiği gibi toplam yöntemlerine paralel, her iş parçacığı üzerinde toplama sistem iş parçacıkları arasında her iş parçacığı tarafından hesaplanan sonuçlarını toplamak ve iyi bir dizeye sonucunda ortaya çıkan proje.</span><span class="sxs-lookup"><span data-stu-id="6dedd-161">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="6dedd-162">Diyagram formunda:</span><span class="sxs-lookup"><span data-stu-id="6dedd-162">In diagram form:</span></span>

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="6dedd-164">LINQ kolayca ifade edilebilir paralelleştirilebilir CPU bağımlı işleri (diğer bir deyişle, saf işlevleri ve hiçbir yan etkisi) PLINQ harika aday olan.</span><span class="sxs-lookup"><span data-stu-id="6dedd-164">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="6dedd-165">İşler, _yapmak_ bir yan etkisi, kullanmayı [görev paralel Kitaplığı](./parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="6dedd-165">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="6dedd-166">Ek kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="6dedd-166">Further Resources:</span></span>

*   [<span data-ttu-id="6dedd-167">101 LINQ örnekleri</span><span class="sxs-lookup"><span data-stu-id="6dedd-167">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   <span data-ttu-id="6dedd-168">[Linqpad](https://www.linqpad.net/), playground ortamı ve veritabanını sorgulama için C# /F #/VB altyapısı</span><span class="sxs-lookup"><span data-stu-id="6dedd-168">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/VB</span></span>
*   <span data-ttu-id="6dedd-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), bir e-LINQ nesneler nasıl uygulandığına öğrenme için kitap</span><span class="sxs-lookup"><span data-stu-id="6dedd-169">[EduLinq](http://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
