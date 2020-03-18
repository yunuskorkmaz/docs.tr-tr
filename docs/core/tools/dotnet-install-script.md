---
title: dotnet-install scripts
description: .NET Core SDK'yı ve paylaşılan çalışma süresini yüklemek için dotnet yükleme komut dosyaları hakkında bilgi edinin.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092869"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="aa4a5-103">dotnet yükleme komut dosyaları başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa4a5-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="aa4a5-104">Adı</span><span class="sxs-lookup"><span data-stu-id="aa4a5-104">Name</span></span>

<span data-ttu-id="aa4a5-105">`dotnet-install.ps1` | `dotnet-install.sh`- .NET Core SDK'yı ve paylaşılan çalışma süresini yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aa4a5-106">Özet</span><span class="sxs-lookup"><span data-stu-id="aa4a5-106">Synopsis</span></span>

<span data-ttu-id="aa4a5-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="aa4a5-108">Linux/macO'lar:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="aa4a5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa4a5-109">Description</span></span>

<span data-ttu-id="aa4a5-110">`dotnet-install` Komut dosyaları,.NET Core CLI ve paylaşılan çalışma süresini içeren .NET Core SDK'nın yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="aa4a5-111">Komut dosyalarının kararlı sürümünü kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="aa4a5-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="aa4a5-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="aa4a5-113">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="aa4a5-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="aa4a5-114">Bu komut dosyalarının temel kullanışlılığı otomasyon senaryoları ve yönetici olmayan yüklemelerdedir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="aa4a5-115">İki komut dosyası vardır: biri Windows'da çalışan bir PowerShell komut dosyası, diğeri ise Linux/macOS üzerinde çalışan bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="aa4a5-116">Her iki komut dosyası da aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="aa4a5-117">Bash komut dosyası da PowerShell anahtarları okur, böylece Linux / macOS sistemlerinde komut dosyası ile PowerShell anahtarları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="aa4a5-118">Yükleme komut dosyaları, Zip/tarball dosyasını CLI yapılarından indirir ve varsayılan konuma veya tarafından `-InstallDir|--install-dir`belirtilen bir konuma yüklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="aa4a5-119">Varsayılan olarak, yükleme komut dosyaları SDK'yı karşıdan yükler ve yükler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="aa4a5-120">Yalnızca paylaşılan çalışma süresini elde etmek istiyorsanız, bağımsız değişkeni belirtin. `-Runtime|--runtime`</span><span class="sxs-lookup"><span data-stu-id="aa4a5-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="aa4a5-121">Varsayılan olarak, komut dosyası yükleme konumunu geçerli oturumun $PATH ekler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="aa4a5-122">`-NoPath|--no-path` Bağımsız değişkeni belirterek bu varsayılan davranışı geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="aa4a5-123">Komut dosyasını çalıştırmadan önce, gerekli [bağımlılıkları](../install/dependencies.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="aa4a5-124">Bağımsız değişkeni `-Version|--version` kullanarak belirli bir sürümü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="aa4a5-125">Sürüm üç bölümlü bir sürüm olarak belirtilmelidir `2.1.0`(örneğin, ).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="aa4a5-126">Sağlanmadıysa, `latest` sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="aa4a5-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="aa4a5-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="aa4a5-128">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="aa4a5-129">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-129">The possible values are:</span></span>

  - <span data-ttu-id="aa4a5-130">`Current`- En güncel sürüm.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="aa4a5-131">`LTS`- Uzun Vadeli Destek kanalı (en güncel desteklenen sürüm).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="aa4a5-132">Belirli bir sürümü temsil eden X.Y formatında `2.1` iki `3.0`parçalı sürüm (örneğin, veya).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="aa4a5-133">Şube adı: `release/3.1.1xx` örneğin, `master` ya da (gece sürümleri için).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="aa4a5-134">Önizleme kanalından bir sürüm yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="aa4a5-135">[Yükleyiciler ve İkili'lerde](https://github.com/dotnet/core-sdk#installers-and-binaries)listelenen kanalın adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="aa4a5-136">Varsayılan değer: `LTS`.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-136">The default value is `LTS`.</span></span> <span data-ttu-id="aa4a5-137">.NET destek kanalları hakkında daha fazla bilgi için [.NET Destek Politikası](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="aa4a5-138">Belirli bir yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-138">Represents a specific build version.</span></span> <span data-ttu-id="aa4a5-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-139">The possible values are:</span></span>

  - <span data-ttu-id="aa4a5-140">`latest`- Kanalüzerinde son yapı `-Channel` (seçeneği ile birlikte kullanılır).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="aa4a5-141">`coherent`- Kanalüzerinde son tutarlı yapı; en son kararlı paket birleşimini `-Channel` kullanır (Şube adı seçenekleriyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="aa4a5-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="aa4a5-142">X.Y.Z formatında belirli bir yapı sürümünü temsil eden üç parçalı sürüm; seçeneğin yerini `-Channel` adakalır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="aa4a5-143">Örneğin: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="aa4a5-144">Belirtilmemişse, `-Version` `latest`varsayılan olarak .</span><span class="sxs-lookup"><span data-stu-id="aa4a5-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="aa4a5-145">SDK sürümünü belirlemek için kullanılacak [global.json](global-json.md) dosyasına giden bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="aa4a5-146">*global.json* dosyasının bir değeri `sdk:version`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="aa4a5-147">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-147">Specifies the installation path.</span></span> <span data-ttu-id="aa4a5-148">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="aa4a5-149">Varsayılan değer *%LocalAppData%\Microsoft\dotnet'tir.*</span><span class="sxs-lookup"><span data-stu-id="aa4a5-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="aa4a5-150">İkili doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="aa4a5-151">.NET Çekirdek ikililerinin mimarisini yüklemek.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="aa4a5-152">Olası değerler `<auto>` `amd64`, `x64` `x86`, `arm64`, `arm`, , ve .</span><span class="sxs-lookup"><span data-stu-id="aa4a5-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="aa4a5-153">Varsayılan değer, `<auto>`şu anda çalışan işletim sistemi mimarisini temsil eden değerdir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="aa4a5-154">Bu parametre eskidir ve komut dosyasının gelecekteki bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="aa4a5-155">Önerilen alternatif `-Runtime|--runtime` seçenektir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="aa4a5-156">SDK'nın tamamını değil, paylaşılan çalışma zamanı bitlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="aa4a5-157">Bu seçenek belirtmeye `-Runtime|--runtime dotnet`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="aa4a5-158">SDK'nın tamamını değil, sadece paylaşılan çalışma süresini yükler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="aa4a5-159">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-159">The possible values are:</span></span>

  - <span data-ttu-id="aa4a5-160">`dotnet`- `Microsoft.NETCore.App` paylaşılan çalışma süresi.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="aa4a5-161">`aspnetcore`- `Microsoft.AspNetCore.App` paylaşılan çalışma süresi.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="aa4a5-162">`windowsdesktop`- `Microsoft.WindowsDesktop.App` paylaşılan çalışma süresi.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="aa4a5-163">Ayarlanırsa, komut dosyası yüklemeyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="aa4a5-164">Bunun yerine, .NET Core CLI'nin istenen sürümünü tutarlı bir şekilde yüklemek için hangi komut satırını kullanacağını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="aa4a5-165">Örneğin, sürüm `latest`belirtirseniz, bu komutun bir yapı komut dosyasında deterministically kullanılabilmesi için belirli sürümile bir bağlantı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="aa4a5-166">Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ederseniz ikilinin konumunu da görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="aa4a5-167">Ayarlanırsa, yükleme klasörü geçerli oturumun yoluna dışa aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="aa4a5-168">Varsayılan olarak, komut dosyası PATH'i değiştirir ve bu da .NET Core CLI'yi yükledikten hemen sonra kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="aa4a5-169">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="aa4a5-170">Azure akışının URL'sini yükleyiciye belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="aa4a5-171">Bu değeri değiştirmemenizi tavsiye ettik.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="aa4a5-172">Varsayılan değer: `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="aa4a5-173">Bu yükleyici tarafından kullanılan cached beslemesi için URL'yi değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="aa4a5-174">Bu değeri değiştirmemenizi tavsiye ettik.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="aa4a5-175">[Azure İçerik Teslim Ağı'ndan (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) indirmeyi devre dışı bırakıp doğrudan önyüklemesiz akışı kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="aa4a5-176">Azure akışına eklemek için sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="aa4a5-177">Genel olmayan blob depolama hesaplarını kullanmak için URL'yi değiştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="aa4a5-178">Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="aa4a5-179">Taşınabilir `linux-x64` Linux için kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="aa4a5-180">(Sadece Linux/macOS için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="aa4a5-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="aa4a5-181">Ayarlanırsa, yükleyici web isteklerini yaparken proxy'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="aa4a5-182">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="aa4a5-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="aa4a5-183">Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="aa4a5-184">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="aa4a5-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="aa4a5-185">*Dotnet.exe*gibi sürümdışı dosyaları yüklemeyi atlar, zaten varsa.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="aa4a5-186">Komut dosyası için yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="aa4a5-187">Örnekler</span><span class="sxs-lookup"><span data-stu-id="aa4a5-187">Examples</span></span>

- <span data-ttu-id="aa4a5-188">En son uzun vadeli desteklenen (LTS) sürümünü varsayılan konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="aa4a5-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="aa4a5-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="aa4a5-191">En son sürümü 3.1 kanalından belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="aa4a5-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="aa4a5-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="aa4a5-194">Paylaşılan çalışma süresinin 3.0.0 sürümünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="aa4a5-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="aa4a5-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="aa4a5-197">Komut dosyası edinin ve bir şirket proxy arkasında 2.1.2 sürümünü yükleyin (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="aa4a5-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="aa4a5-198">Komut dosyası edinin ve .NET Core CLI tek satırlık örnekler yükleyin:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="aa4a5-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="aa4a5-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="aa4a5-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="aa4a5-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa4a5-201">See also</span></span>

- [<span data-ttu-id="aa4a5-202">.NET Core bültenleri</span><span class="sxs-lookup"><span data-stu-id="aa4a5-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="aa4a5-203">.NET Çekirdek Çalışma Süresi ve SDK indirme arşivi</span><span class="sxs-lookup"><span data-stu-id="aa4a5-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
