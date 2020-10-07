---
title: Platform uyumluluk çözümleyicisi
description: Platformlar arası uygulamalarda ve kitaplıklarda platform uyumluluk sorunlarını algılamaya yardımcı olabilecek bir Roslyn Çözümleyicisi.
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: 44c2c2d9674b13f314a057f847df2d4d474cc2be
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805304"
---
# <a name="platform-compatibility-analyzer"></a><span data-ttu-id="a8225-103">Platform uyumluluk çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="a8225-103">Platform compatibility analyzer</span></span>

<span data-ttu-id="a8225-104">Büyük olasılıkla "One .NET" gibi bir uygulama oluşturmak için kullanabileceğiniz tek bir birleştirilmiş platform olduğunu duydunuz.</span><span class="sxs-lookup"><span data-stu-id="a8225-104">You've probably heard the motto of "One .NET": a single, unified platform for building any type of application.</span></span> <span data-ttu-id="a8225-105">.NET 5,0 SDK ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin ve ML.NET içerir ve zaman içinde daha fazla platform için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="a8225-105">The .NET 5.0 SDK includes ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin, and ML.NET, and will add support for more platforms over time.</span></span> <span data-ttu-id="a8225-106">.NET 5,0, .NET 'in farklı özellikleri hakkında neden olmanız gerektiği, ancak temel alınan işletim sistemini (OS) tamamen soyutlamayı denemeyen bir deneyim sunmak için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="a8225-106">.NET 5.0 strives to provide an experience where you don't have to reason about the different flavors of .NET, but doesn't attempt to fully abstract away the underlying operating system (OS).</span></span> <span data-ttu-id="a8225-107">Platforma özgü API 'Leri, örneğin P/Invoke, WinRT veya iOS ve Android için Xamarin bağlamaları gibi bir arayabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a8225-107">You'll continue to be able to call platform-specific APIs, for example, P/Invokes, WinRT, or the Xamarin bindings for iOS and Android.</span></span>

<span data-ttu-id="a8225-108">Ancak, platforma özgü API 'Lerin bir bileşende kullanılması, kodun artık tüm platformlarda çalışmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a8225-108">But using platform-specific APIs on a component means the code no longer works across all platforms.</span></span> <span data-ttu-id="a8225-109">Bu sayede, geliştiricilerin platforma özgü API 'Leri farkında olmadan tanılamayı alması için tasarım zamanında bunu tespit etmek için bir yol gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="a8225-109">We needed a way to detect this at design time so developers get diagnostics when they inadvertently use platform-specific APIs.</span></span> <span data-ttu-id="a8225-110">.NET 5,0, bu hedefe ulaşmak için [Platform uyumluluk Çözümleyicisi](/visualstudio/code-quality/ca1416) 'ni ve tamamlayıcı API 'leri sunarak, geliştiricilerin uygun yerlerde platforma özel API 'leri tanımlamasına ve kullanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a8225-110">To achieve this goal, .NET 5.0 introduces the [platform compatibility analyzer](/visualstudio/code-quality/ca1416) and complementary APIs to help developers identify and use platform-specific APIs where appropriate.</span></span>
<span data-ttu-id="a8225-111">Yeni API 'Ler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a8225-111">The new APIs include:</span></span>

- <span data-ttu-id="a8225-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> API 'Leri platforma özel olarak açıklama eklemek ve <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> API 'leri belirli BIR işletim sisteminde desteklenmeyen şekilde açıklama eklemek için.</span><span class="sxs-lookup"><span data-stu-id="a8225-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> to annotate APIs as being platform-specific and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> to annotate APIs as being unsupported on a particular OS.</span></span> <span data-ttu-id="a8225-113">Bu öznitelikler isteğe bağlı olarak sürüm numarasını içerebilir ve çekirdek .NET kitaplıklarında platforma özgü bazı API 'lere zaten uygulanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-113">These attributes can optionally include the version number, and have already been applied to some platform-specific APIs in the core .NET libraries.</span></span>
- <span data-ttu-id="a8225-114">`Is<Platform>()` ve `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` <xref:System.OperatingSystem?displayProperty=nameWithType> platforma özgü API 'leri güvenle çağırmak için sınıfındaki statik yöntemler.</span><span class="sxs-lookup"><span data-stu-id="a8225-114">`Is<Platform>()` and `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` static methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class for safely calling platform-specific APIs.</span></span> <span data-ttu-id="a8225-115">Örneğin, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> Windows 'a özgü BIR API çağrısını korumak için kullanılabilir ve <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> () sürümü tutulan bir Windows 'A özgü API çağrısını korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-115">For example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> can be used to guard a call to a Windows-specific API, and <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() can be used to guard a versioned Windows-specific API call.</span></span> <span data-ttu-id="a8225-116">Bu yöntemlerin platforma özgü API başvurularının koruyucuları olarak nasıl kullanılabileceği hakkında [örneklere](#guard-platform-specific-apis-with-guard-methods) bakın.</span><span class="sxs-lookup"><span data-stu-id="a8225-116">See these [examples](#guard-platform-specific-apis-with-guard-methods) of how these methods can be used as guards of platform-specific API references.</span></span>

> [!TIP]
> <span data-ttu-id="a8225-117">Platform uyumluluk Çözümleyicisi, [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md)'nin [platformlar arası sorunları keşfetmesini](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) yükseltir ve değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a8225-117">The platform compatibility analyzer upgrades and replaces the [Discovering cross-platform issues](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) feature of the [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8225-118">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a8225-118">Prerequisites</span></span>

<span data-ttu-id="a8225-119">Platform uyumluluğu Çözümleyicisi, Roslyn kod kalitesi çözümleyicilerinin biridir.</span><span class="sxs-lookup"><span data-stu-id="a8225-119">The platform compatibility analyzer is one of the Roslyn code quality analyzers.</span></span> <span data-ttu-id="a8225-120">.NET 5,0 ' den itibaren bu çözümleyiciler [.NET SDK 'ya dahildir](../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="a8225-120">Starting in .NET 5.0, these analyzers are [included with the .NET SDK](../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="a8225-121">Platform uyumluluğu Çözümleyicisi, yalnızca `net5.0` veya sonraki bir sürümü hedefleyen projeler için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="a8225-121">The platform compatibility analyzer is enabled by default only for projects that target `net5.0` or a later version.</span></span> <span data-ttu-id="a8225-122">Ancak, diğer çerçeveleri hedefleyen projeler için [etkinleştirebilirsiniz](/visualstudio/code-quality/ca1416.md#configurability) .</span><span class="sxs-lookup"><span data-stu-id="a8225-122">However, you can [enable](/visualstudio/code-quality/ca1416.md#configurability) it for projects that target other frameworks.</span></span>

## <a name="how-the-analyzer-determines-platform-dependency"></a><span data-ttu-id="a8225-123">Çözümleyici platform bağımlılığını nasıl belirler</span><span class="sxs-lookup"><span data-stu-id="a8225-123">How the analyzer determines platform dependency</span></span>

- <span data-ttu-id="a8225-124">**Öznitelik olmayan BIR API** , **tüm işletim sistemi platformlarında**çalıştığı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-124">An **unattributed API** is considered to work on **all OS platforms**.</span></span>
- <span data-ttu-id="a8225-125">İle işaretlenen bir API `[SupportedOSPlatform("platform")]` yalnızca belirtilen işletim sistemine taşınabilir olarak değerlendirilir `platform` .</span><span class="sxs-lookup"><span data-stu-id="a8225-125">An API marked with `[SupportedOSPlatform("platform")]` is considered only portable to the specified OS `platform`.</span></span>
  - <span data-ttu-id="a8225-126">Özniteliği **birden çok platform desteği** () göstermek için birden çok kez uygulanabilir `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` .</span><span class="sxs-lookup"><span data-stu-id="a8225-126">The attribute can be applied multiple times to indicate **multiple platform support** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`).</span></span>
  - <span data-ttu-id="a8225-127">Platforma özgü API 'Lere uygun bir **Platform bağlamı**olmadan başvuruluyorsa, çözümleyici bir **Uyarı** üretir:</span><span class="sxs-lookup"><span data-stu-id="a8225-127">The analyzer will produce a **warning** if platform-specific APIs are referenced without a proper **platform context**:</span></span>
    - <span data-ttu-id="a8225-128">Projenin desteklenen platformu hedeflediğini (örneğin, Windows 'a özgü bir API çağrısı ve proje hedefleri) yoksa **uyarır** `<TargetFramework>net5.0-ios14.0</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="a8225-128">**Warns** if the project doesn't target the supported platform (for example, a Windows-specific API call and the project targets `<TargetFramework>net5.0-ios14.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="a8225-129">Projenin çoklu hedefli () olduğunu **uyarır** `<TargetFramework>net5.0</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="a8225-129">**Warns** if the project is multi-targeted (`<TargetFramework>net5.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="a8225-130">Platforma özgü API 'ye, **belirtilen platformlardan** herhangi birini hedefleyen bir proje içinde başvuruluyorsa (örneğin, Windows 'a özgü bir API çağrısı ve proje hedefleri için), **uyarı vermez** `<TargetFramework>net5.0-windows</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="a8225-130">**Doesn't warn** if the platform-specific API is referenced within a project that targets any of the **specified platforms** (for example, for a Windows-specific API call and the project targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="a8225-131">Platforma özgü API çağrısı karşılık gelen platform denetimi yöntemleriyle (örneğin,) korunmuş olursa, **uyarı vermez** `if(OperatingSystem.IsWindows())` .</span><span class="sxs-lookup"><span data-stu-id="a8225-131">**Doesn't warn** if the platform-specific API call is guarded by corresponding platform-check methods (for example, `if(OperatingSystem.IsWindows())`).</span></span>
    - <span data-ttu-id="a8225-132">Platforma özgü API 'ye, platforma özgü bir içerikten (aynı zamanda öğesine sahip olan**çağrı sitesi** ) başvuruluyorsa, **uyarı vermez** `[SupportedOSPlatform("platform")` .</span><span class="sxs-lookup"><span data-stu-id="a8225-132">**Doesn't warn** if the platform-specific API is referenced from the same platform-specific context (**call site also attributed** with `[SupportedOSPlatform("platform")`).</span></span>
- <span data-ttu-id="a8225-133">İle işaretlenen bir API `[UnsupportedOSPlatform("platform")]` , yalnızca belirtilen işletim sisteminde desteklenmeyen `platform` ancak diğer tüm platformlar için desteklenen olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-133">An API marked with `[UnsupportedOSPlatform("platform")]` is considered unsupported only on the specified OS `platform` but supported for all other platforms.</span></span>
  - <span data-ttu-id="a8225-134">Özniteliği farklı platformlarla birden çok kez uygulanabilir, örneğin, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` .</span><span class="sxs-lookup"><span data-stu-id="a8225-134">The attribute can be applied multiple times with different platforms, for example, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`.</span></span>
  - <span data-ttu-id="a8225-135">Çözümleyici, yalnızca **warning** `platform` çağrı sitesi için geçerli olduğunda bir uyarı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a8225-135">The analyzer produces a **warning** only if the `platform` is effective for the call site:</span></span>
    - <span data-ttu-id="a8225-136">**Warns** Proje desteklenmeyen platformu hedefliyorsa (ÖRNEĞIN, API ile ilişkilendirilemişse `[UnsupportedOSPlatform("windows")]` ve çağıran site hedefliyorsa `<TargetFramework>net5.0-windows</TargetFramework>` ) uyarır.</span><span class="sxs-lookup"><span data-stu-id="a8225-136">**Warns** if the project targets the platform that's attributed as unsupported (for example, if the API is attributed with `[UnsupportedOSPlatform("windows")]` and the call site targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="a8225-137">**Warns** Projenin çoklu hedefli olduğunu ve `platform` varsayılan [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) öğeleri grubuna dahil edildiğini veya `platform` `MSBuild` \<SupportedPlatform> öğe grubuna el ile dahil edildiğini uyarır:</span><span class="sxs-lookup"><span data-stu-id="a8225-137">**Warns** if the project is multi-targeted and the `platform` is included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group, or the `platform` is manually included within the `MSBuild` \<SupportedPlatform> items group:</span></span>

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - <span data-ttu-id="a8225-138">Desteklenmeyen platformu hedeflemeyen veya çok hedefli ve platform varsayılan [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) öğeleri grubuna dahil edilmeyen bir uygulama oluşturuyorsanız **uyarı vermez** .</span><span class="sxs-lookup"><span data-stu-id="a8225-138">**Doesn't warn** if you're building an app that doesn't target the unsupported platform or is multi-targeted and the platform is not included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group.</span></span>
- <span data-ttu-id="a8225-139">Her iki öznitelik de, platform adının bir parçası olarak sürüm numaraları ile veya bu sayılar olmadan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-139">Both attributes can be instantiated with or without version numbers as part of the platform name.</span></span>
  - <span data-ttu-id="a8225-140">Sürüm numaraları biçimindedir `major.minor[.build[.revision]]` ; `major.minor` gereklidir ve `build` ve `revision` bölümleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a8225-140">Version numbers are in the format of `major.minor[.build[.revision]]`; `major.minor` is required and the `build` and `revision` parts are optional.</span></span> <span data-ttu-id="a8225-141">Örneğin, "Windows 7.0" Windows sürüm 7,0 ' i gösterir, ancak "Windows" Windows 0,0 olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a8225-141">For example, "Windows7.0" indicates Windows version 7.0, but "Windows" is interpreted as Windows 0.0.</span></span>

<span data-ttu-id="a8225-142">Daha fazla bilgi için, [özniteliklerin nasıl çalıştığı ve bu nesnelerin neden olduğu tanılamayı gösteren örneklere](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)bakın.</span><span class="sxs-lookup"><span data-stu-id="a8225-142">For more information, see [examples of how the attributes work and what diagnostics they cause](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).</span></span>

### <a name="advanced-scenarios-for-combining-attributes"></a><span data-ttu-id="a8225-143">Öznitelikleri birleştirmek için gelişmiş senaryolar</span><span class="sxs-lookup"><span data-stu-id="a8225-143">Advanced scenarios for combining attributes</span></span>

- <span data-ttu-id="a8225-144">Ve özniteliklerinin bir birleşimi `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` varsa, tüm öznitelikler işletim sistemi platformu tanımlayıcısına göre gruplandırılır:</span><span class="sxs-lookup"><span data-stu-id="a8225-144">If a combination of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are present, all attributes are grouped by OS platform identifier:</span></span>
  - <span data-ttu-id="a8225-145">**Yalnızca desteklenen liste**.</span><span class="sxs-lookup"><span data-stu-id="a8225-145">**Supported only list**.</span></span> <span data-ttu-id="a8225-146">Her işletim sistemi platformunun en düşük sürümü bir öznitelik ise `[SupportedOSPlatform]` , API yalnızca listelenen platformlar tarafından desteklenir ve tüm diğer platformlar tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a8225-146">If the lowest version for each OS platform is a `[SupportedOSPlatform]` attribute, the API is considered to only be supported by the listed platforms and unsupported by all other platforms.</span></span> <span data-ttu-id="a8225-147">`[UnsupportedOSPlatform]`Her platform için isteğe bağlı öznitelikler, API 'nin belirtilen sürümden başlayarak kaldırıldığını gösteren desteklenen en düşük sürümün daha yüksek sürümüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-147">The optional `[UnsupportedOSPlatform]` attributes for each platform can only have higher version of the minimum supported version, which denotes that the API is removed starting from the specified version.</span></span>

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - <span data-ttu-id="a8225-148">**Yalnızca desteklenmeyen liste**.</span><span class="sxs-lookup"><span data-stu-id="a8225-148">**Unsupported only list**.</span></span> <span data-ttu-id="a8225-149">Her işletim sistemi platformunun en düşük sürümü bir öznitelik ise `[UnsupportedOSPlatform]` , API yalnızca listelenen platformlar tarafından desteklenmeyen ve diğer tüm platformlar tarafından desteklenen kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-149">If the lowest version for each OS platform is an `[UnsupportedOSPlatform]` attribute, then the API is considered to only be unsupported by the listed platforms and supported by all other platforms.</span></span> <span data-ttu-id="a8225-150">Listenin `[SupportedOSPlatform]` aynı platforma sahip özniteliği olabilir, ancak API 'nin Bu sürümden itibaren desteklendiğini belirten daha yüksek bir sürümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-150">The list could have `[SupportedOSPlatform]` attribute with the same platform but a higher version, which denotes that the API is supported starting from that version.</span></span>

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - <span data-ttu-id="a8225-151">**Tutarsız liste**.</span><span class="sxs-lookup"><span data-stu-id="a8225-151">**Inconsistent list**.</span></span> <span data-ttu-id="a8225-152">Bazı platformların en düşük sürümü diğer platformlar için ise, bu, `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` çözümleyici için desteklenmeyen tutarsız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-152">If the lowest version for some platforms is `[SupportedOSPlatform]` while it is `[UnsupportedOSPlatform]` for other platforms, it's considered to be inconsistent, which is not supported for the analyzer.</span></span>
  - <span data-ttu-id="a8225-153">Ve özniteliklerinin en düşük sürümleri `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` eşitse, çözümleyici platformu **yalnızca desteklenen listenin**bir parçası olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a8225-153">If the lowest versions of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are equal, the analyzer considers the platform as part of the **Supported only list**.</span></span>
- <span data-ttu-id="a8225-154">Platform öznitelikleri, türler, Üyeler (metotlar, alanlar, Özellikler ve olaylar) ve farklı platform adları veya sürümleri olan derlemeler için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-154">Platform attributes can be applied to types, members (methods, fields, properties, and events) and assemblies with different platform names or versions.</span></span>
  - <span data-ttu-id="a8225-155">En üst düzeyde uygulanan öznitelikler `target` , tüm üyelerini ve türlerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="a8225-155">Attributes applied at the top level `target` affect all of its members and types.</span></span>
  - <span data-ttu-id="a8225-156">Alt düzey öznitelikler yalnızca "alt ek açıklamalar, platformlar desteğini daraltabilir, ancak bunları genişlezler" kuralına uyduklarında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a8225-156">Child-level attributes only apply if they adhere to the rule "child annotations can narrow the platforms support, but they cannot widen it".</span></span>
    - <span data-ttu-id="a8225-157">Üst öğe **yalnızca listeyi destekledikleri** zaman, alt üye öznitelikleri, ana desteği genişleten gibi yeni bir platform desteği ekleyemez.</span><span class="sxs-lookup"><span data-stu-id="a8225-157">When parent has **Supported only** list, then child member attributes cannot add a new platform support, as that would be extending parent support.</span></span> <span data-ttu-id="a8225-158">Yeni bir platform için destek yalnızca üst öğeye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-158">Support for a new platform can only be added to the parent itself.</span></span> <span data-ttu-id="a8225-159">Ancak alt öğe, `Supported` desteği daralan, daha sonraki sürümlerle aynı platform için özniteliğine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-159">But the child can have the `Supported` attribute for the same platform with later versions as that narrows the support.</span></span> <span data-ttu-id="a8225-160">Ayrıca, alt, `Unsupported` üst desteği de daralan aynı platformlu özniteliğe sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-160">Also, the child can have the `Unsupported` attribute with the same platform as that also narrows parent support.</span></span>
    - <span data-ttu-id="a8225-161">Üst öğe **yalnızca desteklenmeyen** bir liste olduğunda, alt üye öznitelikleri yeni bir platform için destek ekleyebilir ve bu, üst düzey desteği daraltır.</span><span class="sxs-lookup"><span data-stu-id="a8225-161">When parent has **Unsupported only** list, then child member attributes can add support for a new platform, as that narrows parent support.</span></span> <span data-ttu-id="a8225-162">Ancak `Supported` üst desteği genişlettiğinden, üst öğeyle aynı platform için özniteliği olamaz.</span><span class="sxs-lookup"><span data-stu-id="a8225-162">But it cannot have the `Supported` attribute for the same platform as the parent, because that extends parent support.</span></span> <span data-ttu-id="a8225-163">Aynı platform için destek yalnızca özgün özniteliğin uygulandığı üst öğeye eklenebilir `Unsupported` .</span><span class="sxs-lookup"><span data-stu-id="a8225-163">Support for the same platform can only be added to the parent where the original `Unsupported` attribute was applied.</span></span>
  - <span data-ttu-id="a8225-164">`[SupportedOSPlatform("platformVersion")]`Aynı ada sahip BIR API için birden çok kez uygulanırsa `platform` , çözümleyici yalnızca en düşük sürümle birlikte kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a8225-164">If `[SupportedOSPlatform("platformVersion")]` is applied more than once for an API with the same `platform` name, the analyzer only considers the one with the minimum version.</span></span>
  - <span data-ttu-id="a8225-165">`[UnsupportedOSPlatform("platformVersion")]`Aynı ada sahip BIR API için ikiden fazla kez uygulanırsa `platform` , çözümleyici yalnızca en eski sürümlerle ikisini de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a8225-165">If `[UnsupportedOSPlatform("platformVersion")]` is applied more than twice for an API with the same `platform` name, the analyzer only considers the two with the earliest versions.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a8225-166">Başlangıçta desteklenen ancak daha sonraki bir sürümde desteklenmeyen (kaldırılan) bir API, daha sonraki bir sürümde yeniden bağlantı almak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="a8225-166">An API that was supported initially but unsupported (removed) in a later version is not expected to get resupported in an even later version.</span></span>

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a><span data-ttu-id="a8225-167">Özniteliklerin nasıl çalıştığı ve hangi tanılamayı ürettikleri hakkında örnekler</span><span class="sxs-lookup"><span data-stu-id="a8225-167">Examples of how the attributes work and what diagnostics they produce</span></span>

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a><span data-ttu-id="a8225-168">Bildirilen uyarıları işle</span><span class="sxs-lookup"><span data-stu-id="a8225-168">Handle reported warnings</span></span>

<span data-ttu-id="a8225-169">Bu tanılamalarla başa çıkmak için önerilen yol, uygun bir platformda çalışırken yalnızca platforma özgü API 'Leri çağırdığınızdan emin olmak içindir.</span><span class="sxs-lookup"><span data-stu-id="a8225-169">The recommended way to deal with these diagnostics is to make sure you only call platform-specific APIs when running on an appropriate platform.</span></span> <span data-ttu-id="a8225-170">Uyarıları gidermek için kullanabileceğiniz seçenekler şunlardır. durumunuza en uygun olanını seçin:</span><span class="sxs-lookup"><span data-stu-id="a8225-170">Following are the options you can use to address the warnings; choose whichever is most appropriate for your situation:</span></span>

- <span data-ttu-id="a8225-171">**Çağrıyı korumayın**.</span><span class="sxs-lookup"><span data-stu-id="a8225-171">**Guard the call**.</span></span> <span data-ttu-id="a8225-172">Kodu çalışma zamanında koşullu olarak çağırarak bunu elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8225-172">You can achieve this by conditionally calling the code at run time.</span></span> <span data-ttu-id="a8225-173">`Platform`Platform denetimi yöntemlerinden birini (örneğin, veya) kullanarak istediğiniz gibi çalışıp çalışmadığını denetleyin `OperatingSystem.Is<Platform>()` `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` .</span><span class="sxs-lookup"><span data-stu-id="a8225-173">Check whether you're running on a desired `Platform` by using one of platform-check methods, for example, `OperatingSystem.Is<Platform>()` or `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)`.</span></span>

- <span data-ttu-id="a8225-174">**Çağrı sitesini platforma özgü olarak işaretleyin**.</span><span class="sxs-lookup"><span data-stu-id="a8225-174">**Mark the call site as platform-specific**.</span></span> <span data-ttu-id="a8225-175">Ayrıca, kendi API 'lerinizi platforma özel olarak işaretlemeyi tercih edebilir, böylece gereksinimleri arayanlara iletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8225-175">You can also choose to mark your own APIs as being platform-specific, thus effectively just forwarding the requirements to your callers.</span></span> <span data-ttu-id="a8225-176">İçerilen yöntemi veya türü ya da tüm derlemeyi, başvurulan platforma bağımlı çağrıyla aynı özniteliklerle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a8225-176">Mark the containing method or type or the entire assembly with the same attributes as the referenced platform-dependent call.</span></span> <span data-ttu-id="a8225-177">[Örnekler](#mark-call-site-as-platform-specific).</span><span class="sxs-lookup"><span data-stu-id="a8225-177">[Examples](#mark-call-site-as-platform-specific).</span></span>

- <span data-ttu-id="a8225-178">**Platform denetimi ile çağrı sitesini onaylama**.</span><span class="sxs-lookup"><span data-stu-id="a8225-178">**Assert the call site with platform check**.</span></span> <span data-ttu-id="a8225-179">Çalışma zamanında ek bir deyimin ek yükünü istemiyorsanız `if` , kullanın <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a8225-179">If you don't want the overhead of an additional `if` statement at run time, use <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a8225-180">[Örnek](#assert-the-call-site-with-platform-check).</span><span class="sxs-lookup"><span data-stu-id="a8225-180">[Example](#assert-the-call-site-with-platform-check).</span></span>

- <span data-ttu-id="a8225-181">**Kodu silin**.</span><span class="sxs-lookup"><span data-stu-id="a8225-181">**Delete the code**.</span></span> <span data-ttu-id="a8225-182">Kodunuz Windows kullanıcıları tarafından kullanıldığında, genellikle istediğiniz gibi değildir.</span><span class="sxs-lookup"><span data-stu-id="a8225-182">Generally not what you want because it means you lose fidelity when your code is used by Windows users.</span></span> <span data-ttu-id="a8225-183">Platformlar arası bir alternatif olduğu durumlarda, platforma özgü API 'lerden daha iyi bir şekilde faydalanarak daha iyi bir hale getiriyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a8225-183">For cases where a cross-platform alternative exists, you're likely better off using that over platform-specific APIs.</span></span>

- <span data-ttu-id="a8225-184">**Uyarıyı gizleyin**.</span><span class="sxs-lookup"><span data-stu-id="a8225-184">**Suppress the warning**.</span></span> <span data-ttu-id="a8225-185">Ayrıca, bir EditorConfig girişi ya da ya da yalnızca uyarıyı gizleyebilirsiniz `#pragma warning disable ca1416` .</span><span class="sxs-lookup"><span data-stu-id="a8225-185">You can also simply suppress the warning, either via an EditorConfig entry or `#pragma warning disable ca1416`.</span></span> <span data-ttu-id="a8225-186">Ancak, platforma özgü API 'Ler kullanılırken bu seçenek son çare olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8225-186">However, this option should be a last resort when using platform-specific APIs.</span></span>

### <a name="guard-platform-specific-apis-with-guard-methods"></a><span data-ttu-id="a8225-187">Guard yöntemleriyle platforma özel API 'Leri koruma</span><span class="sxs-lookup"><span data-stu-id="a8225-187">Guard platform-specific APIs with guard methods</span></span>

<span data-ttu-id="a8225-188">Guard yönteminin platform adı, çağıran platforma bağımlı API platformu adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8225-188">The guard method's platform name should match with the calling platform-dependent API platform name.</span></span> <span data-ttu-id="a8225-189">Çağıran API 'nin platform dizesi sürümü içeriyorsa:</span><span class="sxs-lookup"><span data-stu-id="a8225-189">If the platform string of the calling API includes the version:</span></span>

- <span data-ttu-id="a8225-190">Özniteliği için `[SupportedOSPlatform("platformVersion")]` , Guard yöntemi platformu, `version` çağıran platformun sayısından büyük veya buna eşit olmalıdır `Version` .</span><span class="sxs-lookup"><span data-stu-id="a8225-190">For the `[SupportedOSPlatform("platformVersion")]` attribute, the guard method platform `version` should be greater than or equal to the calling platform's `Version`.</span></span>
- <span data-ttu-id="a8225-191">Özniteliği için `[UnsupportedOSPlatform("platformVersion")]` , Guard yönteminin platformu, `version` çağıran platformun tarafından daha az veya eşit olmalıdır `Version` .</span><span class="sxs-lookup"><span data-stu-id="a8225-191">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the guard method's platform `version` should be less than or equal to the calling platform's `Version`.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- <span data-ttu-id="a8225-192">Hedeflenen veya yeni API 'lerin kullanılamadığı bir kodu korumaya ihtiyacınız varsa `netstandard` `netcoreapp` <xref:System.OperatingSystem> , <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API kullanılabilir ve çözümleyici tarafından sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="a8225-192">If you need to guard code that targets `netstandard` or `netcoreapp` where new <xref:System.OperatingSystem> APIs are not available, the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API can be used and will be respected by the analyzer.</span></span> <span data-ttu-id="a8225-193">Ancak yeni API 'Ler eklendikçe en iyi duruma getirilmemiştir <xref:System.OperatingSystem> .</span><span class="sxs-lookup"><span data-stu-id="a8225-193">But it's not as optimized as the new APIs added in <xref:System.OperatingSystem>.</span></span> <span data-ttu-id="a8225-194">Platform <xref:System.Runtime.InteropServices.OSPlatform> yapıda desteklenmiyorsa, <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> çözümleyici 'nin de buna karşı platform adını çağırabilir ve geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8225-194">If the platform is not supported in the <xref:System.Runtime.InteropServices.OSPlatform> struct, you can call <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> and pass in the platform name, which the analyzer also respects.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a><span data-ttu-id="a8225-195">Çağrı sitesini platforma özgü olarak işaretle</span><span class="sxs-lookup"><span data-stu-id="a8225-195">Mark call site as platform-specific</span></span>

<span data-ttu-id="a8225-196">Platform adları çağıran platforma bağımlı API ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8225-196">Platform names should match the calling platform-dependent API.</span></span> <span data-ttu-id="a8225-197">Platform dizesi bir sürüm içeriyorsa:</span><span class="sxs-lookup"><span data-stu-id="a8225-197">If the platform string includes a version:</span></span>

- <span data-ttu-id="a8225-198">Özniteliği için `[SupportedOSPlatform("platformVersion")]` , çağrı sitesi platformu, `version` çağıran platformun en fazla veya daha büyük olması gerekir `Version`</span><span class="sxs-lookup"><span data-stu-id="a8225-198">For the `[SupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be greater than or equal to the calling platform's `Version`</span></span>
- <span data-ttu-id="a8225-199">Özniteliği için `[UnsupportedOSPlatform("platformVersion")]` , çağıran site platformu, `version` çağıran platformun en fazla veya daha az olmalıdır `Version`</span><span class="sxs-lookup"><span data-stu-id="a8225-199">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be less than or equal to the calling platform's `Version`</span></span>

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a><span data-ttu-id="a8225-200">Platform denetimi ile çağrı sitesi onaylama</span><span class="sxs-lookup"><span data-stu-id="a8225-200">Assert the call-site with platform check</span></span>

<span data-ttu-id="a8225-201">[Platform Guard örneklerinde](#guard-platform-specific-apis-with-guard-methods) kullanılan tüm koşullu denetimler için de koşul olarak kullanılabilir <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a8225-201">All the conditional checks used in the [platform guard examples](#guard-platform-specific-apis-with-guard-methods) can also be used as the condition for <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span>

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a><span data-ttu-id="a8225-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8225-202">See also</span></span>

- [<span data-ttu-id="a8225-203">.NET 5 ' te hedef çerçeve adları</span><span class="sxs-lookup"><span data-stu-id="a8225-203">Target Framework Names in .NET 5</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [<span data-ttu-id="a8225-204">Platforma özgü API 'Lere açıklama ekleme ve kullanımını algılama</span><span class="sxs-lookup"><span data-stu-id="a8225-204">Annotating platform-specific APIs and detecting its use</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [<span data-ttu-id="a8225-205">API 'Leri belirli platformlarda desteklenmeyen şekilde açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="a8225-205">Annotating APIs as unsupported on specific platforms</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [<span data-ttu-id="a8225-206">CA1416 platform uyumluluğu Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="a8225-206">CA1416 Platform compatibility analyzer</span></span>](../../fundamentals/code-analysis/quality-rules/ca1416.md)
- [<span data-ttu-id="a8225-207">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="a8225-207">.NET API analyzer</span></span>](../../standard/analyzers/api-analyzer.md)
