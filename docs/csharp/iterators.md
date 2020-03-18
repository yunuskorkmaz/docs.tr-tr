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
# <a name="iterators"></a><span data-ttu-id="fe943-103">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="fe943-103">Iterators</span></span>

<span data-ttu-id="fe943-104">Yazdığınız hemen hemen her program bir koleksiyon üzerinde tekrarlamak için bazı ihtiyaç olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fe943-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="fe943-105">Koleksiyondaki her öğeyi inceleyen kod yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="fe943-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="fe943-106">Ayrıca, bu sınıfın öğeleri için bir yineleyici üreten yöntemler olan yineleme yöntemleri de oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="fe943-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="fe943-107">Bunlar şunlar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fe943-107">These can be used for:</span></span>

+ <span data-ttu-id="fe943-108">Koleksiyondaki her öğe üzerinde eylem gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="fe943-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="fe943-109">Özel bir koleksiyonu niçin oyalama.</span><span class="sxs-lookup"><span data-stu-id="fe943-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="fe943-110">[LINQ](linq/index.md) veya diğer kitaplıkları genişletme.</span><span class="sxs-lookup"><span data-stu-id="fe943-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="fe943-111">Veri yineleme yöntemleri ile verimli bir şekilde aktığı bir veri ardışık alanı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fe943-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="fe943-112">C# dili, bu senaryoların her ikisi için de özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe943-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="fe943-113">Bu makalede, bu özelliklere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe943-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="fe943-114">Bu öğreticinin birden çok adımı vardır.</span><span class="sxs-lookup"><span data-stu-id="fe943-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="fe943-115">Her adımdan sonra, uygulamayı çalıştırabilir ve ilerlemeyi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe943-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="fe943-116">Ayrıca, bu konu [için tamamlanan örneği görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/blob/master/csharp/iterators)</span><span class="sxs-lookup"><span data-stu-id="fe943-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="fe943-117">İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="fe943-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="fe943-118">Her biri ile iterating</span><span class="sxs-lookup"><span data-stu-id="fe943-118">Iterating with foreach</span></span>

<span data-ttu-id="fe943-119">Bir koleksiyonu niçin oyalama `foreach` basittir: Anahtar kelime, koleksiyondaki her öğe için katıştırılmış deyimi bir kez çalıştırarak bir koleksiyonu nitreler:</span><span class="sxs-lookup"><span data-stu-id="fe943-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="fe943-120">İşte bu kadar kolay.</span><span class="sxs-lookup"><span data-stu-id="fe943-120">That's all there is to it.</span></span> <span data-ttu-id="fe943-121">Bir koleksiyonun tüm içeriğini tekrarlamak için `foreach` tek ihtiyacınız olan ifadedir.</span><span class="sxs-lookup"><span data-stu-id="fe943-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="fe943-122">İfade `foreach` sihirli değil ama.</span><span class="sxs-lookup"><span data-stu-id="fe943-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="fe943-123">Bir koleksiyonu yeniden sıralamak için gerekli kodu oluşturmak için .NET çekirdek kitaplığında tanımlanan `IEnumerable<T>` `IEnumerator<T>`iki genel arabirime dayanır: ve.</span><span class="sxs-lookup"><span data-stu-id="fe943-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="fe943-124">Bu mekanizma aşağıda daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe943-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="fe943-125">Bu arabirimlerin her ikisi de genel `IEnumerable` olmayan `IEnumerator`muadilleri vardır: ve .</span><span class="sxs-lookup"><span data-stu-id="fe943-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="fe943-126">[Genel](programming-guide/generics/index.md) sürümler modern kod için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fe943-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="fe943-127">Yineleme yöntemleri ile numaralandırma kaynakları</span><span class="sxs-lookup"><span data-stu-id="fe943-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="fe943-128">C# dilinin bir diğer büyük özelliği, numaralandırma için kaynak oluşturan yöntemler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe943-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="fe943-129">Bunlara *yineleyici yöntemleri*denir.</span><span class="sxs-lookup"><span data-stu-id="fe943-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="fe943-130">Yineleyici yöntemi, istendiğinde nesnelerin sırayla nasıl oluşturulabildiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe943-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="fe943-131">Bir yineleyici yöntemitanımlamak için `yield return` bağlamsal anahtar kelimeleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fe943-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="fe943-132">0'dan 9'a kadar tamsayı dizisini oluşturmak için bu yöntemi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe943-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="fe943-133">Yukarıdaki kod, `yield return` bir yineleyici yönteminde birden çok ayrı `yield return` deyim kullanabildiğinizgerçeğini vurgulamak için farklı ifadeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe943-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="fe943-134">Bir yineleyici yönteminin kodunu basitleştirmek için diğer dil yapılarını kullanabilirsiniz (ve genellikle yapabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="fe943-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="fe943-135">Aşağıdaki yöntem tanımı, sayıların tam olarak aynı sırasını üretir:</span><span class="sxs-lookup"><span data-stu-id="fe943-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="fe943-136">Birini ya da diğerini karar vermek zorunda değilsin.</span><span class="sxs-lookup"><span data-stu-id="fe943-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="fe943-137">Yönteminizin gereksinimlerini `yield return` karşılamak için gerektiği kadar ifadeniz olabilir:</span><span class="sxs-lookup"><span data-stu-id="fe943-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="fe943-138">Bu temel sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="fe943-138">That's the basic syntax.</span></span> <span data-ttu-id="fe943-139">Bir yineleme yöntemi yazacağınız gerçek bir örnek düşünelim.</span><span class="sxs-lookup"><span data-stu-id="fe943-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="fe943-140">Bir IoT projesinde olduğunuzu ve cihaz sensörlerinin çok büyük bir veri akışı oluşturduğunuzu düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe943-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="fe943-141">Verileri görmek için her Nth veri öğesini örnekleyen bir yöntem yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe943-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="fe943-142">Bu küçük yineleyici yöntemi hile yapar:</span><span class="sxs-lookup"><span data-stu-id="fe943-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="fe943-143">Yineleyici yöntemleri üzerinde önemli bir kısıtlama vardır: aynı yöntemde hem bir `return` deyim hem de ifade `yield return` olamaz.</span><span class="sxs-lookup"><span data-stu-id="fe943-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="fe943-144">Aşağıdakiderlemeolmaz:</span><span class="sxs-lookup"><span data-stu-id="fe943-144">The following will not compile:</span></span>

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

<span data-ttu-id="fe943-145">Bu kısıtlama normalde bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="fe943-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="fe943-146">Ya yöntem boyunca kullanarak `yield return` bir seçim var, ya da birden çok yöntem, bazı `return` `yield return`kullanarak orijinal yöntem e bölme , ve bazı kullanarak .</span><span class="sxs-lookup"><span data-stu-id="fe943-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="fe943-147">Her yerde kullanmak `yield return` için son yöntemi biraz değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe943-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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

<span data-ttu-id="fe943-148">Bazen doğru cevap, bir yineleyici yöntemini iki farklı yönteme bölmektir.</span><span class="sxs-lookup"><span data-stu-id="fe943-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="fe943-149">Bir kullanır `return`, ve kullanan `yield return`bir saniye .</span><span class="sxs-lookup"><span data-stu-id="fe943-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="fe943-150">Boş bir koleksiyonu veya boolean bağımsız değişkenini temel alan ilk 5 tek sayıyı döndürmek isteyebileceğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe943-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="fe943-151">Bunu şu iki yöntem olarak yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe943-151">You could write that as these two methods:</span></span>

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

<span data-ttu-id="fe943-152">Yukarıdaki yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="fe943-152">Look at the methods above.</span></span> <span data-ttu-id="fe943-153">İlki, boş `return` bir koleksiyonu veya ikinci yöntem tarafından oluşturulan yineleyiciyi döndürmek için standart deyimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe943-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="fe943-154">İkinci yöntem, `yield return` istenen sırayı oluşturmak için deyimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe943-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="fe943-155">Içine Deeper Dalış`foreach`</span><span class="sxs-lookup"><span data-stu-id="fe943-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="fe943-156">Deyim, `foreach` koleksiyonun tüm öğeleriarasında yinelemek `IEnumerable<T>` `IEnumerator<T>` için ve arabirimleri kullanan standart bir deyim olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="fe943-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="fe943-157">Ayrıca, geliştiricilerin kaynakları düzgün yönetmeyerek yaptıkları hataları en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="fe943-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="fe943-158">Derleyici, ilk `foreach` örnekte gösterilen döngüyü bu yapıya benzer bir şeye çevirir:</span><span class="sxs-lookup"><span data-stu-id="fe943-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="fe943-159">Yukarıdaki yapı, C# derleyicisi tarafından sürüm 5 ve üzeri olarak oluşturulan kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe943-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="fe943-160">Sürüm 5'ten `item` önce değişkenin farklı bir kapsamı vardı:</span><span class="sxs-lookup"><span data-stu-id="fe943-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="fe943-161">Bu, önceki davranış ince ve zor lambda ifadeleri içeren hataları teşhis yol açabilir, çünkü değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fe943-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="fe943-162">Lambda ifadeleri hakkında daha fazla bilgi için [Lambda ifadeleri'ne](./programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fe943-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="fe943-163">Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve nesnenin `GetEnumerator()` `IDisposable` arabirimi uyguladığı durumları işler.</span><span class="sxs-lookup"><span data-stu-id="fe943-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="fe943-164">Tam genişletme daha fazla bu gibi kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="fe943-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="fe943-165">Enumeratörün atılma şekli, türünün özelliklerine `enumerator`bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fe943-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="fe943-166">Genel durumda, `finally` yan tümce aşağıdakilere genişletir:</span><span class="sxs-lookup"><span data-stu-id="fe943-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="fe943-167">Ancak, `enumerator` türü mühürlü bir tür ise ve türünden `enumerator` örtülü bir `IDisposable`dönüştürme `finally` yoksa , yan tümce boş bir bloya genişletir:</span><span class="sxs-lookup"><span data-stu-id="fe943-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="fe943-168">Türünden `enumerator` `IDisposable`() `enumerator` ve nullable olmayan bir değer türünden örtülü bir `finally` dönüştürme varsa, yan tümce aşağıdakilere genişletilir:</span><span class="sxs-lookup"><span data-stu-id="fe943-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="fe943-169">Neyse ki, tüm bu ayrıntıları hatırlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe943-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="fe943-170">`foreach` İfade sizin için tüm bu nüansları ele.</span><span class="sxs-lookup"><span data-stu-id="fe943-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="fe943-171">Derleyici, bu yapılardan herhangi biri için doğru kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe943-171">The compiler will generate the correct code for any of these constructs.</span></span>
