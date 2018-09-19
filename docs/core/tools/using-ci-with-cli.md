---
title: Sürekli Tümleştirme (CI içinde) kullanarak, .NET Core SDK'sı ve araçları
description: .NET Core SDK'sı ve araçları yapı sunucusunda'nın kullanımı hakkında bilgi.
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.openlocfilehash: 207a6740f2a483d532c194b2bf8112898e9c3463
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991356"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="a5de1-103">Sürekli Tümleştirme (CI içinde) kullanarak, .NET Core SDK'sı ve araçları</span><span class="sxs-lookup"><span data-stu-id="a5de1-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="a5de1-104">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a5de1-104">Overview</span></span>

<span data-ttu-id="a5de1-105">Bu belge, bir yapı sunucusu üzerinde .NET Core SDK'sı ve araçları kullanarak özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-105">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="a5de1-106">.NET Core araç takımı works hem etkileşimli olarak burada bir geliştirici komutları bir komut istemi ve otomatik olarak bir sürekli tümleştirme (CI) sunucusu burada türleri bir yapı betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-106">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="a5de1-107">Komutlarını, seçeneklerini, girdileri ve çıktıları aynıdır ve araçları ve uygulamanızı oluşturmak için bir sistem edinmenin yolunu sağlamanız yalnızca gerekenler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-107">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="a5de1-108">Bu belge tasarım ve derleme betiklerinizde yapısı hakkında önerilerle senaryoları için CI aracı alım odaklanır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-108">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="a5de1-109">Yükleme seçenekleri için CI yapı sunucusu</span><span class="sxs-lookup"><span data-stu-id="a5de1-109">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="a5de1-110">Yerel yükleyicilerden kullanma</span><span class="sxs-lookup"><span data-stu-id="a5de1-110">Using the native installers</span></span>

<span data-ttu-id="a5de1-111">Yerel yükleyicilerden, macOS, Linux ve Windows için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-111">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="a5de1-112">Yükleyiciler, yapı sunucusunda yönetici (sudo) erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-112">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="a5de1-113">Yerel bir yükleyici kullanmanın avantajı tüm araçları çalıştırmak gerekli yerel bağımlılıkları yükler ' dir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-113">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="a5de1-114">Yerel yükleyicilerden da SDK'sı sistem genelinde yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5de1-114">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="a5de1-115">macOS kullanıcılarını PKG yükleyicileri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-115">macOS users should use the PKG installers.</span></span> <span data-ttu-id="a5de1-116">Linux üzerinde Ubuntu için apt-get veya CentOS için yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak veya paketlerini kendileri DEB veya RPM kullanma seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="a5de1-116">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="a5de1-117">Windows üzerinde MSI yükleyicisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-117">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="a5de1-118">En son kararlı ikili dosyaları adresten [.NET Core ile çalışmaya başlama](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="a5de1-118">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="a5de1-119">En son (ve büyük olasılıkla kararsız) yayın öncesi araçları kullanmak isterseniz, verilen bağlantıları kullanın [dotnet/CLI GitHub deposu](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="a5de1-119">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="a5de1-120">Linux dağıtımları için `tar.gz` arşivler (olarak da bilinen `tarballs`) mevcuttur; yükleme betikleri arşivleri içinde .NET Core yüklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-120">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="a5de1-121">Yükleyici komut dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="a5de1-121">Using the installer script</span></span>

<span data-ttu-id="a5de1-122">Yapı sunucunuz ile araçları almak için kolay Otomasyon yönetici olmayan yüklenmek üzere yükleyicisi betiği kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5de1-122">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="a5de1-123">Komut dosyası araçları indirme ve onu bir varsayılan veya kullanım için belirtilen konuma ayıklayın üstlenir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-123">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="a5de1-124">Yüklemek istediğiniz araçlar ve tüm SDK'sı veya paylaşılan çalışma zamanı yüklemek isteyip istemediğinizi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5de1-124">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="a5de1-125">Getirmek ve istenen SDK sürümünü yüklemek için yapılandırmanın başında çalıştırılacak komut dosyası yükleyici otomatik.</span><span class="sxs-lookup"><span data-stu-id="a5de1-125">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="a5de1-126">*İstenen sürüm* oluşturmak için gereksinim duyduğunuz SDK sürümüyle projelerinizi olduğu.</span><span class="sxs-lookup"><span data-stu-id="a5de1-126">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="a5de1-127">Betik, sunucu üzerindeki yerel bir dizinde SDK'yı yükleme, araçları yüklü konumdan çalıştırın ve ardından temizleme (veya CI service gerisini halleder temizleme) yapıdan sonra sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5de1-127">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="a5de1-128">Bu, derleme işlemi kapsülleme ve tüm yalıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5de1-128">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="a5de1-129">Yükleme komut dosyası başvurusu bulundu [dotnet yükleme](dotnet-install-script.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a5de1-129">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="a5de1-130">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="a5de1-130">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="a5de1-131">Yükleyici komut dosyası kullanırken, yerel bağımlılıkları otomatik olarak yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-131">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="a5de1-132">İşletim sisteminin bunları yoksa yerel bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-132">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="a5de1-133">Önkoşullar listesine bakın [yerel .NET Core önkoşulları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a5de1-133">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="a5de1-134">CI Kurulum örnekleri</span><span class="sxs-lookup"><span data-stu-id="a5de1-134">CI setup examples</span></span>

<span data-ttu-id="a5de1-135">Bu bölümde, çeşitli yazılım olarak hizmet (SaaS) CI çözümleri açıklamalarıyla birlikte bir PowerShell veya bash komut dosyası kullanarak bir el ile Kurulum açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-135">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="a5de1-136">Kapsanan SaaS CI çözümler [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [ yapı](https://docs.microsoft.com/azure/devops/build-release/index).</span><span class="sxs-lookup"><span data-stu-id="a5de1-136">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [ Build](https://docs.microsoft.com/azure/devops/build-release/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="a5de1-137">El ile Kurulum</span><span class="sxs-lookup"><span data-stu-id="a5de1-137">Manual setup</span></span>

<span data-ttu-id="a5de1-138">Her SaaS hizmeti oluşturma ve bir yapı işlemi yapılandırma kendi yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-138">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="a5de1-139">Listelenenden farklı SaaS çözümü kullanın veya özelleştirme ötesinde önceden paketlenmiş destek gerektiren, en azından bazı el ile yapılandırma gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-139">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="a5de1-140">Genel olarak, el ile Kurulum Araçlar'ı (ya da Araçları'nın en son gecelik derlemeleri) sürümünü almak ve derleme betiğinizin çalıştırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-140">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="a5de1-141">Bir PowerShell veya bash betiği, .NET Core komutları düzenlemek ya da yapı işlemi özetleyen bir proje dosyası kullanmak üzere kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5de1-141">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="a5de1-142">[Düzenleme bölümünde](#orchestrating-the-build) Bu seçenekler hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5de1-142">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="a5de1-143">CI yapı Sunucusu Kurulumu el ile gerçekleştiren bir komut dosyası oluşturduktan sonra geliştirme makinenizde yerel olarak test etmek için kodunuzu derlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-143">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="a5de1-144">Komut dosyası da yerel olarak çalıştığını doğruladıktan sonra CI yapı sunucunuzu dağıtın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-144">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="a5de1-145">Görece basit bir PowerShell Betiği, bir Windows yapı sunucusuna yükleyin ve .NET Core SDK'sını elde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a5de1-145">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="a5de1-146">Yapı işleminizin betiğinin sonunda uygulaması sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-146">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="a5de1-147">Komut dosyası araçları edinme ve yapı işleminizin ardından yürütür.</span><span class="sxs-lookup"><span data-stu-id="a5de1-147">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="a5de1-148">UNIX makineler için aşağıdaki bash betiğini PowerShell betiğini benzer bir şekilde açıklanan eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="a5de1-148">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="a5de1-149">Travis CI</span><span class="sxs-lookup"><span data-stu-id="a5de1-149">Travis CI</span></span>

<span data-ttu-id="a5de1-150">Yapılandırabileceğiniz [Travis CI](https://travis-ci.org/) .NET Core SDK'sını kullanarak yüklemek için `csharp` dil ve `dotnet` anahtarı.</span><span class="sxs-lookup"><span data-stu-id="a5de1-150">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="a5de1-151">Resmi Travis CI belgeleri görmek [bir C#, F # veya Visual Basic projesi oluşturmaya](https://docs.travis-ci.com/user/languages/csharp/) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="a5de1-151">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="a5de1-152">Travis CI bilgileri erişim unutmayın, topluluk tarafından tutulan `language: csharp` dil tanımlayıcısı F # ve Mono dahil olmak üzere tüm .NET dilleri için çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-152">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="a5de1-153">Travis CI çalışır (OS X 10.11, OS X 10.12) hem de macOS ve Linux (Ubuntu 14.04) işler bir *matris derleme*, çalışma zamanı ortamı ve uygulamanız için derleme birleşimleri karşılamak için özel durumlar/eklemeleri bir birleşimini belirttiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-153">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="a5de1-154">Bkz: [. travis.yml örnek](https://github.com/dotnet/docs/blob/master/.travis.yml) dosya ve [yapı özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) içinde daha fazla bilgi için Travis CI belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a5de1-154">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="a5de1-155">MSBuild tabanlı araçlar LTS (1.0.x kullanılır) ve geçerli (1.1.x) çalışma zamanları paket içerisine dâhil; SDK'sını yükleyerek oluşturmak için ihtiyacınız olan her şey aldığınız şekilde.</span><span class="sxs-lookup"><span data-stu-id="a5de1-155">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="a5de1-156">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="a5de1-156">AppVeyor</span></span>

<span data-ttu-id="a5de1-157">[AppVeyor](https://www.appveyor.com/) .NET Core 1.0.1 yükler SDK'sı ile `Visual Studio 2017` çalışan görüntüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5de1-157">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="a5de1-158">Diğer derleme görüntüleri farklı sürümleri .NET Core SDK'sı ile kullanılabilir; bkz [appveyor.yml örnek](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [derleme çalışan görüntüleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) konusunda daha fazla bilgi için AppVeyor belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a5de1-158">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="a5de1-159">.NET Core SDK'sı ikili dosyaları indirilir ve yükleme betiğini kullanarak bir alt dizinine geçin ve sonra bunlar için eklenen `PATH` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a5de1-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="a5de1-160">.NET Core SDK'sını birden çok sürümü ile tümleştirme testleri çalıştırmak için bir derleme matris ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5de1-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="a5de1-161">Azure DevOps Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a5de1-161">Azure DevOps Services</span></span>

<span data-ttu-id="a5de1-162">Azure DevOps Services'ı, Bu yaklaşımlardan birini kullanarak .NET Core projeleri derlemek için yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="a5de1-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="a5de1-163">Komut dosyasını çalıştırmak [el ile Kurulum adımı](#manual-setup) komutlarınızı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a5de1-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="a5de1-164">.NET Core Araçları'nı kullanmak üzere yapılandırılmış birden fazla Azure DevOps Hizmetleri yerleşik derleme görevlerini oluşan bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5de1-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="a5de1-165">Her iki çözüm de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-165">Both solutions are valid.</span></span> <span data-ttu-id="a5de1-166">El ile Kurulum betiği kullanarak, yapının bir parçası olarak indirdiğiniz bu yana, aldığınız Araçları sürüm denetimi.</span><span class="sxs-lookup"><span data-stu-id="a5de1-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="a5de1-167">Derleme, oluşturmanız gereken bir betikten çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="a5de1-168">Bu konu, yalnızca el ile seçeneği içermektedir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-168">This topic only covers the manual option.</span></span> <span data-ttu-id="a5de1-169">Derleme görevleri Azure DevOps hizmetleriyle bir derleme oluşturma hakkında daha fazla bilgi için Azure DevOps hizmetler ziyaret [sürekli tümleştirme ve dağıtım](https://docs.microsoft.com/azure/devops/build-release/index) konu.</span><span class="sxs-lookup"><span data-stu-id="a5de1-169">For more information on composing a build with Azure DevOps Services build tasks, visit the Azure DevOps Services [Continuous integration and deployment](https://docs.microsoft.com/azure/devops/build-release/index) topic.</span></span>

<span data-ttu-id="a5de1-170">Azure DevOps Hizmetleri'nde el ile Kurulum komut dosyası kullanmak için yeni bir yapı tanımı oluşturma ve derleme adımı için çalıştırılacak komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a5de1-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="a5de1-171">Bu Azure DevOps Services kullanıcı arabirimi kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a5de1-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="a5de1-172">Yeni bir derleme tanımı oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-172">Start by creating a new build definition.</span></span> <span data-ttu-id="a5de1-173">Ne tür bir yapı, istediğiniz oluşturmak Seç tanımlamak için bir seçenek sunar ekran ulaştıktan sonra **boş** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a5de1-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Boş bir yapıyı seçerek](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="a5de1-175">Depo oluşturmak için yapılandırdıktan sonra yapı tanımlarına ne yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5de1-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="a5de1-176">Seçin **derleme adımı Ekle**:</span><span class="sxs-lookup"><span data-stu-id="a5de1-176">Select **Add build step**:</span></span>

   ![Bir derleme adımı ekleme](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="a5de1-178">Eklemediğiniz **görev kataloğundaki**.</span><span class="sxs-lookup"><span data-stu-id="a5de1-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="a5de1-179">Katalog yapı kullanan görevler içerir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="a5de1-180">Bir komut dosyası olduğundan seçin **Ekle** için düğme **PowerShell: bir PowerShell Betiği çalıştırmanız**.</span><span class="sxs-lookup"><span data-stu-id="a5de1-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Bir PowerShell Betiği adım ekleme](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="a5de1-182">Yapı adımının yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a5de1-182">Configure the build step.</span></span> <span data-ttu-id="a5de1-183">Komut dosyasını oluşturduğunuz depodan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5de1-183">Add the script from the repository that you're building:</span></span>

   ![PowerShell betiğini çalıştırmak için belirtme](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="a5de1-185">Yapı işlemlerini</span><span class="sxs-lookup"><span data-stu-id="a5de1-185">Orchestrating the build</span></span>

<span data-ttu-id="a5de1-186">Bu belge çoğunu açıklar .NET Core araçları edinmek ve bilgiyi nasıl düzenlemek sağlamadan çeşitli CI hizmetlerini yapılandırma veya *gerçekten derleme*, kodunuzu .NET Core ile.</span><span class="sxs-lookup"><span data-stu-id="a5de1-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="a5de1-187">Yapı işleminin nasıl seçimlerine, aşağıda genel hatlarıyla ele birçok faktöre bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a5de1-187">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="a5de1-188">Kaynaklar ve belge kümelerinde sağlanan örnekleri keşfedin [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Azure DevOps Hizmetleri](https://docs.microsoft.com/azure/devops/build-release/index) düzenleme hakkında daha fazla bilgi için Her bir teknolojiyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5de1-188">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/index) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="a5de1-189">.NET Core Araçları'nı kullanarak .NET Core kod için yapı işlemini yapılandırırken alan iki genel yaklaşım kullanarak doğrudan MSBuild veya .NET Core komut satırı komutlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a5de1-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="a5de1-190">Yapmanız gereken hangi yaklaşımın karmaşıklığı yaklaşımları ve dezavantajlarına sahip konfor düzeyinize göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="a5de1-191">MSBuild görevleri ve hedefleri yapı işleminizi express olanağı sağlar, ancak MSBuild proje dosyası sözdizimi öğrenme eklenen karmaşıklık ile gelir.</span><span class="sxs-lookup"><span data-stu-id="a5de1-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="a5de1-192">.NET Core komut satırı araçlarını kullanarak belki de daha basit olmakla birlikte, komut dosyası dilinde düzenleme mantığını yazmanızı gerektirir `bash` veya PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5de1-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5de1-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5de1-193">See also</span></span>

* [<span data-ttu-id="a5de1-194">Ubuntu alma adımları</span><span class="sxs-lookup"><span data-stu-id="a5de1-194">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)
