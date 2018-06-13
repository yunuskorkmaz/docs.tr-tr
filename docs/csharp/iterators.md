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
# <a name="iterators"></a><span data-ttu-id="1c12e-103">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="1c12e-103">Iterators</span></span>

<span data-ttu-id="1c12e-104">Yazdığınız hemen hemen her program, koleksiyon üzerinde yinelenecek gerek bazı sahip olur.</span><span class="sxs-lookup"><span data-stu-id="1c12e-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="1c12e-105">Bir koleksiyondaki her öğe inceler kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1c12e-105">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="1c12e-106">Yineleyici o sınıfın öğelerin üreten yöntemleri yineleyici metotları da oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1c12e-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="1c12e-107">Bunlar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1c12e-107">These can be used for:</span></span>

+ <span data-ttu-id="1c12e-108">Bir koleksiyondaki her öğe bir işlem gerçekleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="1c12e-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="1c12e-109">Özel bir koleksiyona numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="1c12e-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="1c12e-110">Genişletme [LINQ](linq/index.md) veya diğer kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="1c12e-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="1c12e-111">Burada veriler yineleyici metotları verimli bir şekilde akar veri ardışık oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1c12e-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="1c12e-112">C# dili için bu iki senaryoya özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c12e-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="1c12e-113">Bu makalede bu özelliklere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c12e-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="1c12e-114">Bu öğretici, birden çok adım vardır.</span><span class="sxs-lookup"><span data-stu-id="1c12e-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="1c12e-115">Her adımdan sonra uygulamayı çalıştırın ve ilerleme bakın.</span><span class="sxs-lookup"><span data-stu-id="1c12e-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="1c12e-116">Ayrıca [görüntülemek veya tamamlanan örnek indirme](https://github.com/dotnet/samples/blob/master/csharp/iterators) Bu konu için.</span><span class="sxs-lookup"><span data-stu-id="1c12e-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="1c12e-117">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="1c12e-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="1c12e-118">Foreach ile yineleme</span><span class="sxs-lookup"><span data-stu-id="1c12e-118">Iterating with foreach</span></span>

<span data-ttu-id="1c12e-119">Bir koleksiyon numaralandırma basittir: `foreach` anahtar sözcüğü koleksiyondaki her öğe için bir kez katıştırılmış deyimi yürütme bir koleksiyon numaralandırır:</span><span class="sxs-lookup"><span data-stu-id="1c12e-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="1c12e-120">Tüm olan İşte bu kadar.</span><span class="sxs-lookup"><span data-stu-id="1c12e-120">That's all there is to it.</span></span> <span data-ttu-id="1c12e-121">Tüm içeriğini bir koleksiyon yineleme `foreach` açıklamadır olması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1c12e-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="1c12e-122">`foreach` Sihirli, ancak olan ifadesi değil.</span><span class="sxs-lookup"><span data-stu-id="1c12e-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="1c12e-123">Bir koleksiyon yinelemek gerekli kodu oluşturmak için .NET core Kitaplığı'nda tanımlanan iki genel arabirimler kullanır: `IEnumerable<T>` ve `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="1c12e-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="1c12e-124">Bu mekanizma aşağıdaki daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c12e-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="1c12e-125">Bu arabirimleri her ikisinin de genel olmayan ortaklarınıza vardır: `IEnumerable` ve `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="1c12e-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="1c12e-126">[Genel](programming-guide/generics/index.md) sürümleri modern kod için tercih edilen.</span><span class="sxs-lookup"><span data-stu-id="1c12e-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="1c12e-127">Yineleyici metotları kaynaklarıyla numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1c12e-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="1c12e-128">C# dilinin başka bir önemli özellik numaralandırma için bir kaynak oluşturma yöntemleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c12e-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="1c12e-129">Bunlar denir *yineleyici metotları*.</span><span class="sxs-lookup"><span data-stu-id="1c12e-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="1c12e-130">İterator yöntemi istendiğinde bir dizisinde nesneleri oluşturmak nasıl tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c12e-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="1c12e-131">Kullandığınız `yield return` yineleyici yöntemi tanımlamak için bağlamsal anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="1c12e-131">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="1c12e-132">0 ile 9 arasında tam sayı dizisidir üretmek için bu yöntem yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c12e-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="1c12e-133">Yukarıdaki kod ayrı gösterir `yield return` birden çok ayrık kullanabileceğiniz olgu vurgulamak için deyimleri `yield return` yineleyici yöntemi deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="1c12e-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="1c12e-134">(Yapıp genellikle) diğer dil yapıları yineleyici yönteminin kodunu basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c12e-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="1c12e-135">Aşağıdaki yöntem tanımını sayılardan oluşan tam aynı dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="1c12e-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="1c12e-136">Birini veya diğerini karar gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1c12e-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="1c12e-137">Kadar olabilir `yield return` deyimleri yönteminizi ihtiyaçlarını karşılamak için gerekli olarak:</span><span class="sxs-lookup"><span data-stu-id="1c12e-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="1c12e-138">Temel sözdizimi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1c12e-138">That's the basic syntax.</span></span> <span data-ttu-id="1c12e-139">Şimdi burada yineleyici yöntemi yazma gerçek dünya örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1c12e-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="1c12e-140">Bir IOT projede olduğunuz ve cihaz algılayıcılar çok büyük bir veri akışı Oluştur düşünün.</span><span class="sxs-lookup"><span data-stu-id="1c12e-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="1c12e-141">Verileri bir fikir almak için her n. veri öğesi örnekleri bir yöntem yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c12e-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="1c12e-142">Bu küçük yineleyici yöntemi eli yapar:</span><span class="sxs-lookup"><span data-stu-id="1c12e-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="1c12e-143">Yineleyici metotları ilgili önemli bir kısıtlama yoktur: her ikisi de olamaz bir `return` deyimi ve `yield return` aynı yöntemi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="1c12e-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="1c12e-144">Aşağıdaki derlenmez:</span><span class="sxs-lookup"><span data-stu-id="1c12e-144">The following will not compile:</span></span>

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

<span data-ttu-id="1c12e-145">Bu kısıtlama, normalde bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="1c12e-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="1c12e-146">Her iki kullanarak seçenekleriniz vardır `yield return` yöntemi veya birden çok yöntemlerin içine özgün yöntemi ayırarak, bazı kullanarak `return`ve bazı kullanarak `yield return`.</span><span class="sxs-lookup"><span data-stu-id="1c12e-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="1c12e-147">Son yöntemini biraz kullanmak üzere değiştirebileceğiniz `yield return` her yerde:</span><span class="sxs-lookup"><span data-stu-id="1c12e-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="1c12e-148">Bazen, iki farklı yöntemlere yineleyici yöntemi bölme sağ yanıt olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c12e-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="1c12e-149">Kullanan `return`, kullanır ikinci `yield return`.</span><span class="sxs-lookup"><span data-stu-id="1c12e-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="1c12e-150">Burada boş bir koleksiyon veya bir boolean bağımsız göre ilk 5 tek sayıları Döndür isteyebilirsiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="1c12e-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="1c12e-151">Bu iki yöntem yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c12e-151">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="1c12e-152">Yöntemleri yukarıdaki arayın.</span><span class="sxs-lookup"><span data-stu-id="1c12e-152">Look at the methods above.</span></span> <span data-ttu-id="1c12e-153">İlk standardını kullanır `return` boş bir koleksiyon ya da ikinci yöntemi tarafından oluşturulan yineleyici döndürülecek deyimi.</span><span class="sxs-lookup"><span data-stu-id="1c12e-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="1c12e-154">İkinci bir yöntem `yield return` istenen dizisi oluşturmak için ifade.</span><span class="sxs-lookup"><span data-stu-id="1c12e-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="1c12e-155">Derin Dalış içine `foreach`</span><span class="sxs-lookup"><span data-stu-id="1c12e-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="1c12e-156">`foreach` Deyimi genişletir kullanan standart bir deyim `IEnumerable<T>` ve `IEnumerator<T>` bir koleksiyonun tüm öğeler arasında yinelemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="1c12e-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="1c12e-157">Ayrıca düzgün kaynakları yöneterek geliştiriciler olun hatalar en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="1c12e-157">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="1c12e-158">Derleyici çevirir `foreach` bu yapıyı benzer bir şey içine ilk örnekte gösterilen döngü:</span><span class="sxs-lookup"><span data-stu-id="1c12e-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="1c12e-159">Yukarıdaki yapı C# Derleyici sürüm 5'ten itibaren ve yukarıdaki tarafından oluşturulan kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c12e-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="1c12e-160">Sürüm 5, önce `item` değişkeni farklı bir kapsam vardı:</span><span class="sxs-lookup"><span data-stu-id="1c12e-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="1c12e-161">Bu, önceki davranış ince ve sabit lambda ifadeleri içeren hataları tanılamak neden olabileceğinden değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1c12e-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="1c12e-162">Bölümüne bakarak [lambda ifadeleri](lambda-expressions.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="1c12e-162">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="1c12e-163">Derleyici tarafından üretilen tam kod biraz daha karmaşıktır ve nereye nesne tarafından döndürülen durum işleme `GetEnumerator()` uygulayan `IDisposable` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c12e-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="1c12e-164">Tam genişletme bu gibi daha fazla kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1c12e-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="1c12e-165">İçinde Numaralandırıcı, şekilde türü özelliklerine bağlıdır `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="1c12e-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="1c12e-166">Genel durumda `finally` yan tümcesi genişletir için:</span><span class="sxs-lookup"><span data-stu-id="1c12e-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="1c12e-167">Ancak, varsa türünü `enumerator` korumalı türü ve tür örtük bir dönüştürme yok `enumerator` için `IDisposable`, `finally` yan tümcesi için boş bir blok genişletir:</span><span class="sxs-lookup"><span data-stu-id="1c12e-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="1c12e-168">Türü örtük bir dönüştürme olup olmadığını `enumerator` için `IDisposable`, ve `enumerator` bir null değer türü `finally` yan tümcesi genişletir için:</span><span class="sxs-lookup"><span data-stu-id="1c12e-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="1c12e-169">Thankfully, bu ayrıntıları unutmayın gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="1c12e-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="1c12e-170">`foreach` Deyimi sizin için bu nüanslarını işler.</span><span class="sxs-lookup"><span data-stu-id="1c12e-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="1c12e-171">Derleyici herhangi biri bu yapıları için doğru kodunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c12e-171">The compiler will generate the correct code for any of these constructs.</span></span> 


