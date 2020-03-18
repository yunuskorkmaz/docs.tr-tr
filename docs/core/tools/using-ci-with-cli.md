---
title: .NET Core SDK ve araçları ile Sürekli Entegrasyon (CI)
description: .NET Core SDK'yı ve araçlarını yapı sunucusunda sürekli tümleştirme ile nasıl kullanacağınızı öğrenin.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451044"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="e5083-103">Sürekli Entegrasyonda .NET Core SDK ve araçları kullanma (CI)</span><span class="sxs-lookup"><span data-stu-id="e5083-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="e5083-104">Bu belge, .NET Core SDK ve araçlarını bir yapı sunucusunda kullanarak özetliyor.</span><span class="sxs-lookup"><span data-stu-id="e5083-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="e5083-105">.NET Core araç kümesi hem etkileşimli olarak çalışır, burada bir geliştirici komut isteminde komut ları yazar ve otomatik olarak, sürekli tümleştirme (CI) sunucusu bir yapı komut dosyası çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="e5083-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="e5083-106">Komutlar, seçenekler, girişler ve çıktılar aynıdır ve sağladığınız tek şey, aracı ve uygulamanızı oluşturmak için bir sistem edinmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="e5083-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="e5083-107">Bu belge, yapı komut dosyalarınızı nasıl tasarlayıp yapılandırılabildiğini anlatan önerileriçeren CI için araç edinme senaryolarına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="e5083-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="e5083-108">CI yapı sunucuları için yükleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5083-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="e5083-109">Yerel yükleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="e5083-109">Using the native installers</span></span>

<span data-ttu-id="e5083-110">MacOS, Linux ve Windows için yerel yükleyiciler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5083-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="e5083-111">Yükleyiciler yapı sunucusuna yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5083-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="e5083-112">Yerel bir yükleyici kullanmanın avantajı, takım çalışması için gereken tüm yerel bağımlılıkları yüklemesidir.</span><span class="sxs-lookup"><span data-stu-id="e5083-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="e5083-113">Yerel yükleyiciler de SDK bir sistem çapında yükleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5083-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="e5083-114">macOS kullanıcıları PKG yükleyicilerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5083-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="e5083-115">Linux'ta, Ubuntu için apt-get veya CentOS için yum gibi bir özet akışı tabanlı paket yöneticisi veya paketlerin kendileri, DEB veya RPM'yi kullanma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="e5083-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="e5083-116">Windows'da MSI yükleyicisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5083-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="e5083-117">En son kararlı ikililer [.NET indirme bulunur.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="e5083-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="e5083-118">En son (ve potansiyel olarak kararsız) ön sürüm aracını kullanmak istiyorsanız, [dotnet/core-sdk GitHub deposunda](https://github.com/dotnet/core-sdk#installers-and-binaries)sağlanan bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5083-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="e5083-119">Linux dağıtımları `tar.gz` için arşivler `tarballs`(diğer adıyla da bilinir) mevcuttur; .NET Core'u yüklemek için arşivdeki yükleme komut dosyalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5083-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="e5083-120">Yükleyici komut dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="e5083-120">Using the installer script</span></span>

<span data-ttu-id="e5083-121">Yükleyici komut dosyasının kullanılması, yapı sunucunuzda yönetim dışı yükleme ve takım oluşturma yı elde etmek için kolay otomasyon sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5083-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="e5083-122">Komut dosyası, aracı indirmeyi ve kullanmak üzere varsayılan veya belirtilen bir konuma çıkarmayı halleder.</span><span class="sxs-lookup"><span data-stu-id="e5083-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="e5083-123">Ayrıca, yüklemek istediğiniz aracın bir sürümünü ve tüm SDK'yı mı yoksa yalnızca paylaşılan çalışma süresini mi yüklemek istediğinizi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5083-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="e5083-124">Yükleyici komut dosyası, SDK'nın istenen sürümünü almak ve yüklemek için yapının başında çalışmak üzere otomatikleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e5083-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="e5083-125">*İstenilen sürüm,* projelerinizin oluşturması gereken SDK'nın ne reisiyse odur.</span><span class="sxs-lookup"><span data-stu-id="e5083-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="e5083-126">Komut dosyası, SDK'yı sunucudaki yerel bir dizine yüklemenize, yüklenen konumdan araçları çalıştırmanıza ve yapıdan sonra temizlemenize (veya CI hizmetinin temizlenmesine izin vermenize) olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e5083-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="e5083-127">Bu, tüm yapı işleminize kapsülleme ve yalıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5083-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="e5083-128">Yükleme komut dosyası başvurusu [dotnet yükleme](dotnet-install-script.md) makalesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5083-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="e5083-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="e5083-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="e5083-130">Yükleyici komut dosyasını kullanırken, yerel bağımlılıklar otomatik olarak yüklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e5083-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="e5083-131">İşletim sistemi bunlara sahip değilse, yerel bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5083-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="e5083-132">Daha fazla bilgi için [bkz.](../install/dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="e5083-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="e5083-133">CI kurulum örnekleri</span><span class="sxs-lookup"><span data-stu-id="e5083-133">CI setup examples</span></span>

<span data-ttu-id="e5083-134">Bu bölümde, powershell veya bash komut dosyası kullanılarak yapılan el ile kurulum ve hizmet (SaaS) CI çözümleri olarak çeşitli yazılımların tanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5083-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="e5083-135">SaaS CI çözümleri kaplı [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Azure Boru Hatları](https://docs.microsoft.com/azure/devops/pipelines/index)vardır.</span><span class="sxs-lookup"><span data-stu-id="e5083-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="e5083-136">Manuel kurulum</span><span class="sxs-lookup"><span data-stu-id="e5083-136">Manual setup</span></span>

<span data-ttu-id="e5083-137">Her SaaS hizmetinin bir yapı işlemi oluşturmak ve yapılandırmak için kendi yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e5083-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="e5083-138">Listelenenlerden farklı SaaS çözümü kullanıyorsanız veya önceden paketlenmiş desteğin ötesinde özelleştirme gerektiriyorsanız, en azından bazı el ile yapılandırma gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5083-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="e5083-139">Genel olarak, el ile kurulum, araçların (veya araçların en son gece yapılarını) bir sürümünü edinmenizi ve yapı komut dosyanızı çalıştırmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5083-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="e5083-140">.NET Core komutlarını düzenlemek için powershell veya bash komut dosyası kullanabilir veya yapı işlemini özetleyen bir proje dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5083-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="e5083-141">[Orkestrasyon bölümü](#orchestrating-the-build) bu seçenekler hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5083-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="e5083-142">Manuel CI build sunucu kurulumu gerçekleştiren bir komut dosyası oluşturduktan sonra, kodunuzu test amacıyla yerel olarak oluşturmak için geliştirme makinenizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5083-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="e5083-143">Komut dosyasının yerel olarak iyi çalıştığını doğruladıktan sonra, komut dosyasını CI yapı sunucunuza dağıtın.</span><span class="sxs-lookup"><span data-stu-id="e5083-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="e5083-144">Nispeten basit bir PowerShell komut dosyası ,NET Core SDK'nın nasıl elde edilip Windows build sunucusuna yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e5083-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="e5083-145">Komut dosyasının sonunda yapı işleminiz için uygulama sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e5083-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="e5083-146">Komut dosyası araçları edinir ve sonra yapı işleminizi yürütür.</span><span class="sxs-lookup"><span data-stu-id="e5083-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="e5083-147">UNIX makineleri için aşağıdaki bash komut dosyası PowerShell komut dosyasında açıklanan eylemleri benzer bir şekilde gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e5083-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="e5083-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="e5083-148">Travis CI</span></span>

<span data-ttu-id="e5083-149">[Travis CI'yi](https://travis-ci.org/) `csharp` dili ve `dotnet` anahtarı kullanarak .NET Core SDK'yı yükecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5083-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="e5083-150">Daha fazla bilgi için, [C#, F#veya Visual Basic Project oluşturma](https://docs.travis-ci.com/user/languages/csharp/)yla ilgili resmi Travis CI dokümanlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="e5083-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="e5083-151">Topluluk tarafından korunan `language: csharp` dil tanımlayıcısının F#ve Mono dahil olmak üzere tüm .NET dilleri için çalıştığını Travis CI bilgilerine erişirken not edin.</span><span class="sxs-lookup"><span data-stu-id="e5083-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="e5083-152">Travis CI, uygulamanız için yapı kombinasyonlarınızı kapsayacak şekilde çalışma süresi, ortam ve dışlamaların/dahil etmelerin bir birleşimini belirttiğiniz bir *yapı matrisinde*hem macOS hem de Linux işlerini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e5083-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="e5083-153">Daha fazla bilgi için Travis CI belgelerinde Yapı makalesini [özelleştirmeye](https://docs.travis-ci.com/user/customizing-the-build) bakın.</span><span class="sxs-lookup"><span data-stu-id="e5083-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="e5083-154">MSBuild tabanlı araçlar, paketteki LTS (1.0.x) ve Geçerli (1.1.x) çalışma sürelerini içerir; böylece SDK yükleyerek, oluşturmak için gereken her şeyi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e5083-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="e5083-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="e5083-155">AppVeyor</span></span>

<span data-ttu-id="e5083-156">[AppVeyor](https://www.appveyor.com/) `Visual Studio 2017` yapı işçisi görüntüsü ile .NET Core 1.0.1 SDK yükler.</span><span class="sxs-lookup"><span data-stu-id="e5083-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="e5083-157">.NET Core SDK'nın farklı sürümlerine sahip diğer yapı görüntüleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e5083-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="e5083-158">Daha fazla bilgi için [appveyor.yml örneğine](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve AppVeyor dokümanlarında yapı [işçisi resimleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e5083-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="e5083-159">.NET Core SDK ikilileri yük komut dosyası kullanılarak bir alt dizinde indirilir ve fermuarsız olarak çıkarılır ve ortam değişkenine `PATH` eklenir.</span><span class="sxs-lookup"><span data-stu-id="e5083-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="e5083-160">.NET Core SDK'nın birden çok sürümüyle tümleştirme testleri çalıştırmak için bir yapı matrisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5083-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="e5083-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e5083-161">Azure DevOps Services</span></span>

<span data-ttu-id="e5083-162">Azure DevOps Hizmetlerini bu yaklaşımlardan birini kullanarak .NET Core projeleri oluşturmak için yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="e5083-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="e5083-163">Komutlarınızı kullanarak komut dosyasını [el ile kurulum adımından](#manual-setup) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5083-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="e5083-164">.NET Core araçlarını kullanacak şekilde yapılandırılan birkaç Azure DevOps Hizmeti yerleşik yapı görevlerinden oluşan bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5083-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="e5083-165">Her iki çözüm de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e5083-165">Both solutions are valid.</span></span> <span data-ttu-id="e5083-166">El ile kurulum komut dosyası kullanarak, bunları yapının bir parçası olarak karşıdan yüklediğiniz için aldığınız araçların sürümünü denetlersiniz.</span><span class="sxs-lookup"><span data-stu-id="e5083-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="e5083-167">Yapı, oluşturmanız gereken bir komut dosyasından çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e5083-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="e5083-168">Bu makale yalnızca el ile seçeneğini kapsar.</span><span class="sxs-lookup"><span data-stu-id="e5083-168">This article only covers the manual option.</span></span> <span data-ttu-id="e5083-169">Azure DevOps Hizmetleri ile oluşturma görevleri oluşturma hakkında daha fazla bilgi için [Azure Ardışık Hatları](https://docs.microsoft.com/azure/devops/pipelines/index) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e5083-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="e5083-170">Azure DevOps Hizmetleri'nde el ile kurulum komut dosyası kullanmak için yeni bir yapı tanımı oluşturun ve yapı adımı için çalışacak komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="e5083-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="e5083-171">Bu, Azure DevOps Hizmetleri kullanıcı arabirimi kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="e5083-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="e5083-172">Yeni bir yapı tanımı oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="e5083-172">Start by creating a new build definition.</span></span> <span data-ttu-id="e5083-173">Oluşturmak istediğiniz yapı türünü tanımlama seçeneği sunan ekrana ulaştığınızda **Boşver** seçeneğini seçin.</span><span class="sxs-lookup"><span data-stu-id="e5083-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Boş yapı tanımı seçme](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="e5083-175">Depoyu oluşturmak üzere yapılandırdıktan sonra yapı tanımlarına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5083-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="e5083-176">**Yapı adımEkle'yi**seçin :</span><span class="sxs-lookup"><span data-stu-id="e5083-176">Select **Add build step**:</span></span>

   ![Yapı adımı ekleme](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="e5083-178">**Size Görev kataloğu**sunuluyor.</span><span class="sxs-lookup"><span data-stu-id="e5083-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="e5083-179">Katalog, yapıda kullandığınız görevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e5083-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="e5083-180">Bir komut dosyanız olduğundan, PowerShell için **Ekle** düğmesini **seçin: PowerShell komut dosyası çalıştırın.**</span><span class="sxs-lookup"><span data-stu-id="e5083-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![PowerShell komut dosyası adımı ekleme](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="e5083-182">Yapı adımını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e5083-182">Configure the build step.</span></span> <span data-ttu-id="e5083-183">Oluşturmakta olduğunuz depodan komut dosyasını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5083-183">Add the script from the repository that you're building:</span></span>

   ![Çalışacak PowerShell komut dosyasını belirtme](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="e5083-185">Yapıyı düzenleme</span><span class="sxs-lookup"><span data-stu-id="e5083-185">Orchestrating the build</span></span>

<span data-ttu-id="e5083-186">Bu belgenin çoğu ,NET Core araçlarını nasıl edineceklerini ve kodunuzu .NET Core ile nasıl düzenleyecekleriniz veya *gerçekte nasıl oluşturabileceğiniz*hakkında bilgi vermeden çeşitli CI hizmetlerini nasıl yapılandırabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5083-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="e5083-187">Yapı sürecinin nasıl yapılandırılabildiği konusundaki seçimler, burada genel bir şekilde ele alınabilen birçok etkene bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5083-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="e5083-188">Yapılarınızı her teknolojiyle düzenleme hakkında daha fazla bilgi için Travis [CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)dokümantasyon kümelerinde sağlanan kaynakları ve örnekleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="e5083-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="e5083-189">.NET Core araçlarını kullanarak .NET Core kodunun yapılandırılmasında aldığınız iki genel yaklaşım, MSBuild'i doğrudan veya .NET Core komut satırı komutlarını kullanmakta.</span><span class="sxs-lookup"><span data-stu-id="e5083-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="e5083-190">Hangi yaklaşımı almanız gerektiği, karmaşıklıktaki yaklaşımlar ve dengelerle konfor seviyenize göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e5083-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="e5083-191">MSBuild, yapı işleminizi görev ve hedef olarak ifade etme olanağı sağlar, ancak MSBuild proje dosya sözdizimini öğrenmenin ek karmaşıklığıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="e5083-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="e5083-192">.NET Core komut satırı araçlarını kullanmak belki daha kolaydır, ancak powershell gibi `bash` bir komut dosyası dilinde düzenleme mantığı yazmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5083-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5083-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5083-193">See also</span></span>

- [<span data-ttu-id="e5083-194">.NET indirme - Linux</span><span class="sxs-lookup"><span data-stu-id="e5083-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
