---
description: 'Hakkında daha fazla bilgi edinin: .NET Genelleştirme ve ıCU'
title: Genelleştirme ve ICU
ms.date: 05/21/2020
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 9ff6219a06cb05c743089e56b379de1f98bbc42c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702268"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="0a2d7-103">.NET Genelleştirme ve ıCU</span><span class="sxs-lookup"><span data-stu-id="0a2d7-103">.NET globalization and ICU</span></span>

<span data-ttu-id="0a2d7-104">Geçmişte, .NET Genelleştirme API 'Leri farklı platformlarda farklı temel kitaplıklar kullandı.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-104">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="0a2d7-105">UNIX üzerinde, API 'Ler, [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)kullanıyordu ve Windows 'Ta [Ulusal DIL desteği (NLS)](/windows/win32/intl/national-language-support)kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-105">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="0a2d7-106">Bu, uygulamaları farklı platformlarda çalıştırırken genelleştirme API 'Leri ile ilgili bazı davranış farklılıklarıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-106">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="0a2d7-107">Davranış farklılıkları bu alanlarda önyüklendi:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-107">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="0a2d7-108">Kültürler ve kültür verileri</span><span class="sxs-lookup"><span data-stu-id="0a2d7-108">Cultures and culture data</span></span>
- <span data-ttu-id="0a2d7-109">Dize büyük harfleri</span><span class="sxs-lookup"><span data-stu-id="0a2d7-109">String casing</span></span>
- <span data-ttu-id="0a2d7-110">Dize sıralama ve arama</span><span class="sxs-lookup"><span data-stu-id="0a2d7-110">String sorting and searching</span></span>
- <span data-ttu-id="0a2d7-111">Anahtarları Sırala</span><span class="sxs-lookup"><span data-stu-id="0a2d7-111">Sort keys</span></span>
- <span data-ttu-id="0a2d7-112">Dize normalleştirme</span><span class="sxs-lookup"><span data-stu-id="0a2d7-112">String normalization</span></span>
- <span data-ttu-id="0a2d7-113">Uluslararası etki alanı adları (ıDN) desteği</span><span class="sxs-lookup"><span data-stu-id="0a2d7-113">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="0a2d7-114">Linux üzerinde saat dilimi görünen adı</span><span class="sxs-lookup"><span data-stu-id="0a2d7-114">Time zone display name on Linux</span></span>

<span data-ttu-id="0a2d7-115">.NET 5,0 ' den başlayarak, geliştiricilerin platformlar arası farklılıklara engel olmasını sağlayan temel alınan kitaplığın kullanıldığı daha fazla denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-115">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="0a2d7-116">Windows üzerinde ıCU</span><span class="sxs-lookup"><span data-stu-id="0a2d7-116">ICU on Windows</span></span>

<span data-ttu-id="0a2d7-117">Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri, işletim sisteminin bir parçası olarak [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) içerir ve .NET 5,0 ve sonraki sürümler varsayılan olarak ICU kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-117">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="0a2d7-118">Windows üzerinde çalışırken, .NET 5,0 ve sonraki sürümler yüklemeye çalışır `icu.dll` ve varsa Genelleştirme uygulamasında bu uygulamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-118">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and, if it's available, use it for the globalization implementation.</span></span> <span data-ttu-id="0a2d7-119">ICU kitaplığı bulunamazsa veya yüklenemezse (örneğin, Windows 'un eski sürümlerinde çalışırken), .NET 5,0 ve üzeri sürümler NLS tabanlı uygulamaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-119">If the ICU library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="0a2d7-120">ICU kullanırken bile,, `CurrentCulture` `CurrentUICulture` ve `CurrentRegion` üyeleri Kullanıcı ayarlarını kabul etmek için Windows Işletim sistemi API 'lerini kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-120">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="behavioral-differences"></a><span data-ttu-id="0a2d7-121">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="0a2d7-121">Behavioral differences</span></span>

<span data-ttu-id="0a2d7-122">Uygulamanızı .NET 5 hedefleyecek şekilde yükseltirseniz, Genelleştirme tesislerini kullandığınızı fark etmeseniz bile uygulamanızdaki değişiklikleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-122">If you upgrade your app to target .NET 5, you might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="0a2d7-123">Bu bölüm, görebileceğiniz davranış değişikliklerinden birini listeler, ancak diğerleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-123">This section lists one of the behavioral changes you might see, but there are others too.</span></span>

##### <a name="stringindexof"></a><span data-ttu-id="0a2d7-124">String. IndexOf</span><span class="sxs-lookup"><span data-stu-id="0a2d7-124">String.IndexOf</span></span>

<span data-ttu-id="0a2d7-125"><xref:System.String.IndexOf(System.String)?displayProperty=nameWithType>Bir dizedeki yeni satır karakterinin dizinini bulmak için çağıran aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-125">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="0a2d7-126">Önceki .NET sürümlerinde, kod parçacığı yazdırılır `6` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-126">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="0a2d7-127">.NET 5,0 ve sonraki sürümlerde Windows 10 ' da 2019 güncelleştirme ve sonraki sürümlerinde, kod parçacığı yazdırılır `-1` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-127">In .NET 5.0 and later versions on Windows 10 May 2019 Update and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="0a2d7-128">Kültüre duyarlı arama yerine bir sıralı arama gerçekleştirerek bu kodu onarmak için, <xref:System.String.IndexOf(System.String,System.StringComparison)> aşırı yüklemeyi çağırın ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-128">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="0a2d7-129">Kod çözümleme kurallarını [CA1307: açıklık ve CA1309 Için StringComparison belirtin](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) : kodunuzda bu çağrı sitelerini bulmak Için [sıralı StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-129">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="0a2d7-130">Daha fazla bilgi için bkz. [.NET 5 + üzerindeki dizeleri karşılaştırırken davranış değişiklikleri](../base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-130">For more information, see [Behavior changes when comparing strings on .NET 5+](../base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="use-nls-instead-of-icu"></a><span data-ttu-id="0a2d7-131">ICU yerine NLS kullanma</span><span class="sxs-lookup"><span data-stu-id="0a2d7-131">Use NLS instead of ICU</span></span>

<span data-ttu-id="0a2d7-132">NLS yerine ıCU kullanılması, Genelleştirme ile ilgili bazı işlemlerle davranış farklılıkları oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-132">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="0a2d7-133">Bir geliştirici, NLS 'yi kullanmaya geri dönmek için ıCU uygulamasını devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-133">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="0a2d7-134">Uygulamalar, aşağıdaki yollarla NLS modunu etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-134">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="0a2d7-135">Proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-135">In the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="0a2d7-136">`runtimeconfig.json` dosyasında:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-136">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- <span data-ttu-id="0a2d7-137">Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_USENLS` değeri veya değerine ayarlayarak `true` `1` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-137">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="0a2d7-138">Projede veya dosyada ayarlanan bir değer `runtimeconfig.json` , ortam değişkenine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-138">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="0a2d7-139">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../../core/run-time-config/globalization.md#nls).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-139">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="0a2d7-140">Uygulama-yerel ıCU</span><span class="sxs-lookup"><span data-stu-id="0a2d7-140">App-local ICU</span></span>

<span data-ttu-id="0a2d7-141">Her bir ıCU sürümü BT hata düzeltmelerinin yanı sıra dünyanın dillerini açıklayan güncelleştirilmiş ortak yerel ayar veri deposu (CLDR) verilerini de getirebilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-141">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="0a2d7-142">ICU sürümleri arasında geçiş yapmak, Genelleştirme ile ilgili işlemlere geldiğinde uygulama davranışını güvenle etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-142">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span> <span data-ttu-id="0a2d7-143">Uygulama geliştiricilerinin tüm dağıtımlarda tutarlılığın sağlanmasına yardımcı olmak için, .NET 5,0 ve sonraki sürümleri, hem Windows hem de UNIX üzerinde uygulamaların kendi ıU kopyalarını taşıması ve kullanması için olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-143">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="0a2d7-144">Uygulamalar, aşağıdaki yollarla bir App-Local ıCU uygulama modunu kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-144">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="0a2d7-145">Proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-145">In  the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- <span data-ttu-id="0a2d7-146">`runtimeconfig.json` dosyasında:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-146">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- <span data-ttu-id="0a2d7-147">Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` değeri veya değerine ayarlayarak `<suffix>:<version>` `<version>` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-147">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

  <span data-ttu-id="0a2d7-148">`<suffix>`: Genel ıCU paketleme kurallarından sonra, en çok 36 karakterden kısa isteğe bağlı sonek.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-148">`<suffix>`: Optional suffix of fewer than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="0a2d7-149">Özel bir ıU oluştururken, LIB adlarını ve dışarıya aktarılmış sembol adlarını bir sonek içerecek şekilde (örneğin, sonek) oluşturacak şekilde özelleştirebilirsiniz `libicuucmyapp` `myapp` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-149">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

  <span data-ttu-id="0a2d7-150">`<version>`: Geçerli bir ıCU sürümü (örneğin, 67,1).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-150">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="0a2d7-151">Bu sürüm, ikili dosyaları yüklemek ve içe aktarılmış sembolleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-151">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="0a2d7-152">Uygulama yerel anahtarı ayarlandığında ıCU 'yi yüklemek için, .NET <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> birden çok yolu yoklaan yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-152">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="0a2d7-153">Yöntemi ilk olarak, `NATIVE_DLL_SEARCH_DIRECTORIES` uygulamanın dosyasını temel alan DotNet ana bilgisayar tarafından oluşturulan özellikte kitaplığı bulmayı dener `deps.json` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-153">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="0a2d7-154">Daha fazla bilgi için bkz. [Varsayılan yoklama](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-154">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="0a2d7-155">Kendi içinde bulunan uygulamalar için, Kullanıcı tarafından özel bir eylem gerekmez, çünkü ıU 'nin uygulama dizininde olduğundan emin olun (kendi içindeki uygulamalar için, çalışma dizini varsayılan olarak ' dir `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-155">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="0a2d7-156">ICU 'yi bir NuGet paketi aracılığıyla kullanıyorsanız, bu, çerçeveye bağımlı uygulamalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-156">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="0a2d7-157">NuGet yerel varlıkları çözer ve bu dosyaları `deps.json` dosya ve uygulamanın çıkış dizinine dahil eder `runtimes` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-157">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="0a2d7-158">.NET onu buradan yükler.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-158">.NET loads it from there.</span></span>

<span data-ttu-id="0a2d7-159">IU 'nin yerel bir derlemeden kullanıldığı, çerçeveye bağımlı uygulamalar (kendi içinde olmayan) için ek adımlar gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-159">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="0a2d7-160">.NET SDK 'Sı henüz "gevşek" yerel ikililerinin içine dahil edilecek bir özelliğe sahip değildir `deps.json` ( [Bu SDK sorununa](https://github.com/dotnet/sdk/issues/11373)bakın).</span><span class="sxs-lookup"><span data-stu-id="0a2d7-160">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="0a2d7-161">Bunun yerine, uygulamanın proje dosyasına ek bilgiler ekleyerek bunu etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-161">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="0a2d7-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-162">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="0a2d7-163">Bu, desteklenen çalışma zamanları için tüm ıCU ikilileri için yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-163">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="0a2d7-164">Ayrıca, `NuGetPackageId` öğe grubundaki meta verilerin `RuntimeTargetsCopyLocalItems` projenin gerçekten başvurduğu bir NuGet paketiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-164">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="0a2d7-165">macOS davranışı</span><span class="sxs-lookup"><span data-stu-id="0a2d7-165">macOS behavior</span></span>

<span data-ttu-id="0a2d7-166">`macOS` , dosyasında Linux yükleyicinden farklı yükleme komutlarından bağımlı dinamik kitaplıkları çözümlemek için farklı bir davranışa sahiptir `match-o` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-166">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="0a2d7-167">Linux yükleyicisinde .NET, `libicudata` `libicuuc` `libicui18n` ICU bağımlılık grafiğini karşılamak için, ve (Bu sırada) deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-167">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="0a2d7-168">Ancak, macOS üzerinde bu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-168">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="0a2d7-169">MacOS üzerinde ıCU oluştururken, varsayılan olarak, ' de bu yükleme komutlarıyla bir dinamik kitaplık alacaksınız `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-169">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="0a2d7-170">Aşağıdaki kod parçacığında bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-170">The following snippet shows an example.</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="0a2d7-171">Bu komutlar yalnızca ıCU 'nin diğer bileşenleri için bağımlı kitaplıkların adına başvurur.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-171">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="0a2d7-172">Yükleyici `dlopen` , bu kitaplıkların sistem dizinlerinde olmasını veya `LD_LIBRARY_PATH` env VARS 'i ayarlamayı ya da uygulama düzeyi dizininde ICU 'nin olmasını kapsayan kuralları takip eden bir arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-172">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="0a2d7-173">`LD_LIBRARY_PATH`ICU ikililerinin uygulama düzeyi dizininde olmasını veya emin değilseniz, bazı ek işler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-173">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="0a2d7-174">Yükleyici için, gibi bazı yönergeler vardır. Bu, `@loader_path` yükleyiciye bu yük komutuyla aynı dizinde bu bağımlılığı aramasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-174">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="0a2d7-175">Bunu başarmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-175">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="0a2d7-176">Aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-176">Run the following commands:</span></span>

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- <span data-ttu-id="0a2d7-177">İle yüklenen adları oluşturmak için ıCU Patch `@loader_path`</span><span class="sxs-lookup"><span data-stu-id="0a2d7-177">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="0a2d7-178">Oto conf () çalıştırmadan önce `./runConfigureICU` [Bu satırları şu](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-178">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a><span data-ttu-id="0a2d7-179">WebAssembly üzerinde ıCU</span><span class="sxs-lookup"><span data-stu-id="0a2d7-179">ICU on WebAssembly</span></span>

<span data-ttu-id="0a2d7-180">ICU 'nin bir sürümü, özellikle WebAssembly iş yükleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-180">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="0a2d7-181">Bu sürüm, masaüstü profilleriyle Genelleştirme uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-181">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="0a2d7-182">ICU veri dosyasının boyutunu 24 MB 'den 1,4 MB 'ye (veya Brotli ile sıkıştırılmışsa ~ 0,3 MB) azaltmak için, bu iş yükünün bir sınırlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-182">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="0a2d7-183">Aşağıdaki API 'Ler desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-183">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="0a2d7-184">Aşağıdaki API 'Ler sınırlamalarla desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0a2d7-184">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="0a2d7-185"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> ve <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> nadiren kullanılan <xref:System.Text.NormalizationForm.FormKC> ve <xref:System.Text.NormalizationForm.FormKD> formları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-185"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="0a2d7-186"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> ile aynı değeri döndürür <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0a2d7-186"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0a2d7-187">Ayrıca, desteklenen yerel ayarların bir listesi [DotNet/ICU](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54)deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0a2d7-187">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
