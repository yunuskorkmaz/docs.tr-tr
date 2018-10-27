---
title: LINQ (dil ile tümleşik sorgu)
description: Nasıl LINQ dil düzeyinde sorgulama özellikleri ve bir API C# ve VB için etkileyici ve bildirim temelli bir kod yazmak için bir yol sağladığını öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: 8ce7f39d78006765a49bbd4e3d46c611761a4bd1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181741"
---
# <a name="linq-language-integrated-query"></a>LINQ (dil ile tümleşik sorgu)

## <a name="what-is-it"></a>Nedir o?

LINQ dil düzeyinde sorgulama özellikleri sağlar ve bir [yüksek sıralı işlev](https://en.wikipedia.org/wiki/Higher-order_function) C# ve VB ifadesel ve bildirim temelli bir kod yazmak için bir yol olarak API.

Dil düzeyi sorgu söz dizimi:

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

Aynı örneği kullanarak `IEnumerable<T>` API:

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

## <a name="linq-is-expressive"></a>LINQ Expressive olduğu

Evcil Hayvanlar listesi vardır, ancak erişebileceğiniz bir evcil hayvan doğrudan göre bir sözlük içinde dönüştürmek istediğiniz Imagine kendi `RFID` değeri.

Geleneksel kesinlik temelli kod:

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

Yeni bir oluşturmamayı niyetini kod arkasında olan `Dictionary<int, Pet>` ve eklemek için bir döngü yoluyla olan mevcut bir listeyi sözlükteki dönüştürmek için! Kesinlik temelli Kodun desteklemez LINQ niyetini korur.

Eşdeğer LINQ ifadesi:

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

LINQ kullanarak kodu oyun alanını hedefi ile kod arasında bir programcısı akıl olduğunda evens için değerlidir. Başka bir ödül kod kısaltma ' dir. 1/3 yukarıdaki gibi büyük bir kod temeli bölümlerini azaltmayı düşünün. Oldukça tatlı anlaşma, doğru?

## <a name="linq-providers-simplify-data-access"></a>LINQ sağlayıcıları veri erişimini basitleştirme

Out joker yazılım önemli bir öbek için her şeyi (veritabanları, JSON, XML, vb.) bir kaynaktan veri uğraşmanızı geçici olarak döner. Genellikle bu sinir bozucu olabilecek her bir veri kaynağı için yeni bir API öğrenme içerir. LINQ veri erişiminin ortak öğeler aynı hangi veri kaynağı ne olursa olsun, çekme görünen bir sorgu söz dizimi özetleyen tarafından basitleştirir.

Aşağıdakileri dikkate alın: özel öznitelik değeri olan tüm XML öğeleri bulma.

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

Bu görevi gerçekleştirmek için XML belgesi el ile geçirmek için kod yazma, çok daha zor olurdu.

XML ile etkileşim LINQ sağlayıcıları ile yapmanız gereken tek şey değildir. [LINQ to SQL](../../docs/framework/data/adonet/sql/linq/index.md) bir oldukça çıplak kemikler nesne-ilişkisel Eşleyici (ORM) bir MSSQL Server veritabanıdır. [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) kitaplık etkin JSON belgesinde geçişi LINQ aracılığıyla sağlar. Aradığınızı yapan bir kitaplık yoksa, ayrıca, ayrıca [kendi LINQ sağlayıcınızı yazma](https://msdn.microsoft.com/library/Bb546158.aspx)!

## <a name="why-use-the-query-syntax"></a>Sorgu söz dizimi neden kullanmalısınız?

Genellikle gelen bir soru budur. Sonra bu,

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

Bundan çok daha kısa olabilir:

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

API sözdizimi sorgu söz dizimi yapmak için yalnızca daha kısa bir yol değil mi?

Hayır. Sorgu söz dizimi için izin verir **izin** tanıtır ve sonraki ifade parçalarını de kullanmayı ifadesi, kapsamı içinde bir değişken bağlamasına izin veren yan tümcesi. Aynı kodu yeniden oluştururken yalnızca API söz dizimi ile yapılabilir, ancak büyük olasılıkla okunması zor olan kodlara neden.

Soru sorun bu şekilde **yalnızca sorgu söz dizimi kullanmalısınız?**

Bu sorunun yanıtı **Evet** varsa...

*   Mevcut codebase zaten kullandığı sorgu söz dizimi
*   Sorgularınızın karmaşıklığı nedeniyle içinde kapsam değişkenleri gerekir
*   Tercih ettiğiniz sorgu söz dizimi ve kod temelinizde departmanınızı olmaz

Bu sorunun yanıtı **hiçbir** varsa...

*   Mevcut codebase zaten kullandığı API söz dizimi
*   İçinde sorgularınızı kapsam değişkenleri gerek sahip
*   Tercih ettiğiniz API söz dizimi ve kod temelinizde departmanınızı olmaz

## <a name="essential-samples"></a>Temel örnekler

LINQ örnekleri gerçekten kapsamlı bir listesi için ziyaret [101 LINQ örnekleri](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b).

Bazı önemli parçaları LINQ hızlı bir örnek verilmiştir. LINQ burada büyütmüş daha önemli ölçüde daha fazla işlevsellik sağladığından kapsamlı, hiçbir şekilde budur.

*   Ekmekler ve ezmesi - `Where`, `Select`, ve `Aggregate`:

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

*   Bir liste düzleştirme:

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

*   UNION (ile özel bir karşılaştırıcı) iki kümesi arasında:

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

*   İki kesişimi:

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

*   Son olarak, örnek daha gelişmiş: iki örneği aynı türdeki özelliklerin değerlerini eşit olup olmadığını belirleme (Borrowed ve gelen değiştirilmiş [StackOverflow yazıya](https://stackoverflow.com/a/844855)):

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

## <a name="plinq"></a>PLINQ

PLINQ ve paralel LINQ bir paralel yürütme için LINQ ifadelerini altyapısıdır. Diğer bir deyişle, normal bir LINQ ifadesini basit bir şekilde herhangi bir iş parçacığı sayısı arasında paralel. Bu bir çağrı aracılığıyla gerçekleştirilir `AsParallel()` önceki ifade.

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

Bu kod bölüm `facebookUsers` gerekirse, toplam beğenilerin paralel, her bir iş parçacığı üzerinde toplama sistem iş parçacıklarını arasında her iş parçacığı tarafından hesaplanan sonuçlarını toplamak ve bu sonucu güzel bir dizeye proje.

Diyagram formunda:

![PLINQ diyagramı](./media/using-linq/plinq-diagram.png)

LINQ ile kolayca ifade edilebilir paralelleştirilebilir CPU bağımlı iş (diğer bir deyişle, saf işlevler ve yan etkileri) PLINQ için mükemmel bir adaydır. İşler, _yapmak_ bir yan etkisi, kullanmayı [görev paralel Kitaplığı](./parallel-programming/task-parallel-library-tpl.md).

## <a name="further-resources"></a>Ek kaynaklar:

*   [101 LINQ örneği](https://code.msdn.microsoft.com/101-LINQ-Samples-3fb9811b)
*   [Linqpad](https://www.linqpad.net/), oyun alanı ortamı ve veritabanını sorgulama için C# /F #/VB altyapısı
*   [EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/),-LINQ nesnelerin nasıl gerçekleştirilir öğrenmek için kitap
