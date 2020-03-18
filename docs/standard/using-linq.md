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
# <a name="linq-language-integrated-query"></a>LINQ (Dil Tümleşik Sorgu)

## <a name="what-is-it"></a>Bu nedir?

LINQ, anlamlı, bildirimsel kod yazmanın bir yolu olarak C# ve Visual Basic'e dil düzeyinde sorgulama yetenekleri ve [daha yüksek sıralı bir işlev](https://en.wikipedia.org/wiki/Higher-order_function) API'si sağlar.

Dil düzeyinde sorgu sözdizimi:

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

## <a name="linq-is-expressive"></a>LINQ Etkileyicidir

Evcil hayvan bir liste var düşünün, ama doğrudan değeri bir `RFID` evcil hayvan erişebilirsiniz bir sözlük haline dönüştürmek istiyorum.

Geleneksel zorunlu kod:

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

Kodun arkasındaki amaç yeni `Dictionary<int, Pet>` bir oluşturmak ve bir döngü üzerinden eklemek değil, bir sözlük içine mevcut bir liste dönüştürmek için! LINQ amacı nı korurken, zorunlu kod korumaz.

Eşdeğer LINQ ifadesi:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

LINQ'yi kullanan kod değerlidir, çünkü programcı olarak muhakeme yaparken amaç ve kod arasındaki oyun alanını eşitler. Başka bir bonus kod kısalığı olduğunu. Yukarıda yapıldığı gibi bir kod tabanının büyük bölümlerini 1/3 azalttığınızı düşünün. Çok hoş bir anlaşma, değil mi?

## <a name="linq-providers-simplify-data-access"></a>LINQ Sağlayıcıları Veri Erişimini Basitleştirir

Vahşi yazılım önemli bir yığın için, her şey bazı kaynak (Veritabanları, JSON, XML, vb) verileri ile ilgili etrafında döner. Genellikle bu rahatsız edici olabilir her veri kaynağı için yeni bir API öğrenme içerir. LINQ, hangi veri kaynağını seçerseniz seçin aynı görünen bir sorgu sözdizimine ortak veri erişimi öğelerini soyutlayarak bunu basitleştirir.

Aşağıdakileri göz önünde bulundurun: belirli bir öznitelik değeri olan tüm XML öğelerini bulma.

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

Bu görevi gerçekleştirmek için XML belgesini el ile geçmek için kod yazmak çok daha zor olacaktır.

XML ile etkileşim LINQ Sağlayıcıları ile yapabileceğiniz tek şey değildir. [Linq to SQL,](../../docs/framework/data/adonet/sql/linq/index.md) MSSQL Server Veritabanı için oldukça çıplak bir Nesne-İlişkisel Mapper (ORM) dir. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplığı LINQ üzerinden verimli JSON Belge geçiş sağlar. Ayrıca, ihtiyacınız olanı yapan bir kütüphane yoksa, [kendi LINQ Sağlayıcınızı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))da yazabilirsiniz!

## <a name="why-use-the-query-syntax"></a>Sorgu Sözdizimini Neden Kullanıyor?

Bu sık sık gündeme gelen bir sorudur. Ne de olsa, bu,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

bundan çok daha kısa:

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

API sözdizimi sorgu sözdizimini yapmak için daha kısa bir yol değil mi?

Hayır. Sorgu sözdizimi, ifadenin sonraki parçalarında kullanarak ifade kapsamında bir değişken ikleyen ve bağlamanızı sağlayan **let** yan tümcesinin kullanılmasına olanak tanır. Yalnızca API sözdizimi ile aynı kodu çoğaltma yapılabilir, ancak büyük olasılıkla okunması zor koda yol açacaktır.

Yani bu şu soruyu akla getiriyor, **sadece sorgu sözdizimini mi kullanmalısınız?**

Bu sorunun cevabı **evet** eğer ...

* Varolan kod tabanınız sorgu sözdizimini zaten kullanır
* Karmaşıklık nedeniyle sorgularınızdaki değişkenleri kapsamanız gerekir
* Sorgu sözdizimini tercih ederseniz, kod tabanınızdan dikkatini dağıtmaz

Bu sorunun cevabı **hayır** eğer ...

* Varolan kod tabanınız api sözdizimini zaten kullanır
* Sorgularınızda değişkenleri kapsamanız gerekmez
* API sözdizimini tercih ederseniz, kod tabanınızın dikkatini dağıtmaz

## <a name="essential-samples"></a>Temel Örnekler

LINQ örneklerinin gerçekten kapsamlı bir listesi için [101 LINQ Örneği'ni](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)ziyaret edin.

Aşağıda LINQ'nun bazı temel parçalarının hızlı bir gösterimi yer almaktadır. LINQ burada sergilenenden çok daha fazla işlevsellik sağladığından, bu hiçbir şekilde kapsamlı değildir.

* Ekmek ve tereyağı `Where` `Select`- `Aggregate`, , ve:

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

* Listelerin listesini düzleştirmek:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* İki küme arasındaki birlik (özel karşılaştırıcı ile):

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

* İki küme arasındaki kesişme:

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

* Sipariş:

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

* Son olarak, daha gelişmiş bir örnek: aynı türdeki iki örneğin özelliklerinin değerlerinin eşit olup olmadığını belirleme [(Bu StackOverflow gönderisinden](https://stackoverflow.com/a/844855)ödünç alınan ve değiştirilen):

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

PLINQ veya Parallel LINQ, LINQ ifadeleri için paralel bir yürütme motorudur. Başka bir deyişle, normal bir LINQ ifadesi herhangi bir sayıda iş parçacığı arasında önemsiz bir şekilde paralelleştirilebilir. Bu, ifadeden `AsParallel()` önce yapılan bir çağrı ile gerçekleştirilir.

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

Bu kod `facebookUsers` gerektiğinde sistem iş parçacıkları arasında bölüm, paralel olarak her iş parçacığı üzerinde toplam beğeni toplamı, her iş parçacığı tarafından hesaplanan sonuçları toplamı ve güzel bir dize içine sonuç proje.

Diyagram şeklinde:

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

Linq ile kolayca ifade edilebilen paralelleştirilebilir CPU'ya bağlı işler (diğer bir deyişle, saf fonksiyonlardır ve yan etkileri yoktur) PLINQ için harika bir adaydır. Yan etkisi _olan_ işler için Görev [Paralel Kitaplığı'nı](./parallel-programming/task-parallel-library-tpl.md)kullanmayı düşünün.

## <a name="further-resources"></a>Diğer Kaynaklar:

* [101 LINQ Örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
* [Linqpad](https://www.linqpad.net/), C#/F#/Visual Basic için bir oyun alanı ortamı ve Veritabanı sorgulama motoru
* [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), LINQ-to-objects nasıl uygulandığını öğrenmek için bir e-kitap
