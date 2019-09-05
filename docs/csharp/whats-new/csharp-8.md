---
title: C# 8,0 C# kılavuzundaki yenilikler
description: 8,0 ' de C# bulunan yeni özelliklere genel bakış alın. Bu makale, Preview 5 ile güncel değildir.
ms.date: 09/02/2019
ms.openlocfilehash: 7210f2e978f307b3ecef2eff272fea0d19025de6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252898"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="0b1f8-104">C# 8,0 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-104">What's new in C# 8.0</span></span>

<span data-ttu-id="0b1f8-105">C# Dilde daha önce deneyebileceğiniz birçok geliştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="0b1f8-106">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="0b1f8-107">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="0b1f8-108">[Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="0b1f8-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="0b1f8-109">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="0b1f8-110">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="0b1f8-111">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="0b1f8-112">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="0b1f8-113">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="0b1f8-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="0b1f8-114">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="0b1f8-115">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="0b1f8-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="0b1f8-116">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="0b1f8-117">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="0b1f8-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="0b1f8-118">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="0b1f8-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="0b1f8-119">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="0b1f8-119">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="0b1f8-120">Bu makale 8,0 Preview 5 için C# son güncelleştirilme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-120">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="0b1f8-121">Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-121">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="0b1f8-122">Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-122">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="0b1f8-123">`dotnet try` Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-123">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="0b1f8-124">[DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-124">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="0b1f8-125">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-125">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="0b1f8-126">*TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-126">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="0b1f8-127">`dotnet try`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-127">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="0b1f8-128">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-128">Readonly members</span></span>

<span data-ttu-id="0b1f8-129">`readonly` Değiştiricisini bir yapının herhangi bir üyesine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-129">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="0b1f8-130">Üyenin durumu değiştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-130">It indicates that the member does not modify state.</span></span> <span data-ttu-id="0b1f8-131">Bu, `readonly` değiştiricinin bir bildirime uygulanmasıyla daha ayrıntılı bir `struct` hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-131">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="0b1f8-132">Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-132">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="0b1f8-133">Çoğu yapı gibi, `ToString()` yöntemi durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-133">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="0b1f8-134">`readonly` Şu`ToString()`bildirime değiştiricisini ekleyerek belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-134">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="0b1f8-135">Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` bu, işaretlenmeyen `Distance` `readonly`özelliğe erişir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-135">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="0b1f8-136">Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-136">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="0b1f8-137">Özelliği durumu değiştirmez, bu nedenle, bildirime `readonly` değiştiricisini ekleyerek bu uyarıyı giderebilirsiniz: `Distance`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-137">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="0b1f8-138">`readonly` Değiştiricinin salt okuma özelliğinde gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-138">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="0b1f8-139">Derleyici erişimcileri durumu değiştirmez `get` olarak kabul etmez; açıkça bildirmeniz `readonly` gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-139">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="0b1f8-140">Derleyici, `readonly` üyelerin durumu değiştirmediğinden kuralı zorunlu tutar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-140">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="0b1f8-141">`readonly` Değiştirici kaldırmadığınız takdirde aşağıdaki yöntem derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-141">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="0b1f8-142">Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-142">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="0b1f8-143">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-143">Default interface members</span></span>

<span data-ttu-id="0b1f8-144">Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-144">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="0b1f8-145">Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-145">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="0b1f8-146">Mevcut uygulamalar varsayılan uygulamayı *devralınır* .</span><span class="sxs-lookup"><span data-stu-id="0b1f8-146">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="0b1f8-147">Bu özellik aynı zamanda C# , benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'Lerle birlikte çalışmaya de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-147">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="0b1f8-148">Varsayılan arabirim üyeleri, "nitelikler" dil özelliğine benzer senaryolara de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-148">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="0b1f8-149">Varsayılan arabirim üyeleri birçok senaryoyu ve dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-149">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="0b1f8-150">İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](../tutorials/default-interface-members-versions.md)kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-150">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="0b1f8-151">Diğer öğreticiler ve başvuru güncelleştirmeleri genel sürüm için zaman içinde geliyor.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-151">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="0b1f8-152">Daha fazla yerde daha fazla desen</span><span class="sxs-lookup"><span data-stu-id="0b1f8-152">More patterns in more places</span></span>

<span data-ttu-id="0b1f8-153">**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-153">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="0b1f8-154">C#7,0, [`is`](../language-reference/keywords/is.md) ifade [`switch`](../language-reference/keywords/switch.md) ve deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-154">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="0b1f8-155">Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-155">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="0b1f8-156">Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-156">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="0b1f8-157">C#8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-157">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="0b1f8-158">Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-158">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="0b1f8-159">Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-159">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="0b1f8-160">Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-160">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="0b1f8-161">Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler**ekler.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-161">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="0b1f8-162">Herhangi bir model ifadesinin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-162">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="0b1f8-163">Özyinelemeli bir model, sadece başka bir model ifadesinin çıktısına uygulanan bir model ifadesi olur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-163">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="0b1f8-164">anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-164">switch expressions</span></span>

<span data-ttu-id="0b1f8-165">Genellikle, bir [`switch`](../language-reference/keywords/switch.md) ifade `case` blokların her birinde bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-165">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="0b1f8-166">**Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-166">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="0b1f8-167">Daha az yinelenen `case` ve `break` anahtar sözcük ve daha az küme ayraçları vardır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-167">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="0b1f8-168">Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-168">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="0b1f8-169">`RGBColor` Uygulamanız, `G` `Rainbow` ve `R` bileşenlerindenoluşturulmuşbirtürtanımlıysa,birdeğeribiranahtarifadesiiçerenaşağıdakiyöntemikullanarakRGBdeğerlerinedönüştürebilirsiniz:`B`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-169">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="0b1f8-170">Burada birkaç sözdizimi geliştirmesi vardır:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-170">There are several syntax improvements here:</span></span>

- <span data-ttu-id="0b1f8-171">Değişkeni, `switch` anahtar sözcüğünden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-171">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="0b1f8-172">Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-172">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="0b1f8-173">`case` Ve öğeleri`:` ile`=>`değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-173">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="0b1f8-174">Daha kısa ve sezgisel.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-174">It's more concise and intuitive.</span></span>
- <span data-ttu-id="0b1f8-175">Durum `default` , bir `_` atma ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-175">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="0b1f8-176">Gövdeler deyimlerdir, deyimler değildir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-176">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="0b1f8-177">Klasik `switch` deyimin kullanıldığı denk kodla kontrast:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-177">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="0b1f8-178">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-178">Property patterns</span></span>

<span data-ttu-id="0b1f8-179">**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-179">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="0b1f8-180">Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-180">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="0b1f8-181">Bu hesaplama, bir `Address` sınıfın temel sorumluluğu değildir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-181">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="0b1f8-182">Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-182">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="0b1f8-183">Satış vergisi miktarı adresin `State` özelliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-183">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="0b1f8-184">Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-184">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="0b1f8-185">Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-185">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="0b1f8-186">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-186">Tuple patterns</span></span>

<span data-ttu-id="0b1f8-187">Bazı algoritmalar birden fazla girişe bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-187">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="0b1f8-188">**Demet desenleri** , [kayıt düzeni](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-188">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="0b1f8-189">Aşağıdaki kod, oyun *rock, Paper, makas*için bir switch ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-189">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="0b1f8-190">İletiler kazanan kişiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-190">The messages indicate the winner.</span></span> <span data-ttu-id="0b1f8-191">Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-191">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="0b1f8-192">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-192">Positional patterns</span></span>

<span data-ttu-id="0b1f8-193">Bazı türler, özelliklerini `Deconstruct` ayrı değişkenlere oluşturan bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-193">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="0b1f8-194">Bir `Deconstruct` Yöntem erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-194">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="0b1f8-195">`Point` `Deconstruct` Ve için`X`ayrık değişkenler oluşturmak üzere bir yöntemi içeren aşağıdaki sınıfı göz önünde bulundurun: `Y`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-195">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="0b1f8-196">Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-196">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="0b1f8-197">Aşağıdaki yöntem, `x` ve `y`değerlerini ayıklamak için **konumsal model** kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-197">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="0b1f8-198">Sonra, noktanın `Quadrant` konumunu tespit `when` etmek için bir yan tümce kullanır:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-198">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="0b1f8-199">Önceki anahtardaki atma deseninin ya `x` `y` da 0 olduğunda eşleşir ancak ikisi birden değildir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-199">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="0b1f8-200">Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-200">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="0b1f8-201">Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-201">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="0b1f8-202">Anahtar ifadenizde olası tüm durumları kapsamıyordıysanız, derleyici sizin için bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-202">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="0b1f8-203">Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-203">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="0b1f8-204">bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="0b1f8-204">using declarations</span></span>

<span data-ttu-id="0b1f8-205">**Using bildirimi** , `using` anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-205">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="0b1f8-206">Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-206">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="0b1f8-207">Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-207">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="0b1f8-208">Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-208">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="0b1f8-209">İçinde `file` bildirildiği kapsamın sonu.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-209">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="0b1f8-210">Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-210">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="0b1f8-211">Önceki örnekte, `using` ifadesiyle ilişkilendirilen kapanış ayracı aşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-211">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="0b1f8-212">Her iki durumda da derleyici çağrısını `Dispose()`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-212">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="0b1f8-213">`using` Deyimdeki ifade atılabilir değilse, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-213">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="0b1f8-214">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="0b1f8-214">Static local functions</span></span>

<span data-ttu-id="0b1f8-215">Yerel işlevin kapsayan kapsamdaki herhangi `static` bir değişkeni yakalamamasına (başvuru) izin vermek için artık yerel işlevlere değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-215">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="0b1f8-216">Bunu yapmak \<, "statik yerel bir işlev > değişkenine bir başvuru içeremez." `CS8421`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-216">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="0b1f8-217">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-217">Consider the following code.</span></span> <span data-ttu-id="0b1f8-218">Yerel işlev `LocalFunction` , kapsayan kapsamda ( `y`yöntemi `M`) belirtilen değişkenine erişir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-218">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="0b1f8-219">Bu nedenle `LocalFunction` , `static` değiştiriciyle bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-219">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="0b1f8-220">Aşağıdaki kod statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-220">The following code contains a static local function.</span></span> <span data-ttu-id="0b1f8-221">Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-221">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="0b1f8-222">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="0b1f8-222">Disposable ref structs</span></span>

<span data-ttu-id="0b1f8-223">Değiştiriciyle birlikte tanımlanan bir `struct` arabirim uygulayamaz, bu nedenle uygulayamaz <xref:System.IDisposable>. `ref`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-223">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="0b1f8-224">Bu nedenle, bir `ref struct` 'nin atılbilmesini sağlamak için erişilebilir `void Dispose()` bir yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-224">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="0b1f8-225">Bu, bildirimler için `readonly ref struct` de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-225">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="0b1f8-226">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="0b1f8-226">Nullable reference types</span></span>

<span data-ttu-id="0b1f8-227">Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-227">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="0b1f8-228">Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen bir `?` **başvuru türü**olarak bildirmek için ile tür adını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-228">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="0b1f8-229">Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-229">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="0b1f8-230">Alanlar oluşturma sırasında başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-230">Fields must be initialized during construction.</span></span> <span data-ttu-id="0b1f8-231">Değişken, kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-231">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="0b1f8-232">Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-232">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="0b1f8-233">Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-233">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="0b1f8-234">Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-234">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="0b1f8-235">Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-235">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="0b1f8-236">Bu [null yapılabilir başvuru türleri öğreticisindeki](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-236">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="0b1f8-237">[Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](../tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-237">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="0b1f8-238">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="0b1f8-238">Asynchronous streams</span></span>

<span data-ttu-id="0b1f8-239">8,0 ile C# başlayarak akışları zaman uyumsuz olarak oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-239">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="0b1f8-240">Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-240">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="0b1f8-241">`async` Değiştiriciyle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-241">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="0b1f8-242">Döndürür <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-242">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="0b1f8-243">Yöntemi, zaman `yield return` uyumsuz akıştaki birbirini izleyen öğeleri döndürecek deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-243">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="0b1f8-244">Zaman uyumsuz bir akışın kullanılması, akışın öğelerini Numaralandırdığınızda `await` `foreach` anahtar kelimeden önce anahtar sözcüğünü eklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-244">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="0b1f8-245">Anahtar sözcüğü eklemek, zaman uyumsuz akışı belirten ve `async` değiştirici ile belirtilecek ve bir `async` Yöntem için izin verilen bir tür döndürecek yöntemi gerektirir. `await`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-245">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="0b1f8-246">Genellikle, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-246">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0b1f8-247">Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-247">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="0b1f8-248">Bir yöntem, zaman uyumsuz bir akış tüketebilir ve üretebilir, yani dönecektir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-248">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="0b1f8-249">Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-249">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="0b1f8-250">Şu `await foreach` ifadeyi kullanarak sırayı numaralandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-250">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="0b1f8-251">Zaman uyumsuz akışları [oluşturma ve](../tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-251">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="0b1f8-252">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="0b1f8-252">Indices and ranges</span></span>

<span data-ttu-id="0b1f8-253">Aralıklar ve dizinler, veya <xref:System.Span%601> <xref:System.ReadOnlySpan%601>dizisinde alt aralıklar belirtmek için bir kısa söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-253">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="0b1f8-254">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-254">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="0b1f8-255"><xref:System.Index?displayProperty=nameWithType>bir dizinin dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-255"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="0b1f8-256">Bir dizinin sıranın sonuna göreli olduğunu belirten işleç.`^`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-256">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="0b1f8-257"><xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-257"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="0b1f8-258">Aralık işleci (`..`), bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-258">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="0b1f8-259">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-259">Let's start with the rules for indexes.</span></span> <span data-ttu-id="0b1f8-260">Bir dizi `sequence`düşünün.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-260">Consider an array `sequence`.</span></span> <span data-ttu-id="0b1f8-261">Dizin, ile `sequence[0]`aynıdır. `0`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-261">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="0b1f8-262">Dizin, ile `sequence[sequence.Length]`aynıdır. `^0`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-262">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="0b1f8-263">`sequence[^0]` Bunun gibi`sequence[sequence.Length]` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-263">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="0b1f8-264">Herhangi bir sayı `n`için Dizin `^n` aynı `sequence.Length - n`olur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-264">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="0b1f8-265">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-265">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="0b1f8-266">Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *bitiş* aralığa eklenmez.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-266">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="0b1f8-267">Aralık, tüm aralığı temsil eden tüm `[0..sequence.Length]` aralığı temsileder.`[0..^0]`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-267">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="0b1f8-268">Birkaç örneğe bakalım.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-268">Let's look at a few examples.</span></span> <span data-ttu-id="0b1f8-269">Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-269">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="0b1f8-270">Son sözcüğü `^1` şu dizine alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-270">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="0b1f8-271">Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-271">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="0b1f8-272">`words[1]` İle`words[3]`içerir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-272">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="0b1f8-273">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-273">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="0b1f8-274">Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-274">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="0b1f8-275">`words[^2]` Ve`words[^1]`içerir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-275">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="0b1f8-276">Son dizin `words[^0]` dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-276">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="0b1f8-277">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-277">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="0b1f8-278">Aralıkları, değişkenler olarak da bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-278">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="0b1f8-279">Aralık daha sonra `[` ve `]` karakterleri içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0b1f8-279">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="0b1f8-280">Dizinler ve [aralıklar](../tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-280">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="0b1f8-281">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="0b1f8-281">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="0b1f8-282">`@` Birliktebulunan`$@"..."` [](../language-reference/tokens/interpolated.md) tam`@$"..."` dizelerde ve belirteçlerin sırası herhangi biri olabilir: her ikisi de geçerli bir ara tür dizelerdir. `$`</span><span class="sxs-lookup"><span data-stu-id="0b1f8-282">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="0b1f8-283">Önceki C# sürümlerde, `$` belirtecin `@` belirteçten önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1f8-283">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
