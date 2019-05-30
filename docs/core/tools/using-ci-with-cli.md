---
title: Sürekli Tümleştirme (CI içinde) kullanarak, .NET Core SDK'sı ve araçları
description: .NET Core SDK'sı ve araçları yapı sunucusunda'nın kullanımı hakkında bilgi.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 629b7a9e1f2b59981adb77ab4d3125be7036ff02
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299964"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="ca535-103">Sürekli Tümleştirme (CI içinde) kullanarak, .NET Core SDK'sı ve araçları</span><span class="sxs-lookup"><span data-stu-id="ca535-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="ca535-104">Bu belge, bir yapı sunucusu üzerinde .NET Core SDK'sı ve araçları kullanarak özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca535-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="ca535-105">.NET Core araç takımı works hem etkileşimli olarak burada bir geliştirici komutları bir komut istemi ve otomatik olarak bir sürekli tümleştirme (CI) sunucusu burada türleri bir yapı betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ca535-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="ca535-106">Komutlarını, seçeneklerini, girdileri ve çıktıları aynıdır ve araçları ve uygulamanızı oluşturmak için bir sistem edinmenin yolunu sağlamanız yalnızca gerekenler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="ca535-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="ca535-107">Bu belge tasarım ve derleme betiklerinizde yapısı hakkında önerilerle senaryoları için CI aracı alım odaklanır.</span><span class="sxs-lookup"><span data-stu-id="ca535-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="ca535-108">Yükleme seçenekleri için CI yapı sunucusu</span><span class="sxs-lookup"><span data-stu-id="ca535-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="ca535-109">Yerel yükleyicilerden kullanma</span><span class="sxs-lookup"><span data-stu-id="ca535-109">Using the native installers</span></span>

<span data-ttu-id="ca535-110">Yerel yükleyicilerden, macOS, Linux ve Windows için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca535-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="ca535-111">Yükleyiciler, yapı sunucusunda yönetici (sudo) erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ca535-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="ca535-112">Yerel bir yükleyici kullanmanın avantajı tüm araçları çalıştırmak gerekli yerel bağımlılıkları yükler ' dir.</span><span class="sxs-lookup"><span data-stu-id="ca535-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="ca535-113">Yerel yükleyicilerden da SDK'sı sistem genelinde yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca535-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="ca535-114">macOS kullanıcılarını PKG yükleyicileri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca535-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="ca535-115">Linux üzerinde Ubuntu için apt-get veya CentOS için yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak veya paketlerini kendileri DEB veya RPM kullanma seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="ca535-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="ca535-116">Windows üzerinde MSI yükleyicisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca535-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="ca535-117">En son kararlı ikili dosyaları adresten [.NET indirir](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="ca535-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="ca535-118">En son (ve büyük olasılıkla kararsız) yayın öncesi araçları kullanmak isterseniz, verilen bağlantıları kullanın [dotnet/core-SDK'sı GitHub deposu](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="ca535-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="ca535-119">Linux dağıtımları için `tar.gz` arşivler (olarak da bilinen `tarballs`) mevcuttur; yükleme betikleri arşivleri içinde .NET Core yüklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca535-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="ca535-120">Yükleyici komut dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="ca535-120">Using the installer script</span></span>

<span data-ttu-id="ca535-121">Yapı sunucunuz ile araçları almak için kolay Otomasyon yönetici olmayan yüklenmek üzere yükleyicisi betiği kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca535-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="ca535-122">Komut dosyası araçları indirme ve onu bir varsayılan veya kullanım için belirtilen konuma ayıklayın üstlenir.</span><span class="sxs-lookup"><span data-stu-id="ca535-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="ca535-123">Yüklemek istediğiniz araçlar ve tüm SDK'sı veya paylaşılan çalışma zamanı yüklemek isteyip istemediğinizi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca535-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="ca535-124">Getirmek ve istenen SDK sürümünü yüklemek için yapılandırmanın başında çalıştırılacak komut dosyası yükleyici otomatik.</span><span class="sxs-lookup"><span data-stu-id="ca535-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="ca535-125">*İstenen sürüm* oluşturmak için gereksinim duyduğunuz SDK sürümüyle projelerinizi olduğu.</span><span class="sxs-lookup"><span data-stu-id="ca535-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="ca535-126">Betik, sunucu üzerindeki yerel bir dizinde SDK'yı yükleme, araçları yüklü konumdan çalıştırın ve ardından temizleme (veya CI service gerisini halleder temizleme) yapıdan sonra sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca535-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="ca535-127">Bu, derleme işlemi kapsülleme ve tüm yalıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca535-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="ca535-128">Yükleme komut dosyası başvurusu bulundu [dotnet yükleme](dotnet-install-script.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="ca535-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="ca535-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="ca535-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="ca535-130">Yükleyici komut dosyası kullanırken, yerel bağımlılıkları otomatik olarak yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="ca535-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="ca535-131">İşletim sisteminin bunları yoksa yerel bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca535-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="ca535-132">Daha fazla bilgi için [Linux üzerinde .NET Core önkoşulları](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="ca535-132">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="ca535-133">CI Kurulum örnekleri</span><span class="sxs-lookup"><span data-stu-id="ca535-133">CI setup examples</span></span>

<span data-ttu-id="ca535-134">Bu bölümde, çeşitli yazılım olarak hizmet (SaaS) CI çözümleri açıklamalarıyla birlikte bir PowerShell veya bash komut dosyası kullanarak bir el ile Kurulum açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca535-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="ca535-135">Kapsanan SaaS CI çözümler [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Azure işlem hatları](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="ca535-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="ca535-136">El ile Kurulum</span><span class="sxs-lookup"><span data-stu-id="ca535-136">Manual setup</span></span>

<span data-ttu-id="ca535-137">Her SaaS hizmeti oluşturma ve bir yapı işlemi yapılandırma kendi yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ca535-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="ca535-138">Listelenenden farklı SaaS çözümü kullanın veya özelleştirme ötesinde önceden paketlenmiş destek gerektiren, en azından bazı el ile yapılandırma gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="ca535-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="ca535-139">Genel olarak, el ile Kurulum Araçlar'ı (ya da Araçları'nın en son gecelik derlemeleri) sürümünü almak ve derleme betiğinizin çalıştırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ca535-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="ca535-140">Bir PowerShell veya bash betiği, .NET Core komutları düzenlemek ya da yapı işlemi özetleyen bir proje dosyası kullanmak üzere kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca535-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="ca535-141">[Düzenleme bölümünde](#orchestrating-the-build) Bu seçenekler hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca535-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="ca535-142">CI yapı Sunucusu Kurulumu el ile gerçekleştiren bir komut dosyası oluşturduktan sonra geliştirme makinenizde yerel olarak test etmek için kodunuzu derlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca535-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="ca535-143">Komut dosyası da yerel olarak çalıştığını doğruladıktan sonra CI yapı sunucunuzu dağıtın.</span><span class="sxs-lookup"><span data-stu-id="ca535-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="ca535-144">Görece basit bir PowerShell Betiği, bir Windows yapı sunucusuna yükleyin ve .NET Core SDK'sını elde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ca535-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="ca535-145">Yapı işleminizin betiğinin sonunda uygulaması sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ca535-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="ca535-146">Komut dosyası araçları edinme ve yapı işleminizin ardından yürütür.</span><span class="sxs-lookup"><span data-stu-id="ca535-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="ca535-147">UNIX makineler için aşağıdaki bash betiğini PowerShell betiğini benzer bir şekilde açıklanan eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ca535-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="ca535-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="ca535-148">Travis CI</span></span>

<span data-ttu-id="ca535-149">Yapılandırabileceğiniz [Travis CI](https://travis-ci.org/) .NET Core SDK'sını kullanarak yüklemek için `csharp` dil ve `dotnet` anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ca535-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="ca535-150">Daha fazla bilgi için resmi Travis CI belgeleri görmek [yapı bir C#, F#, veya Visual Basic projesi](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="ca535-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="ca535-151">Travis CI bilgileri erişim unutmayın, topluluk tarafından tutulan `language: csharp` dahil olmak üzere tüm .NET dilleri için bir dil tanımlayıcısı çalışır F#ve Mono.</span><span class="sxs-lookup"><span data-stu-id="ca535-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="ca535-152">Travis CI, macOS ve Linux işlerinde hem çalışan bir *matris derleme*, çalışma zamanı ortamı ve uygulamanız için derleme birleşimleri karşılamak için özel durumlar/eklemeleri bir birleşimini belirttiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="ca535-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="ca535-153">Daha fazla bilgi için [yapı özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) makalede Travis CI belgeleri.</span><span class="sxs-lookup"><span data-stu-id="ca535-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="ca535-154">MSBuild tabanlı araçlar LTS (1.0.x kullanılır) ve geçerli (1.1.x) çalışma zamanları paket içerisine dâhil; SDK'sını yükleyerek oluşturmak için ihtiyacınız olan her şey aldığınız şekilde.</span><span class="sxs-lookup"><span data-stu-id="ca535-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="ca535-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="ca535-155">AppVeyor</span></span>

<span data-ttu-id="ca535-156">[AppVeyor](https://www.appveyor.com/) .NET Core 1.0.1 yükler SDK'sı ile `Visual Studio 2017` çalışan görüntüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca535-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="ca535-157">Diğer derleme görüntüleri farklı sürümleri .NET Core SDK'sı ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca535-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="ca535-158">Daha fazla bilgi için [appveyor.yml örnek](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [derleme çalışan görüntüleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) AppVeyor docs makalesinde.</span><span class="sxs-lookup"><span data-stu-id="ca535-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="ca535-159">.NET Core SDK'sı ikili dosyaları indirilir ve yükleme betiğini kullanarak bir alt dizinine geçin ve sonra bunlar için eklenen `PATH` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ca535-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="ca535-160">.NET Core SDK'sını birden çok sürümü ile tümleştirme testleri çalıştırmak için bir derleme matris ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ca535-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="ca535-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="ca535-161">Azure DevOps Services</span></span>

<span data-ttu-id="ca535-162">Azure DevOps Services'ı, Bu yaklaşımlardan birini kullanarak .NET Core projeleri derlemek için yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="ca535-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="ca535-163">Komut dosyasını çalıştırmak [el ile Kurulum adımı](#manual-setup) komutlarınızı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ca535-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="ca535-164">.NET Core Araçları'nı kullanmak üzere yapılandırılmış birden fazla Azure DevOps Hizmetleri yerleşik derleme görevlerini oluşan bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca535-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="ca535-165">Her iki çözüm de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ca535-165">Both solutions are valid.</span></span> <span data-ttu-id="ca535-166">El ile Kurulum betiği kullanarak, yapının bir parçası olarak indirdiğiniz bu yana, aldığınız Araçları sürüm denetimi.</span><span class="sxs-lookup"><span data-stu-id="ca535-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="ca535-167">Derleme, oluşturmanız gereken bir betikten çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="ca535-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="ca535-168">Bu makalede, yalnızca el ile seçeneği kapsar.</span><span class="sxs-lookup"><span data-stu-id="ca535-168">This article only covers the manual option.</span></span> <span data-ttu-id="ca535-169">Derleme görevleri Azure DevOps hizmetleriyle bir derleme oluşturma hakkında daha fazla bilgi için bkz: [Azure işlem hatları](https://docs.microsoft.com/azure/devops/pipelines/index) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="ca535-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="ca535-170">Azure DevOps Hizmetleri'nde el ile Kurulum komut dosyası kullanmak için yeni bir yapı tanımı oluşturma ve derleme adımı için çalıştırılacak komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ca535-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="ca535-171">Bu Azure DevOps Services kullanıcı arabirimi kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="ca535-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="ca535-172">Yeni bir derleme tanımı oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="ca535-172">Start by creating a new build definition.</span></span> <span data-ttu-id="ca535-173">Ne tür bir yapı, istediğiniz oluşturmak Seç tanımlamak için bir seçenek sunar ekran ulaştıktan sonra **boş** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ca535-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Boş bir yapıyı seçerek](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="ca535-175">Depo oluşturmak için yapılandırdıktan sonra yapı tanımlarına ne yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca535-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="ca535-176">Seçin **derleme adımı Ekle**:</span><span class="sxs-lookup"><span data-stu-id="ca535-176">Select **Add build step**:</span></span>

   ![Bir derleme adımı ekleme](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="ca535-178">Eklemediğiniz **görev kataloğundaki**.</span><span class="sxs-lookup"><span data-stu-id="ca535-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="ca535-179">Katalog yapı kullanan görevler içerir.</span><span class="sxs-lookup"><span data-stu-id="ca535-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="ca535-180">Bir komut dosyası olduğundan seçin **Ekle** için düğme **PowerShell: Bir PowerShell Betiği çalıştırmanız**.</span><span class="sxs-lookup"><span data-stu-id="ca535-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Bir PowerShell Betiği adım ekleme](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="ca535-182">Yapı adımının yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ca535-182">Configure the build step.</span></span> <span data-ttu-id="ca535-183">Komut dosyasını oluşturduğunuz depodan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ca535-183">Add the script from the repository that you're building:</span></span>

   ![PowerShell betiğini çalıştırmak için belirtme](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="ca535-185">Yapı işlemlerini</span><span class="sxs-lookup"><span data-stu-id="ca535-185">Orchestrating the build</span></span>

<span data-ttu-id="ca535-186">Bu belge çoğunu açıklar .NET Core araçları edinmek ve bilgiyi nasıl düzenlemek sağlamadan çeşitli CI hizmetlerini yapılandırma veya *gerçekten derleme*, kodunuzu .NET Core ile.</span><span class="sxs-lookup"><span data-stu-id="ca535-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="ca535-187">Yapı işleminin nasıl seçimlerine, aşağıda genel hatlarıyla ele birçok faktöre bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ca535-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="ca535-188">Derlemelerinizi her teknolojisi ile düzenleme hakkında daha fazla bilgi için belge kümelerinde sağlanan örnekleri ve kaynakları keşfedin [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Azure İşlem hatları](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="ca535-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="ca535-189">.NET Core Araçları'nı kullanarak .NET Core kod için yapı işlemini yapılandırırken alan iki genel yaklaşım kullanarak doğrudan MSBuild veya .NET Core komut satırı komutlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ca535-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="ca535-190">Yapmanız gereken hangi yaklaşımın karmaşıklığı yaklaşımları ve dezavantajlarına sahip konfor düzeyinize göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ca535-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="ca535-191">MSBuild görevleri ve hedefleri yapı işleminizi express olanağı sağlar, ancak MSBuild proje dosyası sözdizimi öğrenme eklenen karmaşıklık ile gelir.</span><span class="sxs-lookup"><span data-stu-id="ca535-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="ca535-192">.NET Core komut satırı araçlarını kullanarak belki de daha basit olmakla birlikte, komut dosyası dilinde düzenleme mantığını yazmanızı gerektirir `bash` veya PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca535-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca535-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca535-193">See also</span></span>

- [<span data-ttu-id="ca535-194">.NET indirmeleri - Linux</span><span class="sxs-lookup"><span data-stu-id="ca535-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
