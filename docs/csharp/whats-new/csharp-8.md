---
title: C# 8,0 C# kılavuzundaki yenilikler
description: 8,0 ' de C# bulunan yeni özelliklere genel bakış alın. Bu makale, Preview 5 ile güncel değildir.
ms.date: 09/10/2019
ms.openlocfilehash: 1d6d52692a9a3f8b6fa4e333f086a880c54106b4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117820"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="43742-104">C# 8,0 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="43742-104">What's new in C# 8.0</span></span>

<span data-ttu-id="43742-105">C# Dilde daha önce deneyebileceğiniz birçok geliştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="43742-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="43742-106">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="43742-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="43742-107">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="43742-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="43742-108">[Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="43742-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="43742-109">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="43742-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="43742-110">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="43742-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="43742-111">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="43742-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="43742-112">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="43742-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="43742-113">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="43742-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="43742-114">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="43742-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="43742-115">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="43742-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="43742-116">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="43742-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="43742-117">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="43742-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="43742-118">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="43742-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="43742-119">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="43742-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="43742-120">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="43742-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="43742-121">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="43742-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="43742-122">Bu makale 8,0 Preview 5 için C# son güncelleştirilme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="43742-122">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="43742-123">Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43742-123">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="43742-124">Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="43742-124">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="43742-125">`dotnet try` Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-125">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="43742-126">[DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="43742-126">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="43742-127">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="43742-127">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="43742-128">*TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43742-128">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="43742-129">`dotnet try`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43742-129">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="43742-130">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="43742-130">Readonly members</span></span>

<span data-ttu-id="43742-131">`readonly` Değiştiricisini bir yapının herhangi bir üyesine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-131">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="43742-132">Üyenin durumu değiştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43742-132">It indicates that the member does not modify state.</span></span> <span data-ttu-id="43742-133">Bu, `readonly` değiştiricinin bir bildirime uygulanmasıyla daha ayrıntılı bir `struct` hale gelir.</span><span class="sxs-lookup"><span data-stu-id="43742-133">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="43742-134">Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43742-134">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="43742-135">Çoğu yapı gibi, `ToString()` yöntemi durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="43742-135">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="43742-136">`readonly` Şu`ToString()`bildirime değiştiricisini ekleyerek belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-136">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="43742-137">Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` bu, işaretlenmeyen `Distance` `readonly`özelliğe erişir:</span><span class="sxs-lookup"><span data-stu-id="43742-137">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="43742-138">Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="43742-138">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="43742-139">Özelliği durumu değiştirmez, bu nedenle, bildirime `readonly` değiştiricisini ekleyerek bu uyarıyı giderebilirsiniz: `Distance`</span><span class="sxs-lookup"><span data-stu-id="43742-139">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="43742-140">`readonly` Değiştiricinin salt okuma özelliğinde gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="43742-140">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="43742-141">Derleyici erişimcileri durumu değiştirmez `get` olarak kabul etmez; açıkça bildirmeniz `readonly` gerekir.</span><span class="sxs-lookup"><span data-stu-id="43742-141">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="43742-142">Derleyici, `readonly` üyelerin durumu değiştirmediğinden kuralı zorunlu tutar.</span><span class="sxs-lookup"><span data-stu-id="43742-142">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="43742-143">`readonly` Değiştirici kaldırmadığınız takdirde aşağıdaki yöntem derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="43742-143">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="43742-144">Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-144">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="43742-145">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="43742-145">Default interface members</span></span>

<span data-ttu-id="43742-146">Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-146">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="43742-147">Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-147">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="43742-148">Mevcut uygulamalar varsayılan uygulamayı *devralınır* .</span><span class="sxs-lookup"><span data-stu-id="43742-148">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="43742-149">Bu özellik aynı zamanda C# , benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'Lerle birlikte çalışmaya de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-149">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="43742-150">Varsayılan arabirim üyeleri, "nitelikler" dil özelliğine benzer senaryolara de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="43742-150">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="43742-151">Varsayılan arabirim üyeleri birçok senaryoyu ve dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="43742-151">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="43742-152">İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](../tutorials/default-interface-members-versions.md)kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="43742-152">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="43742-153">Diğer öğreticiler ve başvuru güncelleştirmeleri genel sürüm için zaman içinde geliyor.</span><span class="sxs-lookup"><span data-stu-id="43742-153">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="43742-154">Daha fazla yerde daha fazla desen</span><span class="sxs-lookup"><span data-stu-id="43742-154">More patterns in more places</span></span>

<span data-ttu-id="43742-155">**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-155">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="43742-156">C#7,0, [`is`](../language-reference/keywords/is.md) ifade [`switch`](../language-reference/keywords/switch.md) ve deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="43742-156">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="43742-157">Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43742-157">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="43742-158">Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.</span><span class="sxs-lookup"><span data-stu-id="43742-158">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="43742-159">C#8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir.</span><span class="sxs-lookup"><span data-stu-id="43742-159">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="43742-160">Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="43742-160">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="43742-161">Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="43742-161">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="43742-162">Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-162">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="43742-163">Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler**ekler.</span><span class="sxs-lookup"><span data-stu-id="43742-163">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="43742-164">Herhangi bir model ifadesinin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="43742-164">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="43742-165">Özyinelemeli bir model, sadece başka bir model ifadesinin çıktısına uygulanan bir model ifadesi olur.</span><span class="sxs-lookup"><span data-stu-id="43742-165">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="43742-166">anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="43742-166">switch expressions</span></span>

<span data-ttu-id="43742-167">Genellikle, bir [`switch`](../language-reference/keywords/switch.md) ifade `case` blokların her birinde bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="43742-167">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="43742-168">**Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-168">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="43742-169">Daha az yinelenen `case` ve `break` anahtar sözcük ve daha az küme ayraçları vardır.</span><span class="sxs-lookup"><span data-stu-id="43742-169">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="43742-170">Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43742-170">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="43742-171">Uygulamanız; `R`, `G` ve `B` bileşenlerinden oluşturulmuş bir `RGBColor` türü tanımladıysa bir `Rainbow` değerini, switch ifadesi içeren aşağıdaki yöntemi kullanarak RGB değerlerine dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-171">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="43742-172">Burada birkaç sözdizimi geliştirmesi vardır:</span><span class="sxs-lookup"><span data-stu-id="43742-172">There are several syntax improvements here:</span></span>

- <span data-ttu-id="43742-173">Değişkeni, `switch` anahtar sözcüğünden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="43742-173">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="43742-174">Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="43742-174">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="43742-175">`case` Ve öğeleri`:` ile`=>`değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43742-175">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="43742-176">Daha kısa ve sezgisel.</span><span class="sxs-lookup"><span data-stu-id="43742-176">It's more concise and intuitive.</span></span>
- <span data-ttu-id="43742-177">Durum `default` , bir `_` atma ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43742-177">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="43742-178">Gövdeler deyimlerdir, deyimler değildir.</span><span class="sxs-lookup"><span data-stu-id="43742-178">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="43742-179">Klasik `switch` deyimin kullanıldığı denk kodla kontrast:</span><span class="sxs-lookup"><span data-stu-id="43742-179">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="43742-180">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="43742-180">Property patterns</span></span>

<span data-ttu-id="43742-181">**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-181">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="43742-182">Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün.</span><span class="sxs-lookup"><span data-stu-id="43742-182">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="43742-183">Bu hesaplama, bir `Address` sınıfın temel sorumluluğu değildir.</span><span class="sxs-lookup"><span data-stu-id="43742-183">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="43742-184">Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir.</span><span class="sxs-lookup"><span data-stu-id="43742-184">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="43742-185">Satış vergisi miktarı adresin `State` özelliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="43742-185">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="43742-186">Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="43742-186">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="43742-187">Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-187">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="43742-188">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="43742-188">Tuple patterns</span></span>

<span data-ttu-id="43742-189">Bazı algoritmalar birden fazla girişe bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="43742-189">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="43742-190">**Demet desenleri** , [kayıt düzeni](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-190">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="43742-191">Aşağıdaki kod, oyun *rock, Paper, makas*için bir switch ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="43742-191">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="43742-192">İletiler kazanan kişiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="43742-192">The messages indicate the winner.</span></span> <span data-ttu-id="43742-193">Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43742-193">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="43742-194">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="43742-194">Positional patterns</span></span>

<span data-ttu-id="43742-195">Bazı türler, özelliklerini `Deconstruct` ayrı değişkenlere oluşturan bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="43742-195">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="43742-196">Bir `Deconstruct` Yöntem erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-196">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="43742-197">`Point` `Deconstruct` Ve için`X`ayrık değişkenler oluşturmak üzere bir yöntemi içeren aşağıdaki sınıfı göz önünde bulundurun: `Y`</span><span class="sxs-lookup"><span data-stu-id="43742-197">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="43742-198">Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43742-198">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="43742-199">Aşağıdaki yöntem, `x` ve `y`değerlerini ayıklamak için **konumsal model** kullanır.</span><span class="sxs-lookup"><span data-stu-id="43742-199">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="43742-200">Sonra, noktanın `Quadrant` konumunu tespit `when` etmek için bir yan tümce kullanır:</span><span class="sxs-lookup"><span data-stu-id="43742-200">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="43742-201">Önceki anahtardaki atma deseninin ya `x` `y` da 0 olduğunda eşleşir ancak ikisi birden değildir.</span><span class="sxs-lookup"><span data-stu-id="43742-201">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="43742-202">Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="43742-202">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="43742-203">Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-203">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="43742-204">Anahtar ifadenizde olası tüm durumları kapsamıyordıysanız, derleyici sizin için bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-204">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="43742-205">Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-205">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="43742-206">bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="43742-206">using declarations</span></span>

<span data-ttu-id="43742-207">**Using bildirimi** , `using` anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="43742-207">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="43742-208">Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="43742-208">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="43742-209">Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43742-209">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="43742-210">Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="43742-210">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="43742-211">İçinde `file` bildirildiği kapsamın sonu.</span><span class="sxs-lookup"><span data-stu-id="43742-211">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="43742-212">Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="43742-212">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="43742-213">Önceki örnekte, `using` ifadesiyle ilişkilendirilen kapanış ayracı aşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="43742-213">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="43742-214">Her iki durumda da derleyici çağrısını `Dispose()`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-214">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="43742-215">`using` Deyimdeki ifade atılabilir değilse, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-215">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="43742-216">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="43742-216">Static local functions</span></span>

<span data-ttu-id="43742-217">Yerel işlevin kapsayan kapsamdaki herhangi `static` bir değişkeni yakalamamasına (başvuru) izin vermek için artık yerel işlevlere değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-217">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="43742-218">Bunu yapmak \<, "statik yerel bir işlev > değişkenine bir başvuru içeremez." `CS8421`</span><span class="sxs-lookup"><span data-stu-id="43742-218">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="43742-219">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="43742-219">Consider the following code.</span></span> <span data-ttu-id="43742-220">Yerel işlev `LocalFunction` , kapsayan kapsamda ( `y`yöntemi `M`) belirtilen değişkenine erişir.</span><span class="sxs-lookup"><span data-stu-id="43742-220">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="43742-221">Bu nedenle `LocalFunction` , `static` değiştiriciyle bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="43742-221">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="43742-222">Aşağıdaki kod statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="43742-222">The following code contains a static local function.</span></span> <span data-ttu-id="43742-223">Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="43742-223">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="43742-224">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="43742-224">Disposable ref structs</span></span>

<span data-ttu-id="43742-225">Değiştiriciyle birlikte tanımlanan bir `struct` arabirim uygulayamaz, bu nedenle uygulayamaz <xref:System.IDisposable>. `ref`</span><span class="sxs-lookup"><span data-stu-id="43742-225">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="43742-226">Bu nedenle, bir `ref struct` 'nin atılbilmesini sağlamak için erişilebilir `void Dispose()` bir yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43742-226">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="43742-227">Bu, bildirimler için `readonly ref struct` de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="43742-227">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="43742-228">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="43742-228">Nullable reference types</span></span>

<span data-ttu-id="43742-229">Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="43742-229">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="43742-230">Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen bir `?` **başvuru türü**olarak bildirmek için ile tür adını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="43742-230">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="43742-231">Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="43742-231">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="43742-232">Alanlar oluşturma sırasında başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43742-232">Fields must be initialized during construction.</span></span> <span data-ttu-id="43742-233">Değişken, kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-233">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="43742-234">Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="43742-234">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="43742-235">Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="43742-235">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="43742-236">Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="43742-236">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="43742-237">Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-237">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="43742-238">Bu [null yapılabilir başvuru türleri öğreticisindeki](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="43742-238">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="43742-239">[Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](../tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="43742-239">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="43742-240">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="43742-240">Asynchronous streams</span></span>

<span data-ttu-id="43742-241">8,0 ile C# başlayarak akışları zaman uyumsuz olarak oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-241">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="43742-242">Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="43742-242">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="43742-243">`async` Değiştiriciyle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43742-243">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="43742-244">Döndürür <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="43742-244">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="43742-245">Yöntemi, zaman `yield return` uyumsuz akıştaki birbirini izleyen öğeleri döndürecek deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="43742-245">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="43742-246">Zaman uyumsuz bir akışın kullanılması, akışın öğelerini Numaralandırdığınızda `await` `foreach` anahtar kelimeden önce anahtar sözcüğünü eklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43742-246">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="43742-247">Anahtar sözcüğü eklemek, zaman uyumsuz akışı belirten ve `async` değiştirici ile belirtilecek ve bir `async` Yöntem için izin verilen bir tür döndürecek yöntemi gerektirir. `await`</span><span class="sxs-lookup"><span data-stu-id="43742-247">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="43742-248">Genellikle, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="43742-248">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="43742-249">Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="43742-249">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="43742-250">Bir yöntem, zaman uyumsuz bir akış tüketebilir ve üretebilir, yani dönecektir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="43742-250">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="43742-251">Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:</span><span class="sxs-lookup"><span data-stu-id="43742-251">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="43742-252">Şu `await foreach` ifadeyi kullanarak sırayı numaralandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-252">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="43742-253">Zaman uyumsuz akışları [oluşturma ve](../tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-253">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="43742-254">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="43742-254">Indices and ranges</span></span>

<span data-ttu-id="43742-255">Aralıklar ve dizinler, bir dizi, [dize](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>alt aralıkları belirtmek için bir kısa sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="43742-255">Ranges and indices provide a succinct syntax for specifying subranges in an array, [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="43742-256">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="43742-256">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="43742-257"><xref:System.Index?displayProperty=nameWithType>bir dizinin dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43742-257"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="43742-258">Bir dizinin sıranın sonuna göreli olduğunu belirten işleç.`^`</span><span class="sxs-lookup"><span data-stu-id="43742-258">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="43742-259"><xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43742-259"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="43742-260">Aralık işleci (`..`), bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="43742-260">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="43742-261">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="43742-261">Let's start with the rules for indexes.</span></span> <span data-ttu-id="43742-262">Bir dizi `sequence`düşünün.</span><span class="sxs-lookup"><span data-stu-id="43742-262">Consider an array `sequence`.</span></span> <span data-ttu-id="43742-263">Dizin, ile `sequence[0]`aynıdır. `0`</span><span class="sxs-lookup"><span data-stu-id="43742-263">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="43742-264">Dizin, ile `sequence[sequence.Length]`aynıdır. `^0`</span><span class="sxs-lookup"><span data-stu-id="43742-264">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="43742-265">`sequence[^0]` Bunun gibi`sequence[sequence.Length]` bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-265">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="43742-266">Herhangi bir sayı `n`için Dizin `^n` aynı `sequence.Length - n`olur.</span><span class="sxs-lookup"><span data-stu-id="43742-266">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="43742-267">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="43742-267">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="43742-268">Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *bitiş* aralığa eklenmez.</span><span class="sxs-lookup"><span data-stu-id="43742-268">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="43742-269">Aralık, tüm aralığı temsil eden tüm `[0..sequence.Length]` aralığı temsileder.`[0..^0]`</span><span class="sxs-lookup"><span data-stu-id="43742-269">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="43742-270">Birkaç örneğe bakalım.</span><span class="sxs-lookup"><span data-stu-id="43742-270">Let's look at a few examples.</span></span> <span data-ttu-id="43742-271">Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43742-271">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="43742-272">Son sözcüğü `^1` şu dizine alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-272">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="43742-273">Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-273">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="43742-274">`words[1]` İle`words[3]`içerir.</span><span class="sxs-lookup"><span data-stu-id="43742-274">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="43742-275">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="43742-275">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="43742-276">Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43742-276">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="43742-277">`words[^2]` Ve`words[^1]`içerir.</span><span class="sxs-lookup"><span data-stu-id="43742-277">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="43742-278">Son dizin `words[^0]` dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="43742-278">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="43742-279">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="43742-279">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="43742-280">Aralıkları, değişkenler olarak da bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43742-280">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="43742-281">Aralık daha sonra `[` ve `]` karakterleri içinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="43742-281">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="43742-282">Dizinler ve [aralıklar](../tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-282">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="43742-283">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="43742-283">Null-coalescing assignment</span></span>

<span data-ttu-id="43742-284">C#8,0, null birleşim atama işlecini `??=`tanıtır.</span><span class="sxs-lookup"><span data-stu-id="43742-284">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="43742-285">Sağ işleneninin değerini `??=` , sol taraftaki işlenenin değerini yalnızca sol taraftaki işlenen olarak `null`değerlendirdiğinde atamak için işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43742-285">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(' ', numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="43742-286">Daha fazla bilgi için?? [ve?? = operatörler](../language-reference/operators/null-coalescing-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="43742-286">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="43742-287">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="43742-287">Unmanaged constructed types</span></span>

<span data-ttu-id="43742-288">7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) yönetilmeyen bir tür olamaz. [](../language-reference/builtin-types/unmanaged-types.md) C#</span><span class="sxs-lookup"><span data-stu-id="43742-288">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) cannot be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="43742-289">8,0 ile C# başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="43742-289">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="43742-290">Örneğin, genel `Coords<T>` türün aşağıdaki tanımı verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="43742-290">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="43742-291">türü, C# 8,0 ve üzeri bir yönetilmeyen türdür. `Coords<int>`</span><span class="sxs-lookup"><span data-stu-id="43742-291">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="43742-292">Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :</span><span class="sxs-lookup"><span data-stu-id="43742-292">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="43742-293">Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="43742-293">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="43742-294">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="43742-294">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="43742-295">`@` Birliktebulunan`$@"..."` [](../language-reference/tokens/interpolated.md) tam`@$"..."` dizelerde ve belirteçlerin sırası herhangi biri olabilir: her ikisi de geçerli bir ara tür dizelerdir. `$`</span><span class="sxs-lookup"><span data-stu-id="43742-295">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="43742-296">Önceki C# sürümlerde, `$` belirtecin `@` belirteçten önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="43742-296">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
