---
title: Platform uyumluluğu Çözümleyicisi
description: Platformlar arası uygulamalarda ve kitaplıklarda platform uyumluluk sorunlarını algılamaya yardımcı olabilecek bir Roslyn Çözümleyicisi.
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: 4e842e5bbe90dd5006d9b27d0365f908b6441997
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406605"
---
# <a name="platform-compatibility-analyzer"></a>Platform uyumluluğu Çözümleyicisi

Büyük olasılıkla "One .NET" gibi bir uygulama oluşturmak için kullanabileceğiniz tek bir birleştirilmiş platform olduğunu duydunuz. .NET 5,0 SDK ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin ve ML.NET içerir ve zaman içinde daha fazla platform için destek ekler. .NET 5,0, .NET 'in farklı özellikleri hakkında neden olmanız gerektiği, ancak temel alınan işletim sistemini (OS) tamamen soyutlamayı denemeyen bir deneyim sunmak için çaba harcar. Platforma özgü API 'Leri, örneğin P/Invoke, WinRT veya iOS ve Android için Xamarin bağlamaları gibi bir arayabileceksiniz.

Ancak, platforma özgü API 'Lerin bir bileşende kullanılması, kodun artık tüm platformlarda çalışmamasıdır. Bu sayede, geliştiricilerin platforma özgü API 'Leri farkında olmadan tanılamayı alması için tasarım zamanında bunu tespit etmek için bir yol gerekiyordu. .NET 5,0, bu hedefe ulaşmak için [Platform uyumluluk Çözümleyicisi](/visualstudio/code-quality/ca1416) 'ni ve tamamlayıcı API 'leri sunarak, geliştiricilerin uygun yerlerde platforma özel API 'leri tanımlamasına ve kullanmasına yardımcı olur.
Yeni API 'Ler şunları içerir:

- <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> API 'Leri platforma özel olarak açıklama eklemek ve <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> API 'leri belirli BIR işletim sisteminde desteklenmeyen şekilde açıklama eklemek için. Bu öznitelikler isteğe bağlı olarak sürüm numarasını içerebilir ve çekirdek .NET kitaplıklarında platforma özgü bazı API 'lere zaten uygulanmış olabilir.
- `Is<Platform>()` ve `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` <xref:System.OperatingSystem?displayProperty=nameWithType> platforma özgü API 'leri güvenle çağırmak için sınıfındaki statik yöntemler. Örneğin, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> Windows 'a özgü BIR API çağrısını korumak için kullanılabilir ve <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> () sürümü tutulan bir Windows 'A özgü API çağrısını korumak için kullanılabilir. Bu yöntemlerin platforma özgü API başvurularının koruyucuları olarak nasıl kullanılabileceği hakkında [örneklere](#guard-platform-specific-apis-with-guard-methods) bakın.

> [!TIP]
> Platform uyumluluk Çözümleyicisi, [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md)'nin [platformlar arası sorunları keşfetmesini](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) yükseltir ve değiştirir.

## <a name="prerequisites"></a>Önkoşullar

Platform uyumluluğu Çözümleyicisi, Roslyn kod kalitesi çözümleyicilerinin biridir. .NET 5,0 ' den itibaren bu çözümleyiciler [.NET SDK 'ya dahildir](../../fundamentals/productivity/code-analysis.md). Platform uyumluluğu Çözümleyicisi, yalnızca `net5.0` veya sonraki bir sürümü hedefleyen projeler için varsayılan olarak etkindir. Ancak, diğer çerçeveleri hedefleyen projeler için [etkinleştirebilirsiniz](/visualstudio/code-quality/ca1416.md#configurability) .

## <a name="how-the-analyzer-determines-platform-dependency"></a>Çözümleyici platform bağımlılığını nasıl belirler

- **Öznitelik olmayan BIR API** , **tüm işletim sistemi platformlarında**çalıştığı kabul edilir.
- İle işaretlenen bir API `[SupportedOSPlatform("platform")]` yalnızca belirtilen işletim sistemine taşınabilir olarak değerlendirilir `platform` .
  - Özniteliği **birden çok platform desteği** () göstermek için birden çok kez uygulanabilir `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` .
  - Platforma özgü API 'Lere uygun bir **Platform bağlamı**olmadan başvuruluyorsa, çözümleyici bir **Uyarı** üretir:
    - Projenin desteklenen platformu hedeflediğini (örneğin, Windows 'a özgü bir API çağrısı ve proje hedefleri) yoksa **uyarır** `<TargetFramework>net5.0-ios14.0</TargetFramework>` .
    - Projenin çoklu hedefli () olduğunu **uyarır** `<TargetFramework>net5.0</TargetFramework>` .
    - Platforma özgü API 'ye, **belirtilen platformlardan** herhangi birini hedefleyen bir proje içinde başvuruluyorsa (örneğin, Windows 'a özgü bir API çağrısı ve proje hedefleri için), **uyarı vermez** `<TargetFramework>net5.0-windows</TargetFramework>` .
    - Platforma özgü API çağrısı karşılık gelen platform denetimi yöntemleriyle (örneğin,) korunmuş olursa, **uyarı vermez** `if(OperatingSystem.IsWindows())` .
    - Platforma özgü API 'ye, platforma özgü bir içerikten (aynı zamanda öğesine sahip olan**çağrı sitesi** ) başvuruluyorsa, **uyarı vermez** `[SupportedOSPlatform("platform")` .
- İle işaretlenen bir API `[UnsupportedOSPlatform("platform")]` , yalnızca belirtilen işletim sisteminde desteklenmeyen `platform` ancak diğer tüm platformlar için desteklenen olarak kabul edilir.
  - Özniteliği farklı platformlarla birden çok kez uygulanabilir, örneğin, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` .
  - Çözümleyici, yalnızca **warning** `platform` çağrı sitesi için geçerli olduğunda bir uyarı oluşturur:
    - **Warns** Proje desteklenmeyen platformu hedefliyorsa (ÖRNEĞIN, API ile ilişkilendirilemişse `[UnsupportedOSPlatform("windows")]` ve çağıran site hedefliyorsa `<TargetFramework>net5.0-windows</TargetFramework>` ) uyarır.
    - **Warns** Projenin çoklu hedefli olduğunu ve `platform` varsayılan [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) öğeleri grubuna dahil edildiğini veya `platform` `MSBuild` \<SupportedPlatform> öğe grubuna el ile dahil edildiğini uyarır:

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - Desteklenmeyen platformu hedeflemeyen veya çok hedefli ve platform varsayılan [ `<SupportedPlatform>` MSBuild](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) öğeleri grubuna dahil edilmeyen bir uygulama oluşturuyorsanız **uyarı vermez** .
- Her iki öznitelik de, platform adının bir parçası olarak sürüm numaraları ile veya bu sayılar olmadan oluşturulabilir.
  - Sürüm numaraları biçimindedir `major.minor[.build[.revision]]` ; `major.minor` gereklidir ve `build` ve `revision` bölümleri isteğe bağlıdır. Örneğin, "Windows 7.0" Windows sürüm 7,0 ' i gösterir, ancak "Windows" Windows 0,0 olarak yorumlanır.

Daha fazla bilgi için, [özniteliklerin nasıl çalıştığı ve bu nesnelerin neden olduğu tanılamayı gösteren örneklere](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)bakın.

### <a name="advanced-scenarios-for-combining-attributes"></a>Öznitelikleri birleştirmek için gelişmiş senaryolar

- Ve özniteliklerinin bir birleşimi `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` varsa, tüm öznitelikler işletim sistemi platformu tanımlayıcısına göre gruplandırılır:
  - **Yalnızca desteklenen liste**. Her işletim sistemi platformunun en düşük sürümü bir öznitelik ise `[SupportedOSPlatform]` , API yalnızca listelenen platformlar tarafından desteklenir ve tüm diğer platformlar tarafından desteklenmez. `[UnsupportedOSPlatform]`Her platform için isteğe bağlı öznitelikler, API 'nin belirtilen sürümden başlayarak kaldırıldığını gösteren desteklenen en düşük sürümün daha yüksek sürümüne sahip olabilir.

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - **Yalnızca desteklenmeyen liste**. Her işletim sistemi platformunun en düşük sürümü bir öznitelik ise `[UnsupportedOSPlatform]` , API yalnızca listelenen platformlar tarafından desteklenmeyen ve diğer tüm platformlar tarafından desteklenen kabul edilir. Listenin `[SupportedOSPlatform]` aynı platforma sahip özniteliği olabilir, ancak API 'nin Bu sürümden itibaren desteklendiğini belirten daha yüksek bir sürümü olabilir.
  
    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - **Tutarsız liste**. Bazı platformların en düşük sürümü `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` diğer platformlar için ise, çözümleyici için desteklenmeyen tutarsız olarak değerlendirilir.
  - Ve özniteliklerinin en düşük sürümleri `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` eşitse, çözümleyici platformu **yalnızca desteklenen listenin**bir parçası olarak değerlendirir.
- Platform öznitelikleri, türler, Üyeler (metotlar, alanlar, Özellikler ve olaylar) ve farklı platform adı ve/veya sürümü olan derlemeler için uygulanabilir.
  - En üst düzeyde uygulanan öznitelikler `target` , tüm üyelerini ve türlerini etkiler.
  - Alt düzey öznitelikleri yalnızca "alt ek açıklamalar, platformlar desteğini daraltabilirler, ancak bunları genişlezler" kuralına uyduklarında geçerlidir.
    - Üst öğe **yalnızca listeyi destekledikleri** zaman, alt üye öznitelikleri, üst desteği genişleten şekilde yeni bir platform desteği ekleyemedi, yeni bir platform desteği yalnızca üst öğeye eklenebilir. Ancak `Supported` , desteği daraltalacağı için, daha sonraki sürümlerle aynı platform için özniteliği olabilir. Ayrıca, `Unsupported` üst desteği de daraltmak için aynı platforma sahip özniteliği de olabilir.
    - Üst öğe **yalnızca desteklenmeyen** bir liste olduğunda, alt üye öznitelikleri üst desteğin daraltıleceği için yeni bir platform desteği ekleyebilir, ancak üst `Supported` desteği genişleten üst öğeyle aynı platform için özniteliği olamaz. Aynı platform için destek yalnızca özgün özniteliğin uygulandığı üst düzeye eklenebilir `Unsupported` .
  - `[SupportedOSPlatform("platformVersion")]`Aynı ada sahip BIR API için birden çok kez uygulanırsa `platform` , çözümleyici tarafından yalnızca en düşük sürümle birlikte değerlendirilir.
  - `[UnsupportedOSPlatform("platformVersion")]`Aynı ada sahip BIR API için ikiden fazla kez uygulanırsa `platform` , çözümleyici tarafından yalnızca en eski sürümler olan ikisi de kabul edilir.
  
  > [!NOTE]
  > Başlangıçta desteklenen ancak daha sonraki bir sürümde desteklenmeyen (kaldırılan) bir API, daha sonraki bir sürümde yeniden bağlantı almak zorunda değildir.

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a>Özniteliklerin nasıl çalıştığı ve hangi tanılamayı ürettikleri hakkında örnekler

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

## <a name="handle-reported-warnings"></a>Bildirilen uyarıları işle

Bu tanılamalarla başa çıkmak için önerilen yol, uygun bir platformda çalışırken yalnızca platforma özgü API 'Leri çağırdığınızdan emin olmak içindir. Uyarıları gidermek için kullanabileceğiniz seçenekler şunlardır. durumunuza en uygun olanını seçin:

- **Çağrıyı korumayın**. Kodu çalışma zamanında koşullu olarak çağırarak bunu elde edebilirsiniz. `Platform`Platform denetimi yöntemlerinden birini (örneğin, veya) kullanarak istediğiniz gibi çalışıp çalışmadığını denetleyin `OperatingSystem.Is<Platform>()` `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` .

- **Çağrı sitesini platforma özgü olarak işaretleyin**. Ayrıca, kendi API 'lerinizi platforma özel olarak işaretlemeyi tercih edebilir, böylece gereksinimleri arayanlara iletmeniz gerekir. İçerilen yöntemi veya türü ya da tüm derlemeyi, başvurulan platforma bağımlı çağrıyla aynı özniteliklerle işaretleyin. [Örnekler](#mark-call-site-as-platform-specific).

- **Platform denetimi ile çağrı sitesini onaylama**. Çalışma zamanında ek bir deyimin ek yükünü istemiyorsanız `if` , kullanın <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> . [Örnek](#assert-the-call-site-with-platform-check).

- **Kodu silin**. Kodunuz Windows kullanıcıları tarafından kullanıldığında, genellikle istediğiniz gibi değildir. Platformlar arası bir alternatif olduğu durumlarda, platforma özgü API 'lerden daha iyi bir şekilde faydalanarak daha iyi bir hale getiriyorsunuz.

- **Uyarıyı gizleyin**. Ayrıca, editor.config veya aracılığıyla da bir uyarı da gizleyebilirsiniz `#pragma warning disable ca1416` . Ancak, platforma özgü API 'Ler kullanılırken bu seçenek son çare olmalıdır.

### <a name="guard-platform-specific-apis-with-guard-methods"></a>Guard yöntemleriyle platforma özel API 'Leri koruma

Guard yönteminin platform adı, çağıran platforma bağımlı API platformu adıyla eşleşmelidir. Çağıran API 'nin platform dizesi sürümü içeriyorsa:

- Özniteliği için `[SupportedOSPlatform("platformVersion")]` , Guard yöntemi platformu, `version` çağıran platformun sayısından büyük veya buna eşit olmalıdır `Version` .
- Özniteliği için `[UnsupportedOSPlatform("platformVersion")]` , Guard yönteminin platformu, `version` çağıran platformun tarafından daha az veya eşit olmalıdır `Version` .

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

- Yeni API 'lerin kullanılabilir olmadığı Netstandard veya netcoreapp ' i hedefleyen bir kodu korumaya ihtiyacınız varsa, <xref:System.OperatingSystem> <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> Bu API kullanılabilir ve çözümleyici tarafından kullanılır. Ancak yeni API 'Ler eklendikçe en iyi duruma getirilmemiştir <xref:System.OperatingSystem> . Platformun yapıda desteklenmediği durumlarda <xref:System.Runtime.InteropServices.OSPlatform> , <xref:System.Runtime.InteropServices.OSPlatform.Create%2A?displayProperty=nameWithType> çözümleyici tarafından da kullanılan ("Platform") kullanabilirsiniz.

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

### <a name="mark-call-site-as-platform-specific"></a>Çağrı sitesini platforma özgü olarak işaretle

Platform adları çağıran platforma bağımlı API ile eşleşmelidir. Platform dizesi bir sürüm içeriyorsa:

- Özniteliği için `[SupportedOSPlatform("platformVersion")]` , çağrı sitesi platformu, `version` çağıran platformun en fazla veya daha büyük olması gerekir `Version`
- Özniteliği için `[UnsupportedOSPlatform("platformVersion")]` , çağıran site platformu, `version` çağıran platformun en fazla veya daha az olmalıdır `Version`

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

### <a name="assert-the-call-site-with-platform-check"></a>Platform denetimi ile çağrı sitesi onaylama

[Platform Guard örneklerinde](#guard-platform-specific-apis-with-guard-methods) kullanılan tüm koşullu denetimler için de koşul olarak kullanılabilir <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> .

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

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 5 ' te hedef çerçeve adları](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [Platforma özgü API 'Lere açıklama ekleme ve kullanımını algılama](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [API 'Leri belirli platformlarda desteklenmeyen şekilde açıklama ekleme](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [CA1416 platform uyumluluğu Çözümleyicisi](/visualstudio/code-quality/ca1416)
- [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md)
