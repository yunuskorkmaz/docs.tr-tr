---
title: ".NET Core SDK'yı ve araçları sürekli tümleştirme (CI içinde) kullanma"
description: ".NET Core SDK ve araçlarını derleme sunucusundaki kullanımı hakkında bilgi."
keywords: ".NET, .NET core, sürekli tümleştirme, CI, yapı, otomasyon, Travis CI, AppVeyor, Visual Studio Team Services, vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.openlocfilehash: 596bc689e423082dcae0c79801e9f796b398391e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="ed099-104">.NET Core SDK'yı ve araçları sürekli tümleştirme (CI içinde) kullanma</span><span class="sxs-lookup"><span data-stu-id="ed099-104">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="ed099-105">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed099-105">Overview</span></span>

<span data-ttu-id="ed099-106">Bu belge, bir derleme sunucuda .NET Core SDK ve araçlarını kullanma özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed099-106">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="ed099-107">.NET Core araç takımı works hem etkileşimli olarak, burada bir geliştirici komutları komut istemine komut isteminde ve otomatik olarak bir sürekli tümleştirme (CI) sunucusu burada türleri bir yapı komut dosyasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ed099-107">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="ed099-108">Komutları, seçenekleri, girişleri ve çıkışları aynıdır ve sağladığınız yalnızca araçları ve uygulamanızı oluşturmak için bir sistem edinmenin yolunu noktalardır.</span><span class="sxs-lookup"><span data-stu-id="ed099-108">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="ed099-109">Bu belge CI için aracı alım senaryoları tasarım ve yapı komut dosyalarınızı yapısı hakkında öneriler odaklanır.</span><span class="sxs-lookup"><span data-stu-id="ed099-109">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="ed099-110">CI için yükleme seçeneklerini sunucuları derleme</span><span class="sxs-lookup"><span data-stu-id="ed099-110">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="ed099-111">Yerel yükleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="ed099-111">Using the native installers</span></span>

<span data-ttu-id="ed099-112">Yerel yükleyicileri macOS, Linux ve Windows için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed099-112">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="ed099-113">Yükleyicileri yapı sunucuya yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ed099-113">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="ed099-114">Yerel bir yükleyici kullanmanın avantajı tüm araçları çalıştırmak gerekli yerel bağımlılıkları yükler ' dir.</span><span class="sxs-lookup"><span data-stu-id="ed099-114">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="ed099-115">Yerel yükleyicileri da SDK'ın bir sistem genelinde yüklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-115">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="ed099-116">macOS kullanıcıları PKG yükleyicileri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed099-116">macOS users should use the PKG installers.</span></span> <span data-ttu-id="ed099-117">Linux üzerinde get apt Ubuntu için veya CentOS, yum gibi bir akış tabanlı Paket Yöneticisi veya paketleri kendileri DEB veya RPM kullanarak seçeneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="ed099-117">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="ed099-118">Windows üzerinde MSI yükleyicisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed099-118">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="ed099-119">En son kararlı ikili dosyaları bulunan [.NET Core ile çalışmaya başlama](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="ed099-119">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="ed099-120">En son (ve büyük olasılıkla kararsız) yayın öncesi araçları kullanmak isterseniz, verilen bağlantıları kullanın [dotnet/CLI GitHub deposunu](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="ed099-120">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="ed099-121">Linux dağıtımları için `tar.gz` arşivler (olarak da bilinen `tarballs`) kullanılabilir; .NET Core yüklemek için yükleme komut dosyaları arşivler içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed099-121">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="ed099-122">Yükleyici komut dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="ed099-122">Using the installer script</span></span>

<span data-ttu-id="ed099-123">Yükleyici komut dosyası kullanarak derleme sunucunuz ve araçları alma kolay Otomasyon yönetimsel olmayan yükleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-123">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="ed099-124">Komut dosyası araçları yükleme ve onu bir varsayılan veya kullanım için belirtilen konum ayıklayın ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="ed099-124">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="ed099-125">Bir sürümünü yüklemek istediğiniz araçları ve tüm SDK veya yalnızca paylaşılan çalışma yüklemek isteyip istemediğinizi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed099-125">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="ed099-126">Yükleyicisi betiği fetch ve SDK istenen sürümü yüklemek için yapı başlangıcında çalıştırmak için otomatik hale getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed099-126">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="ed099-127">*İstediğiniz sürümü* oluşturmak için seçtiğiniz sürüm SDK'sının projelerinizi gerektir değil.</span><span class="sxs-lookup"><span data-stu-id="ed099-127">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="ed099-128">Komut dosyası, sunucu üzerindeki yerel bir dizinde SDK'sını yükleyin, araçları yüklü konumundan çalıştırın ve sonra temizleme (veya CI hizmeti sağlayan temizleme) derleme sonrası sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-128">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="ed099-129">Bu derleme işlemi kapsülleme ve bütün yalıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-129">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="ed099-130">Yükleme komut dosyası başvurusu bulunan [dotnet yükleme](dotnet-install-script.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ed099-130">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="ed099-131">Yükleyici komut dosyası kullanırken, yerel bağımlılıkları otomatik olarak yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="ed099-131">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="ed099-132">İşletim sisteminin bunları yoksa yerel bağımlılıkları yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed099-132">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="ed099-133">Önkoşullar listesine bakın [.NET Core Yerel Önkoşullar](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ed099-133">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="ed099-134">CI Kurulum örnekleri</span><span class="sxs-lookup"><span data-stu-id="ed099-134">CI setup examples</span></span>

<span data-ttu-id="ed099-135">Bu bölümde, çeşitli yazılım açıklamasını hizmet (SaaS) CI çözümleri olarak birlikte PowerShell veya bash bir betik kullanarak el ile kuruluma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed099-135">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="ed099-136">Kapsanan SaaS CI çözümleri [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Visual Studio Team Services yapı](https://www.visualstudio.com/docs/build/overview).</span><span class="sxs-lookup"><span data-stu-id="ed099-136">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="ed099-137">El ile Kurulum</span><span class="sxs-lookup"><span data-stu-id="ed099-137">Manual setup</span></span>

<span data-ttu-id="ed099-138">Her SaaS hizmet oluşturma ve derleme sürecinde yapılandırma kendi yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ed099-138">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="ed099-139">Listelenenden farklı SaaS çözümü veya önceden paketlenmiş destek ötesinde özelleştirme gerektiren kullanıyorsanız, en az bazı el ile yapılandırma gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="ed099-139">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="ed099-140">Genel olarak, el ile kuruluma Araçlar (veya Araçları'nın en son gecelik derlemeleri) sürümünü edinin ve derleme betiğinizin çalıştırmak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ed099-140">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="ed099-141">Bir PowerShell veya bash derleme süreci özetlenmektedir bir proje dosyasını kullanmanız veya .NET Core komutları düzenlemek için komut dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed099-141">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="ed099-142">[Orchestration bölüm](#orchestrating-the-build) Bu seçenekler hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-142">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="ed099-143">CI yapı Sunucusu Kurulumu el ile gerçekleştiren bir komut dosyası oluşturduktan sonra geliştirme makinenizde yerel olarak test etmek için kodunuzu oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed099-143">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="ed099-144">Komut dosyası da yerel olarak çalıştığı onaylandıktan sonra CI yapı sunucunuza dağıtın.</span><span class="sxs-lookup"><span data-stu-id="ed099-144">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="ed099-145">Görece basit bir PowerShell komut dosyası, .NET Core SDK edinme ve bir Windows yapı sunucuya yüklemek gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ed099-145">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="ed099-146">Yapı işleminizin betik sonunda için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed099-146">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="ed099-147">Komut dosyası araçları edinir ve yapı işleminizin yürütür.</span><span class="sxs-lookup"><span data-stu-id="ed099-147">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="ed099-148">UNIX makineler için aşağıdaki bash betiği PowerShell Betiği benzer bir şekilde açıklanan eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ed099-148">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="ed099-149">Travis CI</span><span class="sxs-lookup"><span data-stu-id="ed099-149">Travis CI</span></span>

<span data-ttu-id="ed099-150">Yapılandırabileceğiniz [Travis CI](https://travis-ci.org/) .NET Core SDK'sını kullanarak yüklemek için `csharp` dil ve `dotnet` anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ed099-150">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="ed099-151">Resmi Travis CI belgeleri bakın [bir C#, F # veya Visual Basic proje oluşturma](https://docs.travis-ci.com/user/languages/csharp/) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="ed099-151">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="ed099-152">Not Travis CI bilgilere erişme gibi topluluk tarafından tutulan `language: csharp` dil tanımlayıcısını F # ve Mono dahil olmak üzere tüm .NET dilleri için çalışır.</span><span class="sxs-lookup"><span data-stu-id="ed099-152">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="ed099-153">Travis CI hem macOS (OS X 10.11 sürümünü, OS X 10,12) çalıştıran ve Linux (Ubuntu 14.04) işleri bir *matris yapı*çalışma zamanı ortamı ve uygulamanız için derleme birleşimleri karşılamak üzere özel durumlar/içermeler bileşimini burada belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed099-153">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="ed099-154">Bkz: [. travis.yml örnek](https://github.com/dotnet/docs/blob/master/.travis.yml) dosya ve [yapı özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) daha fazla bilgi için Travis CI belgeleri içinde.</span><span class="sxs-lookup"><span data-stu-id="ed099-154">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="ed099-155">MSBuild tabanlı araçlar LTS (1.0.x) ve geçerli (1.1.x) çalışma zamanları pakete dahil; SDK yükleyerek oluşturmak için gereken her şeyi aldığınız şekilde.</span><span class="sxs-lookup"><span data-stu-id="ed099-155">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="ed099-156">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="ed099-156">AppVeyor</span></span>

<span data-ttu-id="ed099-157">[AppVeyor](https://www.appveyor.com/) .NET Core 1.0.1 yükler SDK ile `Visual Studio 2017` çalışan görüntüsünü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed099-157">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="ed099-158">.NET Core SDK farklı sürümlerini diğer yapı görüntülerle kullanılabilir; bkz: [appveyor.yml örnek](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [yapı çalışan görüntüleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) konusunda daha fazla bilgi için AppVeyor belgeleri.</span><span class="sxs-lookup"><span data-stu-id="ed099-158">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="ed099-159">.NET Core SDK ikili dosyaları indirilir ve yükleme komut dosyası kullanarak bir alt dizinde sıkıştırması açılmış ve ardından eklenmiş `PATH` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ed099-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="ed099-160">.NET Core SDK birden çok sürümü ile tümleştirme testleri çalıştırmak için bir yapı matris ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ed099-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="ed099-161">Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="ed099-161">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="ed099-162">Visual Studio Team Services (Bu yaklaşımlardan birini kullanarak .NET Core projeler derlemek için VSTS) yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="ed099-162">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="ed099-163">Komut dosyasını çalıştırmak [el ile kuruluma adım](#manual-setup) , komutları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ed099-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="ed099-164">.NET Core araçları kullanmak üzere yapılandırılmış birkaç VSTS yerleşik yapı görevlerin oluşan bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed099-164">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="ed099-165">Her iki çözüm de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ed099-165">Both solutions are valid.</span></span> <span data-ttu-id="ed099-166">El ile Kurulum betiği kullanarak, bunları derleme bir parçası olarak indirmek bu yana, aldığınız araçları sürümünü denetler.</span><span class="sxs-lookup"><span data-stu-id="ed099-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="ed099-167">Yapı oluşturmanız gereken bir komut dosyasından çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ed099-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="ed099-168">Bu konuda, yalnızca el ile seçeneği ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed099-168">This topic only covers the manual option.</span></span> <span data-ttu-id="ed099-169">Derleme görevleri VSTS ile bir yapı oluşturma hakkında daha fazla bilgi için VSTS ziyaret [sürekli tümleştirme ve dağıtım](https://www.visualstudio.com/docs/build/overview) konu.</span><span class="sxs-lookup"><span data-stu-id="ed099-169">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://www.visualstudio.com/docs/build/overview) topic.</span></span>

<span data-ttu-id="ed099-170">VSTS içinde el ile Kurulum komut dosyası kullanmak için yeni bir derleme tanımı oluşturun ve derleme adımı için çalıştırılacak komut dosyasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed099-170">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="ed099-171">Bu, VSTS kullanıcı arabirimi kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="ed099-171">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="ed099-172">Yeni bir derleme tanımı oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="ed099-172">Start by creating a new build definition.</span></span> <span data-ttu-id="ed099-173">Ne tür bir yapı istediğiniz oluşturmak için seçin tanımlamak için bir seçenek sağlar ekran ulaştıktan sonra **boş** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ed099-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Boş bir yapıyı seçme](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="ed099-175">Yapı depo yapılandırdıktan sonra derleme tanımları yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed099-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="ed099-176">Seçin **Ekle derleme adımı**:</span><span class="sxs-lookup"><span data-stu-id="ed099-176">Select **Add build step**:</span></span>

   ![Bir derleme adımı ekleme](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="ed099-178">İle sunulan **görev katalog**.</span><span class="sxs-lookup"><span data-stu-id="ed099-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="ed099-179">Katalog derlemede kullanma görevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ed099-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="ed099-180">Bir komut dosyası sahip olduğundan, seçin **Ekle** için düğmesini **PowerShell: bir PowerShell betiğini çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="ed099-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Bir PowerShell komut dosyası adımı ekleme](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="ed099-182">Derleme adımı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ed099-182">Configure the build step.</span></span> <span data-ttu-id="ed099-183">Komut dosyası oluşturmakta olduğunuz depodan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ed099-183">Add the script from the repository that you're building:</span></span>

   ![Çalıştırılacak PowerShell komut dosyası belirtme](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="ed099-185">Yapı yönetme</span><span class="sxs-lookup"><span data-stu-id="ed099-185">Orchestrating the build</span></span>

<span data-ttu-id="ed099-186">Bu belge çoğunu açıklar .NET Core araçları edinin ve düzenlemek hakkında bilgi sağlamadan çeşitli CI Hizmetleri Yapılandırma veya *gerçekten yapı*, .NET Core kodunuzla.</span><span class="sxs-lookup"><span data-stu-id="ed099-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="ed099-187">Yapı sürecini yapılandırma konusunda seçenekler burada genel hatlarıyla ele birçok faktöre bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ed099-187">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="ed099-188">Belge kümeleri içinde sağlanan örnekleri ve kaynakları keşfetme [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [VSTS](https://www.visualstudio.com/docs/build/overview) derlemeleriniz her yönetme hakkında daha fazla bilgi teknoloji.</span><span class="sxs-lookup"><span data-stu-id="ed099-188">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://www.visualstudio.com/docs/build/overview) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="ed099-189">.NET Core Araçları'nı kullanarak .NET Core kod derleme işlemi yapılandırılması ele iki genel yaklaşım kullanarak doğrudan MSBuild veya .NET Core komut satırı komutlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ed099-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="ed099-190">Almanız gereken hangi yaklaşımın karmaşıklığı rahatlık düzeyinizi yaklaşımlar ve dengelemeler ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ed099-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="ed099-191">MSBuild hedefleri ve görevleri de yapı işleminizin express olanağı sağlar, ancak MSBuild proje dosyası sözdizimi öğrenme eklenen karmaşıklığını ile gelir.</span><span class="sxs-lookup"><span data-stu-id="ed099-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="ed099-192">.NET Core komut satırı araçlarını kullanarak belki de daha basit olmakla birlikte, bir komut dosyası dili gibi orchestration mantığı yazmanızı gerektirir `bash` veya PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed099-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed099-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed099-193">See also</span></span>

[<span data-ttu-id="ed099-194">Ubuntu alma adımları</span><span class="sxs-lookup"><span data-stu-id="ed099-194">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)   
