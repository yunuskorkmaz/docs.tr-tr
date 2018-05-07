---
title: LINQ (dil ile tümleşik sorgu)
description: Nasıl LINQ dil düzeyi sorgulama özellikleri ve bir API C# ve VB etkileyici, bildirim temelli kod yazmak için bir yol olarak sağladığını öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 21b0995872047484bf1581190622c52f0e2527a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-language-integrated-query"></a>LINQ (dil ile tümleşik sorgu)

## <a name="what-is-it"></a>Nedir o?

LINQ dil düzeyi sorgulama özellikleri sağlar ve bir [daha yüksek sıralı işlevi](https://en.wikipedia.org/wiki/Higher-order_function) C# ve VB etkileyici, bildirim temelli kod yazmak için bir yol olarak API.

Dil düzeyi sorgu söz dizimi:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Aynı örneği kullanarak `IEnumerable<T>` API'si:

```csharp
var linqExperts = programmers.Where(p => IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ Expressive olduğu

Evcil Hayvanlar listesi sahip, ancak erişebileceğiniz bir evcil hayvan doğrudan göre sözlükteki dönüştürmek istediğiniz düşünün kendi `RFID` değeri.

Geleneksel kesinlik temelli kod:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Kod arkasında amacınıza yeni bir değil oluşturmaktır `Dictionary<int, Pet>` ve eklemek için bir döngü olan mevcut bir listeyi sözlükteki dönüştürmek için! Kesinlik temelli kod'in almadığı LINQ amacınıza korur.

Eşdeğer LINQ ifadesi:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

LINQ kullanarak kod Programcı olarak akıl zaman amacı kodu arasında oyun alanını evens için faydalıdır. Başka bir avantaj kod kısaltma ' dir. 1/3 yukarıdaki gibi bir codebase büyük bölümünü azaltmayı düşünün. Oldukça tatlı anlaşma, doğru?

## <a name="linq-providers-simplify-data-access"></a>Veri erişimi LINQ sağlayıcıları basitleştirin

Joker out yazılımda önemli bir öbek için her şeyi (veritabanları, JSON, XML, vb.), bazı kaynağından veri postalarla etrafında döner. Genellikle bu can sıkıcı olabilir her veri kaynağı için yeni bir API öğrenme içerir. LINQ bu veri erişimi ortak öğeler aynı veri kaynağını olsun, çekme görünen bir sorgu sözdizimi özetleyen tarafından basitleştirir.

Aşağıdakileri dikkate alın: belirli öznitelik değeri olan tüm XML öğeleri bulma.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Bu görevi gerçekleştirmek için XML belgesi el ile geçiş için kod yazma, çok daha zor olurdu.

XML ile etkileşim LINQ sağlayıcıları ile yapabileceğiniz tek şey değil. [LINQ-SQL](../../docs/framework/data/adonet/sql/linq/index.md) bir oldukça tam kemikler nesne ilişkisel Eşleyici (ORM) bir MSSQL sunucu için veritabanıdır. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplığı LINQ aracılığıyla verimli JSON belgesi geçişi sağlar. Gerekenler yapan bir kitaplık yoksa, ayrıca, şunları da yapabilirsiniz [kendi LINQ sağlayıcı yazma](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Sorgu sözdizimi neden kullanılır?

Genellikle gelen bir soru budur. Sonra bu,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

Bu çok daha kısa aşağıdaki gibidir:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

API sözdizimi yalnızca sorgu sözdizimi yapmak için daha kısa yol değil mi?

Hayır. Sorgu sözdizimi için kullanımına izin verir **izin** getirir ve ifade sonraki parçalarını de kullanmayı ifadesi, kapsamı içinde bir değişken bağlamak izin veren yan tümcesi. Aynı kodu yeniden yalnızca API sözdizimi ile yapılabilir, ancak büyük olasılıkla okunması zor olan kod çalıştırılmasına neden.

Bu soru begs şekilde **sorgu sözdizimi yalnızca kullanmalısınız?**

Bu soruya yanıt **Evet** varsa...

*   Var olan codebase zaten kullanıyor sorgu söz dizimi
*   Sorgularınızın karmaşıklığı nedeniyle içinde kapsam değişkenlere gerekir
*   Sorgu sözdizimi tercih ve temelinizde gelen rahatsız olmaz

Bu soruya yanıt **hiçbir** varsa...

*   Var olan codebase zaten kullanıyor API sözdizimi
*   Kapsam değişkenleri gerek sorgularınızı içinde sahip
*   Tercih ettiğiniz API sözdizimi ve temelinizde gelen rahatsız olmaz

## <a name="essential-samples"></a>Temel örnekleri

LINQ örnekleri gerçekten kapsamlı bir listesi için ziyaret [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Bazı temel parçalar LINQ hızlı bir örnek verilmiştir. LINQ burada showcased daha önemli ölçüde daha fazla işlevsellik sağlayan bu kapsamlı, hiçbir şekilde aynıdır.

*   Ekmek ve ezmesi - `Where`, `Select`, ve `Aggregate`:

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

*   Liste listesini düzleştirme:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   UNION iki kümeleriyle (özel karşılaştırıcı) arasında:

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

*   İki küme arasındaki kesişimi:

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

*   Sıralama:

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

*   Son olarak, örnek daha gelişmiş: aynı türde iki örneği özelliklerinin değerleri eşit olup olmadığını belirleme (Borrowed ve gelen değiştirilmiş [bu StackOverflow post](http://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ ya da paralel LINQ bir paralel yürütme LINQ ifadeleri için altyapısıdır. Diğer bir deyişle, normal bir LINQ ifadeleri trivially iş parçacıkları arasında herhangi bir sayı paralel birkaç ölçeklendirin. Bu çağrı aracılığıyla gerçekleştirilir `AsParallel()` ifade önceki.

Aşağıdakileri göz önünde bulundurun:

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

Bu kod bölüm `facebookUsers` gerektiği gibi toplam yöntemlerine paralel, her iş parçacığı üzerinde toplama sistem iş parçacıkları arasında her iş parçacığı tarafından hesaplanan sonuçlarını toplamak ve iyi bir dizeye sonucunda ortaya çıkan proje.

Diyagram formunda:

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

LINQ kolayca ifade edilebilir paralelleştirilebilir CPU bağımlı işleri (diğer bir deyişle, saf işlevleri ve hiçbir yan etkisi) PLINQ harika aday olan. İşler, _yapmak_ bir yan etkisi, kullanmayı [görev paralel Kitaplığı](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Ek kaynaklar:

*   [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), playground ortamı ve veritabanını sorgulama için C# /F #/VB altyapısı
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), bir e-LINQ nesneler nasıl uygulandığına öğrenme için kitap
