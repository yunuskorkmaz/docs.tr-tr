---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174275"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="439ee-101">Blazor: derleme zamanında bileşenlerden çok önemli olan boşluk</span><span class="sxs-lookup"><span data-stu-id="439ee-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="439ee-102">ASP.NET Core 5,0 Preview 7 ' den başlayarak, Razor derleyicisi derleme zamanında Blazor Components (*. Razor* dosyaları) içinde önemli olmayan boşluğu atlar.</span><span class="sxs-lookup"><span data-stu-id="439ee-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="439ee-103">Tartışma için bkz. sorun [DotNet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="439ee-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="439ee-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="439ee-104">Version introduced</span></span>

<span data-ttu-id="439ee-105">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="439ee-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="439ee-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="439ee-106">Old behavior</span></span>

<span data-ttu-id="439ee-107">Blazor Server ve Blazor WebAssembly 'in 3. x sürümlerinde, bir bileşenin kaynak kodunda boşluk kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="439ee-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="439ee-108">Görsel efekt olmasa bile yalnızca boşluk metin düğümleri tarayıcının Belge Nesne Modeli (DOM) içinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="439ee-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="439ee-109">Aşağıdaki Blazor bileşen kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="439ee-109">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="439ee-110">Yukarıdaki örnek iki boşluk düğümü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="439ee-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="439ee-111">`@foreach`Kod bloğunun dışında.</span><span class="sxs-lookup"><span data-stu-id="439ee-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="439ee-112">Öğesinin etrafında `<li>` .</span><span class="sxs-lookup"><span data-stu-id="439ee-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="439ee-113">Çıktı etrafında `@item.Text` .</span><span class="sxs-lookup"><span data-stu-id="439ee-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="439ee-114">100 öğe içeren bir liste 402 boşluk düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="439ee-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="439ee-115">Diğer bir deyişle, bir boşluk düğümlerinin hiçbiri işlenmiş çıktıyı görsel olarak etkilemese de, işlenen tüm düğümlerin yarısı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="439ee-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="439ee-116">Bileşenler için statik HTML işlenirken, bir etiket içindeki boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="439ee-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="439ee-117">Örneğin, aşağıdaki bileşenin kaynağını görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="439ee-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="439ee-118">Boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="439ee-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="439ee-119">Önceden işlenmiş çıkış:</span><span class="sxs-lookup"><span data-stu-id="439ee-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="439ee-120">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="439ee-120">New behavior</span></span>

<span data-ttu-id="439ee-121">`@preservewhitespace`Yönergesi değerle kullanılmadığı takdirde, şu `true` durumlarda boşluk düğümleri kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="439ee-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="439ee-122">Bir öğe içinde başında veya sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="439ee-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="439ee-123">Bir parametre içinde başında veya sonunda görüntülenir `RenderFragment` .</span><span class="sxs-lookup"><span data-stu-id="439ee-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="439ee-124">Örneğin, alt içerik başka bir bileşene geçirilmekte.</span><span class="sxs-lookup"><span data-stu-id="439ee-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="439ee-125">Ve gibi bir C# kod bloğunun önüne veya uygulayın `@if` `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="439ee-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="439ee-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="439ee-126">Reason for change</span></span>

<span data-ttu-id="439ee-127">ASP.NET Core 5,0 ' deki Blazor için bir hedef, oluşturma ve dağıtma performansını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="439ee-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="439ee-128">Kıyaslamalar halinde işleme süresinin yüzde 40 ' una kadar tüketilen çok önemli boşluk ağacı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="439ee-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="439ee-129">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="439ee-129">Recommended action</span></span>

<span data-ttu-id="439ee-130">Çoğu durumda, işlenmiş bileşenin görsel düzeni etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="439ee-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="439ee-131">Ancak, boşluk kaldırma, gibi bir CSS kuralı kullanırken işlenen çıktıyı etkileyebilir `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="439ee-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="439ee-132">Bu performans iyileştirmesini devre dışı bırakmak ve boşluğu korumak için aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="439ee-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="439ee-133">`@preservewhitespace true`Tercihi belirli bir bileşene uygulamak için *. Razor* dosyasının en üstündeki yönergeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="439ee-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="439ee-134">`@preservewhitespace true`Tercihi bir alt dizinin tamamına veya tüm projeye uygulamak için bir *_Imports. Razor* dosyası içinde yönergesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="439ee-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="439ee-135">Çoğu durumda, uygulamalar genellikle normal şekilde davranmaya devam edecek şekilde hiçbir eylem gerekmez (ancak daha hızlı).</span><span class="sxs-lookup"><span data-stu-id="439ee-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="439ee-136">Ortaya çıkan boşluk belirli bir bileşen için herhangi bir soruna neden oluyorsa, `@preservewhitespace true` Bu iyileştirmeyi devre dışı bırakmak için o bileşende kullanın.</span><span class="sxs-lookup"><span data-stu-id="439ee-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="439ee-137">Kategori</span><span class="sxs-lookup"><span data-stu-id="439ee-137">Category</span></span>

<span data-ttu-id="439ee-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="439ee-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="439ee-139">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="439ee-139">Affected APIs</span></span>

<span data-ttu-id="439ee-140">Yok</span><span class="sxs-lookup"><span data-stu-id="439ee-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
