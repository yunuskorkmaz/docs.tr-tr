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
ms.openlocfilehash: 65370a2bd21e2474af4cb070bb8d82a167f10070
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555002"
---
# <a name="linq-overview"></a>LINQ'e genel bakış

Dil ile tümleşik sorgu (LINQ), dil düzeyinde sorgulama özellikleri ve C# ve Visual Basic için [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API 'si sağlar. bu sayede, açıklayıcı bildirime dayalı bir kod yazmanıza olanak tanınır.

## <a name="language-level-query-syntax"></a>Dil düzeyi sorgu söz dizimi

Bu, dil düzeyi sorgu sözdizimidir:

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

Bu, API kullanan aynı örneğidir `IEnumerable<T>` :

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ, ifade

Evcil hayvan listenizin bir listesini olduğunu düşünün ancak onu doğrudan değerine göre erişebileceğiniz bir sözlüğe dönüştürmek istiyorsunuz `RFID` .

Bu geleneksel bir zorunlu koddur:

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

Kodun arkasındaki amaç yeni bir oluşturma `Dictionary<int, Pet>` ve bir döngü aracılığıyla buna eklememe, var olan bir listeyi bir sözlüğe dönüştürmektir! LINQ, zorunlu kod değil, amaç korur.

Bu eşdeğer LINQ deyimidir:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

LINQ kullanan kod, bir programcı olarak düşünmekte olan amaç ve kod arasında oynatma alanı olduğunu iddia ettiğinden değerlidir. Başka bir ödül kod örneği. Yukarıdaki kod temelinin büyük bölümlerini, yukarıdaki 1/3 göre azaltmayı düşünün. Tatlı, doğru mu?

## <a name="linq-providers-simplify-data-access"></a>LINQ sağlayıcıları veri erişimini basitleştirir

Joker karakter üzerinde önemli bir yazılım yığını için her şey, bazı kaynaklardan (veritabanları, JSON, XML vb.) verilerle ilgilenir. Genellikle bu, sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenmesini içerir. LINQ, veri erişiminin ortak öğelerinin, hangi veri kaynağını kullandığınıza bağımsız olarak aynı olduğunu gösteren bir sorgu söz dizimine soyutlayarak bunu basitleştirir.

Bu, belirli bir öznitelik değerine sahip tüm XML öğelerini bulur:

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

Bu görevi yapmak için XML belgesine el ile çapraz geçiş yapmak üzere kod yazma çok daha zor olabilir.

XML ile etkileşim kurmak, LINQ sağlayıcılarıyla yapabileceğiniz tek şey değildir. [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) , bir MSSQL sunucu veritabanı için oldukça basit bir nesne Ilişkisel eşleyicisidir (ORM). [JSON.net](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) KITAPLıĞı, LINQ aracılığıyla verimli JSON belge geçişi sağlar. Ayrıca, gerek duyduğunuz şeyi yapan bir kitaplık yoksa [kendı LINQ sağlayıcınızı de yazabilirsiniz](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!

## <a name="reasons-to-use-the-query-syntax"></a>Sorgu söz dizimini kullanma nedenleri

Sorgu söz dizimi neden kullanılmalıdır? Bu, genellikle gelen bir sorudır. Tümü sonrasında aşağıdaki kod:

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

Bundan çok daha kısa.

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

Sorgu söz dizimini yapmak için API sözdizimi yalnızca daha kısa bir yol değil mi?

Hayır. Sorgu söz dizimi, ifadenin sonraki parçalarında kullanarak bir değişkeni ifade kapsamındaki bir değişken oluşturmanıza ve bağlamanıza imkan tanıyan **Let** yan tümcesinin kullanılmasına izin verir. Aynı kodun yalnızca API söz dizimi ile tekrar oluşturulması gerçekleştirilebilir, ancak büyük olasılıkla okunması zor olan koda neden olur.

Bu nedenle, bu soruyu **yalnızca sorgu söz dizimini kullanmanız gerekir mi?**

Şu durumlarda bu sorunun yanıtı **Evet** 'tir:

- Mevcut kod tabanınız sorgu sözdizimini zaten kullanıyor.
- Karmaşıklık nedeniyle Sorgularınızdaki değişkenlerin kapsamını belirlemeniz gerekir.
- Sorgu söz dizimini tercih edersiniz ve kod tabanınızdan yok olmayacaktır.

Bu sorunun **yanıtı şu şekilde değildir.** ..

- Mevcut kod tabanınız API sözdizimini zaten kullanıyor
- Sorgularınızdaki değişkenleri kapsama gerek yok
- API söz dizimini tercih edersiniz ve kod tabanınızdan yok sayılmaz

## <a name="essential-linq"></a>Temel LINQ

LINQ örneklerinin gerçekten kapsamlı bir listesi için, [101 LINQ örnekleri](/samples/dotnet/try-samples/101-linq-samples/)' ni ziyaret edin.

Aşağıdaki örnekler, bazı temel LINQ parçalarından oluşan hızlı bir örnektir. Bu, LINQ 'in burada gösterilen miktardan daha fazla işlevsellik sağladığından, kapsamlı bir şekilde değildir.

### <a name="the-bread-and-butter---where-select-and-aggregate"></a>Ekleyici ve alın- `Where` , `Select` ve `Aggregate`

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

### <a name="flattening-a-list-of-lists"></a>Liste listesini düzleştirme

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a>İki küme arasında birleşim (özel karşılaştırıcı ile)

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

### <a name="intersection-between-two-sets"></a>İki küme arasında kesişim

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

### <a name="ordering"></a>Sıralama

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

### <a name="equality-of-instance-properties"></a>Örnek özelliklerinin eşitliği

Son olarak, daha gelişmiş bir örnek: aynı türde iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme (ödünç alınan ve [Bu StackOverflow Post](https://stackoverflow.com/a/844855)'tan değiştirilmiş):

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

## <a name="plinq"></a>PLINQ

PLıNQ veya Parallel LINQ, LINQ ifadeleri için bir paralel yürütme altyapısıdır. Diğer bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı üzerinde oldukça paralelleştirilmiş olabilir. Bu, önceki ifadeye yönelik bir çağrı aracılığıyla yapılır `AsParallel()` .

Aşağıdaki topluluklara bir göz atın:

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

Bu kod `facebookUsers` , gereken şekilde sistem iş parçacıkları arasında bölümlenir, her iş parçacığında her bir iş parçacığının toplam beğeni paralel olarak toplayın, her bir iş parçacığı tarafından hesaplanan sonuçları ve iyi bir dizeye neden olan projeyi toplayın.

Diyagram formu:

![PLıNQ diyagramı](media/index/plinq-diagram.png)

LINQ aracılığıyla kolayca ifade edebileceğiniz paralelleştirilmiş CPU bağlantılı işler (başka bir deyişle, saf işlevlerdir ve yan etkileri yoktur) PLıNQ için harika bir adaydır. Yan _etkisi olan işler_ Için, [görev paralel kitaplığını](../parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.

## <a name="more-resources"></a>Diğer kaynaklar

* [101 LINQ örnekleri](/samples/dotnet/try-samples/101-linq-samples/)
* C#/F için bir playzemin ortamı ve veritabanı sorgulama altyapısı olan [Linqpad](https://www.linqpad.net/), #/Visual Basic
* [Uıulinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ nesnelerinin nasıl uygulandığını öğrenmek için bir e-kitap
