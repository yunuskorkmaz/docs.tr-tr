---
title: İçindeki yenilikler C# 8.0 - C# Kılavuzu
description: Uygulamasında kullanılabilen yeni özellikleri genel bakış C# 8.0. Bu makalede, preview 5 ile güncel durumda.
ms.date: 02/12/2019
ms.openlocfilehash: 962829b68c5d02c3a7e563a00d391c4698024d47
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397766"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="879e9-104">İçindeki yenilikler C# 8.0</span><span class="sxs-lookup"><span data-stu-id="879e9-104">What's new in C# 8.0</span></span>

<span data-ttu-id="879e9-105">İçin birçok geliştirme vardır C# zaten deneyebileceğiniz dili.</span><span class="sxs-lookup"><span data-stu-id="879e9-105">There are many enhancements to the C# language that you can try out already.</span></span> 

- [<span data-ttu-id="879e9-106">Salt okunur üyeler</span><span class="sxs-lookup"><span data-stu-id="879e9-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="879e9-107">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="879e9-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="879e9-108">[Desen eşleştirme geliştirmeleri](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="879e9-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="879e9-109">Anahtar ifadeler</span><span class="sxs-lookup"><span data-stu-id="879e9-109">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="879e9-110">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-110">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="879e9-111">Kayıt düzenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-111">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="879e9-112">Konumsal desenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="879e9-113">Bildirimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="879e9-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="879e9-114">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="879e9-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="879e9-115">Atılabilir başvuru yapı birimleri</span><span class="sxs-lookup"><span data-stu-id="879e9-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="879e9-116">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="879e9-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="879e9-117">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="879e9-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="879e9-118">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="879e9-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="879e9-119">Bu makale için en son güncelleştirildiği C# 8.0 Önizleme 5.</span><span class="sxs-lookup"><span data-stu-id="879e9-119">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="879e9-120">Bu makalenin geri kalanında bu özelliklere kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="879e9-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="879e9-121">Ayrıntılı makaleleri kullanılabiliyorsa, bu öğreticileri ve genel bakışlar bağlantılar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="879e9-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="879e9-122">Bu özellikleri kullanarak ortamınıza keşfedebilirsiniz `dotnet try` genel aracı:</span><span class="sxs-lookup"><span data-stu-id="879e9-122">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="879e9-123">Yükleme [dotnet deneyin](https://github.com/dotnet/try/blob/master/README.md#setup) genel aracı.</span><span class="sxs-lookup"><span data-stu-id="879e9-123">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="879e9-124">Kopya [dotnet/try-samples](https://github.com/dotnet/try-samples) depo.</span><span class="sxs-lookup"><span data-stu-id="879e9-124">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="879e9-125">Geçerli dizin kümesine *csharp8* alt *deneyin-samples* depo.</span><span class="sxs-lookup"><span data-stu-id="879e9-125">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="879e9-126">`dotnet try`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="879e9-126">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="879e9-127">Salt okunur üyeler</span><span class="sxs-lookup"><span data-stu-id="879e9-127">Readonly members</span></span>

<span data-ttu-id="879e9-128">Uygulayabileceğiniz `readonly` değiştiricisi bir yapının herhangi bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="879e9-128">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="879e9-129">Üyenin durumu değiştirmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="879e9-129">It indicates that the member does not modify state.</span></span> <span data-ttu-id="879e9-130">Uygulama daha fazla ayrıntılı `readonly` değiştiriciyi bir `struct` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="879e9-130">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="879e9-131">Aşağıdaki değişebilir yapısı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="879e9-131">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="879e9-132">Çoğu yapılar gibi `ToString()` yöntemi durumu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="879e9-132">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="879e9-133">Ekleyerek olduğunu gösterebilecek `readonly` değiştiricisi bildirimine `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="879e9-133">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="879e9-134">Yukarıdaki değişikliği bir derleyici uyarısı oluşturur çünkü `ToString` erişen `Distance` işaret konulmadıysa özelliği `readonly`:</span><span class="sxs-lookup"><span data-stu-id="879e9-134">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="879e9-135">Savunma kopyası oluşturmak gerektiğinde derleyici sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="879e9-135">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="879e9-136">`Distance` Özelliği ekleyerek bu uyarıyı giderebilmemiz durumunu değiştirmez `readonly` bildirimine değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="879e9-136">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="879e9-137">Dikkat `readonly` değiştiricisi salt okunur bir özellik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="879e9-137">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="879e9-138">Derleyici varsayılmaz `get` bildirmeniz gerekir; erişimcileri durumu değiştirmeyin `readonly` açıkça.</span><span class="sxs-lookup"><span data-stu-id="879e9-138">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="879e9-139">Derleyici kuralını uygulamak, `readonly` üyeleri durumu değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="879e9-139">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="879e9-140">Kaldırdığınız sürece aşağıdaki yöntemi derlemeyecektir `readonly` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="879e9-140">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="879e9-141">Bu özellik, derleyici onu zorla ve en iyi duruma getirme, amacına olun tasarım amacınızla belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="879e9-141">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="879e9-142">Varsayılan arabirim üyeleri</span><span class="sxs-lookup"><span data-stu-id="879e9-142">Default interface members</span></span>

<span data-ttu-id="879e9-143">Artık üyeleri arabirimler ve bu üyeler için bir uygulama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="879e9-143">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="879e9-144">Bu dil özelliği kaynak ya da o arabirimin mevcut uygulamaları ile ikili uyumluluk bozup olmadan yöntemleri sonraki sürümlerinde bir arabirim eklemek API yazarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="879e9-144">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="879e9-145">Mevcut uygulamaları *devral* varsayılan uygulaması.</span><span class="sxs-lookup"><span data-stu-id="879e9-145">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="879e9-146">Bu özellik ayrıca sağlar C# hedef Android API'leri veya benzer özellikleri destekleyen Swift ile çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="879e9-146">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="879e9-147">Varsayılan arabirim üyeleri, ayrıca bir "Nitelikler" dil özelliğe benzer senaryolara olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="879e9-147">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="879e9-148">Varsayılan arabirim üyeleri birçok senaryoları ve Dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="879e9-148">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="879e9-149">İlk öğreticimize kapsayan [bir arabirimi varsayılan uygulamaları ile güncelleştiriliyor](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-149">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="879e9-150">Diğer öğreticiler ve başvuru güncelleştirmeleri genel yayın süreliğine geliyor.</span><span class="sxs-lookup"><span data-stu-id="879e9-150">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="879e9-151">Daha fazla yerde daha fazla desenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-151">More patterns in more places</span></span>

<span data-ttu-id="879e9-152">**Desen eşleştirme** ilgili ancak farklı türde veriler arasında şekil bağlı işlevler sağlamak için Araçlar verir.</span><span class="sxs-lookup"><span data-stu-id="879e9-152">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="879e9-153">C#7.0 sunulan tür kalıpları ve sabit desenler sözdizimi kullanarak [ `is` ](../language-reference/keywords/is.md) ifade ve [ `switch` ](../language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="879e9-153">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="879e9-154">Bu özellikler veri ve işlevsellik burada parçalayın Canlı programlama paradigmalarını destekleme doğru ilk belirsiz adımları temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="879e9-154">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="879e9-155">Daha fazla mikro Hizmetleri ve diğer bulut tabanlı mimariler doğru sektör hareket ettikçe diğer dil araçları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="879e9-155">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="879e9-156">C#Daha fazla yerde daha fazla desen ifade kodunuzda kullanabilmeniz için bu sözlük 8.0 genişletir.</span><span class="sxs-lookup"><span data-stu-id="879e9-156">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="879e9-157">Veri ve işlevsellik ayrı olduğunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="879e9-157">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="879e9-158">Bir nesnenin çalışma zamanı türü dışında bir olgu algoritmalarınızı bağımlı olduğunda desen eşleştirme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="879e9-158">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="879e9-159">Bu teknikler tasarımları ifade etmek için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="879e9-159">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="879e9-160">Yeni yerde yeni desenler yanı sıra C# 8.0 ekler **özyinelemeli desenleri**.</span><span class="sxs-lookup"><span data-stu-id="879e9-160">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="879e9-161">Bir ifade deseni herhangi bir ifade sonucudur.</span><span class="sxs-lookup"><span data-stu-id="879e9-161">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="879e9-162">Yalnızca başka bir desen ifadesi çıkışına uygulanan bir desen ifadesi özyinelemeli modelidir.</span><span class="sxs-lookup"><span data-stu-id="879e9-162">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="879e9-163">Anahtar ifadeler</span><span class="sxs-lookup"><span data-stu-id="879e9-163">switch expressions</span></span>

<span data-ttu-id="879e9-164">Genellikle, bir [ `switch` ](../language-reference/keywords/switch.md) deyimi, her bir değer oluşturuyor, `case` engeller.</span><span class="sxs-lookup"><span data-stu-id="879e9-164">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="879e9-165">**Anahtar ifadeler** , daha kısa ifade sözdizimini kullanacak şekilde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="879e9-165">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="879e9-166">Vardır daha az tekrarlı `case` ve `break` anahtar sözcükleri ve daha az küme ayraçları.</span><span class="sxs-lookup"><span data-stu-id="879e9-166">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="879e9-167">Örneğin, rainbow renklerini listeleyen aşağıdaki enum göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="879e9-167">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="879e9-168">Uygulama tanımlı değilse bir `RGBColor` nesnesinden oluşturulan türü `R`, `G` ve `B` bileşenleri dönüştürme bir `Rainbow` switch ifadesi içeren aşağıdaki yöntemi kullanarak kendi RGB değerleri için değer:</span><span class="sxs-lookup"><span data-stu-id="879e9-168">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="879e9-169">Burada birkaç söz dizimi geliştirmeleri vardır:</span><span class="sxs-lookup"><span data-stu-id="879e9-169">There are several syntax improvements here:</span></span>

- <span data-ttu-id="879e9-170">Değişken önce gelen `switch` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="879e9-170">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="879e9-171">Farklı sıra switch ifadesi switch deyiminden ayırt görsel olarak kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="879e9-171">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="879e9-172">`case` Ve `:` öğeleri yerine `=>`.</span><span class="sxs-lookup"><span data-stu-id="879e9-172">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="879e9-173">Bu daha kısa ve kolay anlaşılır olur.</span><span class="sxs-lookup"><span data-stu-id="879e9-173">It's more concise and intuitive.</span></span>
- <span data-ttu-id="879e9-174">`default` Çalışması ile değiştirildiği bir `_` atın.</span><span class="sxs-lookup"><span data-stu-id="879e9-174">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="879e9-175">Gövdeleri, değil deyimleri ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="879e9-175">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="879e9-176">Klasik kullanarak eşdeğer kodla, Karşıtlık `switch` deyimi:</span><span class="sxs-lookup"><span data-stu-id="879e9-176">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="879e9-177">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-177">Property patterns</span></span>

<span data-ttu-id="879e9-178">**Özelliği desenini** incelenirken nesnenin özellikleri eşleştirilecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="879e9-178">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="879e9-179">Alıcının adresine göre vergi hesaplamanız gerekir bir e-ticaret sitesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="879e9-179">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="879e9-180">Hesaplama çekirdeği sorumluluğunda değil bir `Address` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="879e9-180">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="879e9-181">Zamanla, büyük olasılıkla adresi biçim değişikliklerini daha sık değişir.</span><span class="sxs-lookup"><span data-stu-id="879e9-181">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="879e9-182">Vergi tutarı bağımlı `State` adresinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="879e9-182">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="879e9-183">Aşağıdaki yöntem özelliği desenini vergi adresi ve fiyat hesaplamak için kullanır:</span><span class="sxs-lookup"><span data-stu-id="879e9-183">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="879e9-184">Desen eşleştirme bu algoritma ifade etmek için kısa bir söz dizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-184">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="879e9-185">Kayıt düzenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-185">Tuple patterns</span></span>

<span data-ttu-id="879e9-186">Birden çok girişler bazı algoritmalar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="879e9-186">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="879e9-187">**Kayıt düzenleri** olarak ifade edilen birden çok değerlere göre geçiş yapmanıza izin bir [demet](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-187">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="879e9-188">Aşağıdaki kod oyun için bir switch ifadesi gösterir *rock, inceleme, Makas*:</span><span class="sxs-lookup"><span data-stu-id="879e9-188">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="879e9-189">Birinci iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="879e9-189">The messages indicate the winner.</span></span> <span data-ttu-id="879e9-190">Atma durum TIES veya diğer metin girişi için üç birleşimleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="879e9-190">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="879e9-191">Konumsal desenleri</span><span class="sxs-lookup"><span data-stu-id="879e9-191">Positional patterns</span></span>

<span data-ttu-id="879e9-192">Bazı türler bir `Deconstruct` özelliklerini ayrık değişkenlere deconstructs yöntemi.</span><span class="sxs-lookup"><span data-stu-id="879e9-192">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="879e9-193">Olduğunda bir `Deconstruct` yöntemi erişilebilir, kullanabileceğiniz **konumsal desenleri** nesnenin özelliklerini inceleyin ve bu özellikler için bir düzen kullanın.</span><span class="sxs-lookup"><span data-stu-id="879e9-193">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="879e9-194">Aşağıdakileri göz önünde bulundurun `Point` içeren sınıf bir `Deconstruct` ayrık değişkenleri yöntemini `X` ve `Y`:</span><span class="sxs-lookup"><span data-stu-id="879e9-194">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="879e9-195">Ayrıca, bir Çeyreğin çeşitli konumlarını temsil eden aşağıdaki enum göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="879e9-195">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="879e9-196">Aşağıdaki yöntemi kullanan **konumsal deseni** değerlerini ayıklamak için `x` ve `y`.</span><span class="sxs-lookup"><span data-stu-id="879e9-196">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="879e9-197">Ardından, kullanan bir `when` belirlemek için yan tümcesi `Quadrant` noktasının:</span><span class="sxs-lookup"><span data-stu-id="879e9-197">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="879e9-198">Eşleşen atma deseni önceki anahtarda ya da `x` veya `y` 0, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="879e9-198">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="879e9-199">Bir switch ifadesi bir değer üreten veya bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="879e9-199">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="879e9-200">Servis taleplerini hiçbiri eşleşen switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-200">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="879e9-201">Tüm olası durumların anahtar İfadenizde kapsamaz varsa derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-201">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="879e9-202">Bu teknikler desen keşfedebilirsiniz [desen eşleştirme Gelişmiş öğretici](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-202">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="879e9-203">Bildirimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="879e9-203">using declarations</span></span>

<span data-ttu-id="879e9-204">A **using bildirimi** bir Değişken bildiriminde öncesinde `using` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="879e9-204">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="879e9-205">Bu, derleyiciye bildirilen değişkenin kapsayan kapsamı sona atılmalıdır bildirir.</span><span class="sxs-lookup"><span data-stu-id="879e9-205">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="879e9-206">Örneğin, bir metin dosyasına yazan aşağıdaki kodu düşünün:</span><span class="sxs-lookup"><span data-stu-id="879e9-206">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="879e9-207">Önceki örnekte, yöntemi için kapanış ayracı ulaşıldığında Dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="879e9-207">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="879e9-208">Kapsamda sonuna olan `file` bildirilir.</span><span class="sxs-lookup"><span data-stu-id="879e9-208">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="879e9-209">Yukarıdaki kod, Klasik kullanarak aşağıdaki koda eşdeğerdir [using deyimlerini](../language-reference/keywords/using-statement.md) deyimi:</span><span class="sxs-lookup"><span data-stu-id="879e9-209">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="879e9-210">Kapanış küme ayracı ile ilişkili olduğunda önceki örnekte, dosyanın elden `using` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="879e9-210">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="879e9-211">Her iki durumda da, derleyici çağrısı oluşturur `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="879e9-211">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="879e9-212">Derleyici bir hata oluşturur kullanarak ifade deyimi atılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="879e9-212">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="879e9-213">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="879e9-213">Static local functions</span></span>

<span data-ttu-id="879e9-214">Artık ekleyebilirsiniz `static` değiştiricisi yerel bu işlevi sağlamak için yerel işlevler için değil (başvuru) yakalama kapsayan kapsamdan gelen tüm değişkenler.</span><span class="sxs-lookup"><span data-stu-id="879e9-214">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="879e9-215">Bunun yapılması oluşturur `CS8421`, "statik bir yerel işleve başvuru içeremez \<değişken >."</span><span class="sxs-lookup"><span data-stu-id="879e9-215">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="879e9-216">Aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="879e9-216">Consider the following code.</span></span> <span data-ttu-id="879e9-217">Yerel işlev `LocalFunction` değişkeni erişen `y`kapsayan kapsamda bildirilen (yöntemi `M`).</span><span class="sxs-lookup"><span data-stu-id="879e9-217">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="879e9-218">Bu nedenle, `LocalFunction` ile bildirilemez `static` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="879e9-218">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="879e9-219">Aşağıdaki kod, statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="879e9-219">The following code contains a static local function.</span></span> <span data-ttu-id="879e9-220">Tüm kapsayan kapsamda değişkenlere erişim yoktur çünkü statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="879e9-220">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="879e9-221">Atılabilir başvuru yapı birimleri</span><span class="sxs-lookup"><span data-stu-id="879e9-221">Disposable ref structs</span></span>

<span data-ttu-id="879e9-222">A `struct` ile bildirilen `ref` değiştiricisi hiçbir arabirim uygulayamaz ve bu nedenle uygulayamaz <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="879e9-222">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="879e9-223">Bu nedenle, etkinleştirmek için bir `ref struct` çıkarılması için bunu bir erişilebilir olmalıdır `void Dispose()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="879e9-223">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="879e9-224">Bu durum için de geçerlidir `readonly ref struct` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="879e9-224">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="879e9-225">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="879e9-225">Nullable reference types</span></span>

<span data-ttu-id="879e9-226">Boş değer atanabilir bir ek açıklama bir bağlam içinde bir başvuru türünün herhangi bir değişken olarak kabul edilir bir **nonnullable başvuru türü**.</span><span class="sxs-lookup"><span data-stu-id="879e9-226">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="879e9-227">Bir değişken null olabilir belirtmek istiyorsanız, tür adıyla ekleme `?` değişken olarak bildirmek için bir **boş değer atanabilir bir başvuru türü**.</span><span class="sxs-lookup"><span data-stu-id="879e9-227">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="879e9-228">Nonnullable başvuru türleri için derleyici yerel değişkenler bir null olmayan değer bildirildiğinde başlatılır emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="879e9-228">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="879e9-229">Oluşturma sırasında alanları yeniden başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="879e9-229">Fields must be initialized during construction.</span></span> <span data-ttu-id="879e9-230">Değişkeni bir başlatıcıya veya kullanılabilir oluşturucular herhangi bir çağrı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-230">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="879e9-231">Ayrıca, nonnullable başvuru türleri null olabilir bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="879e9-231">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="879e9-232">Null başvuru türlerine atanan olmayan veya null'a emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="879e9-232">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="879e9-233">Ancak derleyici, erişilen veya nonnullable başvuru türüne atanan önce herhangi bir değişken bir boş değer atanabilir bir başvuru türünün null karşı seçeneğinin işaretli olduğundan emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="879e9-233">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="879e9-234">Genel Bakış özelliği hakkında daha fazla bilgi [null başvuru türleri](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-234">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="879e9-235">Bu yeni bir uygulamada kendiniz denemek [null başvuru türleri öğretici](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-235">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="879e9-236">Hakkında bilgi edinin yapmak için var olan bir geçiş adımlarını codebase null başvuru türlerinde kullanımı [öğretici türleri null yapılabilir başvurusu kullanmak için bir uygulamayı geçirme](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-236">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="879e9-237">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="879e9-237">Asynchronous streams</span></span>

<span data-ttu-id="879e9-238">İle başlayarak C# 8.0, oluşturabilir ve akışları zaman uyumsuz olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="879e9-238">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="879e9-239">Zaman uyumsuz bir akışa döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="879e9-239">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="879e9-240">İle bildirilen `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="879e9-240">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="879e9-241">Döndürür bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="879e9-241">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="879e9-242">Contains yöntemi `yield return` deyimleri zaman uyumsuz akışın ardışık öğeleri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="879e9-242">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="879e9-243">Zaman uyumsuz bir akışa kullanma, gerektirir eklemeyi `await` anahtar sözcüğünün önüne `foreach` akış öğelerini numaralandırıldığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="879e9-243">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="879e9-244">Ekleme `await` anahtar sözcüğü ile bildirilen zaman uyumsuz akış numaralandırır yöntemi gerektiren `async` değiştiricisi ve bir tür için izin verilecek bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="879e9-244">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="879e9-245">Genellikle döndüren anlamına bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="879e9-245">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="879e9-246">Ayrıca olabilir bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="879e9-246">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="879e9-247">Bir yöntem hem kullanabilir ve şunu döndürür anlamına gelir zaman uyumsuz bir akışa üreten bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="879e9-247">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="879e9-248">Aşağıdaki kod, her bir sayının oluşturma arasında 100 ms bekleniyor 19 için 0'dan bir sıra üretir:</span><span class="sxs-lookup"><span data-stu-id="879e9-248">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="879e9-249">Dizisi kullanarak listeleme `await foreach` deyimi:</span><span class="sxs-lookup"><span data-stu-id="879e9-249">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="879e9-250">Zaman uyumsuz akışlar kendiniz müşterilerimize öğreticide deneyebilirsiniz [oluşturma ve zaman uyumsuz akışlar tüketen](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-250">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="879e9-251">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="879e9-251">Indices and ranges</span></span>

<span data-ttu-id="879e9-252">Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri bir dizi içinde alt aralıklara belirtmek için <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="879e9-252">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="879e9-253">Bu dil desteği, iki yeni türler ve iki yeni işleç kullanır.</span><span class="sxs-lookup"><span data-stu-id="879e9-253">This language support relies on two new types, and two new operators.</span></span>
- <span data-ttu-id="879e9-254"><xref:System.Index?displayProperty=nameWithType> Dizin bir dizisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="879e9-254"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="879e9-255">`^` İşleci bir dizin sonuna göreli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="879e9-255">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="879e9-256"><xref:System.Range?displayProperty=nameWithType> bir dizi alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="879e9-256"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="879e9-257">Aralık işleci (`..`) başlangıç belirtir ve bir aralığın işlenen olduğu.</span><span class="sxs-lookup"><span data-stu-id="879e9-257">The Range operator (`..`), which specifies the start and end of a range as is operands.</span></span>

<span data-ttu-id="879e9-258">Dizinler için kuralları başlayalım.</span><span class="sxs-lookup"><span data-stu-id="879e9-258">Let's start with the rules for indexes.</span></span> <span data-ttu-id="879e9-259">Bir dizi göz önünde bulundurun `sequence`.</span><span class="sxs-lookup"><span data-stu-id="879e9-259">Consider an array `sequence`.</span></span> <span data-ttu-id="879e9-260">`0` Dizin aynıdır `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="879e9-260">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="879e9-261">`^0` Dizin aynıdır `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="879e9-261">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="879e9-262">Unutmayın `sequence[^0]` gibi bir özel durum `sequence[sequence.Length]` yapar.</span><span class="sxs-lookup"><span data-stu-id="879e9-262">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="879e9-263">Herhangi bir sayı için `n`, dizin `^n` aynı `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="879e9-263">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="879e9-264">Bir aralığı belirtir *Başlat* ve *son* aralığının.</span><span class="sxs-lookup"><span data-stu-id="879e9-264">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="879e9-265">Aralığın başlangıcını dahil, ancak aralığın özel anlamı *Başlat* aralığa dahil olan ancak *son* aralığında yer almaz.</span><span class="sxs-lookup"><span data-stu-id="879e9-265">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="879e9-266">Aralığın `[0..^0]` gibi tüm aralığını temsil eden `[0..sequence.Length]` tüm aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="879e9-266">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="879e9-267">Bazı örneklere bakalım.</span><span class="sxs-lookup"><span data-stu-id="879e9-267">Let's look at a few examples.</span></span> <span data-ttu-id="879e9-268">Aşağıdaki dizinin başından ve sonundan dizinini ile açıklanan göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="879e9-268">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="879e9-269">Son sözcüğü alabilirsiniz `^1` dizini:</span><span class="sxs-lookup"><span data-stu-id="879e9-269">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="879e9-270">Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-270">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="879e9-271">İçerdiği `words[1]` aracılığıyla `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="879e9-271">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="879e9-272">Öğe `words[4]` aralığında değil.</span><span class="sxs-lookup"><span data-stu-id="879e9-272">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="879e9-273">Aşağıdaki kod, "geç" ve "köpek" alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="879e9-273">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="879e9-274">İçerdiği `words[^2]` ve `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="879e9-274">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="879e9-275">Bitiş dizini `words[^0]` dahil edilmez:</span><span class="sxs-lookup"><span data-stu-id="879e9-275">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="879e9-276">Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="879e9-276">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="879e9-277">De aralık değişkenleri olarak bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="879e9-277">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="879e9-278">Aralık içinde sonra kullanılabilir `[` ve `]` karakter:</span><span class="sxs-lookup"><span data-stu-id="879e9-278">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="879e9-279">Üzerinde öğreticide dizinleri ve aralıkları hakkında daha fazla keşfedebilirsiniz [dizinleri ve aralıkları](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="879e9-279">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>
