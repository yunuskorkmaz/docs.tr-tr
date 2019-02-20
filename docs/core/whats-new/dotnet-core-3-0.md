---
title: .NET Core 3. 0'yenilikler nelerdir?
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 47a5ae3e81b0320a094ecc79e6b08035de66e785
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56443081"
---
# <a name="whats-new-in-net-core-30-preview-2"></a><span data-ttu-id="c8ac5-103">.NET Core 3.0 (Önizleme 2) yenilikler</span><span class="sxs-lookup"><span data-stu-id="c8ac5-103">What's new in .NET Core 3.0 (Preview 2)</span></span>

<span data-ttu-id="c8ac5-104">Bu makalede, .NET Core 3.0 (Önizleme 2) Yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-104">This article describes what is new in .NET Core 3.0 (preview 2).</span></span> <span data-ttu-id="c8ac5-105">Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="c8ac5-106">Windows Masaüstü adlı bir .NET Core 3.0 SDK'sı bileşeni yararlanarak, Windows Presentation Foundation (WPF) uygulamaları ve Windows Forms bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-106">By utilizing a .NET Core 3.0 SDK component called Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="c8ac5-107">Gerekirse Windows Masaüstü bileşen yalnızca desteklenen ve Windows üzerinde dahil.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="c8ac5-108">Daha fazla bilgi için konudaki [Windows Masaüstü](#windows-desktop) aşağıda.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="c8ac5-109">.NET core 3.0 için destek ekler C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="c8ac5-110">[İndirin ve .NET Core 3.0 Önizleme 2 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-110">[Download and get started with .NET Core 3.0 Preview 2](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="c8ac5-111">Yayın içinde tüm ayrıntılarını görebilirsiniz [.NET Core 3.0 Preview 2 sürüm notları](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-111">You can see complete details of the release in the [.NET Core 3.0 Preview 2 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="c8ac5-112">Her sürümü ile yayımlanmış olan hakkında daha fazla bilgi için aşağıdaki duyuruları bakın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-112">For more information about what was released with each version, see the following announcements:</span></span>

- [<span data-ttu-id="c8ac5-113">.NET core 3.0 Önizleme 1 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="c8ac5-113">.NET Core 3.0 Preview 1 announcement</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [<span data-ttu-id="c8ac5-114">.NET core 3.0 Önizleme 2 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="c8ac5-114">.NET Core 3.0 Preview 2 announcement</span></span>](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/)

## <a name="c-8"></a><span data-ttu-id="c8ac5-115">C# 8</span><span class="sxs-lookup"><span data-stu-id="c8ac5-115">C# 8</span></span>

<span data-ttu-id="c8ac5-116">.NET core 3.0 destekleyen C# 8 ve .NET Core 3.0 Önizleme 2'den itibaren bu yeni özellikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-116">.NET Core 3.0 supports C# 8, and as of .NET Core 3.0 Preview 2, supports these new features.</span></span> <span data-ttu-id="c8ac5-117">Hakkında daha fazla bilgi için C# 8.0 özellikler, aşağıdaki blog gönderilerine bakın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-117">For more information about C# 8.0 features, see the following blog posts:</span></span>

- [<span data-ttu-id="c8ac5-118">Desenler ile daha fazlasını yapın C# 8.0</span><span class="sxs-lookup"><span data-stu-id="c8ac5-118">Do more with patterns in C# 8.0</span></span>](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/)
- [<span data-ttu-id="c8ac5-119">Ele C# 8.0 bir döngü için</span><span class="sxs-lookup"><span data-stu-id="c8ac5-119">Take C# 8.0 for a spin</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/12/05/take-c-8-0-for-a-spin/)
- [<span data-ttu-id="c8ac5-120">Building C# 8.0</span><span class="sxs-lookup"><span data-stu-id="c8ac5-120">Building C# 8.0</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/)


### <a name="ranges-and-indices"></a><span data-ttu-id="c8ac5-121">Aralıkları ve dizinler</span><span class="sxs-lookup"><span data-stu-id="c8ac5-121">Ranges and indices</span></span>

<span data-ttu-id="c8ac5-122">Yeni `Index` türü, dizin oluşturma işlemi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-122">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="c8ac5-123">Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-123">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="c8ac5-124">Ayrıca bir `Range` oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-124">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="c8ac5-125">Ardından ile dizinleyebilirsiniz bir `Range` dilim oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-125">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a><span data-ttu-id="c8ac5-126">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="c8ac5-126">Async streams</span></span>

<span data-ttu-id="c8ac5-127">`IAsyncEnumerable<T>` Türüdür, yeni bir zaman uyumsuz sürümü `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-127">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="c8ac5-128">Dil sayesinde `await foreach` üzerinden `IAsyncEnumerable<T>` öğeleri kullanma ve `yield return` öğeleri oluşturmak için onlara.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-128">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="c8ac5-129">Aşağıdaki örnek, hem üretim hem de zaman uyumsuz akışlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-129">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="c8ac5-130">`foreach` Deyimi, async ve kendisini kullanan `yield return` arayanlar için zaman uyumsuz bir akış oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-130">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="c8ac5-131">Bu düzen (kullanarak `yield return`) zaman uyumsuz akışlar oluşturmayı için önerilen modelidir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-131">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="c8ac5-132">İmkanına yanı sıra `await foreach`, zaman uyumsuz yineleyiciler, örneğin, döndüren bir yineleyicinin oluşturabilirsiniz bir `IAsyncEnumerable/IAsyncEnumerator` her ikisini yapabilirsiniz `await` ve `yield` içinde.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-132">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="c8ac5-133">Çıkarılması gereken nesneler için kullanabileceğiniz `IAsyncDisposable`, çeşitli BCL türleri uygulayan, gibi `Stream` ve `Timer`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-133">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

>[!NOTE]
><span data-ttu-id="c8ac5-134">Visual Studio 2019 Önizleme 2 veya en son önizlemesi ile geliştirmek istiyorsanız, zaman uyumsuz akışlar kullanmak için .NET Core 3.0 Önizleme 2 ihtiyacınız [ C# Visual Studio Code uzantısı](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-134">You need .NET Core 3.0 Preview 2 to use async streams if you want to develop with either Visual Studio 2019 Preview 2 or the latest preview of the [C# extension for Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span></span> <span data-ttu-id="c8ac5-135">Komut satırından .NET Core 3.0 Önizleme 2 kullanıyorsanız, daha sonra her şeyin beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-135">If you are using .NET Core 3.0 Preview 2 at the command line, then everything will work as expected.</span></span>

### <a name="using-declarations"></a><span data-ttu-id="c8ac5-136">Bildirimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="c8ac5-136">Using Declarations</span></span>

<span data-ttu-id="c8ac5-137">*Bildirimi kullanarak* nesnenizin emin olmak için yeni bir yolunu düzgün bir şekilde elden olan.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-137">*Using declarations* are a new way to ensure your object is properly disposed.</span></span> <span data-ttu-id="c8ac5-138">A *using bildirimi* kapsamda devam ederken nesne etkin tutar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-138">A *using declaration* keeps the object alive while it is still in scope.</span></span> <span data-ttu-id="c8ac5-139">Nesne kapsam dışına sunulduktan sonra otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-139">Once the object becomes out of scope, it is automatically disposed.</span></span> <span data-ttu-id="c8ac5-140">Bu iç içe geçmiş azaltır *using deyimlerini* ve kodunuzu daha temiz yapın.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-140">This will reduce nested *using statements* and make your code cleaner.</span></span>

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a><span data-ttu-id="c8ac5-141">Anahtar ifadeler</span><span class="sxs-lookup"><span data-stu-id="c8ac5-141">Switch Expressions</span></span>

<span data-ttu-id="c8ac5-142">*Anahtar ifadeleri* daha net bir şekilde yöntemlerinden biri olan bir *geçiş deyimi* olduğundan bir ifade, ancak bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-142">*Switch expressions* are a cleaner way of doing a *switch statement* but, since it's an expression, returns a value.</span></span> <span data-ttu-id="c8ac5-143">*Anahtar ifadeler* desen eşleştirme ile de tamamen tümleşiktir ve atma deseni kullanın `_`temsil etmek için `default` değeri.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-143">*Switch expressions* are also fully integrated with pattern matching, and use the discard pattern, `_`, to represent the `default` value.</span></span>

<span data-ttu-id="c8ac5-144">Sözdizimi gördüğünüz *anahtar ifadeleri* aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-144">You can see the syntax for *switch expressions* in the following example:</span></span>

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

<span data-ttu-id="c8ac5-145">Bu örnekte yürütme sırasında iki deseni vardır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-145">There are two patterns at play in this example.</span></span> <span data-ttu-id="c8ac5-146">`o` ilk ile eşleşen `Point` *türü deseni* ve ardından *özelliği desenini* içinde *{kaşlı ayraçlar}*.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-146">`o` first matches with the `Point` *type pattern* and then with the *property pattern* inside the *{curly braces}*.</span></span> <span data-ttu-id="c8ac5-147">`_` Açıklar `discard pattern`, aynı olduğu `default` için *switch ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-147">The `_` describes the `discard pattern`, which is the same as `default` for *switch statements*.</span></span>

<span data-ttu-id="c8ac5-148">Desenleri yakalar amacınızla testleri için uygulayan yordam kodu yerine bildirim temelli bir kod yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-148">Patterns enable you to write declarative code that captures your intent instead of procedural code that implements tests for it.</span></span> <span data-ttu-id="c8ac5-149">Derleyici bence Bu yordam kodu uygulamak için sorumlu olur ve doğru şekilde her zaman yapmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-149">The compiler becomes responsible for implementing that boring procedural code and is guaranteed to always do it correctly.</span></span>

<span data-ttu-id="c8ac5-150">Hala olacaktır burada *switch ifadeleri* daha iyi bir seçim olacaktır *anahtar ifadeleri* ve desenleri, her iki sözdizimi stilleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-150">There will still be cases where *switch statements* will be a better choice than *switch expressions* and patterns can be used with both syntax styles.</span></span>

<span data-ttu-id="c8ac5-151">Daha fazla bilgi için [desenleri ile daha fazlasını yapın C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-151">For more information, see [Do more with patterns in C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="c8ac5-152">IEEE kayan nokta geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c8ac5-152">IEEE Floating-point improvements</span></span>

<span data-ttu-id="c8ac5-153">Kayan nokta API'leri olan uymak için güncelleştirilme sürecindedir [IEEE 754-2008 düzeltme](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-153">Floating point APIs are in the process of being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="c8ac5-154">Bu değişikliklerin amacı, davranışsal IEEE belirtimi ile uyumlu olduklarından emin olun ve tüm "required" işlemlerinin açığa sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-154">The goal of these changes is to expose all "required" operations and ensure that they are behaviorally compliant with the IEEE spec.</span></span>

<span data-ttu-id="c8ac5-155">Ayrıştırma ve biçimlendirme düzeltmeleri:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-155">Parsing and formatting fixes:</span></span>

* <span data-ttu-id="c8ac5-156">Doğru ayrıştırma ve herhangi bir uzunluktaki girişleri yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-156">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="c8ac5-157">Doğru ayrıştırma ve negatif sıfır biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-157">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="c8ac5-158">Büyük küçük harf duyarsız bir denetimi gerçekleştirmek ve isteğe bağlı bir önceki vererek sonsuzluk ve NaN düzgün ayrıştırılamadı `+` uygunsa.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-158">Correctly parse Infinity and NaN by performing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="c8ac5-159">Yeni matematik API'ye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-159">New Math APIs have:</span></span>

* `BitIncrement/BitDecrement`\
<span data-ttu-id="c8ac5-160">Karşılık gelen `nextUp` ve `nextDown` IEEE operations.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-160">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="c8ac5-161">Karşılaştıran en küçük kayan noktalı sayı (sırasıyla) giriş'den küçük veya büyük döndürürler.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-161">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="c8ac5-162">Örneğin, `Math.BitIncrement(0.0)` döndürecekti `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-162">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* `MaxMagnitude/MinMagnitude`\
<span data-ttu-id="c8ac5-163">Karşılık gelen `maxNumMag` ve `minNumMag` IEEE işlemleri, bunlar döndürür (sırasıyla) büyük ya da büyüklük açısından iki girişe daha düşük olan değer.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-163">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="c8ac5-164">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecekti `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-164">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* `ILogB`\
<span data-ttu-id="c8ac5-165">Karşılık gelen `logB` bir tamsayı değeri döndüren IEEE işlemi giriş parametresinin tamsayı 2 tabanında günlük döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-165">Corresponds to the `logB` IEEE operation which returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="c8ac5-166">Bu etkili bir şekilde aynıdır `floor(log2(x))`, ancak en az yuvarlama hatası işler bitti.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-166">This is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* `ScaleB`\
<span data-ttu-id="c8ac5-167">Karşılık gelen `scaleB` bir tamsayı değeri alan IEEE işlemi döndürür etkili bir şekilde `x * pow(2, n)`, yuvarlama en az bir hata ile tamamlandı ancak.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-167">Corresponds to the `scaleB` IEEE operation which takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* `Log2`\
<span data-ttu-id="c8ac5-168">Karşılık gelen `log2` IEEE işlemi 2 tabanlı logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-168">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="c8ac5-169">Yuvarlama hata en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-169">It minimizes rounding error.</span></span>

* `FusedMultiplyAdd`\
<span data-ttu-id="c8ac5-170">Karşılık gelen `fma` IEEE işlem gerçekleştirdiği bir çarpım Çarp.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-170">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="c8ac5-171">Diğer bir deyişle, mevcut `(x * y) + z` tek bir işlem olarak, var-tarafından yuvarlama hata en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-171">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="c8ac5-172">Örnek verilebilir `FusedMultiplyAdd(1e308, 2.0, -1e308)` döndüren `1e308`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-172">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="c8ac5-173">Normal `(1e308 * 2.0) - 1e308` döndürür `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-173">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* `CopySign`\
<span data-ttu-id="c8ac5-174">Karşılık gelen `copySign` IEEE işlemi değerini döndürür `x`, ancak işaretini `y`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-174">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="c8ac5-175">.NET platform bağımlı iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="c8ac5-175">.NET Platform Dependent Intrinsics</span></span>

<span data-ttu-id="c8ac5-176">Gibi belirli performans odaklı CPU yönergeleri için erişime izin API'ler eklenmiştir **SIMD** veya **Bit işleme yönerge** ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-176">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="c8ac5-177">Bu yönergeler, verileri verimli bir şekilde paralel işleme gibi bazı senaryolarda büyük performans geliştirmeleri elde etmeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-177">These instructions can help achieve big performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> <span data-ttu-id="c8ac5-178">Kullanılacak API'ler programlarınızın gösterme ek olarak, performansı artırmak için bu yönergeleri kullanarak .NET kitaplıklarına başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-178">In addition to exposing the APIs for your programs to use, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="c8ac5-179">Aşağıdaki CoreCLR Pr'ler birkaç uygulama veya kullanımı aracılığıyla iç bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-179">The following CoreCLR PRs demonstrate a few of the intrinsics, either via implementation or use:</span></span>

* [<span data-ttu-id="c8ac5-180">Basit SSE2 donanım iç uygulama</span><span class="sxs-lookup"><span data-stu-id="c8ac5-180">Implement simple SSE2 hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15585)
* [<span data-ttu-id="c8ac5-181">SSE donanım iç uygulama</span><span class="sxs-lookup"><span data-stu-id="c8ac5-181">Implement the SSE hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15538)
* [<span data-ttu-id="c8ac5-182">Arm64 temel donanım iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="c8ac5-182">Arm64 Base HW Intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/16822)
* [<span data-ttu-id="c8ac5-183">Bul için TZCNT ve LZCNT kullanma {ilk | En son} bulunamadı {bayt | Char}</span><span class="sxs-lookup"><span data-stu-id="c8ac5-183">Use TZCNT and LZCNT for Locate{First|Last}Found{Byte|Char}</span></span>](https://github.com/dotnet/coreclr/pull/21073)

<span data-ttu-id="c8ac5-184">Daha fazla bilgi için [.NET platformu bağımlı yapı içleri](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), Microsoft, yonga satıcılar veya tüm diğer şirket veya tek yongası/tanımlamak bu donanım altyapısını tanımlamak için bir yaklaşım tanımlar .NET kodu için sunulan API'ler.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-184">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), which defines an approach for defining this hardware infrastructure, allowing Microsoft, chip vendors, or any other company or individual to define hardware/chip APIs that should be exposed to .NET code.</span></span>

## <a name="default-executables"></a><span data-ttu-id="c8ac5-185">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="c8ac5-185">Default executables</span></span>

<span data-ttu-id="c8ac5-186">.NET core artık derler [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-186">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="c8ac5-187">.NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-187">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="c8ac5-188">Şimdiye kadar yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-188">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="c8ac5-189">Sırasında `dotnet build` veya `dotnet publish`, kullanmakta olduğunuz SDK platform ve ortam ile eşleşen sağlanan yürütülebilir bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-189">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="c8ac5-190">Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-190">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="c8ac5-191">Yürütülebilir dosya üzerine çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-191">You can double-click on the executable.</span></span>
* <span data-ttu-id="c8ac5-192">Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-192">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="c8ac5-193">Derleme bağımlılıkları kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-193">Build copies dependencies</span></span>

<span data-ttu-id="c8ac5-194">`dotnet build` artık uygulamanız için NuGet bağımlılıklarını NuGet önbellekten yapı çıktı klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-194">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="c8ac5-195">Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-195">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="c8ac5-196">Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-196">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="c8ac5-197">Yerel dotnet araçları</span><span class="sxs-lookup"><span data-stu-id="c8ac5-197">Local dotnet tools</span></span>

>[!WARNING]
><span data-ttu-id="c8ac5-198">.NET Core 3.0 Önizleme 2 ile .NET Core 3.0 Önizleme 1 ila yerel .NET Core Araçları'nda bir değişiklik yoktu.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-198">There was a change in .NET Core Local Tools between .NET Core 3.0 Preview 1 and .NET Core 3.0 Preview 2.</span></span>  <span data-ttu-id="c8ac5-199">Yerel araçları Preview 1'çıkış gibi bir komut çalıştırarak çalıştığınız varsa `dotnet tool restore` veya `dotnet tool install`, yerel araçları Önizleme 2'de doğru çalışmadan önce yerel Araçlar önbellek klasörünü silin gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-199">If you tried out local tools in Preview 1 by running a command like `dotnet tool restore` or `dotnet tool install`, you need to delete your local tools cache folder before local tools will work correctly in Preview 2.</span></span> <span data-ttu-id="c8ac5-200">Bu klasör şu konumdadır:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-200">This folder is located at:</span></span>
>
><span data-ttu-id="c8ac5-201">Mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="c8ac5-201">On mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
><span data-ttu-id="c8ac5-202">Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="c8ac5-202">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>
>
><span data-ttu-id="c8ac5-203">Bu klasör silmezseniz, hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-203">If you do not delete this folder, you will receive an error.</span></span>

<span data-ttu-id="c8ac5-204">.NET Core 2.1 genel araçları destekleniyorsa, .NET Core 3.0 artık yerel araçlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-204">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="c8ac5-205">Yerel Araçlar genel araçları benzerdir, ancak disk üzerindeki belirli bir konum ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-205">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="c8ac5-206">Bu, proje başına ve havuz başına araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-206">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="c8ac5-207">Yerel olarak yüklü herhangi bir aracı genel olarak kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-207">Any tool installed locally isn't available globally.</span></span> <span data-ttu-id="c8ac5-208">Araçlar NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-208">Tools are distributed as NuGet packages.</span></span>

<span data-ttu-id="c8ac5-209">Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-209">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="c8ac5-210">Bu bildirim dosyası, bu klasörü ve altındaki kullanılabilir olması için Araçlar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-210">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="c8ac5-211">Bu bildirim dosyası, depo kökünde oluşturarak, herkesin kodunuzu kopyalama geri yükleyebilir ve başarıyla kodunuzla çalışmak için gereken araçları kullanmanız emin olun.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-211">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="c8ac5-212">Oluşturmak için bir `dotnet-tools.json` bildirim dosyası, kullanın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-212">To create a `dotnet-tools.json` manifest file, use:</span></span>

```console
dotnet new tool-manifest
```

<span data-ttu-id="c8ac5-213">Yeni bir aracı ile yerel bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-213">Add a new tool to the local manifest with:</span></span>

```console
dotnet tool install <packageId>
```

<span data-ttu-id="c8ac5-214">Ayrıca, yerel bildirimi ile araçları listeleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-214">You can also list the tools in the local manifest with:</span></span>

```console
dotnet tool list
```

<span data-ttu-id="c8ac5-215">Genel olarak hangi araçları yüklü olduğunu görmek için bu seçeneği kullanın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-215">To see what tools are installed globally, use:</span></span>

```console
dotnet tool list -g
```

<span data-ttu-id="c8ac5-216">Yerel Araçlar bildirim, dosya kullanılabilir, ancak bildiriminde tanımlanan araçları yüklü değil, otomatik olarak indirip bu araçları yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-216">When the local tools manifest file is available, but the tools defined in the manifest have not been installed, use the following command to automatically download and install those tools:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="c8ac5-217">Yerel bir aracı ile aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-217">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="c8ac5-218">Dotnet, yerel aracı çalıştırdığınızda, bir bildirim geçerli dizin yapısını arar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-218">When a local tool is run, dotnet searches for a manifest up the current directory structure.</span></span> <span data-ttu-id="c8ac5-219">Bir aracı bildirim dosyası bulunduğunda, için istenen aracı aranır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-219">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="c8ac5-220">Aracı bildirimi, ancak önbellek bulunursa, kullanıcı hata alır ve çalıştırmaya gerek duymadığı `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-220">If the tool is found in the manifest, but not the cache, the user receives an error and needs to run `dotnet tool restore`.</span></span>

<span data-ttu-id="c8ac5-221">Bir aracı yerel aracı bildirim dosyasından kaldırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-221">To remove a tool from the local tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <packageId>
```

<span data-ttu-id="c8ac5-222">Aracı bildirim dosyasını elle düzenlemeye – izin vermek için deposuyla çalışmak için gerekli sürümü güncelleştirmek için bunu tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-222">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span> <span data-ttu-id="c8ac5-223">İşte bir örnek `dotnet-tools.json` dosyası:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-223">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="c8ac5-224">Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="c8ac5-225">Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="c8ac5-226">Bu genel olarak veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-226">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="c8ac5-227">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="c8ac5-227">Windows desktop</span></span>

<span data-ttu-id="c8ac5-228">.NET Core 3.0 Önizleme 1'den başlayarak, WPF ve Windows Forms kullanılarak Windows Masaüstü uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-228">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="c8ac5-229">Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-229">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="c8ac5-230">Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-230">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="c8ac5-231">Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-231">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="c8ac5-232">Visual Studio 2019 Önizleme 2 ekler **yeni proje** .NET Core 3.0, Windows Forms ve WPF şablonları.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-232">Visual Studio 2019 Preview 2 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span> <span data-ttu-id="c8ac5-233">Tasarımcılar henüz yine de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-233">Designers are still not yet supported.</span></span> <span data-ttu-id="c8ac5-234">Ve açmak, başlatmak ve Visual Studio 2019 bu projelerde hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-234">And you can open, launch, and debug these projects in Visual Studio 2019.</span></span>

<span data-ttu-id="c8ac5-235">Visual Studio 2017 15.9 yeteneği ekler [.NET Core önizlemelerini etkinleştir](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ancak bu özelliği etkinleştirmek gereken ve desteklenen bir senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-235">Visual Studio 2017 15.9 adds the ability to [enable .NET Core previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), but you need to turn that feature on, and it's not a supported scenario.</span></span>

<span data-ttu-id="c8ac5-236">Yeni Proje birkaç eklemelerle mevcut .NET Core projeleri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-236">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="c8ac5-237">Temel .NET Core konsol projesi ve temel bir Windows Forms ve WPF projesi bir karşılaştırması aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-237">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="c8ac5-238">Bir .NET Core konsol projesi kullandığından `Microsoft.NET.Sdk` SDK ve .NET Core 3.0 üzerinden üzerinde bir bağımlılık bildirir `netcoreapp3.0` hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-238">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="c8ac5-239">Bir Windows masaüstü uygulaması oluşturmak için kullanın `Microsoft.NET.Sdk.WindowsDesktop` SDK ve kullanmak için hangi UI çerçevesi seçin:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-239">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c8ac5-240">Windows Forms, WPF seçmek için ayarlanmış `UseWindowsForms` yerine `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-240">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c8ac5-241">Her ikisi de `UseWPF` ve `UseWindowsForms` ayarlanabilir `true` uygulama için bir Windows Forms iletişim kutusu, bir WPF denetimi barındırmayla örnek her iki çerçeveleri kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-241">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="c8ac5-242">Geri bildiriminizi Lütfen paylaşım [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) ve [dotnet/core](https://github.com/dotnet/core/issues) depolar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-242">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="msix-deployment-for-windows-desktop"></a><span data-ttu-id="c8ac5-243">Windows Masaüstü için MSIX dağıtım</span><span class="sxs-lookup"><span data-stu-id="c8ac5-243">MSIX Deployment for Windows Desktop</span></span>

<span data-ttu-id="c8ac5-244">[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimi.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-244">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows app package format.</span></span> <span data-ttu-id="c8ac5-245">.NET Core 3.0 Windows 10 Masaüstü uygulamaları dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-245">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="c8ac5-246">[Windows uygulaması paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), Visual Studio 2019 Preview 2 sürümündeki kullanılabilir MSIX paketlerle oluşturmanıza olanak tanır [müstakil](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-246">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019 Preview 2, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

><span data-ttu-id="c8ac5-247">Not: .NET Core proje dosyası içinde desteklenen çalışma zamanları belirtmelisiniz `<RuntimeIdentifiers>` özelliği:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-247">Note: The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a><span data-ttu-id="c8ac5-248">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-248">Fast built-in JSON support</span></span>

<span data-ttu-id="c8ac5-249">.NET ekosisteminin yararlandı [ **Json.NET** ](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-249">The .NET ecosystem has relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="c8ac5-250">**Json.NET** UTF-16 başlık altında olan kendi taban datatype .NET dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-250">**Json.NET** uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span>

<span data-ttu-id="c8ac5-251">Yeni yerleşik JSON desteği, yüksek performanslı, düşük ayırma ve temel `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-251">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="c8ac5-252">.NET Core 3.0 için yeni ana JSON ile ilgili üç eklenmiştir `System.Text.Json` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-252">Three new main JSON-related types have been added to .NET Core 3.0 the `System.Text.Json` namespace.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="c8ac5-253">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="c8ac5-253">Utf8JsonReader</span></span>

<span data-ttu-id="c8ac5-254">`System.Text.Json.Utf8JsonReader` yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-254">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="c8ac5-255">`Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey, türüdür.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-255">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="c8ac5-256">Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-256">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="c8ac5-257">JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-257">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="c8ac5-258">Bu yeni API'yi aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-258">This new API will include the following components:</span></span>

* <span data-ttu-id="c8ac5-259">Önizleme 1'de: JSON Okuyucu (sıralı erişim)</span><span class="sxs-lookup"><span data-stu-id="c8ac5-259">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="c8ac5-260">Sonraki yakında: JSON yazıcısı, DOM (rastgele erişim) poco serileştirici poco seri durumdan çıkarıcının</span><span class="sxs-lookup"><span data-stu-id="c8ac5-260">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="c8ac5-261">Temel bir okuyucu döngü için işte `Utf8JsonReader` başlangıç noktası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-261">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a><span data-ttu-id="c8ac5-262">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="c8ac5-262">Utf8JsonWriter</span></span>

<span data-ttu-id="c8ac5-263">`System.Text.Json.Utf8JsonWriter` bir yüksek performanslı, genel .NET türleri JSON metni yalnızca iletme UTF-8 olarak kodlanmış biçimde yazmak ister önbelleğe alınmamış, sağlar `String`, `Int32`, ve `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-263">`System.Text.Json.Utf8JsonWriter` provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="c8ac5-264">Okuyucu gibi özel seri hale getiricileri genişletme oluşturmak için kullanılan bir temel, alt düzey türü, yazardır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-264">Like the reader, the writer is a foundational, low-level type, that can be leveraged to build custom serializers.</span></span> <span data-ttu-id="c8ac5-265">Kullanarak yeni bir JSON yükünü yazmayı `Utf8JsonWriter` yazıcıdan kullanarak daha hızlı % 30-80'idir **Json.NET** ve ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-265">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and does not allocate.</span></span>

<span data-ttu-id="c8ac5-266">İşte bir örnek kullanımı `Utf8JsonWriter` başlangıç noktası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-266">Here is a sample usage of the `Utf8JsonWriter` that can be used as a starting point:</span></span>

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

<span data-ttu-id="c8ac5-267">`Utf8JsonWriter` Kabul `IBufferWriter<byte>` zaman uyumlu olarak json verilerini yazmak için çıkış konumunu ve çağıran olarak gibi somut bir uygulama sunmak amacıyla gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-267">The `Utf8JsonWriter` accepts `IBufferWriter<byte>` as the output location to synchronously write the json data into, and you as the caller need to provide a concrete implementation.</span></span> <span data-ttu-id="c8ac5-268">Platform şu anda bu arabirimi uygulaması içermez.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-268">The platform does not currently include an implementation of this interface.</span></span> <span data-ttu-id="c8ac5-269">Bir örneği `IBufferWriter<byte>`, bkz: [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span><span class="sxs-lookup"><span data-stu-id="c8ac5-269">For an example of `IBufferWriter<byte>`, see [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span></span>

### <a name="jsondocument"></a><span data-ttu-id="c8ac5-270">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="c8ac5-270">JsonDocument</span></span>

<span data-ttu-id="c8ac5-271">`System.Text.Json.JsonDocument` üst kısmındaki yerleşik `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-271">`System.Text.Json.JsonDocument` is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="c8ac5-272">`JsonDocument` JSON verilerini ayrıştırma ve bir salt okunur belge nesne modeli (DOM), derleme olanağı, rastgele erişim ve numaralandırma desteklemek için sorgulanabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-272">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="c8ac5-273">Verileri oluşturan JSON öğeleri aracılığıyla erişilebilir `JsonElement` tarafından sunulan tür `JsonDocument` adlı bir özellik olarak `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-273">The JSON elements that compose the data can be accessed via the `JsonElement` type which is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="c8ac5-274">`JsonElement` Ortak .NET türlerine JSON metnine dönüştürmek için API'leri ile birlikte JSON dizi ve nesne numaralandırıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-274">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="c8ac5-275">Tipik bir JSON yükü ayrıştırma ve tüm kullanarak üyelerine erişilmesi `JsonDocument` 2-3 x daha hızlı bir şekilde **Json.NET** çok az ayırmaları ile verileri (örneğin < 1 MB) makul bir şekilde boyutlandırılmış için.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-275">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with very little allocations for data that is reasonably sized (i.e. < 1 MB).</span></span>

<span data-ttu-id="c8ac5-276">İşte bir örnek kullanımı `JsonDocument` ve `JsonElement` başlangıç noktası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-276">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a><span data-ttu-id="c8ac5-277">Derleme Unloadability</span><span class="sxs-lookup"><span data-stu-id="c8ac5-277">Assembly Unloadability</span></span>

<span data-ttu-id="c8ac5-278">Derleme unloadability, yeni bir özellik olan `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-278">Assembly unloadability is a new capability of `AssemblyLoadContext`.</span></span> <span data-ttu-id="c8ac5-279">Bu yeni özellik, yalnızca birkaç yeni API'ler ile kullanıma sunulan bir API açısından büyük ölçüde saydamdır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-279">This new feature is largely transparent from an API perspective, exposed with just a few new APIs.</span></span> <span data-ttu-id="c8ac5-280">Bu, örneklenen türü statik alanları ve derlemenin kendisini tüm bellek serbest bırakma kaldırılacak bir yükleyici bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-280">It enables a loader context to be unloaded, releasing all memory for instantiated types, static fields and for the assembly itself.</span></span> <span data-ttu-id="c8ac5-281">Bir uygulama, yükleme ve bu mekanizma aracılığıyla derlemeler sonsuza kadar bir bellek sızıntısı almadan kaldırma başlatabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-281">An application should be able to load and unload assemblies via this mechanism forever without experiencing a memory leak.</span></span>

<span data-ttu-id="c8ac5-282">Bu yeni özellik, benzer senaryoları için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-282">This new capability can be used for scenarios similar to:</span></span>

* <span data-ttu-id="c8ac5-283">Yükleme ve kaldırma dinamik eklenti gerekli olduğu senaryolar eklentisi.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-283">Plugin scenarios where dynamic plugin loading and unloading is required.</span></span> 
* <span data-ttu-id="c8ac5-284">Dinamik derleme, çalışan ve sonra kodu temizleme.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-284">Dynamically compiling, running and then flushing code.</span></span> <span data-ttu-id="c8ac5-285">Web siteleri, komut dosyası motorları, vb. için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-285">Useful for web sites, scripting engines, etc.</span></span>
* <span data-ttu-id="c8ac5-286">Derlemeler için iç denetim (gibi ReflectionOnlyLoad), ancak Yükleniyor [MetadataLoadContext](#type-metadataloadcontext) (Önizleme 1'de yayımlanan) daha iyi bir seçenek çoğu durumda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-286">Loading assemblies for introspection (like ReflectionOnlyLoad), although [MetadataLoadContext](#type-metadataloadcontext) (released in Preview 1) will be a better choice in many cases.</span></span>

<span data-ttu-id="c8ac5-287">Daha fazla bilgi için [kullanarak Unloadability](https://github.com/dotnet/coreclr/pull/22221) belge.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-287">For more information, see the [Using Unloadability](https://github.com/dotnet/coreclr/pull/22221) document.</span></span>

<span data-ttu-id="c8ac5-288">Derleme kaldırılması, yönetilen nesneleri bir yükleyici bağlamı dışında tüm başvurularını anladım ve yönetilen emin olmak için önemli dikkat gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-288">Assembly unloading requires significant care to ensure that all references to managed objects from outside a loader context are understood and managed.</span></span> <span data-ttu-id="c8ac5-289">Yükleyici bağlamı kaldırılacak istendiğinde herhangi bir dış başvuruları yükleyici bağlamı yalnızca kendisine tutarlı olmasını başvurulmayan verilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-289">When the loader context is requested to be unloaded, any outside references need to have been unreferenced so that the loader context is self-consistent only to itself.</span></span>

<span data-ttu-id="c8ac5-290">Derleme unloadability .NET Framework'teki uygulama, .NET Core ile desteklenmeyen etki alanları (uygulama etki alanları) tarafından sağlandı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-290">Assembly unloadability was provided in the .NET Framework by Application Domains (AppDomains), which are not supported with .NET Core.</span></span> <span data-ttu-id="c8ac5-291">Uygulama etki alanları, hem avantajları ve sınırlamaları yeni Bu modele kıyasla vardı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-291">AppDomains had both benefits and limitations compared to this new model.</span></span> <span data-ttu-id="c8ac5-292">Uygulama etki alanları için karşılaştırıldığında daha esnek ve yüksek performanslı olmasını bu yeni yükleyici model göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-292">Consider this new loader model to be more flexible and higher performant when compared to AppDomains.</span></span>

## <a name="windows-native-interop"></a><span data-ttu-id="c8ac5-293">Windows yerel birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-293">Windows Native Interop</span></span>

<span data-ttu-id="c8ac5-294">Windows formunda düz C API'leri, COM ve WinRT zengin bir yerel API sunar.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-294">Windows offers a rich native API, in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="c8ac5-295">.NET Core 1.0 sürümünden itibaren **P/Invoke** destek içerir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-295">Since .NET Core 1.0, **P/Invoke** has been supported.</span></span> <span data-ttu-id="c8ac5-296">Özelliği artık .NET Core 3.0 ile desteği **COM API işlemi** ve **etkinleştirme WinRT API'lar** eklendi.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-296">Now with .NET Core 3.0, support for the ability to **CoCreate COM APIs** and **Activate WinRT APIs** has been added.</span></span>

<span data-ttu-id="c8ac5-297">COM ile kullanma örneği gördüğünüz [Excel Demo kaynak kodu](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-297">You can see an example of using COM with the [Excel Demo source code](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>


## <a name="type-sequencereader"></a><span data-ttu-id="c8ac5-298">Tür: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="c8ac5-298">Type: SequenceReader</span></span>

<span data-ttu-id="c8ac5-299">.NET Core 3. 0'da, `System.Buffers.SequenceReader` Okuyucu için olarak kullanılabilecek eklendi `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-299">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="c8ac5-300">Hızlı, yüksek performanslı, böylece düşük ayırma çözümlenmesi `System.IO.Pipelines` birden çok yedekleme arabellekler çapraz veri.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-300">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="c8ac5-301">Aşağıdaki örnek bir girişi sonu `Sequence` geçerli içine `CR/LF` satırları ayrılmış:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-301">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="c8ac5-302">Tür: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="c8ac5-302">Type: MetadataLoadContext</span></span>

<span data-ttu-id="c8ac5-303">`MetadataLoadContext` Türü okuma derleme sağlayan eklenmiş yapanın uygulama etki alanı etkilemeden meta verileri.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-303">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="c8ac5-304">Derlemeleri farklı mimariler ve geçerli çalışma zamanı ortamı daha platformlar için oluşturulmuş derlemeler de dahil olmak üzere veriler olarak okunur.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-304">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="c8ac5-305">`MetadataLoadContext` ile çakışıyor <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, hangi, yalnızca .NET Framework içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-305">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="c8ac5-306">`MetdataLoadContext` kullanılabilir [System.Reflection.MetadataLoadContext paket](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-306">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="c8ac5-307">.NET Standard 2.0 bir pakettir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-307">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="c8ac5-308">`MetadataLoadContext` Benzer olan API'leri gösterir <xref:System.Runtime.Loader.AssemblyLoadContext> yazın, ancak bu türüne göre değil.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-308">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="c8ac5-309">Benzer şekilde <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` evreni yükleniyor yalıtılmış bir derlemenin içinden yükleme derlemelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-309">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="c8ac5-310">`MetdataLoadContext` API'leri dönüş <xref:System.Reflection.Assembly> bilinen yansıma API'leri kullanımını etkinleştirme nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-310">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="c8ac5-311">Yürütme API'leri gibi odaklı [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), izin verilmeyen ve InvalidOperationException oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-311">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="c8ac5-312">Aşağıdaki örnek, belirli bir arabirimi uygulayan bir derlemede somut tür bulmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-312">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="c8ac5-313">Senaryolar için `MetadataLoadContext` tasarım zamanı özellikleri, araçları, derleme zamanı ve çalışma zamanı açık'li veri olarak bir derleme kümesi inceleyin ve tüm dosya kilitleri olması gereken özellikleri ve İnceleme sonra serbest bırakılan bellek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-313">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="c8ac5-314">`MetadataLoadContext` Çözümleyici sınıfı geçirilen yapıcısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-314">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="c8ac5-315">Çözümleyici'nin iş yüklenmesidir bir `Assembly` verilen kendi `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-315">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="c8ac5-316">Özet çözümleyici sınıfı türetilen `MetadataAssemblyResolver` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-316">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="c8ac5-317">Yol tabanlı senaryoları için çözümleyici uygulaması ile sağlanan `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-317">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="c8ac5-318">[MetadataLoadContext testleri](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) birçok kullanım durumları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-318">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="c8ac5-319">[Derleme testleri](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) başlatmak için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-319">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="c8ac5-320">TLS 1.3 & Linux'ta OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="c8ac5-320">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="c8ac5-321">.NET core artık avantajlarından yararlanın [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-321">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="c8ac5-322">Her TLS 1,3 birden çok avantaj vardır [OpenSSL takım](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="c8ac5-322">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="c8ac5-323">Geliştirilmiş bağlantı süreleri nedeniyle bir azalma istemci ve sunucu arasında gerekli gidiş dönüş sayısı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-323">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="c8ac5-324">Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını ve daha fazla bağlantı el sıkışması şifrelenmesi nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-324">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="c8ac5-325">.NET core 3.0 Önizleme 1 yararlanarak özellikli **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** (ne olursa olsun bulunan en iyi, bir Linux sisteminde sürümüdür).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-325">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="c8ac5-326">Zaman **OpenSSL 1.1.1** olduğu SslStream ve HttpClient türleri kullanılabilir kullanacağı **TLS 1.3** kullanırken `SslProtocols.None` (sistem varsayılan protokol), istemci ve sunucu desteği varsayılarak**TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-326">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="c8ac5-327">.NET Core 3.0 Önizleme 1 Ubuntu 18.10 bağlanmak için aşağıdaki örnekte gösterilmiştir <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-327">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="c8ac5-328">Windows ve macOS henüz desteklemediği **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-328">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="c8ac5-329">.NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-329">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="c8ac5-330">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="c8ac5-330">Cryptography</span></span>

<span data-ttu-id="c8ac5-331">İçin destek eklenmiştir **AES GCM** ve **AES-CCM** aracılığıyla uygulanan şifrelemeleri, `System.Security.Cryptography.AesGcm` ve `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-331">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="c8ac5-332">Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption)ve .NET Core için eklenen ilk kimliği doğrulanmış şifreleme (AE) algoritmaları.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-332">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="c8ac5-333">Aşağıdaki kodu **AesGcm** şifrelemek ve rastgele verilerin şifresini çözmek için şifre.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-333">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="c8ac5-334">Kodu **AesCcm** (sınıf değişken adları farklı olacaktır yalnızca) neredeyse aynı görünür.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-334">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="c8ac5-335">Şifreleme anahtarı içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="c8ac5-335">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="c8ac5-336">.NET core 3.0 Önizleme 1 içeri ve dışarı aktarmayı asimetrik ortak ve özel anahtarlar standart biçimlerinden bir X.509 sertifikası kullanmak zorunda kalmadan destekler.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-336">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="c8ac5-337">Tüm anahtar türleri (RSA, DSA, ECDsa, ECDiffieHellman) desteği **X.509 SubjectPublicKeyInfo** biçimi için ortak anahtarları ve **PKCS #8 PrivateKeyInfo** ve **PKCS #8 EncryptedPrivateKeyInfo**  biçimleri özel anahtarlar için.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-337">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="c8ac5-338">RSA ayrıca destekler **PKCS #1 RSAPublicKey** ve **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-338">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="c8ac5-339">Tüm verme yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-339">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="c8ac5-340">Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-340">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="c8ac5-341">PKCS #8 dosya inceledi ile `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-341">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="c8ac5-342">PFX/PKCS #12 dosyaları inceledi ve ile yönetilebilir `System.Security.Cryptography.Pkcs.Pkcs12Info` ve `System.Security.Cryptography.Pkcs.Pkcs12Builder`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-342">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="c8ac5-343">Linux için çevirmek için SerialPort</span><span class="sxs-lookup"><span data-stu-id="c8ac5-343">SerialPort for Linux</span></span>

<span data-ttu-id="c8ac5-344">.NET core 3.0 destekler <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-344">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="c8ac5-345">Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows türü.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-345">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="c8ac5-346">Daha fazla BCL geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c8ac5-346">More BCL Improvements</span></span>

<span data-ttu-id="c8ac5-347">`Span<T>`, `Memory<T>`, Ve .NET Core 2.1 içinde tanıtılan ilgili türleri de .NET Core 3.0 için iyileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-347">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="c8ac5-348">Sık kullanılan işlemler gibi yapı span, dilimleme, ayrıştırma ve biçimlendirme artık daha iyi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-348">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="c8ac5-349">Ayrıca, türleri ister `String` anahtarlarla olarak kullanıldığında daha verimli hale getirmek için altında--kapak geliştirmeleri gördünüz `Dictionary<TKey, TValue>` ve diğer koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-349">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="c8ac5-350">Kod değişikliği olmadan bu iyileştirmeleri yararlanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-350">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="c8ac5-351">Aşağıdaki geliştirmeler de .NET Core 3 Önizleme 1'de yenidir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-351">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="c8ac5-352">HttpClient için yerleşik Brotli desteği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-352">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="c8ac5-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="c8ac5-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="c8ac5-354">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="c8ac5-354">Unsafe.Unbox</span></span>
* <span data-ttu-id="c8ac5-355">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="c8ac5-355">CancellationToken.Unregister</span></span>
* <span data-ttu-id="c8ac5-356">Karmaşık aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="c8ac5-356">Complex arithmetic operators</span></span>
* <span data-ttu-id="c8ac5-357">TCP için yuva API'leri Canlı</span><span class="sxs-lookup"><span data-stu-id="c8ac5-357">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="c8ac5-358">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="c8ac5-358">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="c8ac5-359">Ayrıştırma IPEndPoint</span><span class="sxs-lookup"><span data-stu-id="c8ac5-359">IPEndPoint parsing</span></span>
* <span data-ttu-id="c8ac5-360">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="c8ac5-360">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="c8ac5-361">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="c8ac5-361">Tiered compilation</span></span>

<span data-ttu-id="c8ac5-362">[Katmanlı derleme](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-362">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="c8ac5-363">Daha fazla Desenlerinizi başlangıçta hem de daha iyi performans almak ve aktarım hızını en üst düzeye çıkarmak için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlayan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-363">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="c8ac5-364">Bu özellik bir Tercihli özellik olarak eklenmiştir [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) ve varsayılan olarak etkinleştirildi [.NET Core 2.2 Önizleme 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-364">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="c8ac5-365">Daha sonra yeniden oturum .NET Core 2.2 sürüm geri çevirmek için döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-365">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="c8ac5-366">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-366">ARM64 Linux support</span></span>

<span data-ttu-id="c8ac5-367">Destek için Linux ARM64 için eklendi.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-367">Support has been added for ARM64 for Linux.</span></span> <span data-ttu-id="c8ac5-368">ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-368">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="c8ac5-369">Alpine, Debian ve Ubuntu [ARM64 için .NET Core için Docker görüntüleri kullanılabilir](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-369">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="c8ac5-370">Lütfen denetleyin [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-370">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="c8ac5-371">**ARM64** Windows Destek işlemi henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-371">**ARM64** Windows support isn't yet available.</span></span>

## <a name="install-net-core-30-previews-on-linux-with-snap"></a><span data-ttu-id="c8ac5-372">Ek ile Linux üzerinde .NET Core 3.0 önizlemeleri yükleme</span><span class="sxs-lookup"><span data-stu-id="c8ac5-372">Install .NET Core 3.0 Previews on Linux with Snap</span></span>

<span data-ttu-id="c8ac5-373">Ek, tercih edilen yoludur yükleyin ve .NET Core önizlemeler deneyin [ek destekleyen Linux dağıtımları](https://docs.snapcraft.io/installing-snapd/6735).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-373">Snap is the preferred way to install and try .NET Core previews on [Linux distributions that support Snap](https://docs.snapcraft.io/installing-snapd/6735).</span></span>

<span data-ttu-id="c8ac5-374">Sisteminizde ek yapılandırdıktan sonra yüklemek için aşağıdaki komutu çalıştırın [.NET Core SDK 3.0 Önizleme SDK'sı](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-374">After configuring Snap on your system, run the following command to install the [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk).</span></span>

```console
sudo snap install dotnet-sdk --beta --classic
```
 
<span data-ttu-id="c8ac5-375">Ek paket yüklü kullanarak .NET Core, varsayılan .NET Core komut olduğunda `dotnet-sdk.dotnet`tam olarak `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-375">When .NET Core in installed using the Snap package, the default .NET Core command is `dotnet-sdk.dotnet`, as opposed to just `dotnet`.</span></span> <span data-ttu-id="c8ac5-376">Namespaced komutun etkinleştirmiş olabilirsiniz genel olarak yüklenmiş bir .NET Core sürümle çakışmayacağı avantajdır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-376">The benefit of the namespaced command is that it will not conflict with a globally installed .NET Core version you may have.</span></span> <span data-ttu-id="c8ac5-377">Bu komut için diğer adlı olarak `dotnet` ile:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-377">This command can be aliased to `dotnet` with:</span></span>

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="c8ac5-378">Bazı dağıtımlarda, SSL sertifikası erişimi etkinleştirmek için ek bir adım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-378">Some distros require an additional step to enable access to the SSL certificate.</span></span> <span data-ttu-id="c8ac5-379">Bkz. bizim [Linux Kurulumu](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-379">See our [Linux Setup](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) for details.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="c8ac5-380">Raspberry Pi GPIO'yu desteği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-380">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="c8ac5-381">İki yeni paket için GPIO programlama için kullanabileceğiniz NuGet yayımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-381">Two new packages have been released to NuGet that you can use for GPIO programming.</span></span>

* [<span data-ttu-id="c8ac5-382">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="c8ac5-382">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [<span data-ttu-id="c8ac5-383">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="c8ac5-383">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

<span data-ttu-id="c8ac5-384">Bir GPIO'yu paketleri GPIO, SPI, I2C ve PWM cihazlar için APIleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-384">The GPIO Packages includes APIs for GPIO, SPI, I2C and PWM devices.</span></span> <span data-ttu-id="c8ac5-385">IOT bağlamaları paketi içerir [cihaz bağlamaları](https://github.com/dotnet/iot/blob/master/src/devices/README.md) çeşitli yongaları ve algılayıcılar, aynı anda [dotnet/IOT-src/cihazlar](https://github.com/dotnet/iot/tree/master/src/devices).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-385">The IoT bindings package includes [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) for various chips and sensors, the same ones available at [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span></span>

<span data-ttu-id="c8ac5-386">Güncelleştirilmiş seri bağlantı noktası .NET Core 3.0 Preview 1 kapsamında duyurulan API'leri bu paketlerin bir parçası değildir ancak mevcut .NET Core platformu bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-386">The updated serial port APIs that were announced as part of .NET Core 3.0 Preview 1 are not part of these packages but are available as part of the .NET Core platform.</span></span>


## <a name="platform-support"></a><span data-ttu-id="c8ac5-387">Platform Desteği</span><span class="sxs-lookup"><span data-stu-id="c8ac5-387">Platform Support</span></span>

<span data-ttu-id="c8ac5-388">.NET core 3 aşağıdaki işletim sistemlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-388">.NET Core 3 will be supported on the following operating systems:</span></span>

* <span data-ttu-id="c8ac5-389">Windows İstemcisi: 7, 8.1, 10 (1607+)</span><span class="sxs-lookup"><span data-stu-id="c8ac5-389">Windows Client: 7, 8.1, 10 (1607+)</span></span>
* <span data-ttu-id="c8ac5-390">Windows Server için: 2012 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-390">Windows Server: 2012 R2 SP1+</span></span>
* <span data-ttu-id="c8ac5-391">macOS: 10.12+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-391">macOS: 10.12+</span></span>
* <span data-ttu-id="c8ac5-392">RHEL: 6+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-392">RHEL: 6+</span></span>
* <span data-ttu-id="c8ac5-393">Fedora: 26+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-393">Fedora: 26+</span></span>
* <span data-ttu-id="c8ac5-394">Ubuntu: 16.04+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-394">Ubuntu: 16.04+</span></span>
* <span data-ttu-id="c8ac5-395">Debian: 9+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-395">Debian: 9+</span></span>
* <span data-ttu-id="c8ac5-396">SLES: 12+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-396">SLES: 12+</span></span>
* <span data-ttu-id="c8ac5-397">openSUSE: 42.3+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-397">openSUSE: 42.3+</span></span>
* <span data-ttu-id="c8ac5-398">Alpine: 3.8+</span><span class="sxs-lookup"><span data-stu-id="c8ac5-398">Alpine: 3.8+</span></span>

<span data-ttu-id="c8ac5-399">Yonga desteği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c8ac5-399">Chip support follows:</span></span>

* <span data-ttu-id="c8ac5-400">Windows, macOS ve Linux'ta x64</span><span class="sxs-lookup"><span data-stu-id="c8ac5-400">x64 on Windows, macOS, and Linux</span></span>
* <span data-ttu-id="c8ac5-401">Windows üzerinde x86</span><span class="sxs-lookup"><span data-stu-id="c8ac5-401">x86 on Windows</span></span>
* <span data-ttu-id="c8ac5-402">Windows ve Linux'ta ARM32</span><span class="sxs-lookup"><span data-stu-id="c8ac5-402">ARM32 on Windows and Linux</span></span>
* <span data-ttu-id="c8ac5-403">Linux üzerinde ARM64</span><span class="sxs-lookup"><span data-stu-id="c8ac5-403">ARM64 on Linux</span></span>

<span data-ttu-id="c8ac5-404">Linux için ARM32 Debian 9 + ve Ubuntu 16.04 + desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-404">For Linux, ARM32 is supported on Debian 9+ and Ubuntu 16.04+.</span></span> <span data-ttu-id="c8ac5-405">ARM64 için bunu ARM32 Alpine 3.8 eklenmesi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-405">For ARM64, it is the same as ARM32 with the addition of Alpine 3.8.</span></span> <span data-ttu-id="c8ac5-406">Bunlar X64 için desteklenmediğinden bu distro'lara aynı sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-406">These are the same versions of those distros as is supported for X64.</span></span>

<span data-ttu-id="c8ac5-407">.NET Core 3.0 için docker görüntüleri kullanılabilir [microsoft/dotnet Docker hub'da](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c8ac5-407">Docker images for .NET Core 3.0 are available at [microsoft/dotnet on Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="c8ac5-408">Microsoft şu anda kullandığı sürecinde [Microsoft kapsayıcı kayıt defteri (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) ve son .NET Core 3.0 görüntüleri için MCR yalnızca yayımlanacak beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8ac5-408">Microsoft is currently in the process of adopting [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) and it is expected that the final .NET Core 3.0 images will only be published to MCR.</span></span>
