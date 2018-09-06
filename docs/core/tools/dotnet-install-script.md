---
title: DotNet yükleme betikleri
description: .NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için dotnet-yükleme betikleri hakkında bilgi edinin.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: 8d1c6ebb30bd45575bb61206799c9c3e5c47ff0c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734687"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="f2657-103">DotNet yükleme komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="f2657-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="f2657-104">Ad</span><span class="sxs-lookup"><span data-stu-id="f2657-104">Name</span></span>

<span data-ttu-id="f2657-105">`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="f2657-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f2657-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="f2657-106">Synopsis</span></span>

<span data-ttu-id="f2657-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="f2657-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="f2657-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f2657-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="f2657-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2657-109">Description</span></span>

<span data-ttu-id="f2657-110">`dotnet-install` Betikleri, .NET Core CLI araçları ve paylaşılan çalışma zamanı içeren .NET Core SDK'sı yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2657-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="f2657-111">Üzerinde barındırılan kararlı bir sürüm kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="f2657-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="f2657-112">Komut dosyalarını doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2657-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="f2657-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="f2657-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="f2657-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="f2657-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="f2657-115">Bu komut dosyaları ana kullanışlılığını Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2657-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="f2657-116">İki betik vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir.</span><span class="sxs-lookup"><span data-stu-id="f2657-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="f2657-117">Diğer betik Linux/macOS üzerinde çalışan bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2657-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="f2657-118">Her iki komut dosyaları aynı davranışa sahip.</span><span class="sxs-lookup"><span data-stu-id="f2657-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="f2657-119">Linux/macOS sistemlerde betiğiyle PowerShell anahtarları kullanabilmeniz için bash betiğini de PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="f2657-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="f2657-120">Yükleme betikleri CLI yapı bırakma öğelerini ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yükleme işlemine devam `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="f2657-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="f2657-121">Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f2657-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="f2657-122">Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="f2657-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="f2657-123">Varsayılan olarak, betik geçerli oturum için $PATH için yükleme konumu ekler.</span><span class="sxs-lookup"><span data-stu-id="f2657-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="f2657-124">Bu varsayılan davranışı geçersiz kılma belirterek `--no-path` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="f2657-124">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="f2657-125">Betiği çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="f2657-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="f2657-126">Belirli bir sürümünü kullanarak bir yükleyebilirsiniz `--version` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="f2657-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="f2657-127">Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f2657-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="f2657-128">Atlanırsa, kullandığı `latest` sürümü.</span><span class="sxs-lookup"><span data-stu-id="f2657-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="f2657-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f2657-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="f2657-130">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2657-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="f2657-131">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2657-131">The possible values are:</span></span>

- <span data-ttu-id="f2657-132">`Current` -Geçerli sürüm</span><span class="sxs-lookup"><span data-stu-id="f2657-132">`Current` - Current release</span></span>
- <span data-ttu-id="f2657-133">`LTS` -Uzun süreli destek kanalı (geçerli desteklenen sürüm)</span><span class="sxs-lookup"><span data-stu-id="f2657-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="f2657-134">İki parçalı sürümü belirli bir yayınını temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)</span><span class="sxs-lookup"><span data-stu-id="f2657-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="f2657-135">Dal adı [örneğin `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` dal (gecelik sürümleri "edge taşmasını")]</span><span class="sxs-lookup"><span data-stu-id="f2657-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="f2657-136">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f2657-136">The default value is `LTS`.</span></span> <span data-ttu-id="f2657-137">.NET Destek kanalları hakkında daha fazla bilgi için bkz. [.NET Core destek yaşam döngüsü](https://www.microsoft.com/net/core/support) konu.</span><span class="sxs-lookup"><span data-stu-id="f2657-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="f2657-138">Belirli bir yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2657-138">Represents a specific build version.</span></span> <span data-ttu-id="f2657-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2657-139">The possible values are:</span></span>

- <span data-ttu-id="f2657-140">`latest` -Kanal en son derleme (ile kullanılan `-Channel` seçeneği)</span><span class="sxs-lookup"><span data-stu-id="f2657-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="f2657-141">`coherent` -Tutarlı yapıyı kanalındaki son; en son kararlı paket kullanır (Dal adı ile kullanılan `-Channel` seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f2657-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="f2657-142">Üç bölümlü sürüm X.Y.Z biçiminde temsil eden belirli bir yapı sürümü; yerine geçen `-Channel` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f2657-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="f2657-143">Örneğin: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="f2657-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="f2657-144">Atlanırsa, `-Version` varsayılan olarak `latest`.</span><span class="sxs-lookup"><span data-stu-id="f2657-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="f2657-145">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2657-145">Specifies the installation path.</span></span> <span data-ttu-id="f2657-146">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2657-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="f2657-147">Varsayılan değer *% LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="f2657-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="f2657-148">İkili dosyaları doğrudan dizine yerleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f2657-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="f2657-149">.NET Core ikili dosyaları yüklemek için Mimari.</span><span class="sxs-lookup"><span data-stu-id="f2657-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="f2657-150">Olası değerler `auto`, `x64`, ve `x86`.</span><span class="sxs-lookup"><span data-stu-id="f2657-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="f2657-151">Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2657-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="f2657-152">Ayarlanırsa, bu anahtarı paylaşılan çalışma zamanı yükleme sınırları varsa.</span><span class="sxs-lookup"><span data-stu-id="f2657-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="f2657-153">Tüm SDK'sı yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="f2657-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="f2657-154">Ayarlanırsa, komut dosyası yükleme; gerçekleştiremiyor varsa Ancak, bunun yerine, .NET Core CLI'ın şu anda istenen sürüm tutarlı bir şekilde yüklemek için kullanılacak hangi komut satırını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2657-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="f2657-155">Sürüm belirtirseniz, örneğin `latest`, böylece bu komut, bir derleme betikte belirleyici kullanılabilir belirli bir sürümünü içeren bir bağlantı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2657-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="f2657-156">Yüklemek veya kendiniz indirmek isterseniz de ikili dosyanın konumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2657-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="f2657-157">Ayarlanırsa, ön eki/ınstalldır değil verilir, yolu geçerli oturum için.</span><span class="sxs-lookup"><span data-stu-id="f2657-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="f2657-158">Varsayılan olarak, komut dosyası CLI araçları yüklendikten sonra hemen kullanılabilmesini YOLUNU değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f2657-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="f2657-159">Yükleyici için akış URL'sini Azure belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2657-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="f2657-160">Bu değeri değiştirmeniz önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f2657-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="f2657-161">Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f2657-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="f2657-162">Kümesi, yükleyici web istekleri yaparken proxy kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="f2657-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="f2657-163">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="f2657-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="f2657-164">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2657-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="f2657-165">Komut için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f2657-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="f2657-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f2657-166">Examples</span></span>

<span data-ttu-id="f2657-167">Desteklenen en son uzun vadeli (LTS) sürüm varsayılan konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f2657-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="f2657-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="f2657-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="f2657-169">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f2657-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="f2657-170">En son sürümü 2.0 kanaldan belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f2657-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="f2657-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="f2657-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="f2657-172">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f2657-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="f2657-173">Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:</span><span class="sxs-lookup"><span data-stu-id="f2657-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="f2657-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="f2657-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="f2657-175">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f2657-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="f2657-176">Betiği almak ve .NET Core CLI one-liner örnekleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f2657-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="f2657-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="f2657-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="f2657-178">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="f2657-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="f2657-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2657-179">See also</span></span>

* [<span data-ttu-id="f2657-180">.NET core sürümleri</span><span class="sxs-lookup"><span data-stu-id="f2657-180">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
* [<span data-ttu-id="f2657-181">Arşiv .NET core çalışma zamanı ve SDK'sını indirin</span><span class="sxs-lookup"><span data-stu-id="f2657-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
