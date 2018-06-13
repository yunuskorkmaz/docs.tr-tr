---
title: Yineleyiciler
description: Yerleşik C# yineleyiciler kullanmayı ve kendi özel yineleyici metotları oluşturulacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: d9139f565fb1e426cc1b8cef530187877bdde0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218351"
---
# <a name="iterators"></a>Yineleyiciler

Yazdığınız hemen hemen her program, koleksiyon üzerinde yinelenecek gerek bazı sahip olur. Bir koleksiyondaki her öğe inceler kod yazacaksınız. 

Yineleyici o sınıfın öğelerin üreten yöntemleri yineleyici metotları da oluşturacaksınız. Bunlar için kullanılabilir:

+ Bir koleksiyondaki her öğe bir işlem gerçekleştiriliyor.
+ Özel bir koleksiyona numaralandırma.
+ Genişletme [LINQ](linq/index.md) veya diğer kitaplıkları.
+ Burada veriler yineleyici metotları verimli bir şekilde akar veri ardışık oluşturuluyor.

C# dili için bu iki senaryoya özellikleri sağlar. Bu makalede bu özelliklere genel bakış sağlar.

Bu öğretici, birden çok adım vardır. Her adımdan sonra uygulamayı çalıştırın ve ilerleme bakın. Ayrıca [görüntülemek veya tamamlanan örnek indirme](https://github.com/dotnet/samples/blob/master/csharp/iterators) Bu konu için. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Foreach ile yineleme

Bir koleksiyon numaralandırma basittir: `foreach` anahtar sözcüğü koleksiyondaki her öğe için bir kez katıştırılmış deyimi yürütme bir koleksiyon numaralandırır:
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

Tüm olan İşte bu kadar. Tüm içeriğini bir koleksiyon yineleme `foreach` açıklamadır olması yeterlidir. `foreach` Sihirli, ancak olan ifadesi değil. Bir koleksiyon yinelemek gerekli kodu oluşturmak için .NET core Kitaplığı'nda tanımlanan iki genel arabirimler kullanır: `IEnumerable<T>` ve `IEnumerator<T>`. Bu mekanizma aşağıdaki daha ayrıntılı olarak açıklanmıştır.

Bu arabirimleri her ikisinin de genel olmayan ortaklarınıza vardır: `IEnumerable` ve `IEnumerator`. [Genel](programming-guide/generics/index.md) sürümleri modern kod için tercih edilen.

## <a name="enumeration-sources-with-iterator-methods"></a>Yineleyici metotları kaynaklarıyla numaralandırması

C# dilinin başka bir önemli özellik numaralandırma için bir kaynak oluşturma yöntemleri oluşturmanıza olanak sağlar. Bunlar denir *yineleyici metotları*. İterator yöntemi istendiğinde bir dizisinde nesneleri oluşturmak nasıl tanımlar. Kullandığınız `yield return` yineleyici yöntemi tanımlamak için bağlamsal anahtar sözcükler. 

0 ile 9 arasında tam sayı dizisidir üretmek için bu yöntem yazabilirsiniz:

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

Yukarıdaki kod ayrı gösterir `yield return` birden çok ayrık kullanabileceğiniz olgu vurgulamak için deyimleri `yield return` yineleyici yöntemi deyimlerinde.
(Yapıp genellikle) diğer dil yapıları yineleyici yönteminin kodunu basitleştirmek için kullanın. Aşağıdaki yöntem tanımını sayılardan oluşan tam aynı dizi üretir:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

Birini veya diğerini karar gerekmez. Kadar olabilir `yield return` deyimleri yönteminizi ihtiyaçlarını karşılamak için gerekli olarak:

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

Temel sözdizimi olmasıdır. Şimdi burada yineleyici yöntemi yazma gerçek dünya örneği göz önünde bulundurun. Bir IOT projede olduğunuz ve cihaz algılayıcılar çok büyük bir veri akışı Oluştur düşünün. Verileri bir fikir almak için her n. veri öğesi örnekleri bir yöntem yazabilirsiniz. Bu küçük yineleyici yöntemi eli yapar:

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

Yineleyici metotları ilgili önemli bir kısıtlama yoktur: her ikisi de olamaz bir `return` deyimi ve `yield return` aynı yöntemi deyiminde. Aşağıdaki derlenmez:

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

Bu kısıtlama, normalde bir sorun değildir. Her iki kullanarak seçenekleriniz vardır `yield return` yöntemi veya birden çok yöntemlerin içine özgün yöntemi ayırarak, bazı kullanarak `return`ve bazı kullanarak `yield return`.

Son yöntemini biraz kullanmak üzere değiştirebileceğiniz `yield return` her yerde:

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
 
Bazen, iki farklı yöntemlere yineleyici yöntemi bölme sağ yanıt olabilir. Kullanan `return`, kullanır ikinci `yield return`. Burada boş bir koleksiyon veya bir boolean bağımsız göre ilk 5 tek sayıları Döndür isteyebilirsiniz bir durum düşünün. Bu iki yöntem yazabilirsiniz:

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
 
Yöntemleri yukarıdaki arayın. İlk standardını kullanır `return` boş bir koleksiyon ya da ikinci yöntemi tarafından oluşturulan yineleyici döndürülecek deyimi. İkinci bir yöntem `yield return` istenen dizisi oluşturmak için ifade.

## <a name="deeper-dive-into-foreach"></a>Derin Dalış içine `foreach`

`foreach` Deyimi genişletir kullanan standart bir deyim `IEnumerable<T>` ve `IEnumerator<T>` bir koleksiyonun tüm öğeler arasında yinelemek için arabirim. Ayrıca düzgün kaynakları yöneterek geliştiriciler olun hatalar en aza indirir. 

Derleyici çevirir `foreach` bu yapıyı benzer bir şey içine ilk örnekte gösterilen döngü:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Yukarıdaki yapı C# Derleyici sürüm 5'ten itibaren ve yukarıdaki tarafından oluşturulan kodu temsil eder. Sürüm 5, önce `item` değişkeni farklı bir kapsam vardı:

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

Bu, önceki davranış ince ve sabit lambda ifadeleri içeren hataları tanılamak neden olabileceğinden değiştirildi. Bölümüne bakarak [lambda ifadeleri](lambda-expressions.md) daha fazla bilgi için. 

Derleyici tarafından üretilen tam kod biraz daha karmaşıktır ve nereye nesne tarafından döndürülen durum işleme `GetEnumerator()` uygulayan `IDisposable` arabirimi. Tam genişletme bu gibi daha fazla kod oluşturur:

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

İçinde Numaralandırıcı, şekilde türü özelliklerine bağlıdır `enumerator`. Genel durumda `finally` yan tümcesi genişletir için:

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

Ancak, varsa türünü `enumerator` korumalı türü ve tür örtük bir dönüştürme yok `enumerator` için `IDisposable`, `finally` yan tümcesi için boş bir blok genişletir:
```csharp
finally 
{
} 
```

Türü örtük bir dönüştürme olup olmadığını `enumerator` için `IDisposable`, ve `enumerator` bir null değer türü `finally` yan tümcesi genişletir için:

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

Thankfully, bu ayrıntıları unutmayın gerek yoktur. `foreach` Deyimi sizin için bu nüanslarını işler. Derleyici herhangi biri bu yapıları için doğru kodunu oluşturur. 


