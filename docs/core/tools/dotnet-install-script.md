---
title: dotnet-install scripts
description: .NET Core SDK ve paylaşılan çalışma zamanını yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092869"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="696cd-103">DotNet-betiklerin başvurusunu yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="696cd-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="696cd-104">Name</span><span class="sxs-lookup"><span data-stu-id="696cd-104">Name</span></span>

<span data-ttu-id="696cd-105">`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core SDK ve paylaşılan çalışma zamanını yüklemek için kullanılan betik.</span><span class="sxs-lookup"><span data-stu-id="696cd-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="696cd-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="696cd-106">Synopsis</span></span>

<span data-ttu-id="696cd-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="696cd-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="696cd-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="696cd-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="696cd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="696cd-109">Description</span></span>

<span data-ttu-id="696cd-110">`dotnet-install` betikler, .NET Core CLI ve paylaşılan çalışma zamanını içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="696cd-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="696cd-111">Betiklerin kararlı sürümünü kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="696cd-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="696cd-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="696cd-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="696cd-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="696cd-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="696cd-114">Bu betiklerin temel kullanışlılığı Otomasyon senaryolarında ve yönetici olmayan yüklemelerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="696cd-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="696cd-115">İki komut dosyası vardır: biri Windows üzerinde çalışan bir PowerShell betiğtir ve diğeri de Linux/macOS üzerinde çalışan bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="696cd-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="696cd-116">Her iki komut dosyası da aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="696cd-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="696cd-117">Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="696cd-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="696cd-118">Yükleme betikleri, ZIP/tarbol dosyasını CLı derleme bırakmalarından indirir ve varsayılan konuma veya `-InstallDir|--install-dir`tarafından belirtilen bir konuma yüklemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="696cd-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="696cd-119">Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="696cd-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="696cd-120">Yalnızca paylaşılan çalışma zamanını almak istiyorsanız `-Runtime|--runtime` bağımsız değişkenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="696cd-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="696cd-121">Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler.</span><span class="sxs-lookup"><span data-stu-id="696cd-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="696cd-122">`-NoPath|--no-path` bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="696cd-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="696cd-123">Betiği çalıştırmadan önce gerekli [bağımlılıkları](../install/dependencies.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="696cd-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="696cd-124">`-Version|--version` bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="696cd-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="696cd-125">Sürüm üç bölümlü bir sürüm olarak belirtilmelidir (örneğin, `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="696cd-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="696cd-126">Sağlanmazsa, `latest` sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="696cd-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="696cd-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="696cd-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="696cd-128">Yükleme için kaynak kanalını belirtir.</span><span class="sxs-lookup"><span data-stu-id="696cd-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="696cd-129">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="696cd-129">The possible values are:</span></span>

  - <span data-ttu-id="696cd-130">`Current`-en güncel sürüm.</span><span class="sxs-lookup"><span data-stu-id="696cd-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="696cd-131">`LTS`-uzun süreli destek kanalı (desteklenen en güncel sürüm).</span><span class="sxs-lookup"><span data-stu-id="696cd-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="696cd-132">Belirli bir yayını temsil eden X. Y biçimindeki iki bölümden oluşan sürüm (örneğin, `2.1` veya `3.0`).</span><span class="sxs-lookup"><span data-stu-id="696cd-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="696cd-133">Dal adı: Örneğin, `release/3.1.1xx` veya `master` (gecelik yayınlar için).</span><span class="sxs-lookup"><span data-stu-id="696cd-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="696cd-134">Bir önizleme kanalından sürüm yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="696cd-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="696cd-135">Bir kanalın adını [yükleyiciler ve Ikili dosyalar](https://github.com/dotnet/core-sdk#installers-and-binaries)bölümünde listelendiği şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="696cd-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="696cd-136">Varsayılan değer: `LTS`.</span><span class="sxs-lookup"><span data-stu-id="696cd-136">The default value is `LTS`.</span></span> <span data-ttu-id="696cd-137">.NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="696cd-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="696cd-138">Belirli bir derleme sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="696cd-138">Represents a specific build version.</span></span> <span data-ttu-id="696cd-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="696cd-139">The possible values are:</span></span>

  - <span data-ttu-id="696cd-140">`latest`-kanalda en son derleme (`-Channel` seçeneğiyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="696cd-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="696cd-141">`coherent`-kanalda en son tutarlı derleme; en son kararlı paket birleşimini kullanır (dal adı `-Channel` seçenekleriyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="696cd-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="696cd-142">Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; `-Channel` seçeneğinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="696cd-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="696cd-143">Örneğin: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="696cd-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="696cd-144">Belirtilmemişse, varsayılan olarak `latest``-Version`.</span><span class="sxs-lookup"><span data-stu-id="696cd-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="696cd-145">SDK sürümünü belirlemekte kullanılacak [Global. JSON](global-json.md) dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="696cd-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="696cd-146">*Global. JSON* dosyası `sdk:version`için bir değere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="696cd-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="696cd-147">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="696cd-147">Specifies the installation path.</span></span> <span data-ttu-id="696cd-148">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="696cd-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="696cd-149">Varsayılan değer *%LocalAppData%\microsoft\dotnet*değeridir.</span><span class="sxs-lookup"><span data-stu-id="696cd-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="696cd-150">İkili dosyalar doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="696cd-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="696cd-151">Yüklenecek .NET Core ikililerinin mimarisi.</span><span class="sxs-lookup"><span data-stu-id="696cd-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="696cd-152">Olası değerler şunlardır `<auto>`, `amd64`, `x64`, `x86`, `arm64`ve `arm`.</span><span class="sxs-lookup"><span data-stu-id="696cd-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="696cd-153">Varsayılan değer, çalışmakta olan işletim sistemi mimarisini temsil eden `<auto>`.</span><span class="sxs-lookup"><span data-stu-id="696cd-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="696cd-154">Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="696cd-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="696cd-155">Önerilen alternatif `-Runtime|--runtime` seçenektir.</span><span class="sxs-lookup"><span data-stu-id="696cd-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="696cd-156">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar.</span><span class="sxs-lookup"><span data-stu-id="696cd-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="696cd-157">Bu seçenek `-Runtime|--runtime dotnet`belirtmeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="696cd-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="696cd-158">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar.</span><span class="sxs-lookup"><span data-stu-id="696cd-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="696cd-159">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="696cd-159">The possible values are:</span></span>

  - <span data-ttu-id="696cd-160">`dotnet`-`Microsoft.NETCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="696cd-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="696cd-161">`aspnetcore`-`Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="696cd-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="696cd-162">`windowsdesktop`-`Microsoft.WindowsDesktop.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="696cd-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="696cd-163">Ayarlanırsa, betik yüklemeyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="696cd-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="696cd-164">Bunun yerine, .NET Core CLI Şu anda istenen sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="696cd-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="696cd-165">Örneğin, sürüm `latest`belirtirseniz, bu komutun bir yapı betiğine göre belirlenebilir şekilde kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="696cd-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="696cd-166">Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.</span><span class="sxs-lookup"><span data-stu-id="696cd-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="696cd-167">Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="696cd-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="696cd-168">Varsayılan olarak, komut dosyası yolu değiştirir ve bu, .NET Core CLI yüklemeden hemen sonra kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="696cd-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="696cd-169">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="696cd-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="696cd-170">Yükleyicideki Azure akışına ait URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="696cd-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="696cd-171">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="696cd-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="696cd-172">Varsayılan değer: `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="696cd-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="696cd-173">Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="696cd-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="696cd-174">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="696cd-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="696cd-175">[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="696cd-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="696cd-176">Azure akışına eklemek için sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="696cd-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="696cd-177">Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="696cd-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="696cd-178">Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="696cd-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="696cd-179">Taşınabilir Linux için `linux-x64` kullanın.</span><span class="sxs-lookup"><span data-stu-id="696cd-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="696cd-180">(Yalnızca Linux/macOS için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="696cd-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="696cd-181">Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="696cd-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="696cd-182">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="696cd-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="696cd-183">Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="696cd-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="696cd-184">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="696cd-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="696cd-185">Zaten varsa *DotNet. exe*gibi sürümlenmemiş dosyaları yüklemeyi atlar.</span><span class="sxs-lookup"><span data-stu-id="696cd-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="696cd-186">Betiğe yönelik yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="696cd-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="696cd-187">Örnekler</span><span class="sxs-lookup"><span data-stu-id="696cd-187">Examples</span></span>

- <span data-ttu-id="696cd-188">En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="696cd-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="696cd-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="696cd-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="696cd-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="696cd-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="696cd-191">3,1 kanaldan en son sürümü belirtilen konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="696cd-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="696cd-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="696cd-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="696cd-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="696cd-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="696cd-194">Paylaşılan çalışma zamanının 3.0.0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="696cd-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="696cd-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="696cd-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="696cd-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="696cd-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="696cd-197">Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="696cd-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="696cd-198">Tek bir Oluşturucu örnek .NET Core CLI betiği alın ve yüklemeyi yapın:</span><span class="sxs-lookup"><span data-stu-id="696cd-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="696cd-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="696cd-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="696cd-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="696cd-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="696cd-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="696cd-201">See also</span></span>

- [<span data-ttu-id="696cd-202">.NET Core yayınları</span><span class="sxs-lookup"><span data-stu-id="696cd-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="696cd-203">.NET Core çalışma zamanı ve SDK indirme Arşivi</span><span class="sxs-lookup"><span data-stu-id="696cd-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
