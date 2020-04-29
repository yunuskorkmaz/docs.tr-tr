---
title: LINQ (dil ile tümleşik sorgu)
description: LINQ 'ın dil düzeyinde sorgulama özellikleri ve C# için bir API ve Visual Basic ifade ve bildirim temelli kod yazmanın bir yolu olarak nasıl sağladığı hakkında bilgi edinin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 76872f3ba3ed5106a4cb5bfdd918ae607acc092d
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507526"
---
# <a name="linq-language-integrated-query"></a>LINQ (dil ile tümleşik sorgu)

## <a name="what-is-it"></a>Bu nedir?

LINQ, dil düzeyinde sorgulama özellikleri ve C# için [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API 'si ve Visual Basic ifade, bildirime dayalı kod yazmak için bir yol sağlar.

Dil düzeyi sorgu sözdizimi:

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

`IEnumerable<T>` API kullanarak aynı örnek:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a>LINQ, Ifade

Evcil hayvan listenizin bir listesini olduğunu düşünün ancak onu doğrudan `RFID` değerine göre erişebileceğiniz bir sözlüğe dönüştürmek istiyorsunuz.

Geleneksel kesinlik kodu:

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

Kodun arkasındaki amaç, yeni `Dictionary<int, Pet>` bir oluşturma ve bir döngü aracılığıyla buna ekleme değil, var olan bir listeyi bir sözlüğe dönüştürmektir! LINQ, zorunlu kod değil, amaç korur.

Denk LINQ ifadesi:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

LINQ kullanan kod, bir programcı olarak düşünmekte olan amaç ve kod arasında oynatma alanı olduğunu iddia ettiğinden değerlidir. Başka bir ödül kod örneği. Yukarıdaki kod temelinin büyük bölümlerini, yukarıdaki 1/3 göre azaltmayı düşünün. Harika bir anlaşma, doğru mu?

## <a name="linq-providers-simplify-data-access"></a>LINQ sağlayıcıları veri erişimini basitleştirir

Joker karakter üzerinde önemli bir yazılım yığını için, her şey bir kaynaktaki (veritabanları, JSON, XML, vb.) verilerle ilgilenir. Genellikle bu, sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenmesini içerir. LINQ, veri erişiminin ortak öğelerinin, hangi veri kaynağını kullandığınıza bağımsız olarak aynı olduğunu gösteren bir sorgu söz dizimine soyutlayarak bunu basitleştirir.

Aşağıdakileri göz önünde bulundurun: belirli bir öznitelik değeri ile tüm XML öğelerini bulma.

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

Bu görevi gerçekleştirmek için XML belgesine el ile çapraz geçiş yapmak üzere kod yazmak çok daha zor olabilir.

XML ile etkileşim kurmak, LINQ sağlayıcılarıyla yapabileceğiniz tek şey değildir. [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) , bir MSSQL sunucu veritabanı için oldukça basit bir nesne Ilişkisel eşleyicisidir (ORM). [JSON.net](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) KITAPLıĞı, LINQ aracılığıyla verimli JSON belge geçişi sağlar. Ayrıca, gerek duyduğunuz şeyi belirleyen bir kitaplık yoksa [kendı LINQ sağlayıcınızı de yazabilirsiniz](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!

## <a name="why-use-the-query-syntax"></a>Sorgu söz dizimini neden kullanmalısınız?

Bu, genellikle gelen bir sorudır. Tümü, bu,

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

Bu sorunun yanıtı **Evet** ...

* Mevcut kod tabanınız zaten sorgu sözdizimini kullanıyor
* Karmaşıklık nedeniyle Sorgularınızdaki değişkenlerin kapsamını belirlemeniz gerekir
* Sorgu söz dizimini tercih edersiniz ve kod tabanınızdan yok olmayacaktır

Bu sorunun **yanıtı şu şekilde değildir.** ..

* Mevcut kod tabanınız API sözdizimini zaten kullanıyor
* Sorgularınızdaki değişkenleri kapsama gerek yok
* API söz dizimini tercih edersiniz ve kod tabanınızdan yok sayılmaz

## <a name="essential-samples"></a>Temel örnekler

LINQ örneklerinin gerçekten kapsamlı bir listesi için, [101 LINQ örnekleri](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)' ni ziyaret edin.

Aşağıda, LINQ 'ın bazı temel parçaları için hızlı bir gösterim verilmiştir. Bu, LINQ olarak daha fazla işlevsellik sağladığından, bu kapsamda önemli değildir.

* İçerik- `Where`, `Select`, ve: `Aggregate`

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

* Liste listesini düzleştirme:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* İki küme arasında birleşim (özel karşılaştırıcısı ile):

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

* İki küme arasında kesişim:

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

* Sıralama

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

* Son olarak, daha gelişmiş bir örnek: aynı türde iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme (ödünç alınan ve [Bu StackOverflow Post](https://stackoverflow.com/a/844855)'tan değiştirilmiş):

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

PLıNQ veya Parallel LINQ, LINQ ifadeleri için bir paralel yürütme altyapısıdır. Diğer bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı üzerinde oldukça paralelleştirilmiş olabilir. Bu, önceki ifadeye yönelik `AsParallel()` bir çağrı aracılığıyla yapılır.

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

Bu kod, gereken `facebookUsers` şekilde sistem iş parçacıkları arasında bölümlenir, her iş parçacığında her bir iş parçacığının toplam beğeni paralel olarak toplayın, her bir iş parçacığı tarafından hesaplanan sonuçları ve iyi bir dizeye neden olan projeyi toplayın.

Diyagram formu:

![PLıNQ diyagramı](./media/using-linq/plinq-diagram.png)

LINQ aracılığıyla kolayca ifade edebileceğiniz paralelleştirilmiş, CPU 'ya dayalı işler (başka bir deyişle, saf işlevlerdir ve yan etkileri yoktur) PLıNQ için harika bir adaydır. Yan _etkisi olan işler_ Için, [görev paralel kitaplığını](./parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.

## <a name="further-resources"></a>Daha fazla kaynak:

* [101 LINQ örnekleri](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)
* C#/F için bir playzemin ortamı ve veritabanı sorgulama altyapısı olan [Linqpad](https://www.linqpad.net/), #/Visual Basic
* [Uıulinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ nesnelerinin nasıl uygulandığını öğrenmek için bir e-kitap
