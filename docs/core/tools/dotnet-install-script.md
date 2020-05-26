---
title: dotnet-install scripts
description: .NET Core SDK ve paylaşılan çalışma zamanını yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 04/30/2020
ms.openlocfilehash: 9f5cef9cfcca1d8b344021efe803c063a7393f8e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802717"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="a4116-103">DotNet-betiklerin başvurusunu yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="a4116-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="a4116-104">Name</span><span class="sxs-lookup"><span data-stu-id="a4116-104">Name</span></span>

<span data-ttu-id="a4116-105">`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core SDK ve paylaşılan çalışma zamanını yüklemek için kullanılan betik.</span><span class="sxs-lookup"><span data-stu-id="a4116-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a4116-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="a4116-106">Synopsis</span></span>

<span data-ttu-id="a4116-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4116-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="a4116-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="a4116-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="a4116-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4116-109">Description</span></span>

<span data-ttu-id="a4116-110">`dotnet-install`Betikler, .NET Core CLI ve paylaşılan çalışma zamanını içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4116-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="a4116-111">Betiklerin kararlı sürümünü kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="a4116-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="a4116-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="a4116-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="a4116-113">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="a4116-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="a4116-114">Bu betiklerin temel kullanışlılığı Otomasyon senaryolarında ve yönetici olmayan yüklemelerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a4116-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="a4116-115">İki komut dosyası vardır: biri Windows üzerinde çalışan bir PowerShell betiğtir ve diğeri de Linux/macOS üzerinde çalışan bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4116-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="a4116-116">Her iki komut dosyası da aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a4116-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="a4116-117">Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4116-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="a4116-118">Yükleme betikleri, ZIP/tarbol dosyasını CLı derleme bırakmalarından indirir ve varsayılan konuma ya da tarafından belirtilen bir konuma yüklemeye devam edebilir `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="a4116-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="a4116-119">Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="a4116-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="a4116-120">Yalnızca paylaşılan çalışma zamanını elde etmek istiyorsanız, `-Runtime|--runtime` bağımsız değişkenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a4116-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="a4116-121">Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler.</span><span class="sxs-lookup"><span data-stu-id="a4116-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="a4116-122">Bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın `-NoPath|--no-path` .</span><span class="sxs-lookup"><span data-stu-id="a4116-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="a4116-123">Betiği çalıştırmadan önce gerekli [bağımlılıkları](../install/dependencies.md)yükler.</span><span class="sxs-lookup"><span data-stu-id="a4116-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="a4116-124">Bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz `-Version|--version` .</span><span class="sxs-lookup"><span data-stu-id="a4116-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="a4116-125">Sürüm üç bölümlü bir sürüm olarak belirtilmelidir (örneğin, `2.1.0` ).</span><span class="sxs-lookup"><span data-stu-id="a4116-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="a4116-126">Sağlanmazsa, `latest` sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4116-126">If not provided, it uses the `latest` version.</span></span>

<span data-ttu-id="a4116-127">Install betikleri, Windows 'da kayıt defterini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="a4116-127">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="a4116-128">Yalnızca daraltılmış ikilileri indirir ve bir klasöre kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a4116-128">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="a4116-129">Kayıt defteri anahtarı değerlerinin güncelleştirilmesini istiyorsanız .NET Core yükleyicileri ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4116-129">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="a4116-130">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a4116-130">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="a4116-131">Yüklenecek .NET Core ikililerinin mimarisi.</span><span class="sxs-lookup"><span data-stu-id="a4116-131">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="a4116-132">Olası değerler şunlardır,,,, `<auto>` `amd64` `x64` `x86` `arm64` ve `arm` .</span><span class="sxs-lookup"><span data-stu-id="a4116-132">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="a4116-133">Varsayılan değer `<auto>` , çalışmakta olan işletim sistemi mimarisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4116-133">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="a4116-134">Yükleyicideki Azure akışına ait URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4116-134">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="a4116-135">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a4116-135">We recommended that you don't change this value.</span></span> <span data-ttu-id="a4116-136">Varsayılan değer: `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a4116-136">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="a4116-137">Yükleme için kaynak kanalını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4116-137">Specifies the source channel for the installation.</span></span> <span data-ttu-id="a4116-138">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4116-138">The possible values are:</span></span>

  - <span data-ttu-id="a4116-139">`Current`-En güncel sürüm.</span><span class="sxs-lookup"><span data-stu-id="a4116-139">`Current` - Most current release.</span></span>
  - <span data-ttu-id="a4116-140">`LTS`-Uzun süreli destek kanalı (desteklenen en güncel sürüm).</span><span class="sxs-lookup"><span data-stu-id="a4116-140">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="a4116-141">Belirli bir yayını temsil eden X. Y biçimindeki iki bölümlü sürüm (örneğin, `2.1` veya `3.0` ).</span><span class="sxs-lookup"><span data-stu-id="a4116-141">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="a4116-142">Dal adı: Örneğin, `release/3.1.1xx` veya `master` (gecelik yayınlar için).</span><span class="sxs-lookup"><span data-stu-id="a4116-142">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="a4116-143">Bir önizleme kanalından sürüm yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4116-143">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="a4116-144">Bir kanalın adını [yükleyiciler ve Ikili dosyalar](https://github.com/dotnet/core-sdk#installers-and-binaries)bölümünde listelendiği şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4116-144">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="a4116-145">Varsayılan değer: `LTS`.</span><span class="sxs-lookup"><span data-stu-id="a4116-145">The default value is `LTS`.</span></span> <span data-ttu-id="a4116-146">.NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="a4116-146">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="a4116-147">Ayarlanırsa, betik yüklemeyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="a4116-147">If set, the script won't perform the installation.</span></span> <span data-ttu-id="a4116-148">Bunun yerine, .NET Core CLI Şu anda istenen sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4116-148">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="a4116-149">Örneğin, sürümünü belirtirseniz `latest` , bu komutun bir yapı betiğine göre belirleyici olarak kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4116-149">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="a4116-150">Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4116-150">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="a4116-151">Azure akışına eklemek için sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4116-151">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="a4116-152">Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4116-152">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="a4116-153">Betiğe yönelik yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a4116-153">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="a4116-154">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4116-154">Specifies the installation path.</span></span> <span data-ttu-id="a4116-155">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4116-155">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="a4116-156">Varsayılan değer, Windows üzerinde *%LocalAppData%\microsoft\dotnet* ve Linux/MacOS üzerinde */usr/share/DotNet* değeridir.</span><span class="sxs-lookup"><span data-stu-id="a4116-156">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="a4116-157">İkili dosyalar doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a4116-157">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="a4116-158">SDK sürümünü belirlemekte kullanılacak [Global. JSON](global-json.md) dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4116-158">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="a4116-159">*Global. JSON* dosyası için bir değere sahip olmalıdır `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="a4116-159">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="a4116-160">[Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4116-160">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="a4116-161">Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="a4116-161">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="a4116-162">Varsayılan olarak, komut dosyası yolu değiştirir ve bu, .NET Core CLI yüklemeden hemen sonra kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a4116-162">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="a4116-163">Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4116-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="a4116-164">(Yalnızca Windows için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="a4116-164">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="a4116-165">Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4116-165">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="a4116-166">(Yalnızca Windows için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="a4116-166">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="a4116-167">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar.</span><span class="sxs-lookup"><span data-stu-id="a4116-167">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="a4116-168">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4116-168">The possible values are:</span></span>

  - <span data-ttu-id="a4116-169">`dotnet`- `Microsoft.NETCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4116-169">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a4116-170">`aspnetcore`- `Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4116-170">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a4116-171">`windowsdesktop`- `Microsoft.WindowsDesktop.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4116-171">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="a4116-172">Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4116-172">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="a4116-173">`linux-x64`Taşınabilir Linux için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4116-173">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="a4116-174">(Yalnızca Linux/macOS için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="a4116-174">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="a4116-175">Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4116-175">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="a4116-176">Önerilen alternatif, `-Runtime|--runtime` seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a4116-176">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="a4116-177">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar.</span><span class="sxs-lookup"><span data-stu-id="a4116-177">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="a4116-178">Bu seçenek belirtmeye eşdeğerdir `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="a4116-178">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="a4116-179">Zaten varsa *DotNet. exe*gibi sürümlenmemiş dosyaları yüklemeyi atlar.</span><span class="sxs-lookup"><span data-stu-id="a4116-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="a4116-180">Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="a4116-180">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="a4116-181">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a4116-181">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="a4116-182">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4116-182">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="a4116-183">Belirli bir derleme sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4116-183">Represents a specific build version.</span></span> <span data-ttu-id="a4116-184">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4116-184">The possible values are:</span></span>

  - <span data-ttu-id="a4116-185">`latest`-Kanalda en son derleme ( `-Channel` seçeneğiyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="a4116-185">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="a4116-186">`coherent`-Kanalda en son tutarlı derleme; en son kararlı paket birleşimini kullanır (dal adı seçenekleriyle kullanılır `-Channel` ).</span><span class="sxs-lookup"><span data-stu-id="a4116-186">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="a4116-187">Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; seçeneğinin yerini alır `-Channel` .</span><span class="sxs-lookup"><span data-stu-id="a4116-187">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="a4116-188">Örneğin: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="a4116-188">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="a4116-189">Belirtilmemişse, `-Version` Varsayılan olarak olur `latest` .</span><span class="sxs-lookup"><span data-stu-id="a4116-189">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="a4116-190">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a4116-190">Examples</span></span>

- <span data-ttu-id="a4116-191">En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="a4116-191">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="a4116-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4116-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="a4116-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4116-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="a4116-194">3,1 kanaldan en son sürümü belirtilen konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="a4116-194">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="a4116-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4116-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="a4116-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4116-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="a4116-197">Paylaşılan çalışma zamanının 3.0.0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="a4116-197">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="a4116-198">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4116-198">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="a4116-199">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4116-199">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="a4116-200">Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="a4116-200">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="a4116-201">Tek bir Oluşturucu örnek .NET Core CLI betiği alın ve yüklemeyi yapın:</span><span class="sxs-lookup"><span data-stu-id="a4116-201">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="a4116-202">Windows:</span><span class="sxs-lookup"><span data-stu-id="a4116-202">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="a4116-203">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a4116-203">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="a4116-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4116-204">See also</span></span>

- [<span data-ttu-id="a4116-205">.NET Core yayınları</span><span class="sxs-lookup"><span data-stu-id="a4116-205">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="a4116-206">.NET Core çalışma zamanı ve SDK indirme Arşivi</span><span class="sxs-lookup"><span data-stu-id="a4116-206">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
