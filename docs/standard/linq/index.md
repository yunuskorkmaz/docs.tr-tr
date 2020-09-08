---
title: LINQ genel bakış-.NET
description: Dil ile tümleşik sorgu (LINQ), dil düzeyinde sorgulama özellikleri ve C# ve Visual Basic için daha yüksek sıralı bir işlev API 'SI sağlar. bu sayede, açıklayıcı bildirime dayalı bir kod yazmanıza olanak tanınır.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2e8abef547d8cc06d80b8cbf865ec984eb91d330
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552968"
---
# <a name="linq-overview"></a><span data-ttu-id="313a3-103">LINQ genel bakış</span><span class="sxs-lookup"><span data-stu-id="313a3-103">LINQ overview</span></span>

<span data-ttu-id="313a3-104">Dil ile tümleşik sorgu (LINQ), dil düzeyinde sorgulama özellikleri ve C# ve Visual Basic için [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API 'si sağlar. bu sayede, açıklayıcı bildirime dayalı bir kod yazmanıza olanak tanınır.</span><span class="sxs-lookup"><span data-stu-id="313a3-104">Language-Integrated Query (LINQ) provides language-level querying capabilities, and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic, that enable you to write expressive declarative code.</span></span>

## <a name="language-level-query-syntax"></a><span data-ttu-id="313a3-105">Dil düzeyi sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="313a3-105">Language-level query syntax</span></span>

<span data-ttu-id="313a3-106">Bu, dil düzeyi sorgu sözdizimidir:</span><span class="sxs-lookup"><span data-stu-id="313a3-106">This is the language-level query syntax:</span></span>

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

<span data-ttu-id="313a3-107">Bu, API kullanan aynı örneğidir `IEnumerable<T>` :</span><span class="sxs-lookup"><span data-stu-id="313a3-107">This is the same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="313a3-108">LINQ, ifade</span><span class="sxs-lookup"><span data-stu-id="313a3-108">LINQ is expressive</span></span>

<span data-ttu-id="313a3-109">Evcil hayvan listenizin bir listesini olduğunu düşünün ancak onu doğrudan değerine göre erişebileceğiniz bir sözlüğe dönüştürmek istiyorsunuz `RFID` .</span><span class="sxs-lookup"><span data-stu-id="313a3-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="313a3-110">Bu geleneksel bir zorunlu koddur:</span><span class="sxs-lookup"><span data-stu-id="313a3-110">This is traditional imperative code:</span></span>

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

<span data-ttu-id="313a3-111">Kodun arkasındaki amaç yeni bir oluşturma `Dictionary<int, Pet>` ve bir döngü aracılığıyla buna eklememe, var olan bir listeyi bir sözlüğe dönüştürmektir!</span><span class="sxs-lookup"><span data-stu-id="313a3-111">The intention behind the code isn't to create a new `Dictionary<int, Pet>` and add to it via a loop, it's to convert an existing list into a dictionary!</span></span> <span data-ttu-id="313a3-112">LINQ, zorunlu kod değil, amaç korur.</span><span class="sxs-lookup"><span data-stu-id="313a3-112">LINQ preserves the intention whereas the imperative code doesn't.</span></span>

<span data-ttu-id="313a3-113">Bu eşdeğer LINQ deyimidir:</span><span class="sxs-lookup"><span data-stu-id="313a3-113">This is the equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="313a3-114">LINQ kullanan kod, bir programcı olarak düşünmekte olan amaç ve kod arasında oynatma alanı olduğunu iddia ettiğinden değerlidir.</span><span class="sxs-lookup"><span data-stu-id="313a3-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="313a3-115">Başka bir ödül kod örneği.</span><span class="sxs-lookup"><span data-stu-id="313a3-115">Another bonus is code brevity.</span></span> <span data-ttu-id="313a3-116">Yukarıdaki kod temelinin büyük bölümlerini, yukarıdaki 1/3 göre azaltmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="313a3-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="313a3-117">Tatlı, doğru mu?</span><span class="sxs-lookup"><span data-stu-id="313a3-117">Sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="313a3-118">LINQ sağlayıcıları veri erişimini basitleştirir</span><span class="sxs-lookup"><span data-stu-id="313a3-118">LINQ providers simplify data access</span></span>

<span data-ttu-id="313a3-119">Joker karakter üzerinde önemli bir yazılım yığını için her şey, bazı kaynaklardan (veritabanları, JSON, XML vb.) verilerle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="313a3-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, and so on).</span></span> <span data-ttu-id="313a3-120">Genellikle bu, sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="313a3-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="313a3-121">LINQ, veri erişiminin ortak öğelerinin, hangi veri kaynağını kullandığınıza bağımsız olarak aynı olduğunu gösteren bir sorgu söz dizimine soyutlayarak bunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="313a3-121">LINQ simplifies this by abstracting common elements of data access into a query syntax that looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="313a3-122">Bu, belirli bir öznitelik değerine sahip tüm XML öğelerini bulur:</span><span class="sxs-lookup"><span data-stu-id="313a3-122">This finds all XML elements with a specific attribute value:</span></span>

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

<span data-ttu-id="313a3-123">Bu görevi yapmak için XML belgesine el ile çapraz geçiş yapmak üzere kod yazma çok daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="313a3-123">Writing code to manually traverse the XML document to do this task would be far more challenging.</span></span>

<span data-ttu-id="313a3-124">XML ile etkileşim kurmak, LINQ sağlayıcılarıyla yapabileceğiniz tek şey değildir.</span><span class="sxs-lookup"><span data-stu-id="313a3-124">Interacting with XML isn't the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="313a3-125">[LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) , bir MSSQL sunucu veritabanı için oldukça basit bir nesne Ilişkisel eşleyicisidir (ORM).</span><span class="sxs-lookup"><span data-stu-id="313a3-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="313a3-126">[JSON.net](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) KITAPLıĞı, LINQ aracılığıyla verimli JSON belge geçişi sağlar.</span><span class="sxs-lookup"><span data-stu-id="313a3-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="313a3-127">Ayrıca, gerek duyduğunuz şeyi yapan bir kitaplık yoksa [kendı LINQ sağlayıcınızı de yazabilirsiniz](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span><span class="sxs-lookup"><span data-stu-id="313a3-127">Furthermore, if there isn't a library that does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="reasons-to-use-the-query-syntax"></a><span data-ttu-id="313a3-128">Sorgu söz dizimini kullanma nedenleri</span><span class="sxs-lookup"><span data-stu-id="313a3-128">Reasons to use the query syntax</span></span>

<span data-ttu-id="313a3-129">Sorgu söz dizimi neden kullanılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="313a3-129">Why use query syntax?</span></span> <span data-ttu-id="313a3-130">Bu, genellikle gelen bir sorudır.</span><span class="sxs-lookup"><span data-stu-id="313a3-130">This is a question that often comes up.</span></span> <span data-ttu-id="313a3-131">Tümü sonrasında aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="313a3-131">After all, the following code:</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="313a3-132">Bundan çok daha kısa.</span><span class="sxs-lookup"><span data-stu-id="313a3-132">is a lot more concise than this:</span></span>

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

<span data-ttu-id="313a3-133">Sorgu söz dizimini yapmak için API sözdizimi yalnızca daha kısa bir yol değil mi?</span><span class="sxs-lookup"><span data-stu-id="313a3-133">Isn't the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="313a3-134">Hayır.</span><span class="sxs-lookup"><span data-stu-id="313a3-134">No.</span></span> <span data-ttu-id="313a3-135">Sorgu söz dizimi, ifadenin sonraki parçalarında kullanarak bir değişkeni ifade kapsamındaki bir değişken oluşturmanıza ve bağlamanıza imkan tanıyan **Let** yan tümcesinin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="313a3-135">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="313a3-136">Aynı kodun yalnızca API söz dizimi ile tekrar oluşturulması gerçekleştirilebilir, ancak büyük olasılıkla okunması zor olan koda neden olur.</span><span class="sxs-lookup"><span data-stu-id="313a3-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code that's hard to read.</span></span>

<span data-ttu-id="313a3-137">Bu nedenle, bu soruyu **yalnızca sorgu söz dizimini kullanmanız gerekir mi?**</span><span class="sxs-lookup"><span data-stu-id="313a3-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="313a3-138">Şu durumlarda bu sorunun yanıtı **Evet** 'tir:</span><span class="sxs-lookup"><span data-stu-id="313a3-138">The answer to this question is **yes** if:</span></span>

- <span data-ttu-id="313a3-139">Mevcut kod tabanınız sorgu sözdizimini zaten kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="313a3-139">Your existing codebase already uses the query syntax.</span></span>
- <span data-ttu-id="313a3-140">Karmaşıklık nedeniyle Sorgularınızdaki değişkenlerin kapsamını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="313a3-140">You need to scope variables within your queries because of complexity.</span></span>
- <span data-ttu-id="313a3-141">Sorgu söz dizimini tercih edersiniz ve kod tabanınızdan yok olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="313a3-141">You prefer the query syntax and it won't distract from your codebase.</span></span>

<span data-ttu-id="313a3-142">Bu sorunun **yanıtı şu şekilde değildir.** ..</span><span class="sxs-lookup"><span data-stu-id="313a3-142">The answer to this question is **no** if...</span></span>

- <span data-ttu-id="313a3-143">Mevcut kod tabanınız API sözdizimini zaten kullanıyor</span><span class="sxs-lookup"><span data-stu-id="313a3-143">Your existing codebase already uses the API syntax</span></span>
- <span data-ttu-id="313a3-144">Sorgularınızdaki değişkenleri kapsama gerek yok</span><span class="sxs-lookup"><span data-stu-id="313a3-144">You have no need to scope variables within your queries</span></span>
- <span data-ttu-id="313a3-145">API söz dizimini tercih edersiniz ve kod tabanınızdan yok sayılmaz</span><span class="sxs-lookup"><span data-stu-id="313a3-145">You prefer the API syntax and it won't distract from your codebase</span></span>

## <a name="essential-linq"></a><span data-ttu-id="313a3-146">Temel LINQ</span><span class="sxs-lookup"><span data-stu-id="313a3-146">Essential LINQ</span></span>

<span data-ttu-id="313a3-147">LINQ örneklerinin gerçekten kapsamlı bir listesi için, [101 LINQ örnekleri](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)' ni ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="313a3-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="313a3-148">Aşağıdaki örnekler, bazı temel LINQ parçalarından oluşan hızlı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="313a3-148">The following examples are a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="313a3-149">Bu, LINQ 'in burada gösterilen miktardan daha fazla işlevsellik sağladığından, kapsamlı bir şekilde değildir.</span><span class="sxs-lookup"><span data-stu-id="313a3-149">This is in no way comprehensive, as LINQ provides more functionality than what is showcased here.</span></span>

### <a name="the-bread-and-butter---where-select-and-aggregate"></a><span data-ttu-id="313a3-150">Ekleyici ve alın- `Where` , `Select` ve `Aggregate`</span><span class="sxs-lookup"><span data-stu-id="313a3-150">The bread and butter - `Where`, `Select`, and `Aggregate`</span></span>

```csharp
// Filtering a list.
var germanShepherds = dogs.Where(dog => dog.Breed == DogBreed.GermanShepherd);

// Using the query syntax.
var queryGermanShepherds = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepherd
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
Dim germanShepherds = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepherd)

' Using the query syntax.
Dim queryGermanShepherds = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepherd
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

### <a name="flattening-a-list-of-lists"></a><span data-ttu-id="313a3-151">Liste listesini düzleştirme</span><span class="sxs-lookup"><span data-stu-id="313a3-151">Flattening a list of lists</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a><span data-ttu-id="313a3-152">İki küme arasında birleşim (özel karşılaştırıcı ile)</span><span class="sxs-lookup"><span data-stu-id="313a3-152">Union between two sets (with custom comparator)</span></span>

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

### <a name="intersection-between-two-sets"></a><span data-ttu-id="313a3-153">İki küme arasında kesişim</span><span class="sxs-lookup"><span data-stu-id="313a3-153">Intersection between two sets</span></span>

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

### <a name="ordering"></a><span data-ttu-id="313a3-154">Sıralama</span><span class="sxs-lookup"><span data-stu-id="313a3-154">Ordering</span></span>

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

### <a name="equality-of-instance-properties"></a><span data-ttu-id="313a3-155">Örnek özelliklerinin eşitliği</span><span class="sxs-lookup"><span data-stu-id="313a3-155">Equality of instance properties</span></span>

<span data-ttu-id="313a3-156">Son olarak, daha gelişmiş bir örnek: aynı türde iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme (ödünç alınan ve [Bu StackOverflow Post](https://stackoverflow.com/a/844855)'tan değiştirilmiş):</span><span class="sxs-lookup"><span data-stu-id="313a3-156">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

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

## <a name="plinq"></a><span data-ttu-id="313a3-157">PLINQ</span><span class="sxs-lookup"><span data-stu-id="313a3-157">PLINQ</span></span>

<span data-ttu-id="313a3-158">PLıNQ veya Parallel LINQ, LINQ ifadeleri için bir paralel yürütme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="313a3-158">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="313a3-159">Diğer bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı üzerinde oldukça paralelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="313a3-159">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="313a3-160">Bu, önceki ifadeye yönelik bir çağrı aracılığıyla yapılır `AsParallel()` .</span><span class="sxs-lookup"><span data-stu-id="313a3-160">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="313a3-161">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="313a3-161">Consider the following:</span></span>

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

<span data-ttu-id="313a3-162">Bu kod `facebookUsers` , gereken şekilde sistem iş parçacıkları arasında bölümlenir, her iş parçacığında her bir iş parçacığının toplam beğeni paralel olarak toplayın, her bir iş parçacığı tarafından hesaplanan sonuçları ve iyi bir dizeye neden olan projeyi toplayın.</span><span class="sxs-lookup"><span data-stu-id="313a3-162">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="313a3-163">Diyagram formu:</span><span class="sxs-lookup"><span data-stu-id="313a3-163">In diagram form:</span></span>

![PLıNQ diyagramı](media/index/plinq-diagram.png)

<span data-ttu-id="313a3-165">LINQ aracılığıyla kolayca ifade edebileceğiniz paralelleştirilmiş CPU bağlantılı işler (başka bir deyişle, saf işlevlerdir ve yan etkileri yoktur) PLıNQ için harika bir adaydır.</span><span class="sxs-lookup"><span data-stu-id="313a3-165">Parallelizable CPU-bound jobs that can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="313a3-166">Yan _etkisi olan işler_ Için, [görev paralel kitaplığını](../parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="313a3-166">For jobs that _do_ have a side effect, consider using the [Task Parallel Library](../parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="313a3-167">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="313a3-167">More resources</span></span>

* [<span data-ttu-id="313a3-168">101 LINQ örnekleri</span><span class="sxs-lookup"><span data-stu-id="313a3-168">101 LINQ Samples</span></span>](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="313a3-169">C#/F için bir playzemin ortamı ve veritabanı sorgulama altyapısı olan [Linqpad](https://www.linqpad.net/), #/Visual Basic</span><span class="sxs-lookup"><span data-stu-id="313a3-169">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="313a3-170">[Uıulinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ nesnelerinin nasıl uygulandığını öğrenmek için bir e-kitap</span><span class="sxs-lookup"><span data-stu-id="313a3-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
