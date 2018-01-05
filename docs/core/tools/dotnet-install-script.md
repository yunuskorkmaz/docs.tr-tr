---
title: "DotNet yükleme betikleri"
description: ".NET Core CLI araçlarını ve paylaşılan çalışma zamanı yükleme dotnet yükleme betikleri hakkında bilgi edinin."
keywords: "DotNet yükleme, dotnet yükleme betikleri, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.workload: dotnetcore
ms.openlocfilehash: bc38ca7b9f00c6c252ff4963c42519a64c456b43
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="2ae59-104">DotNet yükleme komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ae59-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="2ae59-105">Ad</span><span class="sxs-lookup"><span data-stu-id="2ae59-105">Name</span></span>

<span data-ttu-id="2ae59-106">`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core CLI araçlarını ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="2ae59-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ae59-107">Özet</span><span class="sxs-lookup"><span data-stu-id="2ae59-107">Synopsis</span></span>

<span data-ttu-id="2ae59-108">Windows:</span><span class="sxs-lookup"><span data-stu-id="2ae59-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="2ae59-109">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2ae59-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="2ae59-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ae59-110">Description</span></span>

<span data-ttu-id="2ae59-111">`dotnet-install` Komut dosyaları, .NET Core CLI araçlarını ve paylaşılan çalışma zamanı içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ae59-111">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="2ae59-112">Üzerinde barındırılan kararlı sürümünü kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="2ae59-112">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="2ae59-113">Komut dosyalarını doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2ae59-113">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="2ae59-114">https://dot.NET/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="2ae59-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="2ae59-115">https://dot.NET/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="2ae59-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="2ae59-116">Bu komut dosyalarını ana yararlılığı Otomasyon senaryoları ve yönetici olmayan yüklemeleri de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2ae59-116">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="2ae59-117">İki komut vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-117">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="2ae59-118">Diğer komut dosyası Linux/macOS üzerinde çalıştığı bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2ae59-118">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="2ae59-119">Her iki komut dosyasını aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-119">Both scripts have the same behavior.</span></span> <span data-ttu-id="2ae59-120">Linux/macOS sistemlerde komut dosyasıyla PowerShell anahtarları kullanabilmeniz için bash komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="2ae59-120">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="2ae59-121">Yükleme betikleri CLI derleme bırakma işlemlerine ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yüklemeye devam `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="2ae59-121">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="2ae59-122">Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2ae59-122">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="2ae59-123">Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2ae59-123">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="2ae59-124">Varsayılan olarak, geçerli oturum için $PATH için yükleme konumu betik ekler.</span><span class="sxs-lookup"><span data-stu-id="2ae59-124">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="2ae59-125">Belirterek bu varsayılan davranışı geçersiz kılma `--no-path` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2ae59-125">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="2ae59-126">Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="2ae59-126">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="2ae59-127">Belirli bir sürüm kullanarak yükleyebilirsiniz `--version` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2ae59-127">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="2ae59-128">Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-128">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="2ae59-129">Belirtilmezse, kullanır `latest` sürümü.</span><span class="sxs-lookup"><span data-stu-id="2ae59-129">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="2ae59-130">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2ae59-130">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="2ae59-131">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-131">Specifies the source channel for the installation.</span></span> <span data-ttu-id="2ae59-132">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2ae59-132">The possible values are:</span></span>

- <span data-ttu-id="2ae59-133">`Current`-Geçerli sürüm</span><span class="sxs-lookup"><span data-stu-id="2ae59-133">`Current` - Current release</span></span>
- <span data-ttu-id="2ae59-134">`LTS`-Uzun vadeli bir destek kanalıyla (geçerli desteklenen sürüm)</span><span class="sxs-lookup"><span data-stu-id="2ae59-134">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="2ae59-135">İki parçalı sürümü belirli bir sürüm temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)</span><span class="sxs-lookup"><span data-stu-id="2ae59-135">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="2ae59-136">Dal adı [Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` şube (gecelik sürümleri "kenar taşmasını")]</span><span class="sxs-lookup"><span data-stu-id="2ae59-136">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="2ae59-137">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-137">The default value is `LTS`.</span></span> <span data-ttu-id="2ae59-138">.NET Destek kanallarını hakkında daha fazla bilgi için bkz: [.NET Core destek ömrü](https://www.microsoft.com/net/core/support) konu.</span><span class="sxs-lookup"><span data-stu-id="2ae59-138">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="2ae59-139">Özel Yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2ae59-139">Represents a specific build version.</span></span> <span data-ttu-id="2ae59-140">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2ae59-140">The possible values are:</span></span>

- <span data-ttu-id="2ae59-141">`latest`-En yeni kanal oluştur (ile kullanılan `-Channel` seçeneği)</span><span class="sxs-lookup"><span data-stu-id="2ae59-141">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="2ae59-142">`coherent`-Son tutarlı yapı kanalda; en son kararlı paket birlikte kullanır (şube adı ile kullanılan `-Channel` seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2ae59-142">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="2ae59-143">Belirli bir temsil eden X.Y.Z biçiminde üç bölümlük sürüm yapı sürümü; yerine geçen `-Channel` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2ae59-143">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="2ae59-144">Örneğin:`2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="2ae59-144">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="2ae59-145">Atlanırsa, `-Version` varsayılan olarak `latest`.</span><span class="sxs-lookup"><span data-stu-id="2ae59-145">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="2ae59-146">Yükleme yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-146">Specifies the installation path.</span></span> <span data-ttu-id="2ae59-147">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ae59-147">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="2ae59-148">Varsayılan değer *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="2ae59-148">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="2ae59-149">İkili dosyaları doğrudan dizindeki yerleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ae59-149">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="2ae59-150">Yüklemek için .NET Core ikili dosyaları mimarisi.</span><span class="sxs-lookup"><span data-stu-id="2ae59-150">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="2ae59-151">Olası değerler şunlardır: `auto`, `x64`, ve `x86`.</span><span class="sxs-lookup"><span data-stu-id="2ae59-151">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="2ae59-152">Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2ae59-152">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="2ae59-153">Ayarlama, bu anahtarı paylaşılan çalışma zamanı yükleme sınırlar durumunda.</span><span class="sxs-lookup"><span data-stu-id="2ae59-153">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="2ae59-154">Tüm SDK yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="2ae59-154">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="2ae59-155">Ayarlama, komut dosyası yüklemesi; gerçekleştiremiyor varsa ancak bunun yerine, tutarlı bir şekilde .NET Core CLI'ın şu anda istenen sürümünü yüklemek için kullanılacak hangi komut satırı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ae59-155">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="2ae59-156">Sürüm belirtirseniz, örneğin `latest`, böylece bu komut bir yapı komut dosyasında belirleyici biçimde kullanılabilir belirli sürümünü içeren bir bağlantı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-156">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="2ae59-157">Yükleme veya kendiniz indirmek isterseniz de ikilinin konumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ae59-157">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="2ae59-158">Ayarlama, önek/InstallDir dışarı aktarılmaz varsa yolu geçerli oturum için.</span><span class="sxs-lookup"><span data-stu-id="2ae59-158">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="2ae59-159">Varsayılan olarak, CLI araçlarını hemen yüklendikten sonra kullanılabilir hale getirir yolu komut dosyasını değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-159">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="2ae59-160">Azure URL'si için yükleyici akış belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-160">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="2ae59-161">Bu değeri değiştirmek önerilmez.</span><span class="sxs-lookup"><span data-stu-id="2ae59-161">It isn't recommended that you change this value.</span></span> <span data-ttu-id="2ae59-162">Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2ae59-162">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="2ae59-163">Ayarlama, yükleyici web isteklerini yaparken proxy kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="2ae59-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="2ae59-164">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="2ae59-164">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="2ae59-165">Tanılama bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ae59-165">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="2ae59-166">Komut dosyası için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2ae59-166">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="2ae59-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2ae59-167">Examples</span></span>

<span data-ttu-id="2ae59-168">En son uzun vadeli desteklenen (LTS) sürüm, varsayılan konuma geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2ae59-168">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="2ae59-169">Windows:</span><span class="sxs-lookup"><span data-stu-id="2ae59-169">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="2ae59-170">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2ae59-170">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="2ae59-171">En son sürümü 2.0 kanala belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2ae59-171">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="2ae59-172">Windows:</span><span class="sxs-lookup"><span data-stu-id="2ae59-172">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="2ae59-173">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2ae59-173">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="2ae59-174">Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:</span><span class="sxs-lookup"><span data-stu-id="2ae59-174">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="2ae59-175">Windows:</span><span class="sxs-lookup"><span data-stu-id="2ae59-175">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="2ae59-176">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2ae59-176">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="2ae59-177">Komut dosyasını edinmek ve .NET Core CLI one-liner örnekleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="2ae59-177">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="2ae59-178">Windows:</span><span class="sxs-lookup"><span data-stu-id="2ae59-178">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="2ae59-179">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2ae59-179">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="2ae59-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ae59-180">See also</span></span>

<span data-ttu-id="2ae59-181">[.NET core serbest bırakır](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="2ae59-181">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="2ae59-182">.NET çekirdeği çalışma zamanı ve SDK arşivi indir</span><span class="sxs-lookup"><span data-stu-id="2ae59-182">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
