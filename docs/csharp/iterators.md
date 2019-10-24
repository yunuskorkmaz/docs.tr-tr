---
title: Yineleyiciler
description: Yerleşik C# yineleyiciler kullanmayı ve kendi özel Yineleyici yöntemlerinizi oluşturmayı öğrenin.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: c378ceb651eed7e7a3d8c738bd4b2b3cf7de2a0f
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773884"
---
# <a name="iterators"></a><span data-ttu-id="c42d4-103">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="c42d4-103">Iterators</span></span>

<span data-ttu-id="c42d4-104">Yazdığınız neredeyse her programın, bir koleksiyon üzerinde yineleme yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="c42d4-105">Bir koleksiyondaki her öğeyi inceleyen bir kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c42d4-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="c42d4-106">Ayrıca, bu sınıfın öğeleri için bir yineleyici üreten Yöntemler olan yineleyici yöntemleri de oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c42d4-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="c42d4-107">Bunlar için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-107">These can be used for:</span></span>

+ <span data-ttu-id="c42d4-108">Bir koleksiyondaki her öğe için bir eylem gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="c42d4-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="c42d4-109">Özel bir koleksiyon numaralandırılıyor.</span><span class="sxs-lookup"><span data-stu-id="c42d4-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="c42d4-110">[LINQ](linq/index.md) veya diğer kitaplıkları genişletme.</span><span class="sxs-lookup"><span data-stu-id="c42d4-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="c42d4-111">Yineleyici yöntemler aracılığıyla veri akışının etkin olduğu bir veri işlem hattı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c42d4-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="c42d4-112">C# Dil bu senaryolara yönelik özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c42d4-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="c42d4-113">Bu makale, bu özelliklere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c42d4-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="c42d4-114">Bu öğreticide birden çok adım vardır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="c42d4-115">Her adımdan sonra, uygulamayı çalıştırabilir ve ilerleme durumunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c42d4-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="c42d4-116">Ayrıca, bu konu için [Tamamlanan örneği görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/blob/master/csharp/iterators) .</span><span class="sxs-lookup"><span data-stu-id="c42d4-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="c42d4-117">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c42d4-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="c42d4-118">Foreach ile yineleme</span><span class="sxs-lookup"><span data-stu-id="c42d4-118">Iterating with foreach</span></span>

<span data-ttu-id="c42d4-119">Bir koleksiyonun numaralandırılması basittir: `foreach` anahtar sözcüğü bir koleksiyonu numaralandırır ve koleksiyondaki her öğe için katıştırılmış deyimin bir kez yürütülmesini ister:</span><span class="sxs-lookup"><span data-stu-id="c42d4-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="c42d4-120">Hepsi bu kadar çok.</span><span class="sxs-lookup"><span data-stu-id="c42d4-120">That's all there is to it.</span></span> <span data-ttu-id="c42d4-121">Bir koleksiyonun tüm içeriğini yinelemek için `foreach` deyimleri yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="c42d4-122">@No__t_0 deyimleri de Magic değildir, ancak.</span><span class="sxs-lookup"><span data-stu-id="c42d4-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="c42d4-123">Bir koleksiyonu yinelemek için gereken kodu oluşturmak üzere .NET Core kitaplığı 'nda tanımlanan iki genel arabirimi kullanır: `IEnumerable<T>` ve `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="c42d4-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="c42d4-124">Bu mekanizma aşağıda daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="c42d4-125">Bu arabirimlerin her ikisi de genel olmayan ortaklarınıza sahiptir: `IEnumerable` ve `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="c42d4-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="c42d4-126">[Genel](programming-guide/generics/index.md) sürümler modern kod için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="c42d4-127">Yineleyici yöntemleriyle listeleme kaynakları</span><span class="sxs-lookup"><span data-stu-id="c42d4-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="c42d4-128">Dilin harika bir özelliği, C# bir numaralandırma için kaynak oluşturan Yöntemler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c42d4-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="c42d4-129">Bunlar *Yineleyici Yöntemler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="c42d4-130">Yineleyici yöntemi, istek sırasında nesnelerin bir dizide nasıl oluşturulacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c42d4-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="c42d4-131">Bir yineleyici yöntemi tanımlamak için `yield return` bağlamsal anahtar sözcükleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c42d4-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="c42d4-132">0 ile 9 arasındaki tamsayıların sırasını oluşturmak için bu yöntemi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c42d4-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="c42d4-133">Yukarıdaki kodda, bir yineleyici yönteminde birden çok ayrık `yield return` deyimi kullanabileceğiniz olguyu vurgulamak için farklı `yield return` deyimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="c42d4-134">Bir yineleyici yönteminin kodunu basitleştirmek için diğer dil yapılarını kullanabilirsiniz (ve genellikle bunu yapabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="c42d4-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="c42d4-135">Aşağıdaki yöntem tanımı, tam olarak aynı sayı dizisini üretir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="c42d4-136">Bir veya başka bir karar vermeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c42d4-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="c42d4-137">Yönteminizin ihtiyaçlarını karşılamak için gereken sayıda `yield return` deyimlerine sahip olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c42d4-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="c42d4-138">Bu temel sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-138">That's the basic syntax.</span></span> <span data-ttu-id="c42d4-139">Bir yineleyici yöntemi yazacağınız gerçek bir dünya örneğini ele alalım.</span><span class="sxs-lookup"><span data-stu-id="c42d4-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="c42d4-140">IoT projesinde olduğunuzu ve cihaz sensörleri çok büyük bir veri akışı üretdiğinizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="c42d4-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="c42d4-141">Veriler hakkında fikir almak için, her n. veri öğesini örnek bir yöntem yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c42d4-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="c42d4-142">Bu küçük yineleyici yöntemi, Eli:</span><span class="sxs-lookup"><span data-stu-id="c42d4-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="c42d4-143">Yineleyici metotlarda önemli bir kısıtlama vardır: aynı yöntemde hem bir `return` deyimin hem de bir `yield return` deyiminiz olamaz.</span><span class="sxs-lookup"><span data-stu-id="c42d4-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="c42d4-144">Aşağıdakiler derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-144">The following will not compile:</span></span>

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

<span data-ttu-id="c42d4-145">Bu kısıtlama normalde bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="c42d4-146">Yöntemi boyunca `yield return` veya özgün yöntemi birden çok metoda ayırarak, bazı `return` ve `yield return` kullanarak bir seçiminiz vardır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="c42d4-147">Son yöntemi `yield return` her yerde kullanmak için biraz daha değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c42d4-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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

<span data-ttu-id="c42d4-148">Bazen doğru yanıt, bir yineleyici yöntemini iki farklı yönteme bölmek olur.</span><span class="sxs-lookup"><span data-stu-id="c42d4-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="c42d4-149">@No__t_0 ve `yield return` kullanan bir ikincisi.</span><span class="sxs-lookup"><span data-stu-id="c42d4-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="c42d4-150">Boole bağımsız değişkenine göre boş bir koleksiyon veya ilk 5 tek sayı döndürmek isteyebileceğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="c42d4-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="c42d4-151">Bu iki yöntem olarak yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c42d4-151">You could write that as these two methods:</span></span>

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

<span data-ttu-id="c42d4-152">Yukarıdaki yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="c42d4-152">Look at the methods above.</span></span> <span data-ttu-id="c42d4-153">İlki, boş bir koleksiyon ya da ikinci yöntem tarafından oluşturulan Yineleyici döndürmek için standart `return` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="c42d4-154">İkinci yöntem, istenen diziyi oluşturmak için `yield return` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="c42d4-155">@No__t_0 daha derin inceleyin</span><span class="sxs-lookup"><span data-stu-id="c42d4-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="c42d4-156">@No__t_0 deyimi, bir koleksiyonun tüm öğelerinde yinelemek için `IEnumerable<T>` ve `IEnumerator<T>` arabirimlerini kullanan standart bir deyim halinde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="c42d4-157">Ayrıca, geliştiricilerin kaynakları düzgün bir şekilde yönetmediğinden yaptığı hataları da en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="c42d4-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="c42d4-158">Derleyici, ilk örnekte gösterilen `foreach` döngüsünü bu yapı ile benzer bir şekilde çevirir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="c42d4-159">Yukarıdaki yapı, C# derleyicinin 5 ve üzeri sürümü itibariyle oluşturulan kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c42d4-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="c42d4-160">Sürüm 5 ' ten önce `item` değişken farklı bir kapsama sahipti:</span><span class="sxs-lookup"><span data-stu-id="c42d4-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="c42d4-161">Bu, önceki davranış lambda ifadeleri içeren hataların tanılanması için hafif ve zor bir yol olabileceğinden değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c42d4-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="c42d4-162">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c42d4-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="c42d4-163">Derleyici tarafından oluşturulan tam kod biraz daha karmaşıktır ve `GetEnumerator()` tarafından döndürülen nesnenin `IDisposable` arabirimini uyguladığı durumları işler.</span><span class="sxs-lookup"><span data-stu-id="c42d4-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="c42d4-164">Tam genişletme şu şekilde kod üretir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="c42d4-165">Numaralandırıcının elden çıkarılma şekli `enumerator` türünün özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="c42d4-166">Genel durumda `finally` yan tümcesi şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="c42d4-167">Ancak, `enumerator` türü korumalı bir tür ise ve `enumerator` türünden `IDisposable` öğesine örtük dönüştürme yoksa, `finally` yan tümcesi boş bir bloğa genişletilir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="c42d4-168">@No__t_0 türünden `IDisposable` örtük bir dönüştürme varsa ve `enumerator` null yapılamayan bir değer türü ise, `finally` yan tümcesi şu şekilde genişletilir:</span><span class="sxs-lookup"><span data-stu-id="c42d4-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="c42d4-169">Ktam, tüm bu ayrıntıları anımsamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c42d4-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="c42d4-170">@No__t_0 deyimleri sizin için tüm bu nusları işler.</span><span class="sxs-lookup"><span data-stu-id="c42d4-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="c42d4-171">Derleyici bu yapıların herhangi biri için doğru kodu oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="c42d4-171">The compiler will generate the correct code for any of these constructs.</span></span>
