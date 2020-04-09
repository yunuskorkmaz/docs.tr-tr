---
title: C# 8.0 -C# Guide'daki yenilikler
description: C# 8.0'da bulunan yeni özellikler hakkında genel bir bakış alın.
ms.date: 04/07/2020
ms.openlocfilehash: 1a005750751129969f2d1e9caf156330dbe61cb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989213"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="209d7-103">C# 8.0'daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="209d7-103">What's new in C# 8.0</span></span>

<span data-ttu-id="209d7-104">C# 8.0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="209d7-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="209d7-105">Yalnızca üyeler okunur</span><span class="sxs-lookup"><span data-stu-id="209d7-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="209d7-106">Varsayılan arabirim metotları</span><span class="sxs-lookup"><span data-stu-id="209d7-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="209d7-107">[Desen eşleştirme geliştirmeleri:](#more-patterns-in-more-places)</span><span class="sxs-lookup"><span data-stu-id="209d7-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="209d7-108">İfadeleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="209d7-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="209d7-109">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="209d7-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="209d7-110">Tuple desenleri</span><span class="sxs-lookup"><span data-stu-id="209d7-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="209d7-111">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="209d7-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="209d7-112">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="209d7-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="209d7-113">Statik yerel fonksiyonlar</span><span class="sxs-lookup"><span data-stu-id="209d7-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="209d7-114">Tek kullanımlık ref structs</span><span class="sxs-lookup"><span data-stu-id="209d7-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="209d7-115">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="209d7-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="209d7-116">Asenkron akarsular</span><span class="sxs-lookup"><span data-stu-id="209d7-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="209d7-117">Asynchronous tek kullanımlık</span><span class="sxs-lookup"><span data-stu-id="209d7-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- [<span data-ttu-id="209d7-118">Endeksler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="209d7-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="209d7-119">Null-coalescing atama</span><span class="sxs-lookup"><span data-stu-id="209d7-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="209d7-120">Yönetilmeyen yapılı türler</span><span class="sxs-lookup"><span data-stu-id="209d7-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="209d7-121">İç içe ifadelerde Stackalloc</span><span class="sxs-lookup"><span data-stu-id="209d7-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="209d7-122">Enterpolasyonlu harfi harfine dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="209d7-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="209d7-123">C# 8.0 **.NET Core 3.x** ve **.NET Standart 2.1**üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="209d7-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="209d7-124">Daha fazla bilgi için [C# dil sürümüne](../language-reference/configure-language-version.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="209d7-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="209d7-125">Bu makalenin geri kalanı kısaca bu özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="209d7-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="209d7-126">Ayrıntılı makalelerin mevcut olduğu yerlerde, bu öğreticilere bağlantılar ve genel bakışlar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="209d7-127">`dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="209d7-128">[dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="209d7-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="209d7-129">[Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.</span><span class="sxs-lookup"><span data-stu-id="209d7-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="209d7-130">*Deneme örnekleri* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="209d7-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="209d7-131">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="209d7-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="209d7-132">Yalnızca üyeler okunur</span><span class="sxs-lookup"><span data-stu-id="209d7-132">Readonly members</span></span>

<span data-ttu-id="209d7-133">`readonly` Değiştiriciyi bir yapının üyelerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="209d7-134">Üyenin durumu değiştirmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="209d7-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="209d7-135">`readonly` Değiştiriciyi bir `struct` bildirime uygulamaktan daha ayrıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="209d7-136">Aşağıdaki mutable struct düşünün:</span><span class="sxs-lookup"><span data-stu-id="209d7-136">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="209d7-137">Çoğu yapı da, `ToString()` yöntem durumu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="209d7-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="209d7-138">`readonly` Aşağıdakileri bildirgeye değiştirici ekleyerek şunları `ToString()`belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="209d7-139">Önceki değişiklik derleyici uyarısı oluşturur, `ToString` çünkü işaretlenmemiş `Distance` `readonly`olan özelliğe erişir:</span><span class="sxs-lookup"><span data-stu-id="209d7-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="209d7-140">Derleyici, savunma amaçlı bir kopya oluşturması gerektiğinde sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="209d7-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="209d7-141">Özellik `Distance` durumu değiştirmez, bu nedenle bildirime `readonly` değiştirici ekleyerek bu uyarıyı düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="209d7-142">Değiştiricinin `readonly` salt okunur bir özellik için gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="209d7-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="209d7-143">Derleyici, erişimedenlerin `get` durumu değiştirmediğini varsaymaz; açıkça bildirmelisiniz. `readonly`</span><span class="sxs-lookup"><span data-stu-id="209d7-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="209d7-144">Otomatik olarak uygulanan özellikler bir özel durumdur; derleyici tüm otomatik olarak uygulanan getters readonly olarak ele alacak, bu `readonly` nedenle burada ve `X` `Y` özellikleri değiştirici eklemek için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="209d7-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="209d7-145">Derleyici, `readonly` üyelerin durumu değiştirmediği kuralı nı uygular.</span><span class="sxs-lookup"><span data-stu-id="209d7-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="209d7-146">`readonly` Değiştiriciyi kaldırmadığınız sürece aşağıdaki yöntem derlenmez:</span><span class="sxs-lookup"><span data-stu-id="209d7-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="209d7-147">Bu özellik, derleyicinin bunu uygulayabilmesi ve bu amacla dayalı optimizasyonlar yapabilmesi için tasarım amacınızı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="209d7-148">Dil referans makalesinde yalnızca okumuş üyeler [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-148">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="209d7-149">Varsayılan arabirim metotları</span><span class="sxs-lookup"><span data-stu-id="209d7-149">Default interface methods</span></span>

<span data-ttu-id="209d7-150">Artık arabirimlere üye ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="209d7-151">Bu dil özelliği, API yazarlarının kaynak veya bu arabirimin varolan uygulamalarıyla ikili uyumluluk bozmadan sonraki sürümlerde bir arabirime yöntem eklemelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="209d7-152">Varolan uygulamalar varsayılan uygulamayı *devralır.*</span><span class="sxs-lookup"><span data-stu-id="209d7-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="209d7-153">Bu özellik aynı zamanda C#'ın benzer özellikleri destekleyen Android veya Swift'i hedefleyen API'lerle birlikte çalışmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="209d7-154">Varsayılan arabirim yöntemleri de bir "özellikler" dil özelliğine benzer senaryolar sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="209d7-155">Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="209d7-155">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="209d7-156">İlk öğreticimiz [varsayılan uygulamalarla bir arabirimi güncelleştirmeyi](../tutorials/default-interface-methods-versions.md)kapsar.</span><span class="sxs-lookup"><span data-stu-id="209d7-156">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="209d7-157">Diğer öğreticiler ve referans güncellemeleri genel sürüm için zamanında geliyor.</span><span class="sxs-lookup"><span data-stu-id="209d7-157">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="209d7-158">Daha fazla yerde daha fazla desen</span><span class="sxs-lookup"><span data-stu-id="209d7-158">More patterns in more places</span></span>

<span data-ttu-id="209d7-159">**Desen eşleştirme,** ilgili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamak için araçlar verir.</span><span class="sxs-lookup"><span data-stu-id="209d7-159">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="209d7-160">C# 7.0 [`is`](../language-reference/keywords/is.md) ifade ve [`switch`](../language-reference/keywords/switch.md) deyimi kullanarak tür desenleri ve sabit desenler için sözdizimi tanıttı.</span><span class="sxs-lookup"><span data-stu-id="209d7-160">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="209d7-161">Bu özellikler, veri ve işlevselliğin birbirinden ayrı yaşadığı programlama paradigmalarını desteklemeye yönelik ilk geçici adımları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="209d7-161">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="209d7-162">Endüstri daha fazla mikro hizmet ve diğer bulut tabanlı mimarilere doğru ilerlerken, diğer dil araçlarına ihtiyaç duyulur.</span><span class="sxs-lookup"><span data-stu-id="209d7-162">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="209d7-163">C# 8.0 bu kelime dağarcığını genişletir, böylece kodunuzda daha fazla yerde daha fazla desen ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-163">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="209d7-164">Verileriniz ve işlevleriniz ayrı olduğunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="209d7-164">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="209d7-165">Algoritmalarınız bir nesnenin çalışma zamanı türü nden başka bir gerçeğe bağlı olduğunda desen eşleştirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="209d7-165">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="209d7-166">Bu teknikler tasarımları ifade etmek için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-166">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="209d7-167">Yeni yerlerde yeni desenlerek, C # 8.0 **özyinelemeli desenler**ekler.</span><span class="sxs-lookup"><span data-stu-id="209d7-167">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="209d7-168">Herhangi bir desen ifadesinin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="209d7-168">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="209d7-169">Özyinelemeli desen, başka bir desen ifadesinin çıktısına uygulanan bir desen ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="209d7-169">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="209d7-170">İfadeleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="209d7-170">Switch expressions</span></span>

<span data-ttu-id="209d7-171">Genellikle, [`switch`](../language-reference/keywords/switch.md) bir deyim bloklarının `case` her birinde bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="209d7-171">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="209d7-172">**İfadeleri değiştirin,** daha kısa ifade sözdizimini kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-172">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="209d7-173">Daha az yinelenen `case` ve `break` anahtar kelimeler ve daha az kıvırcık parantez vardır.</span><span class="sxs-lookup"><span data-stu-id="209d7-173">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="209d7-174">Örnek olarak, gökkuşağının renklerini listeleyen aşağıdaki enum'u göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="209d7-174">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="209d7-175">Uygulamanız `RGBColor` `R`, ve `G` `B` bileşenlerinden oluşturulmuş bir tür tanımlıysa, bir anahtarı ifade içeren aşağıdaki yöntemi kullanarak bir `Rainbow` değeri RGB değerlerine dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-175">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="209d7-176">Burada çeşitli sözdizimi geliştirmeleri vardır:</span><span class="sxs-lookup"><span data-stu-id="209d7-176">There are several syntax improvements here:</span></span>

- <span data-ttu-id="209d7-177">Değişken anahtar kelimeden `switch` önce gelir.</span><span class="sxs-lookup"><span data-stu-id="209d7-177">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="209d7-178">Farklı sıra, anahtar ifadesini anahtar deyiminden ayırt etmeyi görsel olarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="209d7-178">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="209d7-179">Ve `case` `:` elemanları ile `=>`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="209d7-179">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="209d7-180">Daha kısa ve sezgisel.</span><span class="sxs-lookup"><span data-stu-id="209d7-180">It's more concise and intuitive.</span></span>
- <span data-ttu-id="209d7-181">Servis `default` talebi bir `_` atma ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="209d7-181">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="209d7-182">Cesetler ifadelerdir, ifadeler değil.</span><span class="sxs-lookup"><span data-stu-id="209d7-182">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="209d7-183">Klasik `switch` deyimi kullanarak eşdeğer kod ile kontrast:</span><span class="sxs-lookup"><span data-stu-id="209d7-183">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="209d7-184">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="209d7-184">Property patterns</span></span>

<span data-ttu-id="209d7-185">**Özellik deseni,** incelenen nesnenin özellikleriyle eşleşmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-185">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="209d7-186">Alıcının adresine göre satış vergisini hesaplaması gereken bir e-ticaret sitesi düşünün.</span><span class="sxs-lookup"><span data-stu-id="209d7-186">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="209d7-187">Bu hesaplama bir `Address` sınıfın temel sorumluluğu değildir.</span><span class="sxs-lookup"><span data-stu-id="209d7-187">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="209d7-188">Zaman içinde, büyük olasılıkla adres biçimi değişikliklerinden daha sık değişecektir.</span><span class="sxs-lookup"><span data-stu-id="209d7-188">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="209d7-189">Satış vergisi nin tutarı adresin özelliğine `State` bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-189">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="209d7-190">Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik deseni kullanır:</span><span class="sxs-lookup"><span data-stu-id="209d7-190">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="209d7-191">Desen eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-191">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="209d7-192">Tuple desenleri</span><span class="sxs-lookup"><span data-stu-id="209d7-192">Tuple patterns</span></span>

<span data-ttu-id="209d7-193">Bazı algoritmalar birden çok girişe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="209d7-194">**Tuple desenleri,** [tuple](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="209d7-195">Aşağıdaki kod oyun *kaya, kağıt, makas*için bir anahtar ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="209d7-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="209d7-196">İletiler kazananı gösterir.</span><span class="sxs-lookup"><span data-stu-id="209d7-196">The messages indicate the winner.</span></span> <span data-ttu-id="209d7-197">Atma örneği, bağlar veya diğer metin girişleri için üç birleşimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="209d7-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="209d7-198">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="209d7-198">Positional patterns</span></span>

<span data-ttu-id="209d7-199">Bazı türler, `Deconstruct` özelliklerini ayrı değişkenlere dönüştüren bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="209d7-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="209d7-200">Bir `Deconstruct` yönteme erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak için **konumsal desenlerk** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="209d7-201">Ayrı değişkenler `Point` oluşturmak `Deconstruct` için `X` bir yöntem içeren aşağıdaki `Y`sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="209d7-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="209d7-202">Ayrıca, bir çeyreğin çeşitli konumlarını temsil eden aşağıdaki enum düşünün:</span><span class="sxs-lookup"><span data-stu-id="209d7-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="209d7-203">Aşağıdaki yöntem ve değerlerini `x` ayıklamak için **konumsal desen** `y`kullanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="209d7-204">Daha sonra, `when` noktanın `Quadrant` belirlenmesi için bir yan tümce kullanır:</span><span class="sxs-lookup"><span data-stu-id="209d7-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="209d7-205">Önceki anahtardaki atma deseni, `x` 0 `y` olduğunda veya 0 olduğunda eşleşir, ancak her ikisi yle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="209d7-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="209d7-206">Bir anahtar ifadesi bir değer oluşturmalı veya bir özel durum atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="209d7-207">Servis taleplerini hiçbiri eşleşmiyorsa, anahtar ifadesi bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="209d7-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="209d7-208">Derleyici, anahtar ifadenizdeki olası tüm durumları kapsamazsanız, sizin için bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="209d7-209">Desen eşleştirme bu gelişmiş [öğretici](../tutorials/pattern-matching.md)desen eşleştirme teknikleri keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="209d7-210">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="209d7-210">Using declarations</span></span>

<span data-ttu-id="209d7-211">**Using declaration,** anahtar sözcüğün `using` önünde yer alan değişken bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="209d7-211">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="209d7-212">Derleyiciye, bildirilen değişkenin ilgili kapsamın sonunda atılması gerektiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="209d7-212">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="209d7-213">Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="209d7-213">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="209d7-214">Önceki örnekte, yöntemin kapanış ayracına ulaşıldığında dosya atılır.</span><span class="sxs-lookup"><span data-stu-id="209d7-214">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="209d7-215">Bu, beyan `file` edilen kapsamın sonudur.</span><span class="sxs-lookup"><span data-stu-id="209d7-215">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="209d7-216">Önceki kod klasik [kullanarak deyimi](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="209d7-216">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

<span data-ttu-id="209d7-217">Önceki örnekte, `using` deyimle ilişkili kapanış ayracına ulaşıldığında dosya atılır.</span><span class="sxs-lookup"><span data-stu-id="209d7-217">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="209d7-218">Her iki durumda da `Dispose()`derleyici.</span><span class="sxs-lookup"><span data-stu-id="209d7-218">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="209d7-219">`using` İfadedeki ifade tek kullanımlık değilse derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-219">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="209d7-220">Statik yerel fonksiyonlar</span><span class="sxs-lookup"><span data-stu-id="209d7-220">Static local functions</span></span>

<span data-ttu-id="209d7-221">Artık yerel işlevin ilgili kapsamdan herhangi bir değişkeni yakalamadığından (başvuru) olmadığından emin olmak için değiştiriciyi yerel işlevlere ekleyebilirsiniz. `static`</span><span class="sxs-lookup"><span data-stu-id="209d7-221">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="209d7-222">Bunu yapmak `CS8421`, "Statik yerel bir işlev değişken \<> bir başvuru içeremez" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-222">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="209d7-223">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="209d7-223">Consider the following code.</span></span> <span data-ttu-id="209d7-224">Yerel işlev, `LocalFunction` ekkapsamda `y`bildirilen değişkene (yöntem) `M`erişer.</span><span class="sxs-lookup"><span data-stu-id="209d7-224">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="209d7-225">Bu `LocalFunction` nedenle, `static` değiştirici ile ilan edilemez:</span><span class="sxs-lookup"><span data-stu-id="209d7-225">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="209d7-226">Aşağıdaki kod statik yerel bir işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="209d7-226">The following code contains a static local function.</span></span> <span data-ttu-id="209d7-227">Statik olabilir, çünkü ekkapsamdaki herhangi bir değişkene erişemez:</span><span class="sxs-lookup"><span data-stu-id="209d7-227">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="209d7-228">Tek kullanımlık ref structs</span><span class="sxs-lookup"><span data-stu-id="209d7-228">Disposable ref structs</span></span>

<span data-ttu-id="209d7-229">Değiştirici ile bildirilen bir `struct` arabirim uygulayamaz ve bu nedenle uygulayamaz. <xref:System.IDisposable> `ref`</span><span class="sxs-lookup"><span data-stu-id="209d7-229">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="209d7-230">Bu nedenle, `ref struct` bir bertaraf sağlamak için, erişilebilir `void Dispose()` bir yöntem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-230">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="209d7-231">Bu özellik bildirimler `readonly ref struct` için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="209d7-231">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="209d7-232">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="209d7-232">Nullable reference types</span></span>

<span data-ttu-id="209d7-233">Geçersiz bir ek açıklama bağlamı içinde, başvuru türünün herhangi bir değişkeni geçersiz bir **başvuru türü**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="209d7-233">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="209d7-234">Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni geçersiz bir `?` **başvuru türü**olarak bildirmek için tür adını eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-234">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="209d7-235">Nullable olmayan başvuru türleri için derleyici, yerel değişkenlerin beyan edildiğinde null olmayan bir değere başvurulmasını sağlamak için akış çözümlemesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-235">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="209d7-236">Alanlar inşaat sırasında başharfle alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-236">Fields must be initialized during construction.</span></span> <span data-ttu-id="209d7-237">Derleyici, değişken kullanılabilir yapıcılardan herhangi birini arayarak veya bir baş harfe çağırışla ayarlamıyorsa bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-237">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="209d7-238">Ayrıca, geçersiz başvuru türleri null olabilir bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="209d7-238">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="209d7-239">Nullable başvuru türleri, null'a atanmadıklarından veya başharfe atanmadıklarından emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="209d7-239">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="209d7-240">Ancak derleyici, nullable başvuru türündeki herhangi bir değişkenin null'a erişilmeden veya nullable olmayan bir başvuru türüne atanmadan önce null'a karşı denetlenmesini sağlamak için akış çözümlemesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="209d7-240">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="209d7-241">Nullable [başvuru türlerinin](../nullable-references.md)genel bakışında özellik hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-241">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="209d7-242">Bu [nullable referans türleri öğretici](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="209d7-242">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="209d7-243">Geçersiz [başvuru türleri öğretici kullanmak için bir uygulama geçirinde](../tutorials/upgrade-to-nullable-references.md)geçersiz başvuru türlerini kullanmak için varolan bir kod tabanını geçirme adımları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="209d7-243">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="209d7-244">Asenkron akarsular</span><span class="sxs-lookup"><span data-stu-id="209d7-244">Asynchronous streams</span></span>

<span data-ttu-id="209d7-245">C# 8.0 ile başlayarak, akışları eşit bir şekilde oluşturabilir ve tüketebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-245">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="209d7-246">Bir eşzamanlı akış döndüren bir yöntem üç özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="209d7-246">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="209d7-247">`async` Değiştirici ile ilan edildi.</span><span class="sxs-lookup"><span data-stu-id="209d7-247">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="209d7-248">Bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="209d7-248">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="209d7-249">Yöntem, `yield return` eşzamanlı akışta ardışık öğeleri döndürmek için ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="209d7-249">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="209d7-250">Asenkron akışı tüketmek, akışın öğelerini sayısala rken `await` anahtar kelimeden `foreach` önce anahtar kelimeeklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="209d7-250">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="209d7-251">Anahtar `await` kelimenin eklenmesi, değiştirici ile `async` bildirilecek ve bir `async` yöntem için izin verilen bir türü döndürmek için eşzamanlı akışı sayısala getiren bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="209d7-251">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="209d7-252">Genellikle bu bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="209d7-252">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="209d7-253">Ayrıca bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir .</span><span class="sxs-lookup"><span data-stu-id="209d7-253">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="209d7-254">Bir yöntem hem tüketebilir hem de bir eşzamanlı akış üretebilir, bu da bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="209d7-254">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="209d7-255">Aşağıdaki kod, her sayı oluşturma arasında 100 ms bekleyen 0'dan 19'a kadar bir sıra oluşturur:</span><span class="sxs-lookup"><span data-stu-id="209d7-255">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="209d7-256">`await foreach` İfadeyi kullanarak sırayı sıralarsınız:</span><span class="sxs-lookup"><span data-stu-id="209d7-256">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="209d7-257">Async [akışları oluşturma ve tüketme](../tutorials/generate-consume-asynchronous-stream.md)konusunda öğreticimizde asynchronous akışlarını kendiniz deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-257">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="209d7-258">Varsayılan olarak, akış öğeleri yakalanan bağlamında işlenir.</span><span class="sxs-lookup"><span data-stu-id="209d7-258">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="209d7-259">Bağlamın ele geçirilmesini devre dışı kılmış <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> olmak istiyorsanız, uzantı yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="209d7-259">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="209d7-260">Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi [için, Görev tabanlı eşzamanlı deseni tüketme makalesine](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="209d7-260">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="209d7-261">Asynchronous tek kullanımlık</span><span class="sxs-lookup"><span data-stu-id="209d7-261">Asynchronous disposable</span></span>

<span data-ttu-id="209d7-262">C# 8.0 ile başlayarak, dil <xref:System.IAsyncDisposable?displayProperty=nameWithType> arabirimi uygulayan tek kullanımlık türleri destekler.</span><span class="sxs-lookup"><span data-stu-id="209d7-262">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="209d7-263">Bir `using` ifadenin operand ya <xref:System.IDisposable> <xref:System.IAsyncDisposable>da uygulayabilirsiniz .</span><span class="sxs-lookup"><span data-stu-id="209d7-263">The operand of a `using` expression can implement either <xref:System.IDisposable> or <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="209d7-264">Durumunda `IAsyncDisposable`, derleyici `await` <xref:System.Threading.Tasks.Task> döndürülen <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-264">In the case of `IAsyncDisposable`, the compiler generates code to `await` the <xref:System.Threading.Tasks.Task> returned from <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="209d7-265">Daha fazla bilgi için [ `using` ifadeye](../language-reference/keywords/using-statement.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="209d7-265">For more information, see the [`using` statement](../language-reference/keywords/using-statement.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="209d7-266">Endeksler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="209d7-266">Indices and ranges</span></span>

<span data-ttu-id="209d7-267">Endeksler ve aralıklar, bir dizideki tek öğelere veya aralıklara erişmek için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="209d7-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="209d7-268">Bu dil desteği iki yeni türe ve iki yeni işleçe dayanır:</span><span class="sxs-lookup"><span data-stu-id="209d7-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="209d7-269"><xref:System.Index?displayProperty=nameWithType>diziye bir dizi içine bir dizi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="209d7-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="209d7-270">Bir dizin `^`dizinin dizinin sonuna göreolduğunu belirten son işleçten gelen dizin.</span><span class="sxs-lookup"><span data-stu-id="209d7-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="209d7-271"><xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="209d7-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="209d7-272">Aralık işleci, `..`bir aralığın başlangıcını ve sonunu operands olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="209d7-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="209d7-273">Dizinler için kurallarla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="209d7-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="209d7-274">Bir dizi `sequence`düşünün.</span><span class="sxs-lookup"><span data-stu-id="209d7-274">Consider an array `sequence`.</span></span> <span data-ttu-id="209d7-275">Dizin `0` `sequence[0]`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="209d7-276">Dizin `^0` `sequence[sequence.Length]`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="209d7-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="209d7-277">Bu `sequence[^0]` bir özel durum atmak `sequence[sequence.Length]` yok unutmayın, tıpkı yok.</span><span class="sxs-lookup"><span data-stu-id="209d7-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="209d7-278">Herhangi bir `n`sayı `^n` için dizin `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="209d7-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="209d7-279">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="209d7-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="209d7-280">Aralığın başlangıcı dahildir, ancak aralığın sonu özeldir, yani *başlangıç* aralıkta yer alan ancak *sonu* aralıkta yer almıyor.</span><span class="sxs-lookup"><span data-stu-id="209d7-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="209d7-281">Aralık, `[0..^0]` tüm aralığı `[0..sequence.Length]` temsil eder gibi tüm aralığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="209d7-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="209d7-282">Bazı örneklere bakalım.</span><span class="sxs-lookup"><span data-stu-id="209d7-282">Let's look at a few examples.</span></span> <span data-ttu-id="209d7-283">Başından ve sonundan itibaren diziniyle açıklamalı aşağıdaki diziyi düşünün:</span><span class="sxs-lookup"><span data-stu-id="209d7-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="209d7-284">`^1` Dizinile son sözcüğü alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="209d7-285">Aşağıdaki kod ,"hızlı", "kahverengi" ve "tilki" sözcükleri içeren bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="209d7-286">Bu `words[1]` aracılığıyla `words[3]`içerir.</span><span class="sxs-lookup"><span data-stu-id="209d7-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="209d7-287">Öğe `words[4]` aralıkta değil.</span><span class="sxs-lookup"><span data-stu-id="209d7-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="209d7-288">Aşağıdaki kod "tembel" ve "köpek" ile bir alt aralığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="209d7-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="209d7-289">Bu `words[^2]` içerir `words[^1]`ve .</span><span class="sxs-lookup"><span data-stu-id="209d7-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="209d7-290">Bitiş dizini `words[^0]` dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="209d7-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="209d7-291">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık uçlu aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="209d7-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="209d7-292">Aralıkları değişken olarak da bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="209d7-293">Aralık daha sonra `[` `]` ve karakterler içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="209d7-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="209d7-294">Yalnızca diziler endeksleri ve aralıkları desteklemekle kalmıyor.</span><span class="sxs-lookup"><span data-stu-id="209d7-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="209d7-295">Ayrıca [dize](../language-reference/builtin-types/reference-types.md#the-string-type)ile endeksleri ve aralıkları kullanabilirsiniz , <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="209d7-295">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="209d7-296">Daha fazla bilgi [için, endeksler ve aralıklar için Tür desteğine](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges)bakın.</span><span class="sxs-lookup"><span data-stu-id="209d7-296">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="209d7-297">Endeksler ve aralıklarla ilgili öğreticide [endeksler ve aralıklar](../tutorials/ranges-indexes.md)hakkında daha fazla şey keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="209d7-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="209d7-298">Null-coalescing atama</span><span class="sxs-lookup"><span data-stu-id="209d7-298">Null-coalescing assignment</span></span>

<span data-ttu-id="209d7-299">C# 8.0 null-coalescing atama `??=`işleci tanıttı.</span><span class="sxs-lookup"><span data-stu-id="209d7-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="209d7-300">İşleç, `??=` sağ el operand değerini sol operand'ına atamak için kullanabilirsiniz ve yalnızca sol `null`operand'ın .'a değer biçerek.</span><span class="sxs-lookup"><span data-stu-id="209d7-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="209d7-301">Daha fazla bilgi için, bkz [?? = işleçler](../language-reference/operators/null-coalescing-operator.md) makale.</span><span class="sxs-lookup"><span data-stu-id="209d7-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="209d7-302">Yönetilmeyen yapılı türler</span><span class="sxs-lookup"><span data-stu-id="209d7-302">Unmanaged constructed types</span></span>

<span data-ttu-id="209d7-303">C# 7.3 ve daha önce, yapılandırılan bir tür (en az bir tür bağımsız değişken içeren bir tür) [yönetilmeyen](../language-reference/builtin-types/unmanaged-types.md)bir tür olamaz.</span><span class="sxs-lookup"><span data-stu-id="209d7-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="209d7-304">C# 8.0 ile başlayarak, yalnızca yönetilmeyen türlerde alanlar içeriyorsa, yapılandırılan bir değer türü yönetilemez.</span><span class="sxs-lookup"><span data-stu-id="209d7-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="209d7-305">Örneğin, genel `Coords<T>` türün aşağıdaki tanımı göz önüne alındığında:</span><span class="sxs-lookup"><span data-stu-id="209d7-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="209d7-306">`Coords<int>` türü C# 8.0 ve sonraki yıllarda yönetilmeyen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="209d7-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="209d7-307">Herhangi bir yönetilmeyen tür için olduğu gibi, bu tür bir değişken için bir işaretçi oluşturabilir veya bu tür örnekleri için [yığınüzerinde bellek bloğu tahsis](../language-reference/operators/stackalloc.md) edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="209d7-308">Daha fazla bilgi için [yönetilmeyen türlere](../language-reference/builtin-types/unmanaged-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="209d7-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="209d7-309">İç içe ifadelerde Stackalloc</span><span class="sxs-lookup"><span data-stu-id="209d7-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="209d7-310">C# 8.0 ile başlayarak, [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin <xref:System.Span%601?displayProperty=nameWithType> sonucu <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> veya türündeise, diğer ifadelerdeki ifadeyi `stackalloc` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="209d7-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="209d7-311">Enterpolasyonlu harfi harfine dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="209d7-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="209d7-312">[Enterpolasyonlu](../language-reference/tokens/interpolated.md) `$@"..."` kelime dizeleri `@$"..."` `$` ve `@` belirteçleri sırası herhangi olabilir: her ikisi de ve geçerli interpolated verbatim dizeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="209d7-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="209d7-313">Önceki C# sürümlerinde `$` belirteç belirteçten `@` önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="209d7-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
