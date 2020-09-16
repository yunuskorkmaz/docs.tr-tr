---
ms.openlocfilehash: edff55d540f08e8a9fd4d0687aaf6bd963ee3a84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539527"
---
### <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="802fe-101">Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi</span><span class="sxs-lookup"><span data-stu-id="802fe-101">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="802fe-102">ASP.NET Core 3,0 ve 3,1 ' de, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> Yapı, `readonly public` <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> ve diğer gibi çeşitli alanları kullanıma sunuldu <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="802fe-102">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="802fe-103">ASP.NET Core 5,0 RC1 ve sonraki sürümlerinde, tüm `readonly public` alanlar özellikler olarak değiştirilmiştir `readonly public` .</span><span class="sxs-lookup"><span data-stu-id="802fe-103">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="802fe-104">Bu değişiklik birçok geliştirici etkilemez, çünkü:</span><span class="sxs-lookup"><span data-stu-id="802fe-104">This change won't affect many developers because:</span></span>

* <span data-ttu-id="802fe-105">`.razor`Bileşenlerini tanımlamak için dosyaları (veya hatta el ile çağrıları) kullanan herhangi bir uygulama veya kitaplık <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> , bu türe doğrudan başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="802fe-105">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="802fe-106">`RenderTreeFrame`Türün kendisi, Framework dışında kullanılması amaçlanmayan bir uygulama ayrıntısı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="802fe-106">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="802fe-107">ASP.NET Core 3,0 ve üzeri, tür doğrudan kullanılıyorsa Derleyici uyarıları veren bir çözümleyici içerir.</span><span class="sxs-lookup"><span data-stu-id="802fe-107">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="802fe-108">Doğrudan başvursanız bile `RenderTreeFrame` Bu değişiklik ikili bir değer değildir ancak kaynak bölünmez.</span><span class="sxs-lookup"><span data-stu-id="802fe-108">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="802fe-109">Diğer bir deyişle, var olan kaynak kodunuz doğru şekilde derlenir ve davranacaktır.</span><span class="sxs-lookup"><span data-stu-id="802fe-109">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="802fe-110">Yalnızca bir .NET Core 3. x çerçevesinde derleme yaptıysanız ve daha sonra bu ikili dosyaları .NET 5,0 RC1 ve sonraki bir çerçeveye karşı çalıştırmak için bir sorunla karşılaşacaksınız.</span><span class="sxs-lookup"><span data-stu-id="802fe-110">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="802fe-111">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).</span><span class="sxs-lookup"><span data-stu-id="802fe-111">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="802fe-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="802fe-112">Version introduced</span></span>

<span data-ttu-id="802fe-113">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="802fe-113">5.0 RC1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="802fe-114">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="802fe-114">Old behavior</span></span>

<span data-ttu-id="802fe-115">Ortak Üyeler `RenderTreeFrame` alan olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="802fe-115">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="802fe-116">Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="802fe-116">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="802fe-117">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="802fe-117">New behavior</span></span>

<span data-ttu-id="802fe-118">Ortak Üyeler `RenderTreeFrame` , önceki ile aynı adlara sahip özellikler olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="802fe-118">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="802fe-119">Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="802fe-119">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="802fe-120">Daha önceden derlenmiş kod bu değişiklikten bu yana yeniden derlenmemişse, MissingFieldException şuna benzer bir özel durum oluşturabilir: *alan bulunamadı: ' Microsoft. AspNetCore. components. RenderTree. RenderTreeFrame. FrameType '*.</span><span class="sxs-lookup"><span data-stu-id="802fe-120">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="802fe-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="802fe-121">Reason for change</span></span>

<span data-ttu-id="802fe-122">Bu değişiklik, ASP.NET Core 5,0 ' de Blazor bileşeni işlemede yüksek etkili performans iyileştirmeleri uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="802fe-122">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="802fe-123">Aynı güvenlik ve kapsülleme düzeyleri korunur.</span><span class="sxs-lookup"><span data-stu-id="802fe-123">The same levels of safety and encapsulation are maintained.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="802fe-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="802fe-124">Recommended action</span></span>

<span data-ttu-id="802fe-125">Çoğu Blazor geliştiricisi bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="802fe-125">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="802fe-126">Bu değişiklik, kitaplığı ve paket yazarlarını yalnızca nadir bir durumda etkilemekle daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="802fe-126">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="802fe-127">Geliştirmekte olduğunuz özel olarak:</span><span class="sxs-lookup"><span data-stu-id="802fe-127">Specifically, if you're developing:</span></span>

* <span data-ttu-id="802fe-128">Bir uygulama ve ASP.NET Core 3. x veya 5,0 RC1 veya sonraki bir sürüme yükseltme yapmak için kendi kodunuzu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="802fe-128">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="802fe-129">Ancak, bu değişiklik için hesaba yükseltilen bir kitaplığa bağlı değilseniz, bu kitaplığın daha yeni bir sürümüne güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="802fe-129">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="802fe-130">Bir kitaplık ve yalnızca ASP.NET Core 5,0 RC1 veya üstünü desteklemek istiyorsanız, herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="802fe-130">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="802fe-131">Yalnızca proje dosyanızın bir `<TargetFramework>` değeri `net5.0` veya daha sonraki bir sürümü bildirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="802fe-131">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="802fe-132">Bir kitaplık ve ASP.NET Core 3. x *ve* 5,0 ' i desteklemek istiyorsanız, kodunuzun herhangi bir üyeyi okuyup okumadığını saptayın `RenderTreeFrame` .</span><span class="sxs-lookup"><span data-stu-id="802fe-132">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="802fe-133">Örneğin, değerlendirme `someRenderTreeFrame.FrameType` .</span><span class="sxs-lookup"><span data-stu-id="802fe-133">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="802fe-134">Çoğu kitaplık `RenderTreeFrame` , bileşenleri içeren kitaplıklar da dahil olmak üzere, üyeleri okummaz `.razor` .</span><span class="sxs-lookup"><span data-stu-id="802fe-134">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="802fe-135">Bu durumda, hiçbir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="802fe-135">In this case, no action is needed.</span></span>
  * <span data-ttu-id="802fe-136">Ancak, kitaplığınız bunu destekliyorsa, hem hem de desteklemek için birden çok hedef gerekir `netstandard2.1` `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="802fe-136">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="802fe-137">Proje dosyanıza aşağıdaki değişiklikleri uygulayın:</span><span class="sxs-lookup"><span data-stu-id="802fe-137">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="802fe-138">Var olan `<TargetFramework>` öğeyi ile değiştirin `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .</span><span class="sxs-lookup"><span data-stu-id="802fe-138">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="802fe-139">`Microsoft.AspNetCore.Components`Desteklemek istediğiniz her iki sürümü de hesaba eklemek için koşullu paket başvurusu kullanın.</span><span class="sxs-lookup"><span data-stu-id="802fe-139">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="802fe-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="802fe-140">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="802fe-141">Daha fazla açıklama için, [ @jsakamoto `Toolbelt.Blazor.HeadElement` kitaplığın zaten nasıl yükseltildiğini gösteren bu fark](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="802fe-141">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

#### <a name="category"></a><span data-ttu-id="802fe-142">Kategori</span><span class="sxs-lookup"><span data-stu-id="802fe-142">Category</span></span>

<span data-ttu-id="802fe-143">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="802fe-143">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="802fe-144">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="802fe-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
