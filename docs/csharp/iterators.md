---
title: Yineleyiciler
description: Yerleşik C# yineleyicilerini kullanmayı ve kendi özel Yineleyici yöntemlerinizi oluşturmayı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: efa755c2243c18fb51b653abccb2bfc702bbc055
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507383"
---
# <a name="iterators"></a>Yineleyiciler

Yazdığınız neredeyse her programın, bir koleksiyon üzerinde yineleme yapması gerekir. Bir koleksiyondaki her öğeyi inceleyen bir kod yazacaksınız.

Ayrıca, bir yineleyici üreten Yöntemler (Bu sınıfın öğeleri için bir kapsayıcıya geçiş yapan bir nesne, özellikle listeler) olan yineleyici yöntemleri de oluşturacaksınız. Bunlar için kullanılabilir:

+ Bir koleksiyondaki her öğe için bir eylem gerçekleştirme.
+ Özel bir koleksiyon numaralandırılıyor.
+ [LINQ](linq/index.md) veya diğer kitaplıkları genişletme.
+ Yineleyici yöntemler aracılığıyla veri akışının etkin olduğu bir veri işlem hattı oluşturma.

C# dili, bu senaryoların her ikisi için de özellikler sağlar. Bu makale, bu özelliklere genel bir bakış sağlar.

Bu öğreticide birden çok adım vardır. Her adımdan sonra, uygulamayı çalıştırabilir ve ilerleme durumunu görebilirsiniz. Ayrıca, bu konu için [Tamamlanan örneği görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/blob/master/csharp/iterators) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Foreach ile yineleme

Bir koleksiyonun numaralandırılması basittir: `foreach` anahtar sözcüğü bir koleksiyonu numaralandırır ve koleksiyondaki her öğe için katıştırılmış deyimin bir kez yürütülmesini ister:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

İşte bu kadar kolay. Bir koleksiyonun tüm içeriğini yinelemek için, tek yapmanız gereken `foreach` ifadedir. `foreach` İfade, olmasa da Magic değildir. Bir koleksiyonu yinelemek için gereken kodu oluşturmak üzere .NET Core kitaplığı 'nda tanımlanan iki genel arabirimi kullanır: `IEnumerable<T>` ve. `IEnumerator<T>` Bu mekanizma aşağıda daha ayrıntılı olarak açıklanmıştır.

Bu arabirimlerin her ikisi de genel olmayan ortaklarınıza sahiptir: `IEnumerable` ve. `IEnumerator` [Genel](programming-guide/generics/index.md) sürümler modern kod için tercih edilir.

## <a name="enumeration-sources-with-iterator-methods"></a>Yineleyici yöntemleriyle listeleme kaynakları

C# dilinin başka harika bir özelliği, bir numaralandırma için kaynak oluşturan Yöntemler oluşturmanıza olanak sağlar. Bunlar *Yineleyici Yöntemler*olarak adlandırılır. Yineleyici yöntemi, istek sırasında nesnelerin bir dizide nasıl oluşturulacağını tanımlar. Bir yineleyici yöntemi `yield return` tanımlamak için bağlamsal anahtar sözcükleri kullanın.

0 ile 9 arasındaki tamsayıların sırasını oluşturmak için bu yöntemi yazabilirsiniz:

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

Yukarıdaki kodda, bir yineleyici `yield return` yönteminde birden çok ayrık `yield return` deyim kullanabileceğiniz olguyu vurgulamak için DISTINCT deyimleri gösterilmektedir.
Bir yineleyici yönteminin kodunu basitleştirmek için diğer dil yapılarını kullanabilirsiniz (ve genellikle bunu yapabilirsiniz). Aşağıdaki yöntem tanımı, tam olarak aynı sayı dizisini üretir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Bir veya başka bir karar vermeniz gerekmez. Yönteminizin ihtiyaçlarını karşılamak için gereken `yield return` sayıda deyime sahip olabilirsiniz:

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

Bu temel sözdizimidir. Bir yineleyici yöntemi yazacağınız gerçek bir dünya örneğini ele alalım. IoT projesinde olduğunuzu ve cihaz sensörleri çok büyük bir veri akışı üretdiğinizi düşünün. Veriler hakkında fikir almak için, her n. veri öğesini örnek bir yöntem yazabilirsiniz. Bu küçük yineleyici yöntemi, Eli:

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

Yineleyici metotlarda önemli bir kısıtlama vardır: aynı yöntemde hem `return` deyimden hem de `yield return` deyiminiz olamaz. Aşağıdakiler derlenmeyecektir:

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

Bu kısıtlama normalde bir sorun değildir. Yöntemini kullanarak `yield return` ya da özgün yöntemi birden çok metoda, bazı kullanımı `return`ve bazı using `yield return`seçeneklerine ayırarak tercih edersiniz.

Son yöntemi her yerde kullanmak `yield return` için biraz daha değiştirebilirsiniz:

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

Bazen doğru yanıt, bir yineleyici yöntemini iki farklı yönteme bölmek olur. `return`Tarafından kullanılan bir ve bir `yield return`. Boole bağımsız değişkenine göre boş bir koleksiyon veya ilk 5 tek sayı döndürmek isteyebileceğiniz bir durum düşünün. Bu iki yöntem olarak yazabilirsiniz:

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

Yukarıdaki yöntemlere bakın. İlki, boş bir koleksiyon `return` ya da ikinci yöntem tarafından oluşturulan Yineleyici döndürmek için standart ifadeyi kullanır. İkinci yöntem, istenen diziyi `yield return` oluşturmak için ifadesini kullanır.

## <a name="deeper-dive-into-foreach"></a>Daha ayrıntılı bilgi`foreach`

`foreach` Deyimi, bir koleksiyonun tüm öğelerinde yinelemek için `IEnumerable<T>` ve `IEnumerator<T>` arabirimlerini kullanan standart bir IOM olarak genişletilir. Ayrıca, geliştiricilerin kaynakları düzgün bir şekilde yönetmediğinden yaptığı hataları da en aza indirir.

Derleyici, ilk örnekte `foreach` gösterilen döngüyü bu yapı ile benzer bir şekilde çevirir:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Yukarıdaki yapı, C# derleyicisi tarafından sürüm 5 ve üzeri itibariyle oluşturulan kodu temsil eder. Sürüm 5 ' ten önce, `item` değişken farklı bir kapsama sahipti:

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

Bu, önceki davranış lambda ifadeleri içeren hataların tanılanması için hafif ve zor bir yol olabileceğinden değiştirildi. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve tarafından `GetEnumerator()` döndürülen nesnenin `IDisposable` Arabirimi uyguladığı durumları işler. Tam genişletme şu şekilde kod üretir:

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

Numaralandırıcının ne şekilde atıldığı, türünün özelliklerine bağlıdır `enumerator`. Genel durumda, `finally` yan tümce şu şekilde genişletilir:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Ancak, `enumerator` türü korumalı bir tür ise ve `enumerator` türünden öğesine `IDisposable`örtülü dönüşüm yoksa, `finally` yan tümce boş bir bloğa genişletilir:

```csharp
finally
{
}
```

Türünden `enumerator` öğesine `IDisposable`örtük bir dönüştürme varsa ve `enumerator` null yapılamayan bir değer türü ise, `finally` yan tümce şu şekilde genişletilir:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Ktam, tüm bu ayrıntıları anımsamanız gerekmez. İfade `foreach` , tüm bu nuslarını sizin için işler. Derleyici bu yapıların herhangi biri için doğru kodu oluşturacaktır.
