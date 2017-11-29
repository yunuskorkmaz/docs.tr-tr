---
title: Yineleyiciler
description: "Yerleşik C# yineleyiciler kullanmayı ve kendi özel yineleyici metotları oluşturulacağını öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 18a5819402c752f32aecd0cd4c3bd5a490292ebf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iterators"></a><span data-ttu-id="91906-104">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="91906-104">Iterators</span></span>

<span data-ttu-id="91906-105">Yazdığınız hemen hemen her program, koleksiyon üzerinde yinelenecek gerek bazı sahip olur.</span><span class="sxs-lookup"><span data-stu-id="91906-105">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="91906-106">Bir koleksiyondaki her öğe inceler kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="91906-106">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="91906-107">Yineleyici o sınıfın öğelerin üreten yöntemleri yineleyici metotları da oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="91906-107">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="91906-108">Bunlar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="91906-108">These can be used for:</span></span>

+ <span data-ttu-id="91906-109">Bir koleksiyondaki her öğe bir işlem gerçekleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="91906-109">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="91906-110">Özel bir koleksiyona numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="91906-110">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="91906-111">Genişletme [LINQ](linq/index.md) veya diğer kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="91906-111">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="91906-112">Burada veriler yineleyici metotları verimli bir şekilde akar veri ardışık oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="91906-112">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="91906-113">C# dili için bu iki senaryoya özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="91906-113">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="91906-114">Bu makalede bu özelliklere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="91906-114">This article provides an overview of those features.</span></span>

<span data-ttu-id="91906-115">Bu öğretici, birden çok adım vardır.</span><span class="sxs-lookup"><span data-stu-id="91906-115">This tutorial has multiple steps.</span></span> <span data-ttu-id="91906-116">Her adımdan sonra uygulamayı çalıştırın ve ilerleme bakın.</span><span class="sxs-lookup"><span data-stu-id="91906-116">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="91906-117">Ayrıca [görüntülemek veya tamamlanan örnek indirme](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) Bu konu için.</span><span class="sxs-lookup"><span data-stu-id="91906-117">You can also [view or download the completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) for this topic.</span></span> <span data-ttu-id="91906-118">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="91906-118">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="91906-119">Foreach ile yineleme</span><span class="sxs-lookup"><span data-stu-id="91906-119">Iterating with foreach</span></span>

<span data-ttu-id="91906-120">Bir koleksiyon numaralandırma basittir: `foreach` anahtar sözcüğü koleksiyondaki her öğe için bir kez katıştırılmış deyimi yürütme bir koleksiyon numaralandırır:</span><span class="sxs-lookup"><span data-stu-id="91906-120">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="91906-121">Tüm olan İşte bu kadar.</span><span class="sxs-lookup"><span data-stu-id="91906-121">That's all there is to it.</span></span> <span data-ttu-id="91906-122">Tüm içeriğini bir koleksiyon yineleme `foreach` açıklamadır olması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="91906-122">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="91906-123">`foreach` Sihirli, ancak olan ifadesi değil.</span><span class="sxs-lookup"><span data-stu-id="91906-123">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="91906-124">Bir koleksiyon yinelemek gerekli kodu oluşturmak için .NET core Kitaplığı'nda tanımlanan iki genel arabirimler kullanır: `IEnumerable<T>` ve `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="91906-124">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="91906-125">Bu mekanizma aşağıdaki daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="91906-125">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="91906-126">Bu arabirimleri her ikisinin de genel olmayan ortaklarınıza vardır: `IEnumerable` ve `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="91906-126">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="91906-127">[Genel](programming-guide/generics/index.md) sürümleri modern kod için tercih edilen.</span><span class="sxs-lookup"><span data-stu-id="91906-127">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="91906-128">Yineleyici metotları kaynaklarıyla numaralandırması</span><span class="sxs-lookup"><span data-stu-id="91906-128">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="91906-129">C# dilinin başka bir önemli özellik numaralandırma için bir kaynak oluşturma yöntemleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="91906-129">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="91906-130">Bunlar denir *yineleyici metotları*.</span><span class="sxs-lookup"><span data-stu-id="91906-130">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="91906-131">İterator yöntemi istendiğinde bir dizisinde nesneleri oluşturmak nasıl tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91906-131">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="91906-132">Kullandığınız `yield return` yineleyici yöntemi tanımlamak için bağlamsal anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="91906-132">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="91906-133">0 ile 9 arasında tam sayı dizisidir üretmek için bu yöntem yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91906-133">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="91906-134">Yukarıdaki kod ayrı gösterir `yield return` birden çok ayrık kullanabileceğiniz olgu vurgulamak için deyimleri `yield return` yineleyici yöntemi deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="91906-134">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="91906-135">(Yapıp genellikle) diğer dil yapıları yineleyici yönteminin kodunu basitleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="91906-135">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="91906-136">Aşağıdaki yöntem tanımını sayılardan oluşan tam aynı dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="91906-136">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="91906-137">Birini veya diğerini karar gerekmez.</span><span class="sxs-lookup"><span data-stu-id="91906-137">You don't have to decide one or the other.</span></span> <span data-ttu-id="91906-138">Kadar olabilir `yield return` deyimleri yönteminizi ihtiyaçlarını karşılamak için gerekli olarak:</span><span class="sxs-lookup"><span data-stu-id="91906-138">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="91906-139">Temel sözdizimi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="91906-139">That's the basic syntax.</span></span> <span data-ttu-id="91906-140">Şimdi burada yineleyici yöntemi yazma gerçek dünya örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="91906-140">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="91906-141">Bir IOT projede olduğunuz ve cihaz algılayıcılar çok büyük bir veri akışı Oluştur düşünün.</span><span class="sxs-lookup"><span data-stu-id="91906-141">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="91906-142">Verileri bir fikir almak için her n. veri öğesi örnekleri bir yöntem yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91906-142">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="91906-143">Bu küçük yineleyici yöntemi eli yapar:</span><span class="sxs-lookup"><span data-stu-id="91906-143">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="91906-144">Yineleyici metotları ilgili önemli bir kısıtlama yoktur: her ikisi de olamaz bir `return` deyimi ve `yield return` aynı yöntemi deyiminde.</span><span class="sxs-lookup"><span data-stu-id="91906-144">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="91906-145">Aşağıdaki derlenmez:</span><span class="sxs-lookup"><span data-stu-id="91906-145">The following will not compile:</span></span>

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

<span data-ttu-id="91906-146">Bu kısıtlama, normalde bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="91906-146">This restriction normally isn't a problem.</span></span> <span data-ttu-id="91906-147">Her iki kullanarak seçenekleriniz vardır `yield return` yöntemi veya birden çok yöntemlerin içine özgün yöntemi ayırarak, bazı kullanarak `return`ve bazı kullanarak `yield return`.</span><span class="sxs-lookup"><span data-stu-id="91906-147">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="91906-148">Son yöntemini biraz kullanmak üzere değiştirebileceğiniz `yield return` her yerde:</span><span class="sxs-lookup"><span data-stu-id="91906-148">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="91906-149">Bazen, iki farklı yöntemlere yineleyici yöntemi bölme sağ yanıt olabilir.</span><span class="sxs-lookup"><span data-stu-id="91906-149">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="91906-150">Kullanan `return`, kullanır ikinci `yield return`.</span><span class="sxs-lookup"><span data-stu-id="91906-150">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="91906-151">Burada boş bir koleksiyon veya bir boolean bağımsız göre ilk 5 tek sayıları Döndür isteyebilirsiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="91906-151">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="91906-152">Bu iki yöntem yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91906-152">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="91906-153">Yöntemleri yukarıdaki arayın.</span><span class="sxs-lookup"><span data-stu-id="91906-153">Look at the methods above.</span></span> <span data-ttu-id="91906-154">İlk standardını kullanır `return` boş bir koleksiyon ya da ikinci yöntemi tarafından oluşturulan yineleyici döndürülecek deyimi.</span><span class="sxs-lookup"><span data-stu-id="91906-154">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="91906-155">İkinci bir yöntem `yield return` istenen dizisi oluşturmak için ifade.</span><span class="sxs-lookup"><span data-stu-id="91906-155">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="91906-156">Derin Dalış içine`foreach`</span><span class="sxs-lookup"><span data-stu-id="91906-156">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="91906-157">`foreach` Deyimi genişletir kullanan standart bir deyim `IEnumable<T>` ve `IEnumerator<T>` bir koleksiyonun tüm öğeler arasında yinelemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="91906-157">The `foreach` statement expands into a standard idiom that uses the `IEnumable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="91906-158">Ayrıca düzgün kaynakları yöneterek geliştiriciler olun hatalar en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="91906-158">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="91906-159">Derleyici çevirir `foreach` bu yapıyı benzer bir şey içine ilk örnekte gösterilen döngü:</span><span class="sxs-lookup"><span data-stu-id="91906-159">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="91906-160">Yukarıdaki yapı C# Derleyici sürüm 5'ten itibaren ve yukarıdaki tarafından oluşturulan kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91906-160">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="91906-161">Sürüm 5, önce `item` değişkeni farklı bir kapsam vardı:</span><span class="sxs-lookup"><span data-stu-id="91906-161">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="91906-162">Bu, önceki davranış ince ve sabit lambda ifadeleri içeren hataları tanılamak neden olabileceğinden değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="91906-162">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="91906-163">Bölümüne bakarak [lambda ifadeleri](lambda-expressions.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="91906-163">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="91906-164">Derleyici tarafından üretilen tam kod biraz daha karmaşıktır ve nereye nesne tarafından döndürülen durum işleme `GetEnumerator()` uygulayan `IDisposable` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="91906-164">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="91906-165">Tam genişletme bu gibi daha fazla kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="91906-165">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="91906-166">İçinde Numaralandırıcı, şekilde türü özelliklerine bağlıdır `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="91906-166">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="91906-167">Genel durumda `finally` yan tümcesi genişletir için:</span><span class="sxs-lookup"><span data-stu-id="91906-167">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="91906-168">Ancak, varsa türünü `enumerator` korumalı türü ve tür örtük bir dönüştürme yok `enumerator` için `IDisposable`, `finally` yan tümcesi için boş bir blok genişletir:</span><span class="sxs-lookup"><span data-stu-id="91906-168">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="91906-169">Türü örtük bir dönüştürme olup olmadığını `enumerator` için `IDisposable`, ve `enumerator` bir null değer türü `finally` yan tümcesi genişletir için:</span><span class="sxs-lookup"><span data-stu-id="91906-169">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="91906-170">Thankfully, bu ayrıntıları unutmayın gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="91906-170">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="91906-171">`foreach` Deyimi sizin için bu nüanslarını işler.</span><span class="sxs-lookup"><span data-stu-id="91906-171">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="91906-172">Derleyici herhangi biri bu yapıları için doğru kodunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91906-172">The compiler will generate the correct code for any of these constructs.</span></span> 


