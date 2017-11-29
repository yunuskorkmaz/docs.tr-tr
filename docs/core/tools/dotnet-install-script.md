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
ms.openlocfilehash: 2f15f37016fe824d76b501e4793e0b28bbdbe167
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="3b9cb-104">DotNet yükleme komut başvurusu</span><span class="sxs-lookup"><span data-stu-id="3b9cb-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="3b9cb-105">Ad</span><span class="sxs-lookup"><span data-stu-id="3b9cb-105">Name</span></span>

<span data-ttu-id="3b9cb-106">`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core CLI araçlarını ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b9cb-107">Özet</span><span class="sxs-lookup"><span data-stu-id="3b9cb-107">Synopsis</span></span>

<span data-ttu-id="3b9cb-108">Windows:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="3b9cb-109">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="3b9cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b9cb-110">Description</span></span>

<span data-ttu-id="3b9cb-111">`dotnet-install` Komut dosyaları, .NET Core CLI araçlarını ve paylaşılan çalışma zamanı içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-111">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="3b9cb-112">Üzerinde barındırılan kararlı sürümünü kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="3b9cb-112">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="3b9cb-113">Komut dosyalarını doğrudan yolları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-113">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="3b9cb-114">https://dot.NET/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="3b9cb-115">https://dot.NET/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="3b9cb-116">Bu komut dosyalarını ana yararlılığı Otomasyon senaryoları ve yönetici olmayan yüklemeleri de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-116">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="3b9cb-117">İki komut vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-117">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="3b9cb-118">Diğer komut dosyası Linux/macOS üzerinde çalıştığı bir bash komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-118">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="3b9cb-119">Her iki komut dosyasını aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-119">Both scripts have the same behavior.</span></span> <span data-ttu-id="3b9cb-120">Linux/macOS sistemlerde komut dosyasıyla PowerShell anahtarları kullanabilmeniz için bash komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-120">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="3b9cb-121">Yükleme betikleri CLI derleme bırakma işlemlerine ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yüklemeye devam `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-121">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="3b9cb-122">Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-122">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="3b9cb-123">Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-123">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="3b9cb-124">Varsayılan olarak, geçerli oturum için $PATH için yükleme konumu betik ekler.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-124">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="3b9cb-125">Belirterek bu varsayılan davranışı geçersiz kılma `--no-path` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-125">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="3b9cb-126">Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="3b9cb-126">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="3b9cb-127">Belirli bir sürüm kullanarak yükleyebilirsiniz `--version` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-127">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="3b9cb-128">Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-128">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="3b9cb-129">Belirtilmezse, kullanır `latest` sürümü.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-129">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="3b9cb-130">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3b9cb-130">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="3b9cb-131">Yükleme için kaynak kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-131">Specifies the source channel for the installation.</span></span> <span data-ttu-id="3b9cb-132">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-132">The possible values are:</span></span>

- <span data-ttu-id="3b9cb-133">`Current`-Geçerli sürüm</span><span class="sxs-lookup"><span data-stu-id="3b9cb-133">`Current` - Current release</span></span>
- <span data-ttu-id="3b9cb-134">`LTS`-Uzun vadeli bir destek kanalıyla (geçerli desteklenen sürüm)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-134">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="3b9cb-135">İki parçalı sürümü belirli bir sürüm temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-135">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="3b9cb-136">Dal adı [Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` şube (gecelik sürümleri "kenar taşmasını")]</span><span class="sxs-lookup"><span data-stu-id="3b9cb-136">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="3b9cb-137">Varsayılan değer `LTS` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-137">The default value is `LTS`.</span></span> <span data-ttu-id="3b9cb-138">.NET Destek kanallarını hakkında daha fazla bilgi için bkz: [.NET Core destek ömrü](https://www.microsoft.com/net/core/support) konu.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-138">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="3b9cb-139">Özel Yapı sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-139">Represents a specific build version.</span></span> <span data-ttu-id="3b9cb-140">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-140">The possible values are:</span></span>

- <span data-ttu-id="3b9cb-141">`latest`-En yeni kanal oluştur (ile kullanılan `-Channel` seçeneği)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-141">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="3b9cb-142">`coherent`-Son tutarlı yapı kanalda; en son kararlı paket birlikte kullanır (şube adı ile kullanılan `-Channel` seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-142">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="3b9cb-143">Belirli bir temsil eden X.Y.Z biçiminde üç bölümlük sürüm yapı sürümü; yerine geçen `-Channel` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-143">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="3b9cb-144">Örneğin:`2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="3b9cb-144">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="3b9cb-145">Atlanırsa, `-Version` varsayılan olarak `latest`.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-145">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="3b9cb-146">Yükleme yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-146">Specifies the installation path.</span></span> <span data-ttu-id="3b9cb-147">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-147">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="3b9cb-148">Varsayılan değer *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-148">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="3b9cb-149">İkili dosyaları doğrudan dizindeki yerleştirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-149">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="3b9cb-150">Yüklemek için .NET Core ikili dosyaları mimarisi.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-150">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="3b9cb-151">Olası değerler şunlardır: `auto`, `x64`, ve `x86`.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-151">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="3b9cb-152">Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-152">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="3b9cb-153">Ayarlama, bu anahtarı paylaşılan çalışma zamanı yükleme sınırlar durumunda.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-153">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="3b9cb-154">Tüm SDK yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-154">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="3b9cb-155">Ayarlama, komut dosyası yüklemesi; gerçekleştiremiyor varsa ancak bunun yerine, tutarlı bir şekilde .NET Core CLI'ın şu anda istenen sürümünü yüklemek için kullanılacak hangi komut satırı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-155">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="3b9cb-156">Sürüm belirtirseniz, örneğin `latest`, böylece bu komut bir yapı komut dosyasında belirleyici biçimde kullanılabilir belirli sürümünü içeren bir bağlantı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-156">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="3b9cb-157">Yükleme veya kendiniz indirmek isterseniz de ikilinin konumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-157">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="3b9cb-158">Ayarlama, önek/InstallDir dışarı aktarılmaz varsa yolu geçerli oturum için.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-158">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="3b9cb-159">Varsayılan olarak, CLI araçlarını hemen yüklendikten sonra kullanılabilir hale getirir yolu komut dosyasını değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-159">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="3b9cb-160">Azure URL'si için yükleyici akış belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-160">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="3b9cb-161">Bu değeri değiştirmek önerilmez.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-161">It isn't recommended that you change this value.</span></span> <span data-ttu-id="3b9cb-162">Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-162">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="3b9cb-163">Ayarlama, yükleyici web isteklerini yaparken proxy kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="3b9cb-164">(Yalnızca Windows için geçerlidir)</span><span class="sxs-lookup"><span data-stu-id="3b9cb-164">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="3b9cb-165">Tanılama bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-165">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="3b9cb-166">Komut dosyası için Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-166">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="3b9cb-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3b9cb-167">Examples</span></span>

<span data-ttu-id="3b9cb-168">En son uzun vadeli desteklenen (LTS) sürüm, varsayılan konuma geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-168">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="3b9cb-169">Windows:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-169">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="3b9cb-170">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-170">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="3b9cb-171">En son sürümü 2.0 kanala belirtilen konuma yükleyin:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-171">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="3b9cb-172">Windows:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-172">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="3b9cb-173">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-173">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="3b9cb-174">Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-174">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="3b9cb-175">Windows:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-175">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="3b9cb-176">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-176">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="3b9cb-177">Komut dosyasını edinmek ve .NET Core CLI one-liner örnekleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-177">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="3b9cb-178">Windows:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-178">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="3b9cb-179">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="3b9cb-179">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="3b9cb-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9cb-180">See also</span></span>

<span data-ttu-id="3b9cb-181">[.NET core serbest bırakır](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="3b9cb-181">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="3b9cb-182">.NET çekirdeği çalışma zamanı ve SDK arşivi indir</span><span class="sxs-lookup"><span data-stu-id="3b9cb-182">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
