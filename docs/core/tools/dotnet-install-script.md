---
title: DotNet yükleme betikleri
description: .NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için dotnet-yükleme betikleri hakkında bilgi edinin.
ms.date: 01/16/2019
ms.openlocfilehash: 5b266d484aae482d79674660417a834f03d53e4c
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362837"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="be07e-103">DotNet yükleme komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="be07e-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="be07e-104">Ad</span><span class="sxs-lookup"><span data-stu-id="be07e-104">Name</span></span>

<span data-ttu-id="be07e-105">`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="be07e-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be07e-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="be07e-106">Synopsis</span></span>

<span data-ttu-id="be07e-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="be07e-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="be07e-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="be07e-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="be07e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be07e-109">Description</span></span>

<span data-ttu-id="be07e-110">`dotnet-install` Betikleri, .NET Core CLI araçları ve paylaşılan çalışma zamanı içeren .NET Core SDK'sı yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be07e-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="be07e-111">Üzerinde barındırılan kararlı bir sürüm kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="be07e-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="be07e-112">Komut dosyalarını doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="be07e-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="be07e-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="be07e-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="be07e-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="be07e-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="be07e-115">Bu komut dosyaları ana kullanışlılığını Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be07e-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="be07e-116">İki betik vardır: bir Windows üzerinde çalışan bir PowerShell Betiği ve diğer Linux/Macos'ta çalışır bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="be07e-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="be07e-117">Her iki komut dosyaları aynı davranışa sahip.</span><span class="sxs-lookup"><span data-stu-id="be07e-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="be07e-118">Linux/macOS sistemlerde betiğiyle PowerShell anahtarları kullanabilmeniz için bash betiğini de PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="be07e-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="be07e-119">Yükleme betikleri CLI yapı bırakma öğelerini ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yükleme işlemine devam `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="be07e-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="be07e-120">Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="be07e-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="be07e-121">Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="be07e-121">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="be07e-122">Varsayılan olarak, betik geçerli oturum için $PATH için yükleme konumu ekler.</span><span class="sxs-lookup"><span data-stu-id="be07e-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="be07e-123">Bu varsayılan davranışı geçersiz kılma belirterek `--no-path` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="be07e-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="be07e-124">Betiği çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="be07e-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="be07e-125">Belirli bir sürümünü kullanarak bir yükleyebilirsiniz `--version` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="be07e-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="be07e-126">Sürüm, üç bölümden sürümü (örneğin, 1.0.0-13232) belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="be07e-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="be07e-127">Sağlanmazsa, kullandığı `latest` sürümü.</span><span class="sxs-lookup"><span data-stu-id="be07e-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="be07e-128">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be07e-128">Options</span></span>

* **`-Channel <CHANNEL>`**

  <span data-ttu-id="be07e-129">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="be07e-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="be07e-130">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="be07e-130">The possible values are:</span></span>

  * <span data-ttu-id="be07e-131">`Current` -En son sürüm.</span><span class="sxs-lookup"><span data-stu-id="be07e-131">`Current` - Most current release.</span></span>
  * <span data-ttu-id="be07e-132">`LTS` -Uzun süreli destek kanalı (en son desteklenen sürüm).</span><span class="sxs-lookup"><span data-stu-id="be07e-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  * <span data-ttu-id="be07e-133">İki parçalı sürümü belirli bir yayınını temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`).</span><span class="sxs-lookup"><span data-stu-id="be07e-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  * <span data-ttu-id="be07e-134">Dal adı.</span><span class="sxs-lookup"><span data-stu-id="be07e-134">Branch name.</span></span> <span data-ttu-id="be07e-135">Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` (için gecelik sürümleri için).</span><span class="sxs-lookup"><span data-stu-id="be07e-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="be07e-136">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="be07e-136">The default value is `LTS`.</span></span> <span data-ttu-id="be07e-137">.NET Destek kanalları hakkında daha fazla bilgi için bkz. [.NET desteği İlkesi](https://www.microsoft.com/net/platform/support-policy#dotnet-core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="be07e-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

* **`-Version <VERSION>`**

  <span data-ttu-id="be07e-138">Belirli bir yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be07e-138">Represents a specific build version.</span></span> <span data-ttu-id="be07e-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="be07e-139">The possible values are:</span></span>

  * <span data-ttu-id="be07e-140">`latest` -Kanal en son derleme (ile kullanılan `-Channel` seçeneği).</span><span class="sxs-lookup"><span data-stu-id="be07e-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  * <span data-ttu-id="be07e-141">`coherent` -Tutarlı yapıyı kanalındaki son; en son kararlı paket kullanır (Dal adı ile kullanılan `-Channel` seçenekleri).</span><span class="sxs-lookup"><span data-stu-id="be07e-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  * <span data-ttu-id="be07e-142">Üç bölümlü sürüm X.Y.Z biçiminde temsil eden belirli bir yapı sürümü; yerine geçen `-Channel` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="be07e-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="be07e-143">Örneğin: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="be07e-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="be07e-144">Belirtilmezse, `-Version` varsayılan olarak `latest`.</span><span class="sxs-lookup"><span data-stu-id="be07e-144">If not specified, `-Version` defaults to `latest`.</span></span>

* **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="be07e-145">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be07e-145">Specifies the installation path.</span></span> <span data-ttu-id="be07e-146">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be07e-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="be07e-147">Varsayılan değer *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="be07e-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="be07e-148">İkili dosyaları, doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="be07e-148">Binaries are placed directly in this directory.</span></span>

* **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="be07e-149">.NET Core ikili dosyaları yüklemek için Mimari.</span><span class="sxs-lookup"><span data-stu-id="be07e-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="be07e-150">Olası değerler `<auto>`, `amd64`, `x64`, `x86`, `arm64`, ve `arm`.</span><span class="sxs-lookup"><span data-stu-id="be07e-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="be07e-151">Varsayılan değer `<auto>`, şu anda çalışan işletim sistemi mimarisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be07e-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

* **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="be07e-152">Bu parametre kullanılmıyor ve betik gelecek bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="be07e-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="be07e-153">Önerilen alternatif `Runtime` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="be07e-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="be07e-154">Tüm SDK yalnızca paylaşılan çalışma zamanı BITS yükler.</span><span class="sxs-lookup"><span data-stu-id="be07e-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="be07e-155">Bu belirtmeye eşdeğerdir `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="be07e-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

* **`-Runtime <RUNTIME>`**

  <span data-ttu-id="be07e-156">Yalnızca paylaşılan çalışma zamanı, tüm SDK yükler.</span><span class="sxs-lookup"><span data-stu-id="be07e-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="be07e-157">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="be07e-157">The possible values are:</span></span>

  * <span data-ttu-id="be07e-158">`dotnet` - `Microsoft.NETCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="be07e-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  * <span data-ttu-id="be07e-159">`aspnetcore` - `Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="be07e-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

* **`-DryRun`**

  <span data-ttu-id="be07e-160">Ayarlanırsa, komut dosyası yükleme gerçekleştiremiyor varsa.</span><span class="sxs-lookup"><span data-stu-id="be07e-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="be07e-161">Bunun yerine, .NET Core CLI'ın şu anda istenen sürüm tutarlı bir şekilde yüklemek için kullanılacak hangi komut satırı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be07e-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="be07e-162">Örneğin, sürüm belirtirseniz `latest`, böylece bu komut, bir derleme betikte belirleyici kullanılabilir belirli bir sürümünü içeren bir bağlantı gösterir.</span><span class="sxs-lookup"><span data-stu-id="be07e-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="be07e-163">Yüklemek veya kendiniz indirmek isterseniz de ikili dosyanın konumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be07e-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

* **`-NoPath`**

  <span data-ttu-id="be07e-164">Kümesi, yükleme klasörünün yolu geçerli oturum için veriliyorsa değil.</span><span class="sxs-lookup"><span data-stu-id="be07e-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="be07e-165">Varsayılan olarak, komut dosyası CLI araçları yüklendikten sonra hemen kullanılabilmesini YOLUNU değiştirir.</span><span class="sxs-lookup"><span data-stu-id="be07e-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

* **`-Verbose`**

  <span data-ttu-id="be07e-166">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be07e-166">Displays diagnostics information.</span></span>

* **`-AzureFeed`**

  <span data-ttu-id="be07e-167">Yükleyici için akış URL'sini Azure belirtir.</span><span class="sxs-lookup"><span data-stu-id="be07e-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="be07e-168">Bu değer değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="be07e-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="be07e-169">Varsayılan değer `https://dotnetcli.azureedge.net/dotnet` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="be07e-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

* **`-UncachedFeed`**

  <span data-ttu-id="be07e-170">Bu yükleyici tarafından kullanılan önbelleğe alınmamış akış URL'sini değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="be07e-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="be07e-171">Bu değer değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="be07e-171">We recommended that you don't change this value.</span></span>

* **`-NoCdn`**

  <span data-ttu-id="be07e-172">İçinden indirme devre dışı bırakır [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ve önbelleğe alınmamış akışı doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="be07e-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

* **`-FeedCredential`**

  <span data-ttu-id="be07e-173">Akış Azure'a eklenecek sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be07e-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="be07e-174">Genel olmayan blob depolama hesaplarını kullanmak için URL'nin değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="be07e-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

* **`-ProxyAddress`**

  <span data-ttu-id="be07e-175">Kümesi, yükleyici web istekleri yaparken proxy kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="be07e-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="be07e-176">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="be07e-176">(Only valid for Windows)</span></span>

* **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="be07e-177">Proxy adresi kullanılırken geçerli kullanıcının kimlik bilgilerini ayarlama, yükleyici kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="be07e-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="be07e-178">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="be07e-178">(Only valid for Windows)</span></span>

* **`-SkipNonVersionedFiles`**

  <span data-ttu-id="be07e-179">Sürüm bilgisi olmayan dosyaları gibi yükleme atlar *dotnet.exe*, zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="be07e-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

* **`-Help`**

  <span data-ttu-id="be07e-180">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be07e-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="be07e-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="be07e-181">Examples</span></span>

* <span data-ttu-id="be07e-182">Desteklenen en son uzun vadeli (LTS) sürüm varsayılan konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="be07e-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="be07e-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="be07e-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="be07e-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="be07e-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* <span data-ttu-id="be07e-185">En son sürümü 2.0 kanaldan belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="be07e-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="be07e-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="be07e-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="be07e-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="be07e-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* <span data-ttu-id="be07e-188">Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:</span><span class="sxs-lookup"><span data-stu-id="be07e-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="be07e-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="be07e-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  <span data-ttu-id="be07e-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="be07e-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* <span data-ttu-id="be07e-191">Betiği almak ve 2.1.2'yi yükleyin (yalnızca Windows) kurumsal bir proxy'nin arkasında sürümü:</span><span class="sxs-lookup"><span data-stu-id="be07e-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* <span data-ttu-id="be07e-192">Betiği almak ve .NET Core CLI one-liner örnekleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="be07e-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="be07e-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="be07e-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="be07e-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="be07e-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="be07e-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be07e-195">See also</span></span>

* [<span data-ttu-id="be07e-196">.NET core sürümleri</span><span class="sxs-lookup"><span data-stu-id="be07e-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
* [<span data-ttu-id="be07e-197">Arşiv .NET core çalışma zamanı ve SDK'sını indirin</span><span class="sxs-lookup"><span data-stu-id="be07e-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
