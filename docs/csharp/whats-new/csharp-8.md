---
title: C# 8,0 C# kılavuzundaki yenilikler
description: 8,0 ' de C# bulunan yeni özelliklere genel bakış alın.
ms.date: 09/20/2019
ms.openlocfilehash: 540b95beaf00c17812a3b602602504278be69b0e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429396"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="7b6eb-103">C# 8,0 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-103">What's new in C# 8.0</span></span>

<span data-ttu-id="7b6eb-104">C#8,0 aşağıdaki özellikleri ve geliştirmeleri C# dile ekler:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="7b6eb-105">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="7b6eb-106">Varsayılan arabirim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="7b6eb-107">[Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="7b6eb-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="7b6eb-108">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="7b6eb-109">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="7b6eb-110">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="7b6eb-111">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="7b6eb-112">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7b6eb-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="7b6eb-113">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="7b6eb-114">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="7b6eb-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="7b6eb-115">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="7b6eb-116">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="7b6eb-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="7b6eb-117">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="7b6eb-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="7b6eb-118">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="7b6eb-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="7b6eb-119">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="7b6eb-120">İç içe ifadelerde stackalloc</span><span class="sxs-lookup"><span data-stu-id="7b6eb-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="7b6eb-121">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="7b6eb-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="7b6eb-122">C#8,0, **.NET Core 3. x** ve **.NET Standard 2,1**' de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="7b6eb-123">Daha fazla bilgi için bkz [ C# . dil sürümü oluşturma](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="7b6eb-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="7b6eb-124">Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="7b6eb-125">Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="7b6eb-126">Ortamınızdaki bu özellikleri, `dotnet try` genel aracını kullanarak inceleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="7b6eb-127">[DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="7b6eb-128">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="7b6eb-129">*TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="7b6eb-130">`dotnet try`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="7b6eb-131">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-131">Readonly members</span></span>

<span data-ttu-id="7b6eb-132">`readonly` değiştiricisini bir yapının üyelerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-132">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="7b6eb-133">Üyenin durumu değiştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-133">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="7b6eb-134">`readonly` değiştiricisinin `struct` bildirimine uygulanmasıyla daha ayrıntılı bir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="7b6eb-135">Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-135">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="7b6eb-136">Çoğu yapı gibi `ToString()` yöntemi durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-136">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="7b6eb-137">`ToString()`bildirimine `readonly` değiştiricisini ekleyerek bunu belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="7b6eb-138">Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString`, `readonly`işaretlenmemiş `Distance` özelliğine erişir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="7b6eb-139">Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="7b6eb-140">`Distance` özelliği durumu değiştirmez, bu nedenle `readonly` değiştiricisini bildirime ekleyerek bu uyarıyı çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="7b6eb-141">`readonly` değiştiricinin salt okunurdur özelliğinde gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-141">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="7b6eb-142">Derleyici `get` erişimcilerinin durumu değiştirmediğini varsaymaz; `readonly` açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="7b6eb-143">Otomatik uygulanan özellikler bir özel durumdur; derleyici otomatik uygulanan tüm alıcıları ReadOnly olarak değerlendirir, bu nedenle `X` ve `Y` özelliklerine `readonly` değiştiricisini eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="7b6eb-144">Derleyici, `readonly` üyelerin durumu değiştirmiyor kuralını zorlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-144">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="7b6eb-145">`readonly` değiştiricisini kaldırmadığınız takdirde aşağıdaki yöntem derlenmez:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-145">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="7b6eb-146">Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-146">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="7b6eb-147">[`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)dil başvurusu makalesindeki salt okunur Üyeler hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="7b6eb-148">Varsayılan arabirim metotları</span><span class="sxs-lookup"><span data-stu-id="7b6eb-148">Default interface methods</span></span>

<span data-ttu-id="7b6eb-149">Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-149">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="7b6eb-150">Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-150">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="7b6eb-151">Mevcut uygulamalar varsayılan uygulamayı *devralınır* .</span><span class="sxs-lookup"><span data-stu-id="7b6eb-151">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="7b6eb-152">Bu özellik aynı zamanda C# , benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'Lerle birlikte çalışmaya de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-152">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="7b6eb-153">Varsayılan arabirim yöntemleri, "nitelikler" dil özelliğine benzer senaryolar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="7b6eb-154">Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-154">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="7b6eb-155">İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](../tutorials/default-interface-methods-versions.md)kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-155">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="7b6eb-156">Diğer öğreticiler ve başvuru güncelleştirmeleri genel sürüm için zaman içinde geliyor.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-156">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="7b6eb-157">Daha fazla yerde daha fazla desen</span><span class="sxs-lookup"><span data-stu-id="7b6eb-157">More patterns in more places</span></span>

<span data-ttu-id="7b6eb-158">**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="7b6eb-159">C#7,0 [`is`](../language-reference/keywords/is.md) ifade ve [`switch`](../language-reference/keywords/switch.md) deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunuldu.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="7b6eb-160">Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="7b6eb-161">Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="7b6eb-162">C#8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="7b6eb-163">Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="7b6eb-164">Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="7b6eb-165">Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="7b6eb-166">Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler**ekler.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="7b6eb-167">Herhangi bir model ifadesinin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-167">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="7b6eb-168">Özyinelemeli bir model, sadece başka bir model ifadesinin çıktısına uygulanan bir model ifadesi olur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-168">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="7b6eb-169">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-169">Switch expressions</span></span>

<span data-ttu-id="7b6eb-170">Genellikle [`switch`](../language-reference/keywords/switch.md) bir ifade, `case` bloklarının her birinde bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-170">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="7b6eb-171">**Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-171">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="7b6eb-172">Daha az sayıda yinelenen `case` ve `break` anahtar sözcüğü ve daha az küme ayraçları vardır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-172">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="7b6eb-173">Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-173">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="7b6eb-174">Uygulamanız `R`, `G` ve `B` bileşenlerinden oluşturulan bir `RGBColor` türü tanımlıysa, bir anahtar ifadesi içeren aşağıdaki yöntemi kullanarak bir `Rainbow` değerini RGB değerlerine dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-174">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="7b6eb-175">Burada birkaç sözdizimi geliştirmesi vardır:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-175">There are several syntax improvements here:</span></span>

- <span data-ttu-id="7b6eb-176">Değişkeni, `switch` anahtar sözcüğünden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-176">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="7b6eb-177">Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-177">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="7b6eb-178">`case` ve `:` öğeleri `=>`ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-178">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="7b6eb-179">Daha kısa ve sezgisel.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-179">It's more concise and intuitive.</span></span>
- <span data-ttu-id="7b6eb-180">`default` durum, `_` bir atma ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-180">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="7b6eb-181">Gövdeler deyimlerdir, deyimler değildir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-181">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="7b6eb-182">Klasik `switch` ifadesini kullanarak denk kodla kontrast:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-182">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="7b6eb-183">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-183">Property patterns</span></span>

<span data-ttu-id="7b6eb-184">**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="7b6eb-185">Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="7b6eb-186">Bu hesaplama, bir `Address` sınıfının temel sorumluluğu değildir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="7b6eb-187">Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="7b6eb-188">Satış vergisi miktarı, adresin `State` özelliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="7b6eb-189">Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="7b6eb-190">Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="7b6eb-191">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-191">Tuple patterns</span></span>

<span data-ttu-id="7b6eb-192">Bazı algoritmalar birden fazla girişe bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-192">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="7b6eb-193">**Demet desenleri** , [kayıt düzeni](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-193">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="7b6eb-194">Aşağıdaki kod, oyun *rock, Paper, makas*için bir switch ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-194">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="7b6eb-195">İletiler kazanan kişiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-195">The messages indicate the winner.</span></span> <span data-ttu-id="7b6eb-196">Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-196">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="7b6eb-197">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-197">Positional patterns</span></span>

<span data-ttu-id="7b6eb-198">Bazı türler, özelliklerini ayrık değişkenlere bağlayan bir `Deconstruct` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-198">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="7b6eb-199">`Deconstruct` yöntemi erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-199">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="7b6eb-200">`X` ve `Y`için ayrık değişkenler oluşturmak üzere bir `Deconstruct` yöntemi içeren aşağıdaki `Point` sınıfını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-200">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="7b6eb-201">Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-201">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="7b6eb-202">Aşağıdaki yöntem `x` ve `y`değerlerini ayıklamak için **konumsal model** kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-202">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="7b6eb-203">Sonra, noktanın `Quadrant` belirlenmesi için bir `when` yan tümcesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-203">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="7b6eb-204">Yukarıdaki anahtardaki atma deseninin `x` ya da `y` 0 olması ancak her ikisi birden olmaması durumunda eşleşir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-204">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="7b6eb-205">Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-205">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="7b6eb-206">Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-206">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="7b6eb-207">Anahtar ifadenizde olası tüm durumları kapsamıyorsanız, derleyici sizin için bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="7b6eb-208">Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-208">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="7b6eb-209">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7b6eb-209">Using declarations</span></span>

<span data-ttu-id="7b6eb-210">**Using bildirimi** , `using` anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-210">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="7b6eb-211">Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-211">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="7b6eb-212">Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-212">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="7b6eb-213">Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-213">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="7b6eb-214">`file` bildirildiği kapsamın sonu.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-214">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="7b6eb-215">Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-215">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="7b6eb-216">Yukarıdaki örnekte, `using` ifadesiyle ilişkilendirilen kapanış ayracı erişildiğinde dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-216">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="7b6eb-217">Her iki durumda da derleyici `Dispose()`çağrısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-217">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="7b6eb-218">`using` deyimindeki ifade atılabilir değilse derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="7b6eb-219">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-219">Static local functions</span></span>

<span data-ttu-id="7b6eb-220">Yerel işlevin kapsayan kapsamdaki herhangi bir değişkeni yakalamamasına (başvuru) izin vermek için artık yerel işlevlere `static` değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-220">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="7b6eb-221">Bunu yapmak `CS8421`üretir, "statik bir yerel işlev > \<değişkenine başvuru içeremez."</span><span class="sxs-lookup"><span data-stu-id="7b6eb-221">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="7b6eb-222">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-222">Consider the following code.</span></span> <span data-ttu-id="7b6eb-223">Yerel işlev `LocalFunction`, kapsayan kapsamda (`M`yöntemi) belirtilen `y`değişkenine erişir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-223">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="7b6eb-224">Bu nedenle, `LocalFunction` `static` değiştiricisiyle bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-224">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="7b6eb-225">Aşağıdaki kod statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-225">The following code contains a static local function.</span></span> <span data-ttu-id="7b6eb-226">Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-226">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="7b6eb-227">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="7b6eb-227">Disposable ref structs</span></span>

<span data-ttu-id="7b6eb-228">`ref` değiştiricisiyle bildirildiği `struct` hiçbir arabirim uygulayamaz, bu nedenle <xref:System.IDisposable>uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="7b6eb-229">Bu nedenle, bir `ref struct` elden çıkarılbilmesini sağlamak için, erişilebilir bir `void Dispose()` yöntemine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-229">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="7b6eb-230">Bu özellik `readonly ref struct` bildirimleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-230">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="7b6eb-231">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="7b6eb-231">Nullable reference types</span></span>

<span data-ttu-id="7b6eb-232">Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-232">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="7b6eb-233">Bir değişkenin null olabileceğini belirtmek isterseniz, değişkeni null olabilen bir **başvuru türü**olarak bildirmek için tür adını `?` eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-233">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="7b6eb-234">Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-234">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="7b6eb-235">Alanlar oluşturma sırasında başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-235">Fields must be initialized during construction.</span></span> <span data-ttu-id="7b6eb-236">Derleyici, değişken kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="7b6eb-237">Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-237">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="7b6eb-238">Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-238">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="7b6eb-239">Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-239">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="7b6eb-240">Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-240">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="7b6eb-241">Bu [null yapılabilir başvuru türleri öğreticisindeki](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-241">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="7b6eb-242">[Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](../tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-242">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="7b6eb-243">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="7b6eb-243">Asynchronous streams</span></span>

<span data-ttu-id="7b6eb-244">8,0 ile C# başlayarak akışları zaman uyumsuz olarak oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-244">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="7b6eb-245">Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-245">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="7b6eb-246">`async` değiştiricisiyle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-246">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="7b6eb-247">Bir <xref:System.Collections.Generic.IAsyncEnumerable%601>döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-247">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="7b6eb-248">Yöntemi, zaman uyumsuz akıştaki birbirini izleyen öğeleri döndürmek için `yield return` deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-248">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="7b6eb-249">Zaman uyumsuz bir akışın kullanılması, akışın öğelerini Numaralandırdığınızda `foreach` anahtar sözcüğünden önce `await` anahtar sözcüğünü eklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-249">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="7b6eb-250">`await` anahtar sözcüğünü eklemek, zaman uyumsuz akışı, `async` değiştiricisiyle belirtilecek ve bir `async` yöntemi için izin verilen bir tür döndürecek şekilde numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-250">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="7b6eb-251">Genellikle bu, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-251">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7b6eb-252">Ayrıca, bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-252">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="7b6eb-253">Bir yöntem, bir zaman uyumsuz akış tüketebilir ve üretebilir, bu da bir <xref:System.Collections.Generic.IAsyncEnumerable%601>dönecektir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-253">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="7b6eb-254">Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-254">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="7b6eb-255">`await foreach` ifadesini kullanarak sırayı numaralandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-255">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="7b6eb-256">Zaman uyumsuz akışları [oluşturma ve](../tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-256">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="7b6eb-257">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="7b6eb-257">Indices and ranges</span></span>

<span data-ttu-id="7b6eb-258">Dizinler ve aralıklar bir dizideki tek öğelere veya aralıklara erişmek için bir kısa söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-258">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="7b6eb-259">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-259">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="7b6eb-260"><xref:System.Index?displayProperty=nameWithType> bir dizini bir diziye temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-260"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="7b6eb-261">Bir dizinin dizinin sonuna göre olduğunu belirten bitiş işlecinden Dizin `^`.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-261">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="7b6eb-262"><xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-262"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="7b6eb-263">Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirten `..`.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-263">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="7b6eb-264">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-264">Let's start with the rules for indexes.</span></span> <span data-ttu-id="7b6eb-265">Dizi `sequence`değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-265">Consider an array `sequence`.</span></span> <span data-ttu-id="7b6eb-266">`0` Dizin `sequence[0]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-266">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="7b6eb-267">`^0` Dizin `sequence[sequence.Length]`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-267">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="7b6eb-268">`sequence[^0]`, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-268">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="7b6eb-269">Herhangi bir sayı `n`için Dizin `^n` `sequence.Length - n`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-269">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="7b6eb-270">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-270">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="7b6eb-271">Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *uç* aralığa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-271">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="7b6eb-272">Aralık `[0..^0]`, tüm aralığı temsil eden `[0..sequence.Length]` aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-272">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="7b6eb-273">Birkaç örneğe bakalım.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-273">Let's look at a few examples.</span></span> <span data-ttu-id="7b6eb-274">Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-274">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="7b6eb-275">Son kelimeyi `^1` diziniyle alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-275">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="7b6eb-276">Aşağıdaki kod, "quick", "brown" ve "fox" sözcüklerinin bulunduğu bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-276">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="7b6eb-277">`words[3]`üzerinden `words[1]` içerir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-277">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="7b6eb-278">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-278">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="7b6eb-279">Aşağıdaki kod, "lazy" ve "dog" sözcüklerini içeren bir alt aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-279">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="7b6eb-280">`words[^2]` ve `words[^1]`içerir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-280">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="7b6eb-281">Son dizin `words[^0]` dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-281">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="7b6eb-282">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-282">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="7b6eb-283">Aralıkları, değişkenler olarak da bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-283">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="7b6eb-284">Aralık daha sonra `[` ve `]` karakterleri içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-284">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="7b6eb-285">Yalnızca dizin ve aralıkları destekleyen diziler değil.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-285">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="7b6eb-286">Ayrıca, dizin ve aralıkları [dize](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-286">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="7b6eb-287">Daha fazla bilgi için bkz. [Dizinler ve aralıklar için destek türü](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="7b6eb-287">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="7b6eb-288">Dizinler ve [aralıklar](../tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-288">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="7b6eb-289">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="7b6eb-289">Null-coalescing assignment</span></span>

<span data-ttu-id="7b6eb-290">C#8,0, null birleşim atama işleci `??=`tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-290">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="7b6eb-291">Sağ işleneninin değerini yalnızca sol taraftaki işlenenin `null`değerlendirilirse, sol taraftaki işlenene atamak için `??=` işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-291">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="7b6eb-292">Daha fazla bilgi için?? [ve?? = operatörler](../language-reference/operators/null-coalescing-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-292">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="7b6eb-293">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="7b6eb-293">Unmanaged constructed types</span></span>

<span data-ttu-id="7b6eb-294">7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) yönetilmeyen bir tür olamaz. [](../language-reference/builtin-types/unmanaged-types.md) C#</span><span class="sxs-lookup"><span data-stu-id="7b6eb-294">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="7b6eb-295">8,0 ile C# başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-295">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="7b6eb-296">Örneğin, genel `Coords<T>` türünün Aşağıdaki tanımı verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-296">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="7b6eb-297">`Coords<int>` türü, C# 8,0 ve sonraki sürümlerde yönetilmeyen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-297">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="7b6eb-298">Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :</span><span class="sxs-lookup"><span data-stu-id="7b6eb-298">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="7b6eb-299">Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="7b6eb-299">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="7b6eb-300">İç içe ifadelerde stackalloc</span><span class="sxs-lookup"><span data-stu-id="7b6eb-300">Stackalloc in nested expressions</span></span>

<span data-ttu-id="7b6eb-301">8,0 ile C# başlayarak, bir [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin sonucu <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> türünde ise, diğer ifadelerde `stackalloc` ifadesini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6eb-301">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="7b6eb-302">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="7b6eb-302">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="7b6eb-303">`$` ve `@` belirteçlerinin sırası, her [ikisi de olabilir](../language-reference/tokens/interpolated.md) : hem `$@"..."` hem de `@$"..."` geçerli bir ara değerli dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-303">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="7b6eb-304">Önceki C# sürümlerde `$` belirtecinin `@` belirtecinden önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b6eb-304">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
