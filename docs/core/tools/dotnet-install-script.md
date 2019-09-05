---
title: dotnet-install scripts
description: .NET Core CLI araçlarını ve paylaşılan çalışma zamanını yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 01/16/2019
ms.openlocfilehash: ed1a3341e678b405ae4aca35e3b49ada89eb069a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253906"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="f6259-103">DotNet-betiklerin başvurusunu yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="f6259-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="f6259-104">Ad</span><span class="sxs-lookup"><span data-stu-id="f6259-104">Name</span></span>

<span data-ttu-id="f6259-105">`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core CLI araçları ve paylaşılan çalışma zamanını yüklemek için kullanılan betik.</span><span class="sxs-lookup"><span data-stu-id="f6259-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6259-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="f6259-106">Synopsis</span></span>

<span data-ttu-id="f6259-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="f6259-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="f6259-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f6259-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="f6259-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6259-109">Description</span></span>

<span data-ttu-id="f6259-110">`dotnet-install` Betikler, .NET Core CLI araçlarını ve paylaşılan çalışma zamanını içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6259-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="f6259-111">[.NET Core ana web sitesinde](https://dot.net)barındırılan kararlı sürümü kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f6259-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="f6259-112">Betiklerin doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f6259-112">The direct paths to the scripts are:</span></span>

- <span data-ttu-id="f6259-113"><https://dot.net/v1/dotnet-install.sh>(Bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="f6259-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
- <span data-ttu-id="f6259-114"><https://dot.net/v1/dotnet-install.ps1>(PowerShell, Windows)</span><span class="sxs-lookup"><span data-stu-id="f6259-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="f6259-115">Bu betiklerin temel kullanışlılığı Otomasyon senaryolarında ve yönetici olmayan yüklemelerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f6259-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="f6259-116">İki komut dosyası vardır: biri Windows üzerinde çalışan bir PowerShell betiğtir ve diğeri de Linux/macOS üzerinde çalışan bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f6259-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="f6259-117">Her iki komut dosyası da aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f6259-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="f6259-118">Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6259-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="f6259-119">Yükleme betikleri, ZIP/tarbol dosyasını CLı derleme bırakmalarından indirir ve varsayılan konuma ya da tarafından `-InstallDir|--install-dir`belirtilen bir konuma yüklemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="f6259-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="f6259-120">Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="f6259-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="f6259-121">Yalnızca paylaşılan çalışma zamanını elde etmek istiyorsanız, `--runtime` bağımsız değişkenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6259-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="f6259-122">Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler.</span><span class="sxs-lookup"><span data-stu-id="f6259-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="f6259-123">`--no-path` Bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="f6259-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="f6259-124">Betiği çalıştırmadan önce gerekli [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="f6259-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="f6259-125">`--version` Bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6259-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="f6259-126">Sürüm üç bölümlü bir sürüm olarak belirtilmelidir (örneğin, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="f6259-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="f6259-127">Sağlanmazsa, `latest` sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6259-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="f6259-128">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f6259-128">Options</span></span>

- **`-Channel <CHANNEL>`**

  <span data-ttu-id="f6259-129">Yükleme için kaynak kanalını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6259-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="f6259-130">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f6259-130">The possible values are:</span></span>

  - <span data-ttu-id="f6259-131">`Current`-En güncel sürüm.</span><span class="sxs-lookup"><span data-stu-id="f6259-131">`Current` - Most current release.</span></span>
  - <span data-ttu-id="f6259-132">`LTS`-Uzun süreli destek kanalı (desteklenen en güncel sürüm).</span><span class="sxs-lookup"><span data-stu-id="f6259-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="f6259-133">Belirli bir yayını temsil eden X. Y biçimindeki iki bölümlü sürüm (örneğin, `2.0` veya `1.0`).</span><span class="sxs-lookup"><span data-stu-id="f6259-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  - <span data-ttu-id="f6259-134">Dal adı.</span><span class="sxs-lookup"><span data-stu-id="f6259-134">Branch name.</span></span> <span data-ttu-id="f6259-135">Örneğin `release/2.0.0` `master` ,, veya (gecelik yayınlar için). `release/2.0.0-preview2`</span><span class="sxs-lookup"><span data-stu-id="f6259-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="f6259-136">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f6259-136">The default value is `LTS`.</span></span> <span data-ttu-id="f6259-137">.NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://www.microsoft.com/net/platform/support-policy#dotnet-core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="f6259-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

- **`-Version <VERSION>`**

  <span data-ttu-id="f6259-138">Belirli bir derleme sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6259-138">Represents a specific build version.</span></span> <span data-ttu-id="f6259-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f6259-139">The possible values are:</span></span>

  - <span data-ttu-id="f6259-140">`latest`-Kanalda en son derleme ( `-Channel` seçeneğiyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="f6259-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="f6259-141">`coherent`-Kanalda en son tutarlı derleme; en son kararlı paket birleşimini kullanır (dal adı `-Channel` seçenekleriyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="f6259-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="f6259-142">Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; `-Channel` seçeneğinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="f6259-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="f6259-143">Örneğin: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="f6259-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="f6259-144">Belirtilmemişse, `-Version` varsayılan olarak `latest`olur.</span><span class="sxs-lookup"><span data-stu-id="f6259-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="f6259-145">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6259-145">Specifies the installation path.</span></span> <span data-ttu-id="f6259-146">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6259-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="f6259-147">Varsayılan değer *%LocalAppData%\microsoft\dotnet*değeridir.</span><span class="sxs-lookup"><span data-stu-id="f6259-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="f6259-148">İkili dosyalar doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f6259-148">Binaries are placed directly in this directory.</span></span>

- **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="f6259-149">Yüklenecek .NET Core ikililerinin mimarisi.</span><span class="sxs-lookup"><span data-stu-id="f6259-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="f6259-150">Olası değerler şunlardır `<auto>` `amd64` ,,`x64`,, ve .`arm` `x86` `arm64`</span><span class="sxs-lookup"><span data-stu-id="f6259-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="f6259-151">Varsayılan değer `<auto>`, çalışmakta olan işletim sistemi mimarisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6259-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="f6259-152">Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6259-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="f6259-153">Önerilen alternatif `Runtime` , seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f6259-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="f6259-154">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar.</span><span class="sxs-lookup"><span data-stu-id="f6259-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="f6259-155">Bu, belirtmeye `-Runtime dotnet`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f6259-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

- **`-Runtime <RUNTIME>`**

  <span data-ttu-id="f6259-156">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar.</span><span class="sxs-lookup"><span data-stu-id="f6259-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="f6259-157">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f6259-157">The possible values are:</span></span>

  - <span data-ttu-id="f6259-158">`dotnet``Microsoft.NETCore.App` -paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="f6259-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="f6259-159">`aspnetcore``Microsoft.AspNetCore.App` -paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="f6259-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

- **`-DryRun`**

  <span data-ttu-id="f6259-160">Ayarlanırsa, betik yüklemeyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f6259-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="f6259-161">Bunun yerine, .NET Core CLI Şu anda istenen sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6259-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="f6259-162">Örneğin, sürümünü `latest`belirtirseniz, bu komutun bir yapı betiğine göre belirleyici olarak kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6259-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="f6259-163">Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6259-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath`**

  <span data-ttu-id="f6259-164">Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="f6259-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="f6259-165">Varsayılan olarak, komut dosyası yolu değiştirir ve bu, CLı araçlarının yüklemeden hemen sonra kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6259-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose`**

  <span data-ttu-id="f6259-166">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6259-166">Displays diagnostics information.</span></span>

- **`-AzureFeed`**

  <span data-ttu-id="f6259-167">Yükleyicideki Azure akışına ait URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6259-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="f6259-168">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="f6259-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="f6259-169">Varsayılan değer `https://dotnetcli.azureedge.net/dotnet` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f6259-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed`**

  <span data-ttu-id="f6259-170">Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="f6259-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="f6259-171">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="f6259-171">We recommended that you don't change this value.</span></span>

- **`-NoCdn`**

  <span data-ttu-id="f6259-172">[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6259-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential`**

  <span data-ttu-id="f6259-173">Azure akışına eklemek için sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6259-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="f6259-174">Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6259-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="f6259-175">Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6259-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="f6259-176">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="f6259-176">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="f6259-177">Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6259-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="f6259-178">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="f6259-178">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles`**

  <span data-ttu-id="f6259-179">Zaten varsa *DotNet. exe*gibi sürümlenmemiş dosyaları yüklemeyi atlar.</span><span class="sxs-lookup"><span data-stu-id="f6259-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help`**

  <span data-ttu-id="f6259-180">Betiğe yönelik yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f6259-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="f6259-181">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f6259-181">Examples</span></span>

- <span data-ttu-id="f6259-182">En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="f6259-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="f6259-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="f6259-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="f6259-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f6259-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="f6259-185">2,0 kanaldan en son sürümü belirtilen konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="f6259-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="f6259-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="f6259-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="f6259-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f6259-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- <span data-ttu-id="f6259-188">Paylaşılan çalışma zamanının 1.1.0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="f6259-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="f6259-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="f6259-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="f6259-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f6259-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- <span data-ttu-id="f6259-191">Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="f6259-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="f6259-192">Tek bir Oluşturucu örnek .NET Core CLI betiği alın ve yüklemeyi yapın:</span><span class="sxs-lookup"><span data-stu-id="f6259-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="f6259-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="f6259-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="f6259-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f6259-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="f6259-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6259-195">See also</span></span>

- [<span data-ttu-id="f6259-196">.NET Core yayınları</span><span class="sxs-lookup"><span data-stu-id="f6259-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="f6259-197">.NET Core çalışma zamanı ve SDK indirme Arşivi</span><span class="sxs-lookup"><span data-stu-id="f6259-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
