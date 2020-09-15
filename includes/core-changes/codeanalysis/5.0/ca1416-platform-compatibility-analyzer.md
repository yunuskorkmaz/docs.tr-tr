---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065214"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="cbeb0-101">CA1416: platform uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="cbeb0-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="cbeb0-102">.Net Code Analyzer Rule CA1416, varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-102">.NET code analyzer rule CA1416 is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="cbeb0-103">İşletim sistemini doğrulamaktan gelen çağrı sitelerinden platforma özel API 'lere çağrılar için bir derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cbeb0-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="cbeb0-104">Change description</span></span>

<span data-ttu-id="cbeb0-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="cbeb0-106">Bu kuralların bazıları varsayılan olarak CA1416 dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-106">Several of these rules are enabled, by default, including CA1416.</span></span> <span data-ttu-id="cbeb0-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="cbeb0-108">Rule CA1416, platform bağlamının doğrulanmadığı yerlerden platforma özel API 'Ler kullandığınızda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="cbeb0-109">CA1416 kuralı, platform uyumluluğu Çözümleyicisi, .NET 5,0 ' de yeni olan diğer özelliklerle birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-109">Rule CA1416, the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="cbeb0-110">.NET 5,0 `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> , bir API *'nin* üzerinde veya desteklenmeyen platformları belirtmenize olanak tanıyan ve öznitelikleri (önceki bir önizleme sürümünde ve olarak adlandırılır). *isn't*</span><span class="sxs-lookup"><span data-stu-id="cbeb0-110">.NET 5.0 introduces `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes (named <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> and <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> in an earlier preview release), which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="cbeb0-111">Bu özniteliklerin yokluğunda, tüm platformlarda desteklenen bir API 'nin olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="cbeb0-112">Bu öznitelikler, çekirdek .NET kitaplıklarında platforma özel API 'lere uygulandı.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="cbeb0-113">Kullandıkları API 'Leri hedefleyen projelerde, kural CA1416 platform bağlamının doğrulanmadığı herhangi bir platforma özgü API çağrısını işaretler.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-113">In projects that target platforms for which APIs that they use aren't available, rule CA1416 flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="cbeb0-114">Artık ve öznitelikleri ile donatılmış API 'lerin çoğu, `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` <xref:System.PlatformNotSupportedException> Desteklenmeyen bir işletim sisteminde çağrıldığında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-114">Most of the APIs that are now decorated with the `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="cbeb0-115">Artık bu API 'Lerin platforma özel olarak işaretlendiğinden, kural CA1416, <xref:System.PlatformNotSupportedException> çağrı sitelerinize işletim sistemi denetimleri ekleyerek çalışma zamanı özel durumlarını engellemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-115">Now that these APIs are marked as platform-specific, rule CA1416 helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="cbeb0-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cbeb0-116">Examples</span></span>

- <span data-ttu-id="cbeb0-117"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>Yöntemi yalnızca Windows 'ta desteklenir (ile tasarlanmıştır `[SupportedOSPlatform("windows")]` ).</span><span class="sxs-lookup"><span data-stu-id="cbeb0-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows (it's decorated with `[SupportedOSPlatform("windows")]`).</span></span> <span data-ttu-id="cbeb0-118">Aşağıdaki kod, proje [hedefliyorsa](../../../../docs/standard/frameworks.md) `net5.0` (ancak yoksa) derleme zamanında bir CA1416 uyarısı oluşturur `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="cbeb0-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="cbeb0-119">Uyarı oluşmasını önlemek için gerçekleştirebileceğiniz eylemler için bkz. [Önerilen eylem](#recommended-action).</span><span class="sxs-lookup"><span data-stu-id="cbeb0-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="cbeb0-120"><xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType>Yöntem tarayıcıda desteklenmez (ile donatılmış `[UnsupportedOSPlatform("browser")]` ).</span><span class="sxs-lookup"><span data-stu-id="cbeb0-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser (it's decorated with `[UnsupportedOSPlatform("browser")]`).</span></span> <span data-ttu-id="cbeb0-121">Aşağıdaki kod, proje dosyasında Blazor WebAssembly SDK ( `<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">` ) veya `browser` desteklenen platform () olarak içeriyorsa derleme ZAMANıNDA bir CA1416 uyarısı oluşturur `<SupportedPlatform Include="browser" />` .</span><span class="sxs-lookup"><span data-stu-id="cbeb0-121">The following code will produce a CA1416 warning at build time if the project uses the Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) or includes `browser` as a supported platform (`<SupportedPlatform Include="browser" />`) in the project file.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a><span data-ttu-id="cbeb0-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="cbeb0-122">Version introduced</span></span>

<span data-ttu-id="cbeb0-123">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="cbeb0-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cbeb0-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cbeb0-124">Recommended action</span></span>

<span data-ttu-id="cbeb0-125">Platforma özgü API 'Lerin yalnızca kod uygun bir platformda çalışırken çağrıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-125">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="cbeb0-126">Geçerli işletim sistemini, sınıfındaki yöntemlerden birini kullanarak (örneğin, `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> `System.OperatingSystem.IsWindows()` platforma özgü bir API çağrılmadan önce) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-126">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, `System.OperatingSystem.IsWindows()`, before calling a platform-specific API.</span></span>

<span data-ttu-id="cbeb0-127">`Is<Platform>`Bir deyimin koşulunda yöntemlerden birini kullanabilirsiniz `if` :</span><span class="sxs-lookup"><span data-stu-id="cbeb0-127">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="cbeb0-128">Ya da çalışma zamanında ek bir deyimin ek yükünü istemiyorsanız `if` , şunu çağırın <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="cbeb0-128">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="cbeb0-129">Ayrıca, API 'nizi platforma özel olarak işaretleyebilirsiniz. Bu durumda, gereksinimleri denetleme yükü çağıranlarınızın üzerine düşer.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-129">You can also mark your API as platform-specific, in which case the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="cbeb0-130">Belirli yöntemleri veya türleri ya da tüm derlemeyi işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-130">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="cbeb0-131">Tüm çağrı sitelerinizi onarmak istemiyorsanız, uyarıyı bastırmak için aşağıdaki seçeneklerden birini belirleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbeb0-131">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="cbeb0-132">Rule CA1416 'ı bastırmak için ya da `#pragma` [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) derleyici bayrağını kullanarak ya da [kuralın önem derecesini](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) `none` bir. editorconfig dosyasında olarak ayarlayarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-132">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="cbeb0-133">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-133">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="cbeb0-134">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="cbeb0-134">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="cbeb0-135">Kategori</span><span class="sxs-lookup"><span data-stu-id="cbeb0-135">Category</span></span>

- <span data-ttu-id="cbeb0-136">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="cbeb0-136">Code analysis</span></span>
- <span data-ttu-id="cbeb0-137">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="cbeb0-137">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cbeb0-138">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cbeb0-138">Affected APIs</span></span>

<span data-ttu-id="cbeb0-139">Windows platformu için:</span><span class="sxs-lookup"><span data-stu-id="cbeb0-139">For Windows platform:</span></span>

- <span data-ttu-id="cbeb0-140">Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .</span><span class="sxs-lookup"><span data-stu-id="cbeb0-140">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="cbeb0-141">Blazor WebAssembly platformu için:</span><span class="sxs-lookup"><span data-stu-id="cbeb0-141">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="cbeb0-142">Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/runtime/issues/41087> .</span><span class="sxs-lookup"><span data-stu-id="cbeb0-142">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="cbeb0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbeb0-143">See also</span></span>

- [<span data-ttu-id="cbeb0-144">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="cbeb0-144">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
