---
title: Yineleyiciler
description: Yerleşik C# yineleyicilerini nasıl kullanacağınızı ve kendi özel yineleme yöntemlerinizi nasıl oluşturup oluşturup oluşturup oluşturup oluşturmayı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 1933ecf83e9fa234f9b88c815d8ab527997c97f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399618"
---
# <a name="iterators"></a>Yineleyiciler

Yazdığınız hemen hemen her program bir koleksiyon üzerinde tekrarlamak için bazı ihtiyaç olacaktır. Koleksiyondaki her öğeyi inceleyen kod yazarsınız.

Ayrıca, bu sınıfın öğeleri için bir yineleyici üreten yöntemler olan yineleme yöntemleri de oluşturursunuz. Bunlar şunlar için kullanılabilir:

+ Koleksiyondaki her öğe üzerinde eylem gerçekleştirme.
+ Özel bir koleksiyonu niçin oyalama.
+ [LINQ](linq/index.md) veya diğer kitaplıkları genişletme.
+ Veri yineleme yöntemleri ile verimli bir şekilde aktığı bir veri ardışık alanı oluşturma.

C# dili, bu senaryoların her ikisi için de özellikler sağlar. Bu makalede, bu özelliklere genel bir bakış sağlar.

Bu öğreticinin birden çok adımı vardır. Her adımdan sonra, uygulamayı çalıştırabilir ve ilerlemeyi görebilirsiniz. Ayrıca, bu konu [için tamamlanan örneği görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/blob/master/csharp/iterators) İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

## <a name="iterating-with-foreach"></a>Her biri ile iterating

Bir koleksiyonu niçin oyalama `foreach` basittir: Anahtar kelime, koleksiyondaki her öğe için katıştırılmış deyimi bir kez çalıştırarak bir koleksiyonu nitreler:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

İşte bu kadar kolay. Bir koleksiyonun tüm içeriğini tekrarlamak için `foreach` tek ihtiyacınız olan ifadedir. İfade `foreach` sihirli değil ama. Bir koleksiyonu yeniden sıralamak için gerekli kodu oluşturmak için .NET çekirdek kitaplığında tanımlanan `IEnumerable<T>` `IEnumerator<T>`iki genel arabirime dayanır: ve. Bu mekanizma aşağıda daha ayrıntılı olarak açıklanmıştır.

Bu arabirimlerin her ikisi de genel `IEnumerable` olmayan `IEnumerator`muadilleri vardır: ve . [Genel](programming-guide/generics/index.md) sürümler modern kod için tercih edilir.

## <a name="enumeration-sources-with-iterator-methods"></a>Yineleme yöntemleri ile numaralandırma kaynakları

C# dilinin bir diğer büyük özelliği, numaralandırma için kaynak oluşturan yöntemler oluşturmanıza olanak tanır. Bunlara *yineleyici yöntemleri*denir. Yineleyici yöntemi, istendiğinde nesnelerin sırayla nasıl oluşturulabildiğini tanımlar. Bir yineleyici yöntemitanımlamak için `yield return` bağlamsal anahtar kelimeleri kullanırsınız.

0'dan 9'a kadar tamsayı dizisini oluşturmak için bu yöntemi yazabilirsiniz:

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

Yukarıdaki kod, `yield return` bir yineleyici yönteminde birden çok ayrı `yield return` deyim kullanabildiğinizgerçeğini vurgulamak için farklı ifadeler gösterir.
Bir yineleyici yönteminin kodunu basitleştirmek için diğer dil yapılarını kullanabilirsiniz (ve genellikle yapabilirsiniz). Aşağıdaki yöntem tanımı, sayıların tam olarak aynı sırasını üretir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Birini ya da diğerini karar vermek zorunda değilsin. Yönteminizin gereksinimlerini `yield return` karşılamak için gerektiği kadar ifadeniz olabilir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

Bu temel sözdizimi. Bir yineleme yöntemi yazacağınız gerçek bir örnek düşünelim. Bir IoT projesinde olduğunuzu ve cihaz sensörlerinin çok büyük bir veri akışı oluşturduğunuzu düşünün. Verileri görmek için her Nth veri öğesini örnekleyen bir yöntem yazabilirsiniz. Bu küçük yineleyici yöntemi hile yapar:

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

Yineleyici yöntemleri üzerinde önemli bir kısıtlama vardır: aynı yöntemde hem bir `return` deyim hem de ifade `yield return` olamaz. Aşağıdakiderlemeolmaz:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

Bu kısıtlama normalde bir sorun değildir. Ya yöntem boyunca kullanarak `yield return` bir seçim var, ya da birden çok yöntem, bazı `return` `yield return`kullanarak orijinal yöntem e bölme , ve bazı kullanarak .

Her yerde kullanmak `yield return` için son yöntemi biraz değiştirebilirsiniz:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

Bazen doğru cevap, bir yineleyici yöntemini iki farklı yönteme bölmektir. Bir kullanır `return`, ve kullanan `yield return`bir saniye . Boş bir koleksiyonu veya boolean bağımsız değişkenini temel alan ilk 5 tek sayıyı döndürmek isteyebileceğiniz bir durum düşünün. Bunu şu iki yöntem olarak yazabilirsiniz:

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
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

Yukarıdaki yöntemlere bakın. İlki, boş `return` bir koleksiyonu veya ikinci yöntem tarafından oluşturulan yineleyiciyi döndürmek için standart deyimi kullanır. İkinci yöntem, `yield return` istenen sırayı oluşturmak için deyimi kullanır.

## <a name="deeper-dive-into-foreach"></a>Içine Deeper Dalış`foreach`

Deyim, `foreach` koleksiyonun tüm öğeleriarasında yinelemek `IEnumerable<T>` `IEnumerator<T>` için ve arabirimleri kullanan standart bir deyim olarak genişletir. Ayrıca, geliştiricilerin kaynakları düzgün yönetmeyerek yaptıkları hataları en aza indirir.

Derleyici, ilk `foreach` örnekte gösterilen döngüyü bu yapıya benzer bir şeye çevirir:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Yukarıdaki yapı, C# derleyicisi tarafından sürüm 5 ve üzeri olarak oluşturulan kodu temsil eder. Sürüm 5'ten `item` önce değişkenin farklı bir kapsamı vardı:

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

Bu, önceki davranış ince ve zor lambda ifadeleri içeren hataları teşhis yol açabilir, çünkü değiştirildi. Lambda ifadeleri hakkında daha fazla bilgi için [Lambda ifadeleri'ne](./programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.

Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve nesnenin `GetEnumerator()` `IDisposable` arabirimi uyguladığı durumları işler. Tam genişletme daha fazla bu gibi kod oluşturur:

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

Enumeratörün atılma şekli, türünün özelliklerine `enumerator`bağlıdır. Genel durumda, `finally` yan tümce aşağıdakilere genişletir:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Ancak, `enumerator` türü mühürlü bir tür ise ve türünden `enumerator` örtülü bir `IDisposable`dönüştürme `finally` yoksa , yan tümce boş bir bloya genişletir:

```csharp
finally
{
}
```

Türünden `enumerator` `IDisposable`() `enumerator` ve nullable olmayan bir değer türünden örtülü bir `finally` dönüştürme varsa, yan tümce aşağıdakilere genişletilir:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Neyse ki, tüm bu ayrıntıları hatırlamak gerekmez. `foreach` İfade sizin için tüm bu nüansları ele. Derleyici, bu yapılardan herhangi biri için doğru kodu oluşturur.
