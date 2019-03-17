---
title: Yineleyiciler
description: Yerleşik kullanmayı öğrenin C# yineleyiciler ve kendi özel yineleyici yöntemleri oluşturma.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 37ed45fc563eacf0c6bf412dcfb28dbc6db2bb17
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126051"
---
# <a name="iterators"></a><span data-ttu-id="15b58-103">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="15b58-103">Iterators</span></span>

<span data-ttu-id="15b58-104">Yazdığınız hemen hemen her program bir koleksiyon üzerinde yinelemek için bazı ihtiyacı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="15b58-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="15b58-105">Bir koleksiyondaki her öğe inceler kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="15b58-105">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="15b58-106">Ayrıca, söz konusu sınıfın öğeler için bir yineleyici oluşturur yöntemler olan yineleyici yöntemleri oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="15b58-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="15b58-107">Bunlar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="15b58-107">These can be used for:</span></span>

+ <span data-ttu-id="15b58-108">Bir koleksiyondaki her öğe üzerinde eylem gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="15b58-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="15b58-109">Özel bir koleksiyona numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="15b58-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="15b58-110">Genişletme [LINQ](linq/index.md) veya diğer kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="15b58-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="15b58-111">Burada veri yineleyici yöntemleri verimli bir şekilde akış veri işlem hattı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="15b58-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="15b58-112">C# Dil, bu her iki senaryo için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="15b58-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="15b58-113">Bu makalede özelliklere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="15b58-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="15b58-114">Bu öğreticide, birden fazla adım vardır.</span><span class="sxs-lookup"><span data-stu-id="15b58-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="15b58-115">Her adımdan sonra uygulamayı çalıştırmak ve ilerleme durumuna bakın.</span><span class="sxs-lookup"><span data-stu-id="15b58-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="15b58-116">Ayrıca [görüntüleme veya indirme tamamlanan örnek](https://github.com/dotnet/samples/blob/master/csharp/iterators) için bu konuda.</span><span class="sxs-lookup"><span data-stu-id="15b58-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="15b58-117">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="15b58-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="15b58-118">Foreach ile yineleme</span><span class="sxs-lookup"><span data-stu-id="15b58-118">Iterating with foreach</span></span>

<span data-ttu-id="15b58-119">Koleksiyon numaralandırma basittir: `foreach` Anahtar sözcüğü, koleksiyondaki her öğe için bir kez katıştırılmış deyimi yürütülürken, bir koleksiyon numaralandırır:</span><span class="sxs-lookup"><span data-stu-id="15b58-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="15b58-120">Tüm İşte bu kadar kolay.</span><span class="sxs-lookup"><span data-stu-id="15b58-120">That's all there is to it.</span></span> <span data-ttu-id="15b58-121">Tüm içeriğini bir koleksiyon üzerinde yinelemek için `foreach` deyimi tek ihtiyacınız olan.</span><span class="sxs-lookup"><span data-stu-id="15b58-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="15b58-122">`foreach` Sihirli, ancak olan deyimi değil.</span><span class="sxs-lookup"><span data-stu-id="15b58-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="15b58-123">Bir koleksiyon yineleme için gereken kodu oluşturmak için .NET core Kitaplığı'nda tanımlanan iki genel arabirimler kullanır: `IEnumerable<T>` ve `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="15b58-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="15b58-124">Bu mekanizma, aşağıda daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="15b58-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="15b58-125">Bu arabirimlerin her ikisi de genel olmayan karşılıkları vardır: `IEnumerable` ve `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="15b58-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="15b58-126">[Genel](programming-guide/generics/index.md) sürümlere modern kod için tercih edilen sahip.</span><span class="sxs-lookup"><span data-stu-id="15b58-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="15b58-127">Yineleyici yöntemleri kaynaklarıyla numaralandırması</span><span class="sxs-lookup"><span data-stu-id="15b58-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="15b58-128">Bir diğer harika özelliği C# dil numaralandırması için bir kaynağı oluşturan yöntemleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="15b58-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="15b58-129">Bunlar olarak adlandırılır *yineleyici metotları*.</span><span class="sxs-lookup"><span data-stu-id="15b58-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="15b58-130">İstendiğinde bir sırayla nesneleri oluşturmak nasıl bir yineleyici yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15b58-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="15b58-131">Kullandığınız `yield return` yineleyici yöntemini tanımlamak için bağlamsal anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="15b58-131">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="15b58-132">0 ile 9 arasında bir tamsayı dizisi oluşturmak için bu yöntemi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15b58-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="15b58-133">Yukarıdaki kod ayrı gösterir `yield return` birden çok ayrı kullanabileceğiniz olgu vurgulamak için deyimleri `yield return` yineleyici yöntemini deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="15b58-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="15b58-134">Kullanabilirsiniz (ve çoğunlukla üyedir) bir yineleyici yöntemin kodu basitleştirmek için diğer dil yapılarının kullanımı.</span><span class="sxs-lookup"><span data-stu-id="15b58-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="15b58-135">Aşağıdaki yöntem tanımını sayıları tam aynı dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="15b58-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="15b58-136">Birini veya diğerini karar vermek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b58-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="15b58-137">Kadar olabilir `yield return` deyimleri yönteminizi ihtiyaçlarını karşılamak için gerekirse:</span><span class="sxs-lookup"><span data-stu-id="15b58-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="15b58-138">Temel söz dizimi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="15b58-138">That's the basic syntax.</span></span> <span data-ttu-id="15b58-139">Burada bir yineleyici yöntemini yazma bir gerçek dünya örnek düşünelim.</span><span class="sxs-lookup"><span data-stu-id="15b58-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="15b58-140">Bir IOT projesi üzerinde olduğunuzu ve cihaz sensörlerden çok büyük bir veri akışı oluşturmak düşünün.</span><span class="sxs-lookup"><span data-stu-id="15b58-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="15b58-141">Bir genel görünüm verilerini almak için her n. veri öğesi örnekleri bir yöntem yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b58-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="15b58-142">Bu küçük yineleyici yöntem ux'in yapar:</span><span class="sxs-lookup"><span data-stu-id="15b58-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="15b58-143">Yineleyici yöntemlerde önemli bir kısıtlama yoktur: her ikisini birden olamaz bir `return` deyimi ve `yield return` deyiminde aynı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15b58-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="15b58-144">Aşağıdaki derlemeyecektir:</span><span class="sxs-lookup"><span data-stu-id="15b58-144">The following will not compile:</span></span>

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

<span data-ttu-id="15b58-145">Bu kısıtlama, normalde bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="15b58-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="15b58-146">Ya da kullanımının bir seçeneğiniz `yield return` yöntemi veya özgün yöntemi içinde birden çok yöntem ayırarak, bazı kullanarak `return`ve bazı kullanarak `yield return`.</span><span class="sxs-lookup"><span data-stu-id="15b58-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="15b58-147">Biraz kullanılacak son yöntemi değiştirebilirsiniz `yield return` her yerde:</span><span class="sxs-lookup"><span data-stu-id="15b58-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="15b58-148">Bazen, bir yineleyici yöntem içinde iki farklı yöntemle bölmek için doğru yanıtı olabilir.</span><span class="sxs-lookup"><span data-stu-id="15b58-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="15b58-149">Kullanan bir `return`ve kullandığı ikinci `yield return`.</span><span class="sxs-lookup"><span data-stu-id="15b58-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="15b58-150">Boş bir koleksiyon ya da bir Boole bağımsız değişkenine göre ilk 5 tek sayıları döndürmek için isteyebileceğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="15b58-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="15b58-151">Bu iki yöntem, yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15b58-151">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="15b58-152">Yöntemleri yukarıdaki arayın.</span><span class="sxs-lookup"><span data-stu-id="15b58-152">Look at the methods above.</span></span> <span data-ttu-id="15b58-153">İlk standardını kullanan `return` deyimini boş bir koleksiyon ya da ikinci yöntemi tarafından oluşturulan bir yineleyici döndürür.</span><span class="sxs-lookup"><span data-stu-id="15b58-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="15b58-154">İkinci yöntem kullanan `yield return` istenen dizisi oluşturmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="15b58-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="15b58-155">Derinlemesine `foreach`</span><span class="sxs-lookup"><span data-stu-id="15b58-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="15b58-156">`foreach` Deyimi kullanan standart bir deyim genişler `IEnumerable<T>` ve `IEnumerator<T>` bir koleksiyonun tüm öğeler arasında yineleme yapmak için gereken arabirimler.</span><span class="sxs-lookup"><span data-stu-id="15b58-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="15b58-157">Ayrıca geliştiricilerin kaynaklar düzgün şekilde yöneterek olun hataları en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="15b58-157">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="15b58-158">Derleyici çevirir `foreach` bu yapı için benzer bir şeyi ilk örnekte gösterilen döngü:</span><span class="sxs-lookup"><span data-stu-id="15b58-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="15b58-159">Yukarıdaki yapısı tarafından oluşturulan kodu temsil eden C# derleyici itibaren sürüm 5 ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="15b58-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="15b58-160">Sürüm 5, önce `item` değişkeni farklı bir kapsam sahipti:</span><span class="sxs-lookup"><span data-stu-id="15b58-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="15b58-161">İnce ve sabit lambda ifadeleri içeren hataları tanılamak eski davranışa neden olabileceğinden değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="15b58-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="15b58-162">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="15b58-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="15b58-163">Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve burada nesne tarafından döndürülen durum işleme `GetEnumerator()` uygulayan `IDisposable` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="15b58-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="15b58-164">Bu gibi daha fazla kod tam genişletmeyle oluşturur:</span><span class="sxs-lookup"><span data-stu-id="15b58-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="15b58-165">İçinde Numaralandırıcı, şekilde türünün özelliklerine bağlıdır `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="15b58-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="15b58-166">Genel durumda `finally` yan tümcesini genişletir:</span><span class="sxs-lookup"><span data-stu-id="15b58-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="15b58-167">Ancak, varsa türünü `enumerator` mühürlenmiş bir tür olduğu ve hiç örtük dönüştürme türünden `enumerator` için `IDisposable`, `finally` yan tümcesi için boş bir blok genişletir:</span><span class="sxs-lookup"><span data-stu-id="15b58-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="15b58-168">Örtük bir dönüştürme türü olup olmadığını `enumerator` için `IDisposable`, ve `enumerator` bir NULL olmayan değer türü `finally` yan tümcesini genişletir:</span><span class="sxs-lookup"><span data-stu-id="15b58-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="15b58-169">Ne bu ayrıntıları unutmayın gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="15b58-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="15b58-170">`foreach` Deyimi sizin için söz konusu farklılıklarına işler.</span><span class="sxs-lookup"><span data-stu-id="15b58-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="15b58-171">Derleyici herhangi birini bu yapıları için doğru kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15b58-171">The compiler will generate the correct code for any of these constructs.</span></span> 


