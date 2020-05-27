---
title: Genelleştirme ve ıCU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 6ea848d4a60069e6702b9d60fd90a55f572fb043
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842529"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="e2180-102">.NET Genelleştirme ve ıCU</span><span class="sxs-lookup"><span data-stu-id="e2180-102">.NET globalization and ICU</span></span>

<span data-ttu-id="e2180-103">Geçmişte, .NET Genelleştirme API 'Leri farklı platformlarda farklı temel kitaplıklar kullandı.</span><span class="sxs-lookup"><span data-stu-id="e2180-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="e2180-104">UNIX üzerinde, API 'Ler, [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)kullanıyordu ve Windows 'Ta [Ulusal DIL desteği (NLS)](/windows/win32/intl/national-language-support)kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="e2180-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="e2180-105">Bu, uygulamaları farklı platformlarda çalıştırırken genelleştirme API 'Leri ile ilgili bazı davranış farklılıklarıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e2180-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="e2180-106">Davranış farklılıkları bu alanlarda önyüklendi:</span><span class="sxs-lookup"><span data-stu-id="e2180-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="e2180-107">Kültürler ve kültür verileri</span><span class="sxs-lookup"><span data-stu-id="e2180-107">Cultures and culture data</span></span>
- <span data-ttu-id="e2180-108">Dize büyük harfleri</span><span class="sxs-lookup"><span data-stu-id="e2180-108">String casing</span></span>
- <span data-ttu-id="e2180-109">Dize sıralama ve arama</span><span class="sxs-lookup"><span data-stu-id="e2180-109">String sorting and searching</span></span>
- <span data-ttu-id="e2180-110">Anahtarları Sırala</span><span class="sxs-lookup"><span data-stu-id="e2180-110">Sort keys</span></span>
- <span data-ttu-id="e2180-111">Dize normalleştirme</span><span class="sxs-lookup"><span data-stu-id="e2180-111">String normalization</span></span>
- <span data-ttu-id="e2180-112">Uluslararası etki alanı adları (ıDN) desteği</span><span class="sxs-lookup"><span data-stu-id="e2180-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="e2180-113">Linux üzerinde saat dilimi görünen adı</span><span class="sxs-lookup"><span data-stu-id="e2180-113">Time zone display name on Linux</span></span>

<span data-ttu-id="e2180-114">.NET 5,0 ' den başlayarak, geliştiricilerin platformlar arası farklılıklara engel olmasını sağlayan temel alınan kitaplığın kullanıldığı daha fazla denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="e2180-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="e2180-115">Windows üzerinde ıCU</span><span class="sxs-lookup"><span data-stu-id="e2180-115">ICU on Windows</span></span>

<span data-ttu-id="e2180-116">Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri, işletim sisteminin bir parçası olarak [ICU. dll dosyasını](/windows/win32/intl/international-components-for-unicode--icu-) içerir ve .NET 5,0 ve sonraki sürümleri varsayılan olarak ICU kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2180-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="e2180-117">Windows üzerinde çalışırken, .NET 5,0 ve sonraki sürümler yüklemeye çalışır `icu.dll` ve varsa Genelleştirme uygulamasında bu uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2180-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and if it's available, uses it for the globalization implementation.</span></span>  <span data-ttu-id="e2180-118">Bu kitaplık bulunamazsa veya yüklenemezse (örneğin, Windows 'un eski sürümlerinde çalışırken), .NET 5,0 ve üzeri sürümler NLS tabanlı uygulamaya geri döner.</span><span class="sxs-lookup"><span data-stu-id="e2180-118">If that library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="e2180-119">ICU kullanırken bile,, `CurrentCulture` `CurrentUICulture` ve `CurrentRegion` üyeleri Kullanıcı ayarlarını kabul etmek için Windows Işletim sistemi API 'lerini kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e2180-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="using-nls-instead-of-icu"></a><span data-ttu-id="e2180-120">ICU yerine NLS kullanma</span><span class="sxs-lookup"><span data-stu-id="e2180-120">Using NLS instead of ICU</span></span>

<span data-ttu-id="e2180-121">NLS yerine ıCU kullanılması, Genelleştirme ile ilgili bazı işlemlerle davranış farklılıkları oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2180-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="e2180-122">Bir geliştirici, NLS 'yi kullanmaya geri dönmek için ıCU uygulamasını devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2180-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="e2180-123">Uygulamalar, aşağıdaki yollarla NLS modunu etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="e2180-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="e2180-124">Proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="e2180-124">In the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- <span data-ttu-id="e2180-125">`runtimeconfig.json` dosyasında:</span><span class="sxs-lookup"><span data-stu-id="e2180-125">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- <span data-ttu-id="e2180-126">Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_USENLS` değeri veya değerine ayarlayarak `true` `1` .</span><span class="sxs-lookup"><span data-stu-id="e2180-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="e2180-127">Projede veya dosyada ayarlanan bir değer `runtimeconfig.json` , ortam değişkenine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e2180-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="e2180-128">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../../core/run-time-config/globalization.md#nls).</span><span class="sxs-lookup"><span data-stu-id="e2180-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="e2180-129">Uygulama-yerel ıCU</span><span class="sxs-lookup"><span data-stu-id="e2180-129">App-local ICU</span></span>

<span data-ttu-id="e2180-130">Her bir ıCU sürümü BT hata düzeltmelerinin yanı sıra dünyanın dillerini açıklayan güncelleştirilmiş ortak yerel ayar veri deposu (CLDR) verilerini de getirebilir.</span><span class="sxs-lookup"><span data-stu-id="e2180-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="e2180-131">ICU sürümleri arasında geçiş yapmak, Genelleştirme ile ilgili işlemlere geldiğinde uygulama davranışını güvenle etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e2180-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span>  <span data-ttu-id="e2180-132">Uygulama geliştiricilerinin tüm dağıtımlarda tutarlılığın sağlanmasına yardımcı olmak için, .NET 5,0 ve sonraki sürümleri, hem Windows hem de UNIX üzerinde uygulamaların kendi ıU kopyalarını taşıması ve kullanması için olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2180-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="e2180-133">Uygulamalar, aşağıdaki yollarla bir App-Local ıCU uygulama modunu kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="e2180-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="e2180-134">Proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="e2180-134">In  the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- <span data-ttu-id="e2180-135">`runtimeconfig.json` dosyasında:</span><span class="sxs-lookup"><span data-stu-id="e2180-135">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- <span data-ttu-id="e2180-136">Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` değeri veya değerine ayarlayarak `<suffix>:<version>` `<version>` .</span><span class="sxs-lookup"><span data-stu-id="e2180-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

<span data-ttu-id="e2180-137">`<suffix>`: Genel ıCU paketleme kurallarından sonra, 36 karakterden daha az karakter uzunluğunda isteğe bağlı son ek.</span><span class="sxs-lookup"><span data-stu-id="e2180-137">`<suffix>`: Optional suffix of less than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="e2180-138">Özel bir ıU oluştururken, LIB adlarını ve dışarıya aktarılmış sembol adlarını bir sonek içerecek şekilde (örneğin, sonek) oluşturacak şekilde özelleştirebilirsiniz `libicuucmyapp` `myapp` .</span><span class="sxs-lookup"><span data-stu-id="e2180-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

<span data-ttu-id="e2180-139">`<version>`: Geçerli bir ıCU sürümü (örneğin, 67,1).</span><span class="sxs-lookup"><span data-stu-id="e2180-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="e2180-140">Bu sürüm, ikili dosyaları yüklemek ve içe aktarılmış sembolleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2180-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="e2180-141">Uygulama yerel anahtarı ayarlandığında ıCU 'yi yüklemek için, .NET <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> birden çok yolu yoklaan yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2180-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="e2180-142">Yöntemi ilk olarak, `NATIVE_DLL_SEARCH_DIRECTORIES` uygulamanın dosyasını temel alan DotNet ana bilgisayar tarafından oluşturulan özellikte kitaplığı bulmayı dener `deps.json` .</span><span class="sxs-lookup"><span data-stu-id="e2180-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="e2180-143">Daha fazla bilgi için bkz. [Varsayılan yoklama](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="e2180-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="e2180-144">Kendi içinde bulunan uygulamalar için, Kullanıcı tarafından özel bir eylem gerekmez, çünkü ıU 'nin uygulama dizininde olduğundan emin olun (kendi içindeki uygulamalar için, çalışma dizini varsayılan olarak ' dir `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="e2180-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="e2180-145">ICU 'yi bir NuGet paketi aracılığıyla kullanıyorsanız, bu, çerçeveye bağımlı uygulamalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2180-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="e2180-146">NuGet yerel varlıkları çözer ve bu dosyaları `deps.json` dosya ve uygulamanın çıkış dizinine dahil eder `runtimes` .</span><span class="sxs-lookup"><span data-stu-id="e2180-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="e2180-147">.NET onu buradan yükler.</span><span class="sxs-lookup"><span data-stu-id="e2180-147">.NET loads it from there.</span></span>

<span data-ttu-id="e2180-148">IU 'nin yerel bir derlemeden kullanıldığı, çerçeveye bağımlı uygulamalar (kendi içinde olmayan) için ek adımlar gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2180-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="e2180-149">.NET SDK 'Sı henüz "gevşek" yerel ikililerinin içine dahil edilecek bir özelliğe sahip değildir `deps.json` ( [Bu SDK sorununa](https://github.com/dotnet/sdk/issues/11373)bakın).</span><span class="sxs-lookup"><span data-stu-id="e2180-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="e2180-150">Bunun yerine, uygulamanın proje dosyasına ek bilgiler ekleyerek bunu etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2180-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="e2180-151">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e2180-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="e2180-152">Bu, desteklenen çalışma zamanları için tüm ıCU ikilileri için yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2180-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="e2180-153">Ayrıca, `NuGetPackageId` öğe grubundaki meta verilerin `RuntimeTargetsCopyLocalItems` projenin gerçekten başvurduğu bir NuGet paketiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2180-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="e2180-154">macOS davranışı</span><span class="sxs-lookup"><span data-stu-id="e2180-154">macOS behavior</span></span>

<span data-ttu-id="e2180-155">`macOS`, dosyasında Linux yükleyicinden farklı yükleme komutlarından bağımlı dinamik kitaplıkları çözümlemek için farklı bir davranışa sahiptir `match-o` .</span><span class="sxs-lookup"><span data-stu-id="e2180-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="e2180-156">Linux yükleyicisinde .NET, `libicudata` `libicuuc` `libicui18n` ICU bağımlılık grafiğini karşılamak için, ve (Bu sırada) deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="e2180-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="e2180-157">Ancak, macOS üzerinde bu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e2180-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="e2180-158">MacOS üzerinde ıCU oluştururken, varsayılan olarak, ' de bu yükleme komutlarıyla bir dinamik kitaplık alacaksınız `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="e2180-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="e2180-159">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2180-159">For example.:</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="e2180-160">Bu komutlar yalnızca ıCU 'nin diğer bileşenleri için bağımlı kitaplıkların adına başvurur.</span><span class="sxs-lookup"><span data-stu-id="e2180-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="e2180-161">Yükleyici `dlopen` , bu kitaplıkların sistem dizinlerinde olmasını veya `LD_LIBRARY_PATH` env VARS 'i ayarlamayı ya da uygulama düzeyi dizininde ICU 'nin olmasını kapsayan kuralları takip eden bir arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e2180-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="e2180-162">`LD_LIBRARY_PATH`ICU ikililerinin uygulama düzeyi dizininde olmasını veya emin değilseniz, bazı ek işler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2180-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="e2180-163">Yükleyici için, gibi bazı yönergeler vardır. Bu, `@loader_path` yükleyiciye bu yük komutuyla aynı dizinde bu bağımlılığı aramasını söyler.</span><span class="sxs-lookup"><span data-stu-id="e2180-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="e2180-164">Bunu başarmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="e2180-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="e2180-165">Aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e2180-165">Run the following commands:</span></span>

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- <span data-ttu-id="e2180-166">İle yüklenen adları oluşturmak için ıCU Patch`@loader_path`</span><span class="sxs-lookup"><span data-stu-id="e2180-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="e2180-167">Oto conf () çalıştırmadan önce `./runConfigureICU` [Bu satırları şu](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e2180-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
