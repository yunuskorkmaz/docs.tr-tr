---
title: LINQ (Dil Tümleşik Sorgu)
description: LINQ'un anlamlı, bildirimsel kod yazmanın bir yolu olarak c# ve Visual Basic'e dil düzeyinde sorgulama özelliklerini ve API'yi nasıl sağladığını öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: eafd8f78c3d8de1ba064021111f869571d5a570f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160332"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="982bf-103">LINQ (Dil Tümleşik Sorgu)</span><span class="sxs-lookup"><span data-stu-id="982bf-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="982bf-104">Bu nedir?</span><span class="sxs-lookup"><span data-stu-id="982bf-104">What is it?</span></span>

<span data-ttu-id="982bf-105">LINQ, anlamlı, bildirimsel kod yazmanın bir yolu olarak C# ve Visual Basic'e dil düzeyinde sorgulama yetenekleri ve [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API'si sağlar.</span><span class="sxs-lookup"><span data-stu-id="982bf-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="982bf-106">Dil düzeyinde sorgu sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="982bf-106">Language-level query syntax:</span></span>

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

<span data-ttu-id="982bf-107">`IEnumerable<T>` API kullanarak aynı örnek:</span><span class="sxs-lookup"><span data-stu-id="982bf-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="982bf-108">LINQ Etkileyicidir</span><span class="sxs-lookup"><span data-stu-id="982bf-108">LINQ is Expressive</span></span>

<span data-ttu-id="982bf-109">Evcil hayvan bir liste var düşünün, ama doğrudan değeri bir `RFID` evcil hayvan erişebilirsiniz bir sözlük haline dönüştürmek istiyorum.</span><span class="sxs-lookup"><span data-stu-id="982bf-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="982bf-110">Geleneksel zorunlu kod:</span><span class="sxs-lookup"><span data-stu-id="982bf-110">Traditional imperative code:</span></span>

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

<span data-ttu-id="982bf-111">Kodun arkasındaki amaç yeni `Dictionary<int, Pet>` bir oluşturmak ve bir döngü üzerinden eklemek değil, bir sözlük içine mevcut bir liste dönüştürmek için!</span><span class="sxs-lookup"><span data-stu-id="982bf-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="982bf-112">LINQ amacı nı korurken, zorunlu kod korumaz.</span><span class="sxs-lookup"><span data-stu-id="982bf-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="982bf-113">Eşdeğer LINQ ifadesi:</span><span class="sxs-lookup"><span data-stu-id="982bf-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="982bf-114">LINQ'yi kullanan kod değerlidir, çünkü programcı olarak muhakeme yaparken amaç ve kod arasındaki oyun alanını eşitler.</span><span class="sxs-lookup"><span data-stu-id="982bf-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="982bf-115">Başka bir bonus kod kısalığı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="982bf-115">Another bonus is code brevity.</span></span> <span data-ttu-id="982bf-116">Yukarıda yapıldığı gibi bir kod tabanının büyük bölümlerini 1/3 azalttığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="982bf-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="982bf-117">Çok hoş bir anlaşma, değil mi?</span><span class="sxs-lookup"><span data-stu-id="982bf-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="982bf-118">LINQ Sağlayıcıları Veri Erişimini Basitleştirir</span><span class="sxs-lookup"><span data-stu-id="982bf-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="982bf-119">Vahşi yazılım önemli bir yığın için, her şey bazı kaynak (Veritabanları, JSON, XML, vb) verileri ile ilgili etrafında döner.</span><span class="sxs-lookup"><span data-stu-id="982bf-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="982bf-120">Genellikle bu rahatsız edici olabilir her veri kaynağı için yeni bir API öğrenme içerir.</span><span class="sxs-lookup"><span data-stu-id="982bf-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="982bf-121">LINQ, hangi veri kaynağını seçerseniz seçin aynı görünen bir sorgu sözdizimine ortak veri erişimi öğelerini soyutlayarak bunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="982bf-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="982bf-122">Aşağıdakileri göz önünde bulundurun: belirli bir öznitelik değeri olan tüm XML öğelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="982bf-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

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

<span data-ttu-id="982bf-123">Bu görevi gerçekleştirmek için XML belgesini el ile geçmek için kod yazmak çok daha zor olacaktır.</span><span class="sxs-lookup"><span data-stu-id="982bf-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="982bf-124">XML ile etkileşim LINQ Sağlayıcıları ile yapabileceğiniz tek şey değildir.</span><span class="sxs-lookup"><span data-stu-id="982bf-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="982bf-125">[Linq to SQL,](../../docs/framework/data/adonet/sql/linq/index.md) MSSQL Server Veritabanı için oldukça çıplak bir Nesne-İlişkisel Mapper (ORM) dir.</span><span class="sxs-lookup"><span data-stu-id="982bf-125">[Linq to SQL](../../docs/framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="982bf-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplığı LINQ üzerinden verimli JSON Belge geçiş sağlar.</span><span class="sxs-lookup"><span data-stu-id="982bf-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="982bf-127">Ayrıca, ihtiyacınız olanı yapan bir kütüphane yoksa, [kendi LINQ Sağlayıcınızı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))da yazabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="982bf-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="982bf-128">Sorgu Sözdizimini Neden Kullanıyor?</span><span class="sxs-lookup"><span data-stu-id="982bf-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="982bf-129">Bu sık sık gündeme gelen bir sorudur.</span><span class="sxs-lookup"><span data-stu-id="982bf-129">This is a question which often comes up.</span></span> <span data-ttu-id="982bf-130">Ne de olsa, bu,</span><span class="sxs-lookup"><span data-stu-id="982bf-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="982bf-131">bundan çok daha kısa:</span><span class="sxs-lookup"><span data-stu-id="982bf-131">is a lot more concise than this:</span></span>

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

<span data-ttu-id="982bf-132">API sözdizimi sorgu sözdizimini yapmak için daha kısa bir yol değil mi?</span><span class="sxs-lookup"><span data-stu-id="982bf-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="982bf-133">Hayır.</span><span class="sxs-lookup"><span data-stu-id="982bf-133">No.</span></span> <span data-ttu-id="982bf-134">Sorgu sözdizimi, ifadenin sonraki parçalarında kullanarak ifade kapsamında bir değişken ikleyen ve bağlamanızı sağlayan **let** yan tümcesinin kullanılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="982bf-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="982bf-135">Yalnızca API sözdizimi ile aynı kodu çoğaltma yapılabilir, ancak büyük olasılıkla okunması zor koda yol açacaktır.</span><span class="sxs-lookup"><span data-stu-id="982bf-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="982bf-136">Yani bu şu soruyu akla getiriyor, **sadece sorgu sözdizimini mi kullanmalısınız?**</span><span class="sxs-lookup"><span data-stu-id="982bf-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="982bf-137">Bu sorunun cevabı **evet** eğer ...</span><span class="sxs-lookup"><span data-stu-id="982bf-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="982bf-138">Varolan kod tabanınız sorgu sözdizimini zaten kullanır</span><span class="sxs-lookup"><span data-stu-id="982bf-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="982bf-139">Karmaşıklık nedeniyle sorgularınızdaki değişkenleri kapsamanız gerekir</span><span class="sxs-lookup"><span data-stu-id="982bf-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="982bf-140">Sorgu sözdizimini tercih ederseniz, kod tabanınızdan dikkatini dağıtmaz</span><span class="sxs-lookup"><span data-stu-id="982bf-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="982bf-141">Bu sorunun cevabı **hayır** eğer ...</span><span class="sxs-lookup"><span data-stu-id="982bf-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="982bf-142">Varolan kod tabanınız api sözdizimini zaten kullanır</span><span class="sxs-lookup"><span data-stu-id="982bf-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="982bf-143">Sorgularınızda değişkenleri kapsamanız gerekmez</span><span class="sxs-lookup"><span data-stu-id="982bf-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="982bf-144">API sözdizimini tercih ederseniz, kod tabanınızın dikkatini dağıtmaz</span><span class="sxs-lookup"><span data-stu-id="982bf-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="982bf-145">Temel Örnekler</span><span class="sxs-lookup"><span data-stu-id="982bf-145">Essential Samples</span></span>

<span data-ttu-id="982bf-146">LINQ örneklerinin gerçekten kapsamlı bir listesi için [101 LINQ Örneği'ni](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="982bf-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).</span></span>

<span data-ttu-id="982bf-147">Aşağıda LINQ'nun bazı temel parçalarının hızlı bir gösterimi yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="982bf-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="982bf-148">LINQ burada sergilenenden çok daha fazla işlevsellik sağladığından, bu hiçbir şekilde kapsamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="982bf-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="982bf-149">Ekmek ve tereyağı `Where` `Select`- `Aggregate`, , ve:</span><span class="sxs-lookup"><span data-stu-id="982bf-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

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

* <span data-ttu-id="982bf-150">Listelerin listesini düzleştirmek:</span><span class="sxs-lookup"><span data-stu-id="982bf-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="982bf-151">İki küme arasındaki birlik (özel karşılaştırıcı ile):</span><span class="sxs-lookup"><span data-stu-id="982bf-151">Union between two sets (with custom comparator):</span></span>

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

* <span data-ttu-id="982bf-152">İki küme arasındaki kesişme:</span><span class="sxs-lookup"><span data-stu-id="982bf-152">Intersection between two sets:</span></span>

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

* <span data-ttu-id="982bf-153">Sipariş:</span><span class="sxs-lookup"><span data-stu-id="982bf-153">Ordering:</span></span>

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

* <span data-ttu-id="982bf-154">Son olarak, daha gelişmiş bir örnek: aynı türdeki iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme [(Bu StackOverflow gönderisinden](https://stackoverflow.com/a/844855)ödünç alınan ve değiştirilen):</span><span class="sxs-lookup"><span data-stu-id="982bf-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

## <a name="plinq"></a><span data-ttu-id="982bf-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="982bf-155">PLINQ</span></span>

<span data-ttu-id="982bf-156">PLINQ veya Parallel LINQ, LINQ ifadeleri için paralel bir yürütme motorudur.</span><span class="sxs-lookup"><span data-stu-id="982bf-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="982bf-157">Başka bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı arasında önemsiz bir şekilde paralelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="982bf-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="982bf-158">Bu, ifadeden `AsParallel()` önce yapılan bir çağrı ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="982bf-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="982bf-159">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="982bf-159">Consider the following:</span></span>

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

<span data-ttu-id="982bf-160">Bu kod `facebookUsers` gerektiğinde sistem iş parçacıkları arasında bölüm, paralel olarak her iş parçacığı üzerinde toplam beğeni toplamı, her iş parçacığı tarafından hesaplanan sonuçları toplamı ve güzel bir dize içine sonuç proje.</span><span class="sxs-lookup"><span data-stu-id="982bf-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="982bf-161">Diyagram şeklinde:</span><span class="sxs-lookup"><span data-stu-id="982bf-161">In diagram form:</span></span>

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="982bf-163">Linq ile kolayca ifade edilebilen paralelleştirilebilir CPU'ya bağlı işler (diğer bir deyişle, saf fonksiyonlardır ve yan etkileri yoktur) PLINQ için harika bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="982bf-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="982bf-164">Yan etkisi _olan_ işler için Görev [Paralel Kitaplığı'nı](./parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="982bf-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="982bf-165">Diğer Kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="982bf-165">Further Resources:</span></span>

* [<span data-ttu-id="982bf-166">101 LINQ Örnekleri</span><span class="sxs-lookup"><span data-stu-id="982bf-166">101 LINQ Samples</span></span>](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* <span data-ttu-id="982bf-167">[Linqpad](https://www.linqpad.net/), C#/F#/Visual Basic için bir oyun alanı ortamı ve Veritabanı sorgulama motoru</span><span class="sxs-lookup"><span data-stu-id="982bf-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="982bf-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ-to-objects nasıl uygulandığını öğrenmek için bir e-kitap</span><span class="sxs-lookup"><span data-stu-id="982bf-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
