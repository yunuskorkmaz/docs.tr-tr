---
title: .NET Core SDK ve araçlarla sürekli tümleştirme (CI)
description: .NET Core SDK ve araçlarını sürekli tümleştirme ile yapı sunucusunda nasıl kullanacağınızı öğrenin.
author: mairaw
ms.date: 05/18/2017
ms.openlocfilehash: 65d062fce2f364932ebf8091bd9c6cdef561b633
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714115"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="04d4b-103">Sürekli tümleştirme (CI) içinde .NET Core SDK ve araçları kullanma</span><span class="sxs-lookup"><span data-stu-id="04d4b-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="04d4b-104">Bu belge, yapı sunucusunda .NET Core SDK ve araçlarını kullanarak özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="04d4b-105">.NET Core araç takımı hem etkileşimli olarak hem de bir geliştirici komut isteminde komutlar yazdığında ve sürekli tümleştirme (CI) sunucusunun bir yapı betiğini çalıştırdığı otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="04d4b-106">Komutlar, Seçenekler, girişler ve çıktılar aynıdır ve sağladığınız tek şey, uygulamayı derlemek için araç ve bir sistem elde etmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="04d4b-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="04d4b-107">Bu belge, derleme betiklerinizi tasarlamaya ve oluşturmaya yönelik önerilere sahip CI için araç alımı senaryolarına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="04d4b-108">CI derleme sunucuları için yükleme seçenekleri</span><span class="sxs-lookup"><span data-stu-id="04d4b-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="04d4b-109">Yerel yükleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="04d4b-109">Using the native installers</span></span>

<span data-ttu-id="04d4b-110">Yerel yükleyiciler macOS, Linux ve Windows için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="04d4b-111">Yükleyiciler, derleme sunucusuna yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="04d4b-112">Yerel bir yükleyiciyi kullanmanın avantajı, araçları çalıştırmak için gerekli tüm yerel bağımlılıkların yüklenidir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="04d4b-113">Yerel yükleyiciler Ayrıca SDK 'nın sistem genelinde bir yüklemesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="04d4b-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="04d4b-114">macOS kullanıcıları paket yükleyicilerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="04d4b-115">Linux 'ta, bir akış tabanlı Paket Yöneticisi (örneğin, Ubuntu veya CentOS için apt-get) veya paketlerin kendilerini, DEB veya RPM 'yi kullanmayı tercih eden bir seçim vardır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="04d4b-116">Windows 'ta, MSI yükleyicisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="04d4b-117">En son kararlı ikili dosyalar [.net indirmelerinde](https://dotnet.microsoft.com/download)bulunur.</span><span class="sxs-lookup"><span data-stu-id="04d4b-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="04d4b-118">En son (ve kararsız) yayın öncesi araçları kullanmak istiyorsanız, [DotNet/Core-SDK GitHub deposunda](https://github.com/dotnet/core-sdk#installers-and-binaries)sunulan bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="04d4b-119">Linux dağıtımları için `tar.gz` arşivleri (`tarballs`olarak da bilinir) kullanılabilir; .NET Core yüklemek için arşivleri içindeki yükleme betiklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="04d4b-120">Yükleyici betiğini kullanma</span><span class="sxs-lookup"><span data-stu-id="04d4b-120">Using the installer script</span></span>

<span data-ttu-id="04d4b-121">Yükleyici betiğinin kullanılması, yapı sunucunuzda yönetimsel olmayan yüklemeye ve araçları almak için kolay otomatikleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="04d4b-122">Betik, araçları indirme ve varsayılan veya belirtilen bir konuma çıkarma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="04d4b-123">Ayrıca, yüklemek istediğiniz bir araç sürümünü ve tüm SDK 'Yı mı yoksa yalnızca paylaşılan çalışma zamanını mı yüklemek istediğinizi de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="04d4b-124">Yükleyici betiği, SDK 'nın istenen sürümünü getirmek ve yüklemek üzere Yapı başlangıcında çalışmak için otomatikleştirilir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="04d4b-125">*İstediğiniz sürüm* , projelerinizin derlemek için IHTIYAç duyduğu SDK 'nın herhangi bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="04d4b-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="04d4b-126">Komut dosyası, SDK 'Yı sunucudaki yerel bir dizine yüklemenize, yüklü konumdan araçları çalıştırmanıza ve sonra da derlemeyi (ya da CI hizmeti temizlemeye izin verir) derlemeden sonra temizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="04d4b-127">Bu, tüm derleme sürecinizi kapsülleme ve yalıtıma sağlar.</span><span class="sxs-lookup"><span data-stu-id="04d4b-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="04d4b-128">Yükleme betiği başvurusu [DotNet yükleme](dotnet-install-script.md) makalesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="04d4b-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="04d4b-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="04d4b-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="04d4b-130">Yükleyici betiği kullanılırken, yerel bağımlılıklar otomatik olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="04d4b-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="04d4b-131">İşletim sisteminde yoksa yerel bağımlılıkları yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="04d4b-132">Daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="04d4b-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="04d4b-133">CI kurulum örnekleri</span><span class="sxs-lookup"><span data-stu-id="04d4b-133">CI setup examples</span></span>

<span data-ttu-id="04d4b-134">Bu bölümde, bir PowerShell veya bash betiği kullanılarak el ile yapılan bir kurulum ve hizmet olarak yazılım (SaaS) CI çözümlerinin bir açıklaması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="04d4b-135">Kapsanan SaaS CI çözümleri, [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="04d4b-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="04d4b-136">El ile kurulum</span><span class="sxs-lookup"><span data-stu-id="04d4b-136">Manual setup</span></span>

<span data-ttu-id="04d4b-137">Her SaaS hizmeti bir yapı işlemi oluşturmak ve yapılandırmak için kendi yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="04d4b-138">Listelenenlerden farklı SaaS çözümü kullanıyorsanız veya önceden paketlenmiş desteğin ötesinde özelleştirme yapmayı düşünüyorsanız, en az bir el ile yapılandırma gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="04d4b-139">Genel olarak, el ile kurulum, araçların bir sürümünü (veya araçların en son gecelik sürümlerini) almanızı ve derleme betiğinizi çalıştırmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="04d4b-140">.NET Core komutlarını düzenlemek veya yapı sürecini özetleyen bir proje dosyası kullanmak için bir PowerShell veya bash betiği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="04d4b-141">[Orchestration bölümü](#orchestrating-the-build) , bu seçenekler hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="04d4b-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="04d4b-142">El ile CI derleme sunucusu kurulumu gerçekleştiren bir komut dosyası oluşturduktan sonra, test amacıyla kodunuzu yerel olarak derlemek için geliştirme makinenizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="04d4b-143">Betiğin yerel olarak çalıştığını onaylayıp CI Build sunucunuza dağıtın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="04d4b-144">Görece basit bir PowerShell betiği, .NET Core SDK nasıl alınacağını ve bir Windows Build Server 'a nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="04d4b-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="04d4b-145">Betik sonunda derleme işleminiz için uygulama sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="04d4b-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="04d4b-146">Komut dosyası araçları alır ve yapı işleminizi yürütür.</span><span class="sxs-lookup"><span data-stu-id="04d4b-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="04d4b-147">UNIX makineler için aşağıdaki Bash betiği, PowerShell komut dosyasında açıklanan eylemleri benzer bir şekilde gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="04d4b-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="04d4b-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="04d4b-148">Travis CI</span></span>

<span data-ttu-id="04d4b-149">`csharp` dilini ve `dotnet` anahtarını kullanarak .NET Core SDK yüklemek için [Travis CI](https://travis-ci.org/) 'yi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="04d4b-150">Daha fazla bilgi için, bkz., [veya Visual Basic projesi oluşturma C# F#](https://docs.travis-ci.com/user/languages/csharp/)hakkında resmi Travis CI belgeleri.</span><span class="sxs-lookup"><span data-stu-id="04d4b-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="04d4b-151">Topluluk tarafından korunan `language: csharp` Dil tanımlayıcısının, ve mono dahil olmak üzere F#tüm .NET dilleri için işe Çalıştığınızdaki TRAVIS CI bilgilerine eriştiğinizde dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="04d4b-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="04d4b-152">Travis CI hem macOS hem de Linux işlerini, uygulamanızın yapı kombinasyonlarını kapsayacak çalışma zamanı, ortam ve dışlamaları/eklemeleri belirlediğiniz bir *derleme matrisi*içinde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="04d4b-153">Daha fazla bilgi için bkz. Travis CI belgelerindeki [derlemeyi özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) makalesi.</span><span class="sxs-lookup"><span data-stu-id="04d4b-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="04d4b-154">MSBuild tabanlı araçlar, paketteki LTS (1.0. x) ve geçerli (1.1. x) çalışma zamanlarını içerir; Bu nedenle SDK 'yı yükleyerek, oluşturmanız gereken her şeyi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="04d4b-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="04d4b-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="04d4b-155">AppVeyor</span></span>

<span data-ttu-id="04d4b-156">[AppVeyor](https://www.appveyor.com/) , `Visual Studio 2017` derlemesi çalışan görüntüsü Ile .NET Core 1.0.1 SDK 'sını yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="04d4b-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="04d4b-157">.NET Core SDK farklı sürümlerine sahip diğer derleme görüntüleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="04d4b-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="04d4b-158">Daha fazla bilgi için AppVeyor docs içindeki [AppVeyor. yıml örneğine](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [Build Worker Images](https://www.appveyor.com/docs/build-environment/#build-worker-images) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="04d4b-159">.NET Core SDK ikililer, install betiği kullanılarak bir alt dizinde indirilir ve sıkıştırılırsınız ve sonra `PATH` ortam değişkenine eklenir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="04d4b-160">.NET Core SDK birden çok sürümüyle tümleştirme testlerini çalıştırmak için bir derleme matrisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="04d4b-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="04d4b-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="04d4b-161">Azure DevOps Services</span></span>

<span data-ttu-id="04d4b-162">Aşağıdaki yaklaşımlardan birini kullanarak .NET Core projeleri oluşturmak için Azure DevOps Services yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="04d4b-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="04d4b-163">Komutlarınızı kullanarak [el ile kurulum adımından](#manual-setup) betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="04d4b-164">.NET Core araçları kullanmak üzere yapılandırılmış çeşitli Azure DevOps Services yerleşik oluşturma görevlerinden oluşan bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="04d4b-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="04d4b-165">Her iki çözüm de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-165">Both solutions are valid.</span></span> <span data-ttu-id="04d4b-166">El ile kurulum betiği kullanarak, bunları yapılandırmanın bir parçası olarak indirdiklerinden, aldığınız araçların sürümünü kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="04d4b-167">Derleme, oluşturmanız gereken bir betikten çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="04d4b-168">Bu makale yalnızca el ile seçeneği içerir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-168">This article only covers the manual option.</span></span> <span data-ttu-id="04d4b-169">Azure DevOps Services yapı görevleriyle derleme oluşturma hakkında daha fazla bilgi için [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="04d4b-170">Azure DevOps Services içinde el ile kurulum betiği kullanmak için yeni bir derleme tanımı oluşturun ve derleme adımı için çalıştırılacak betiği belirtin.</span><span class="sxs-lookup"><span data-stu-id="04d4b-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="04d4b-171">Bu, Azure DevOps Services kullanıcı arabirimi kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="04d4b-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="04d4b-172">Yeni bir derleme tanımı oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-172">Start by creating a new build definition.</span></span> <span data-ttu-id="04d4b-173">Oluşturmak istediğiniz bir yapı türünü tanımlama seçeneği sunan ekrana ulaştığınızda **boş** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="04d4b-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Boş bir derleme tanımı seçme](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="04d4b-175">Derlemeyi derlemek için yapılandırdıktan sonra, derleme tanımlarına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="04d4b-176">**Yapı Ekle adımını**seçin:</span><span class="sxs-lookup"><span data-stu-id="04d4b-176">Select **Add build step**:</span></span>

   ![Derleme adımı ekleme](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="04d4b-178">**Görev kataloğu**ile karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="04d4b-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="04d4b-179">Katalog, derlemede kullandığınız görevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="04d4b-180">Bir betiğinizin olduğundan, PowerShell için **Ekle** düğmesini seçin **: PowerShell betiği çalıştırın**.</span><span class="sxs-lookup"><span data-stu-id="04d4b-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![PowerShell betiği ekleme adımı](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="04d4b-182">Yapı adımını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="04d4b-182">Configure the build step.</span></span> <span data-ttu-id="04d4b-183">Oluşturmakta olduğunuz depodan betiği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="04d4b-183">Add the script from the repository that you're building:</span></span>

   ![Çalıştırılacak PowerShell betiğini belirtme](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="04d4b-185">Derlemeyi düzenleme</span><span class="sxs-lookup"><span data-stu-id="04d4b-185">Orchestrating the build</span></span>

<span data-ttu-id="04d4b-186">Bu belgenin çoğunda, .NET Core ile kodunuzu *düzenleme veya yapılandırma*hakkında bilgi sağlamadan .NET Core araçlarının nasıl elde edileceğini ve çeşitli CI hizmetlerinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="04d4b-187">Yapı işlemini nasıl yapılandıracağınıza ilişkin seçimler burada genel bir şekilde ele alınmayan birçok etkene bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="04d4b-188">Her teknolojiyle derlemelerinizi düzenleme hakkında daha fazla bilgi için, [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)belge kümelerinde sağlanan kaynakları ve örnekleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="04d4b-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="04d4b-189">.NET Core araçları kullanılarak .NET Core kodu için derleme işlemini yapılandırırken uygulamanız gereken iki genel yaklaşım doğrudan MSBuild 'i veya .NET Core komut satırı komutlarını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="04d4b-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="04d4b-190">Uygulamanız gereken yaklaşım, yaklaşımlar ve yüksek düzeyde karmaşıklığa sahip olan rahatlık düzeyinize göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="04d4b-191">MSBuild, derleme işleminizi görev ve hedef olarak ifade etme olanağı sağlar, ancak öğrenme MSBuild proje dosyası sözdiziminin ek karmaşıklığı ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="04d4b-192">.NET Core komut satırı araçlarının kullanılması belki de basittir, ancak düzenleme mantığını `bash` veya PowerShell gibi bir betik dilinde yazmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="04d4b-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="04d4b-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04d4b-193">See also</span></span>

- [<span data-ttu-id="04d4b-194">.NET İndirmeleri-Linux</span><span class="sxs-lookup"><span data-stu-id="04d4b-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
