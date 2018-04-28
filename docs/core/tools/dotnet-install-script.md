---
title: DotNet yükleme betikleri
description: .NET Core CLI araçlarını ve paylaşılan çalışma zamanı yükleme dotnet yükleme betikleri hakkında bilgi edinin.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 96336df087ea2ad01584010f0715ad31e079b663
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="248d3-103">DotNet yükleme komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="248d3-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="248d3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="248d3-104">Name</span></span>

<span data-ttu-id="248d3-105">`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçlarını ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="248d3-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="248d3-106">Özet</span><span class="sxs-lookup"><span data-stu-id="248d3-106">Synopsis</span></span>

<span data-ttu-id="248d3-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="248d3-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="248d3-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="248d3-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="248d3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="248d3-109">Description</span></span>

<span data-ttu-id="248d3-110">`dotnet-install` Komut dosyaları, .NET Core CLI araçlarını ve paylaşılan çalışma zamanı içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="248d3-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="248d3-111">Üzerinde barındırılan kararlı sürümünü kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="248d3-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="248d3-112">Komut dosyalarını doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="248d3-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="248d3-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="248d3-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="248d3-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="248d3-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="248d3-115">Bu komut dosyalarını ana yararlılığı Otomasyon senaryoları ve yönetici olmayan yüklemeleri de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="248d3-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="248d3-116">İki komut vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir.</span><span class="sxs-lookup"><span data-stu-id="248d3-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="248d3-117">Diğer komut dosyası Linux/macOS üzerinde çalıştığı bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="248d3-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="248d3-118">Her iki komut dosyasını aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="248d3-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="248d3-119">Linux/macOS sistemlerde komut dosyasıyla PowerShell anahtarları kullanabilmeniz için bash komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="248d3-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="248d3-120">Yükleme betikleri CLI derleme bırakma işlemlerine ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yüklemeye devam `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="248d3-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="248d3-121">Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="248d3-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="248d3-122">Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="248d3-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="248d3-123">Varsayılan olarak, geçerli oturum için $PATH için yükleme konumu betik ekler.</span><span class="sxs-lookup"><span data-stu-id="248d3-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="248d3-124">Belirterek bu varsayılan davranışı geçersiz kılma `--no-path` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="248d3-124">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="248d3-125">Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="248d3-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="248d3-126">Belirli bir sürüm kullanarak yükleyebilirsiniz `--version` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="248d3-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="248d3-127">Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="248d3-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="248d3-128">Belirtilmezse, kullanır `latest` sürümü.</span><span class="sxs-lookup"><span data-stu-id="248d3-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="248d3-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="248d3-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="248d3-130">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="248d3-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="248d3-131">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="248d3-131">The possible values are:</span></span>

- <span data-ttu-id="248d3-132">`Current` -Geçerli sürüm</span><span class="sxs-lookup"><span data-stu-id="248d3-132">`Current` - Current release</span></span>
- <span data-ttu-id="248d3-133">`LTS` -Uzun vadeli bir destek kanalıyla (geçerli desteklenen sürüm)</span><span class="sxs-lookup"><span data-stu-id="248d3-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="248d3-134">İki parçalı sürümü belirli bir sürüm temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)</span><span class="sxs-lookup"><span data-stu-id="248d3-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="248d3-135">Dal adı [Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` şube (gecelik sürümleri "kenar taşmasını")]</span><span class="sxs-lookup"><span data-stu-id="248d3-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="248d3-136">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="248d3-136">The default value is `LTS`.</span></span> <span data-ttu-id="248d3-137">.NET Destek kanallarını hakkında daha fazla bilgi için bkz: [.NET Core destek ömrü](https://www.microsoft.com/net/core/support) konu.</span><span class="sxs-lookup"><span data-stu-id="248d3-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="248d3-138">Özel Yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="248d3-138">Represents a specific build version.</span></span> <span data-ttu-id="248d3-139">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="248d3-139">The possible values are:</span></span>

- <span data-ttu-id="248d3-140">`latest` -En yeni kanal oluştur (ile kullanılan `-Channel` seçeneği)</span><span class="sxs-lookup"><span data-stu-id="248d3-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="248d3-141">`coherent` -Son tutarlı yapı kanalda; en son kararlı paket birlikte kullanır (şube adı ile kullanılan `-Channel` seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="248d3-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="248d3-142">Belirli bir temsil eden X.Y.Z biçiminde üç bölümlük sürüm yapı sürümü; yerine geçen `-Channel` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="248d3-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="248d3-143">Örneğin: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="248d3-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="248d3-144">Atlanırsa, `-Version` varsayılan olarak `latest`.</span><span class="sxs-lookup"><span data-stu-id="248d3-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="248d3-145">Yükleme yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="248d3-145">Specifies the installation path.</span></span> <span data-ttu-id="248d3-146">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="248d3-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="248d3-147">Varsayılan değer *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="248d3-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="248d3-148">İkili dosyaları doğrudan dizindeki yerleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="248d3-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="248d3-149">Yüklemek için .NET Core ikili dosyaları mimarisi.</span><span class="sxs-lookup"><span data-stu-id="248d3-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="248d3-150">Olası değerler şunlardır: `auto`, `x64`, ve `x86`.</span><span class="sxs-lookup"><span data-stu-id="248d3-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="248d3-151">Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="248d3-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="248d3-152">Ayarlama, bu anahtarı paylaşılan çalışma zamanı yükleme sınırlar durumunda.</span><span class="sxs-lookup"><span data-stu-id="248d3-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="248d3-153">Tüm SDK yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="248d3-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="248d3-154">Ayarlama, komut dosyası yüklemesi; gerçekleştiremiyor varsa ancak bunun yerine, tutarlı bir şekilde .NET Core CLI'ın şu anda istenen sürümünü yüklemek için kullanılacak hangi komut satırı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="248d3-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="248d3-155">Sürüm belirtirseniz, örneğin `latest`, böylece bu komut bir yapı komut dosyasında belirleyici biçimde kullanılabilir belirli sürümünü içeren bir bağlantı gösterir.</span><span class="sxs-lookup"><span data-stu-id="248d3-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="248d3-156">Yükleme veya kendiniz indirmek isterseniz de ikilinin konumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="248d3-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="248d3-157">Ayarlama, önek/InstallDir dışarı aktarılmaz varsa yolu geçerli oturum için.</span><span class="sxs-lookup"><span data-stu-id="248d3-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="248d3-158">Varsayılan olarak, CLI araçlarını hemen yüklendikten sonra kullanılabilir hale getirir yolu komut dosyasını değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="248d3-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="248d3-159">Azure URL'si için yükleyici akış belirtir.</span><span class="sxs-lookup"><span data-stu-id="248d3-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="248d3-160">Bu değeri değiştirmek önerilmez.</span><span class="sxs-lookup"><span data-stu-id="248d3-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="248d3-161">Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.</span><span class="sxs-lookup"><span data-stu-id="248d3-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="248d3-162">Ayarlama, yükleyici web isteklerini yaparken proxy kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="248d3-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="248d3-163">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="248d3-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="248d3-164">Tanılama bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="248d3-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="248d3-165">Komut dosyası için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="248d3-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="248d3-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="248d3-166">Examples</span></span>

<span data-ttu-id="248d3-167">En son uzun vadeli desteklenen (LTS) sürüm, varsayılan konuma geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="248d3-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="248d3-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="248d3-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="248d3-169">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="248d3-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="248d3-170">En son sürümü 2.0 kanala belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="248d3-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="248d3-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="248d3-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="248d3-172">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="248d3-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="248d3-173">Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:</span><span class="sxs-lookup"><span data-stu-id="248d3-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="248d3-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="248d3-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="248d3-175">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="248d3-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="248d3-176">Komut dosyasını edinmek ve .NET Core CLI one-liner örnekleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="248d3-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="248d3-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="248d3-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="248d3-178">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="248d3-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="248d3-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="248d3-179">See also</span></span>

<span data-ttu-id="248d3-180">[.NET core serbest bırakır](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="248d3-180">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="248d3-181">.NET çekirdeği çalışma zamanı ve SDK arşivi indir</span><span class="sxs-lookup"><span data-stu-id="248d3-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
