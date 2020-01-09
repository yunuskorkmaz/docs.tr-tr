---
title: LINQ (dil ile tümleşik sorgu)
description: LINQ 'in C# nasıl dil düzeyi sorgulama özellikleri ve bir API sağladığını ve Visual Basic ifade, bildirime dayalı kod yazma yöntemi olarak nasıl sağladığını öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 6ec86b7e728eef2cb4937662fd013d7fe951904d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347269"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="718a2-103">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="718a2-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="718a2-104">Nedir?</span><span class="sxs-lookup"><span data-stu-id="718a2-104">What is it?</span></span>

<span data-ttu-id="718a2-105">LINQ, dil düzeyinde sorgulama özellikleri ve [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API 'si sağlar C# ve ifade, bildirime dayalı kod yazmak için bir yol Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="718a2-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="718a2-106">Dil düzeyi sorgu sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="718a2-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="718a2-107">`IEnumerable<T>` API 'SI ile aynı örnek:</span><span class="sxs-lookup"><span data-stu-id="718a2-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="718a2-108">LINQ, Ifade</span><span class="sxs-lookup"><span data-stu-id="718a2-108">LINQ is Expressive</span></span>

<span data-ttu-id="718a2-109">Evcil hayvan listenizin bir listesini olduğunu düşünün, ancak onu `RFID` değerine göre doğrudan bir evcil hayvan 'ye erişebileceğiniz bir sözlüğe dönüştürmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="718a2-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="718a2-110">Geleneksel kesinlik kodu:</span><span class="sxs-lookup"><span data-stu-id="718a2-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="718a2-111">Kodun arkasındaki amaç yeni bir `Dictionary<int, Pet>` oluşturup bir döngü aracılığıyla buna eklemektir, var olan bir listeyi bir sözlüğe dönüştürmektir!</span><span class="sxs-lookup"><span data-stu-id="718a2-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="718a2-112">LINQ, zorunlu kod değil, amaç korur.</span><span class="sxs-lookup"><span data-stu-id="718a2-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="718a2-113">Denk LINQ ifadesi:</span><span class="sxs-lookup"><span data-stu-id="718a2-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="718a2-114">LINQ kullanan kod, bir programcı olarak düşünmekte olan amaç ve kod arasında oynatma alanı olduğunu iddia ettiğinden değerlidir.</span><span class="sxs-lookup"><span data-stu-id="718a2-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="718a2-115">Başka bir ödül kod örneği.</span><span class="sxs-lookup"><span data-stu-id="718a2-115">Another bonus is code brevity.</span></span> <span data-ttu-id="718a2-116">Yukarıdaki kod temelinin büyük bölümlerini, yukarıdaki 1/3 göre azaltmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="718a2-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="718a2-117">Harika bir anlaşma, doğru mu?</span><span class="sxs-lookup"><span data-stu-id="718a2-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="718a2-118">LINQ sağlayıcıları veri erişimini basitleştirir</span><span class="sxs-lookup"><span data-stu-id="718a2-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="718a2-119">Joker karakter üzerinde önemli bir yazılım yığını için, her şey bir kaynaktaki (veritabanları, JSON, XML, vb.) verilerle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="718a2-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="718a2-120">Genellikle bu, sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="718a2-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="718a2-121">LINQ, veri erişiminin ortak öğelerinin, hangi veri kaynağını kullandığınıza bağımsız olarak aynı olduğunu gösteren bir sorgu söz dizimine soyutlayarak bunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="718a2-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="718a2-122">Aşağıdakileri göz önünde bulundurun: belirli bir öznitelik değeri ile tüm XML öğelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="718a2-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function

```

<span data-ttu-id="718a2-123">Bu görevi gerçekleştirmek için XML belgesine el ile çapraz geçiş yapmak üzere kod yazmak çok daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="718a2-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="718a2-124">XML ile etkileşim kurmak, LINQ sağlayıcılarıyla yapabileceğiniz tek şey değildir.</span><span class="sxs-lookup"><span data-stu-id="718a2-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="718a2-125">[LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) , bir MSSQL sunucu veritabanı için oldukça basit bir nesne Ilişkisel eşleyicisidir (ORM).</span><span class="sxs-lookup"><span data-stu-id="718a2-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="718a2-126">[JSON.net](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) KITAPLıĞı, LINQ aracılığıyla verimli JSON belge geçişi sağlar.</span><span class="sxs-lookup"><span data-stu-id="718a2-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="718a2-127">Ayrıca, gerek duyduğunuz şeyi belirleyen bir kitaplık yoksa [kendı LINQ sağlayıcınızı de yazabilirsiniz](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="718a2-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="718a2-128">Sorgu söz dizimini neden kullanmalısınız?</span><span class="sxs-lookup"><span data-stu-id="718a2-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="718a2-129">Bu, genellikle gelen bir sorudır.</span><span class="sxs-lookup"><span data-stu-id="718a2-129">This is a question which often comes up.</span></span> <span data-ttu-id="718a2-130">Tümü, bu,</span><span class="sxs-lookup"><span data-stu-id="718a2-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="718a2-131">Bundan çok daha kısa.</span><span class="sxs-lookup"><span data-stu-id="718a2-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="718a2-132">Sorgu söz dizimini yapmak için API sözdizimi yalnızca daha kısa bir yol değil mi?</span><span class="sxs-lookup"><span data-stu-id="718a2-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="718a2-133">Hayır.</span><span class="sxs-lookup"><span data-stu-id="718a2-133">No.</span></span> <span data-ttu-id="718a2-134">Sorgu söz dizimi, ifadenin sonraki parçalarında kullanarak bir değişkeni ifade kapsamındaki bir değişken oluşturmanıza ve bağlamanıza imkan tanıyan **Let** yan tümcesinin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="718a2-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="718a2-135">Aynı kodun yalnızca API söz dizimi ile tekrar oluşturulması gerçekleştirilebilir, ancak büyük olasılıkla okunması zor olan koda neden olur.</span><span class="sxs-lookup"><span data-stu-id="718a2-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="718a2-136">Bu nedenle, bu soruyu **yalnızca sorgu söz dizimini kullanmanız gerekir mi?**</span><span class="sxs-lookup"><span data-stu-id="718a2-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="718a2-137">Bu sorunun yanıtı **Evet** ...</span><span class="sxs-lookup"><span data-stu-id="718a2-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="718a2-138">Mevcut kod tabanınız zaten sorgu sözdizimini kullanıyor</span><span class="sxs-lookup"><span data-stu-id="718a2-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="718a2-139">Karmaşıklık nedeniyle Sorgularınızdaki değişkenlerin kapsamını belirlemeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="718a2-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="718a2-140">Sorgu söz dizimini tercih edersiniz ve kod tabanınızdan yok olmayacaktır</span><span class="sxs-lookup"><span data-stu-id="718a2-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="718a2-141">Bu sorunun **yanıtı şu şekilde değildir.** ..</span><span class="sxs-lookup"><span data-stu-id="718a2-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="718a2-142">Mevcut kod tabanınız API sözdizimini zaten kullanıyor</span><span class="sxs-lookup"><span data-stu-id="718a2-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="718a2-143">Sorgularınızdaki değişkenleri kapsama gerek yok</span><span class="sxs-lookup"><span data-stu-id="718a2-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="718a2-144">API söz dizimini tercih edersiniz ve kod tabanınızdan yok sayılmaz</span><span class="sxs-lookup"><span data-stu-id="718a2-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="718a2-145">Temel örnekler</span><span class="sxs-lookup"><span data-stu-id="718a2-145">Essential Samples</span></span>

<span data-ttu-id="718a2-146">LINQ örneklerinin gerçekten kapsamlı bir listesi için, [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)' ni ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="718a2-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="718a2-147">Aşağıda, LINQ 'ın bazı temel parçaları için hızlı bir gösterim verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="718a2-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="718a2-148">Bu, LINQ olarak daha fazla işlevsellik sağladığından, bu kapsamda önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="718a2-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="718a2-149">İçerik-`Where`, `Select`ve `Aggregate`:</span><span class="sxs-lookup"><span data-stu-id="718a2-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

* <span data-ttu-id="718a2-150">Liste listesini düzleştirme:</span><span class="sxs-lookup"><span data-stu-id="718a2-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="718a2-151">İki küme arasında birleşim (özel karşılaştırıcısı ile):</span><span class="sxs-lookup"><span data-stu-id="718a2-151">Union between two sets (with custom comparator):</span></span>

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
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

```vb
Public Class DogHairLengthComparer 
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

* <span data-ttu-id="718a2-152">İki küme arasında kesişim:</span><span class="sxs-lookup"><span data-stu-id="718a2-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

* <span data-ttu-id="718a2-153">Sıralama</span><span class="sxs-lookup"><span data-stu-id="718a2-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

* <span data-ttu-id="718a2-154">Son olarak, daha gelişmiş bir örnek: aynı türde iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme (ödünç alınan ve [Bu StackOverflow Post](https://stackoverflow.com/a/844855)'tan değiştirilmiş):</span><span class="sxs-lookup"><span data-stu-id="718a2-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

```vb
<System.Runtime.CompilerServices.Extension()> 
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance) 
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="718a2-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="718a2-155">PLINQ</span></span>

<span data-ttu-id="718a2-156">PLıNQ veya Parallel LINQ, LINQ ifadeleri için bir paralel yürütme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="718a2-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="718a2-157">Diğer bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı üzerinde oldukça paralelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="718a2-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="718a2-158">Bu, ifadeden önceki bir `AsParallel()` çağrısıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="718a2-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="718a2-159">Aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="718a2-159">Consider the following:</span></span>

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

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="718a2-160">Bu kod, gerektiği şekilde sistem iş parçacıkları arasında `facebookUsers` bölümlenir, her bir iş parçacığında her iş parçacığı için toplam beğeneni paralel olarak toplayın, her iş parçacığı tarafından hesaplanan sonuçları ve iyi bir dizeye neden olan projeyi toplayın.</span><span class="sxs-lookup"><span data-stu-id="718a2-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="718a2-161">Diyagram formu:</span><span class="sxs-lookup"><span data-stu-id="718a2-161">In diagram form:</span></span>

![PLıNQ diyagramı](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="718a2-163">LINQ aracılığıyla kolayca ifade edebileceğiniz paralelleştirilmiş, CPU 'ya dayalı işler (başka bir deyişle, saf işlevlerdir ve yan etkileri yoktur) PLıNQ için harika bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="718a2-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="718a2-164">Yan _etkisi olan işler_ Için, [görev paralel kitaplığını](./parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="718a2-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="718a2-165">Daha fazla kaynak:</span><span class="sxs-lookup"><span data-stu-id="718a2-165">Further Resources:</span></span>

* [<span data-ttu-id="718a2-166">101 LINQ örnekleri</span><span class="sxs-lookup"><span data-stu-id="718a2-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="718a2-167">C#/F#/Visual Basic için bir playzemin ortamı ve veritabanı sorgulama altyapısı olan [linqpad](https://www.linqpad.net/)</span><span class="sxs-lookup"><span data-stu-id="718a2-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="718a2-168">[Uıulinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ nesnelerinin nasıl uygulandığını öğrenmek için bir e-kitap</span><span class="sxs-lookup"><span data-stu-id="718a2-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
