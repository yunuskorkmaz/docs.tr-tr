---
title: Yineleyiciler
description: Yerleşik kullanmayı öğrenin C# yineleyiciler ve kendi özel yineleyici yöntemleri oluşturma.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: e816af698a39a4b44aefa92017efdbc9e3c8cc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672048"
---
# <a name="iterators"></a>Yineleyiciler

Yazdığınız hemen hemen her program bir koleksiyon üzerinde yinelemek için bazı ihtiyacı olacaktır. Bir koleksiyondaki her öğe inceler kod yazacaksınız.

Ayrıca, söz konusu sınıfın öğeler için bir yineleyici oluşturur yöntemler olan yineleyici yöntemleri oluşturacaksınız. Bunlar için kullanılabilir:

+ Bir koleksiyondaki her öğe üzerinde eylem gerçekleştirme.
+ Özel bir koleksiyona numaralandırma.
+ Genişletme [LINQ](linq/index.md) veya diğer kitaplıkları.
+ Burada veri yineleyici yöntemleri verimli bir şekilde akış veri işlem hattı oluşturma.

C# Dil, bu her iki senaryo için özellikleri sağlar. Bu makalede özelliklere genel bakış sağlar.

Bu öğreticide, birden fazla adım vardır. Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın. Ayrıca [görüntüleme veya indirme tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/iterators) için bu konuda. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Foreach ile yineleme

Koleksiyon numaralandırma basittir: `foreach` Anahtar sözcüğü, koleksiyondaki her öğe için bir kez katıştırılmış deyimi yürütülürken, bir koleksiyon numaralandırır:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

Tüm İşte bu kadar kolay. Tüm içeriğini bir koleksiyon üzerinde yinelemek için `foreach` deyimi tek ihtiyacınız olan. `foreach` Sihirli, ancak olan deyimi değil. Bir koleksiyon yineleme için gereken kodu oluşturmak için .NET core Kitaplığı'nda tanımlanan iki genel arabirimler kullanır: `IEnumerable<T>` ve `IEnumerator<T>`. Bu mekanizma, aşağıda daha ayrıntılı olarak açıklanmıştır.

Bu arabirimlerin her ikisi de genel olmayan karşılıkları vardır: `IEnumerable` ve `IEnumerator`. [Genel](programming-guide/generics/index.md) sürümlere modern kod için tercih edilen sahip.

## <a name="enumeration-sources-with-iterator-methods"></a>Yineleyici yöntemleri kaynaklarıyla numaralandırması

Bir diğer harika özelliği C# dil numaralandırması için bir kaynağı oluşturan yöntemleri oluşturmanıza olanak sağlar. Bunlar olarak adlandırılır *yineleyici metotları*. İstendiğinde bir sırayla nesneleri oluşturmak nasıl bir yineleyici yöntemini tanımlar. Kullandığınız `yield return` yineleyici yöntemini tanımlamak için bağlamsal anahtar sözcükler.

0 ile 9 arasında bir tamsayı dizisi oluşturmak için bu yöntemi yazabilirsiniz:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

Yukarıdaki kod ayrı gösterir `yield return` birden çok ayrı kullanabileceğiniz olgu vurgulamak için deyimleri `yield return` yineleyici yöntemini deyimlerinde.
Kullanabilirsiniz (ve çoğunlukla üyedir) bir yineleyici yöntemin kodu basitleştirmek için diğer dil yapılarının kullanımı. Aşağıdaki yöntem tanımını sayıları tam aynı dizi üretir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Birini veya diğerini karar vermek zorunda değilsiniz. Kadar olabilir `yield return` deyimleri yönteminizi ihtiyaçlarını karşılamak için gerekirse:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    index = 100;
    while (index++ < 110)
        yield return index;
}
```

Temel söz dizimi olmasıdır. Burada bir yineleyici yöntemini yazma bir gerçek dünya örnek düşünelim. Bir IOT projesi üzerinde olduğunuzu ve cihaz sensörlerden çok büyük bir veri akışı oluşturmak düşünün. Bir genel görünüm verilerini almak için her n. veri öğesi örnekleri bir yöntem yazabilirsiniz. Bu küçük yineleyici yöntem ux'in yapar:

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

Yineleyici yöntemlerde önemli bir kısıtlama yoktur: her ikisini birden olamaz bir `return` deyimi ve `yield return` deyiminde aynı yöntemi. Aşağıdaki derlemeyecektir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

Bu kısıtlama, normalde bir sorun değildir. Ya da kullanımının bir seçeneğiniz `yield return` yöntemi veya özgün yöntemi içinde birden çok yöntem ayırarak, bazı kullanarak `return`ve bazı kullanarak `yield return`.

Biraz kullanılacak son yöntemi değiştirebilirsiniz `yield return` her yerde:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

Bazen, bir yineleyici yöntem içinde iki farklı yöntemle bölmek için doğru yanıtı olabilir. Kullanan bir `return`ve kullandığı ikinci `yield return`. Boş bir koleksiyon ya da bir Boole bağımsız değişkenine göre ilk 5 tek sayıları döndürmek için isteyebileceğiniz bir durum düşünün. Bu iki yöntem, yazabilirsiniz:

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```

Yöntemleri yukarıdaki arayın. İlk standardını kullanan `return` deyimini boş bir koleksiyon ya da ikinci yöntemi tarafından oluşturulan bir yineleyici döndürür. İkinci yöntem kullanan `yield return` istenen dizisi oluşturmak için deyimi.

## <a name="deeper-dive-into-foreach"></a>Derinlemesine `foreach`

`foreach` Deyimi kullanan standart bir deyim genişler `IEnumerable<T>` ve `IEnumerator<T>` bir koleksiyonun tüm öğeler arasında yineleme yapmak için gereken arabirimler. Ayrıca geliştiricilerin kaynaklar düzgün şekilde yöneterek olun hataları en aza indirir.

Derleyici çevirir `foreach` bu yapı için benzer bir şeyi ilk örnekte gösterilen döngü:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Yukarıdaki yapısı tarafından oluşturulan kodu temsil eden C# derleyici itibaren sürüm 5 ve üzeri. Sürüm 5, önce `item` değişkeni farklı bir kapsam sahipti:

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

İnce ve sabit lambda ifadeleri içeren hataları tanılamak eski davranışa neden olabileceğinden değiştirildi. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve burada nesne tarafından döndürülen durum işleme `GetEnumerator()` uygulayan `IDisposable` arabirimi. Bu gibi daha fazla kod tam genişletmeyle oluşturur:

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

İçinde Numaralandırıcı, şekilde türünün özelliklerine bağlıdır `enumerator`. Genel durumda `finally` yan tümcesini genişletir:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Ancak, varsa türünü `enumerator` mühürlenmiş bir tür olduğu ve hiç örtük dönüştürme türünden `enumerator` için `IDisposable`, `finally` yan tümcesi için boş bir blok genişletir:

```csharp
finally
{
}
```

Örtük bir dönüştürme türü olup olmadığını `enumerator` için `IDisposable`, ve `enumerator` bir NULL olmayan değer türü `finally` yan tümcesini genişletir:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Ne bu ayrıntıları unutmayın gerek yoktur. `foreach` Deyimi sizin için söz konusu farklılıklarına işler. Derleyici herhangi birini bu yapıları için doğru kodu oluşturur.
