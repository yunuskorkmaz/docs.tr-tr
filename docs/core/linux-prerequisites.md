---
title: .NET Core Linux önkoşulları
description: Desteklenen Linux sürümleri ve geliştirmek, dağıtmak ve Linux makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları.
keywords: .NET, .NET core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 04/12/2018
ms.topic: conceptual
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 37dc4f25b6c4915971bc79931a105474fcd43670
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="f8924-104">.NET Core Linux önkoşulları</span><span class="sxs-lookup"><span data-stu-id="f8924-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="f8924-105">Bu makalede Linux'ta .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8924-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="f8924-106">Desteklenen Linux dağıtımları/sürümleri ve izleyin bağımlılıkları Linux'ta .NET Core uygulama geliştirme iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f8924-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="f8924-107">Tercih ettiğiniz Düzenleyicisi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="f8924-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="f8924-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f8924-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="f8924-109">.NET Core SDK'sı paketinin üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f8924-109">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="f8924-110">Yalnızca .NET çekirdeği çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8924-110">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="f8924-111">.NET çekirdeği çalışma zamanı müstakil dağıtımının bir parçası uygulamaları ile dağıtılır, Framework bağımlı uygulamaları ayrı olarak dağıtılan için Bununla birlikte, dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8924-111">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="f8924-112">Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8924-112">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="f8924-113">Ayrıca bkz. [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler.</span><span class="sxs-lookup"><span data-stu-id="f8924-113">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="f8924-114">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="f8924-114">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-115">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-115">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f8924-116">.NET core 2.x davranır tek bir işletim sistemi olarak Linux.</span><span class="sxs-lookup"><span data-stu-id="f8924-116">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="f8924-117">Bir tek desteklenen Linux dağıtımları Linux yapı (her yonga Mimarisi) yoktur.</span><span class="sxs-lookup"><span data-stu-id="f8924-117">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="f8924-118">NET çekirdek 2.x, aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f8924-118">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="f8924-119">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="f8924-119">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="f8924-120">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f8924-120">CentOS 7</span></span>
* <span data-ttu-id="f8924-121">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="f8924-121">Oracle Linux 7</span></span>
* <span data-ttu-id="f8924-122">Fedora 27, 26</span><span class="sxs-lookup"><span data-stu-id="f8924-122">Fedora 27, 26</span></span>
* <span data-ttu-id="f8924-123">Debian 9 8,7 veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f8924-123">Debian 9, 8.7 or later versions</span></span>
* <span data-ttu-id="f8924-124">Ubuntu 17.10, 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="f8924-124">Ubuntu 17.10, 16.04, 14.04</span></span>
* <span data-ttu-id="f8924-125">Linux Naneli 18, 17</span><span class="sxs-lookup"><span data-stu-id="f8924-125">Linux Mint 18, 17</span></span>
* <span data-ttu-id="f8924-126">openSUSE 42.3 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f8924-126">openSUSE 42.3 or later versions</span></span>
* <span data-ttu-id="f8924-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya sonraki sürümü</span><span class="sxs-lookup"><span data-stu-id="f8924-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later</span></span>

<span data-ttu-id="f8924-128">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, dağıtımlar ve Destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında sürümleri.</span><span class="sxs-lookup"><span data-stu-id="f8924-128">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-129">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-129">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f8924-130">.NET core 1.x aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f8924-130">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="f8924-131">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="f8924-131">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="f8924-132">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f8924-132">CentOS 7</span></span>
* <span data-ttu-id="f8924-133">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="f8924-133">Oracle Linux 7</span></span>
* <span data-ttu-id="f8924-134">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="f8924-134">Fedora 26</span></span>
* <span data-ttu-id="f8924-135">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f8924-135">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="f8924-136">Ubuntu 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="f8924-136">Ubuntu 16.04, 14.04</span></span>
* <span data-ttu-id="f8924-137">Linux Naneli 18, 17</span><span class="sxs-lookup"><span data-stu-id="f8924-137">Linux Mint 18, 17</span></span>
* <span data-ttu-id="f8924-138">openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="f8924-138">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="f8924-139">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="f8924-139">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="f8924-140">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="f8924-140">Linux distribution dependencies</span></span>

<span data-ttu-id="f8924-141">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f8924-141">The following are intended to be examples.</span></span> <span data-ttu-id="f8924-142">Tam sürümünü ve adları, seçim Linux dağıtımını biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="f8924-142">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="f8924-143">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f8924-143">Ubuntu</span></span>

<span data-ttu-id="f8924-144">Ubuntu dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8924-144">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="f8924-145">libunwind8</span><span class="sxs-lookup"><span data-stu-id="f8924-145">libunwind8</span></span>
* <span data-ttu-id="f8924-146">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="f8924-146">liblttng-ust0</span></span>
* <span data-ttu-id="f8924-147">libcurl3</span><span class="sxs-lookup"><span data-stu-id="f8924-147">libcurl3</span></span>
* <span data-ttu-id="f8924-148">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="f8924-148">libssl1.0.0</span></span>
* <span data-ttu-id="f8924-149">libuuid1</span><span class="sxs-lookup"><span data-stu-id="f8924-149">libuuid1</span></span>
* <span data-ttu-id="f8924-150">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="f8924-150">libkrb5-3</span></span>
* <span data-ttu-id="f8924-151">zlib1g</span><span class="sxs-lookup"><span data-stu-id="f8924-151">zlib1g</span></span>
* <span data-ttu-id="f8924-152">libicu52 (için 14.x)</span><span class="sxs-lookup"><span data-stu-id="f8924-152">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="f8924-153">libicu55 (için 16.x)</span><span class="sxs-lookup"><span data-stu-id="f8924-153">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="f8924-154">libicu57 (için 17.x)</span><span class="sxs-lookup"><span data-stu-id="f8924-154">libicu57 (for 17.x)</span></span>

### <a name="centos"></a><span data-ttu-id="f8924-155">CentOS</span><span class="sxs-lookup"><span data-stu-id="f8924-155">CentOS</span></span>

<span data-ttu-id="f8924-156">CentOS dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8924-156">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="f8924-157">libunwind</span><span class="sxs-lookup"><span data-stu-id="f8924-157">libunwind</span></span>
* <span data-ttu-id="f8924-158">lttng hakkınızın</span><span class="sxs-lookup"><span data-stu-id="f8924-158">lttng-ust</span></span>
* <span data-ttu-id="f8924-159">libcurl</span><span class="sxs-lookup"><span data-stu-id="f8924-159">libcurl</span></span>
* <span data-ttu-id="f8924-160">openssl kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="f8924-160">openssl-libs</span></span>
* <span data-ttu-id="f8924-161">libuuid</span><span class="sxs-lookup"><span data-stu-id="f8924-161">libuuid</span></span>
* <span data-ttu-id="f8924-162">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="f8924-162">krb5-libs</span></span>
* <span data-ttu-id="f8924-163">libicu</span><span class="sxs-lookup"><span data-stu-id="f8924-163">libicu</span></span>
* <span data-ttu-id="f8924-164">Zlib</span><span class="sxs-lookup"><span data-stu-id="f8924-164">zlib</span></span>

<span data-ttu-id="f8924-165">Bağımlılıklar hakkında daha fazla bilgi için bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f8924-165">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="f8924-166">.NET Core bağımlılıkları ile yerel yükleyicileri yükleme</span><span class="sxs-lookup"><span data-stu-id="f8924-166">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="f8924-167">Desteklenen Linux dağıtımları/sürümleri .NET core yerel yükleyicileri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8924-167">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="f8924-168">Yerel yükleyicileri sunucusuna yönetici (sudo) erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8924-168">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="f8924-169">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıklarını yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="f8924-169">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="f8924-170">Yerel yükleyicileri ayrıca .NET Core SDK sistem genelinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f8924-170">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="f8924-171">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="f8924-171">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="f8924-172">Get apt Ubuntu için veya yum gibi bir akış tabanlı Paket Yöneticisi CentOS/RHEL için kullanma.</span><span class="sxs-lookup"><span data-stu-id="f8924-172">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="f8924-173">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="f8924-173">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="f8924-174">.NET Core Yükleyici komut dosyasıyla yükler komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8924-174">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="f8924-175">[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI zincirinin ve paylaşılan çalışma zamanı yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8924-175">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="f8924-176">Komut dosyasını karşıdan [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="f8924-176">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="f8924-177">Yükleyici bash betik Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8924-177">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="f8924-178">Linux/OS X sistemleri komut ile kullanılabilmesi için bu komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="f8924-178">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a><span data-ttu-id="f8924-179">Desteklenen Red Hat Enterprise Linux (RHEL) sürümleri için .NET Core yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-179">Install .NET Core for supported Red Hat Enterprise Linux (RHEL) versions</span></span>

<span data-ttu-id="f8924-180">.NET Core yüklemek için RHEL sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f8924-180">To install .NET Core on supported RHEL versions:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-181">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-181">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f8924-182">En son yükleme bilgileri sahip olmak için izleyin [.NET Core 2.x SDK ve çalışma zamanı yükleyicisi yönergeleri](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) için RHEL sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f8924-182">To ensure you have the latest installation information, follow the [.NET Core 2.x SDK and Runtime Installer instructions](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) for supported RHEL versions.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-183">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-183">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f8924-184">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-184">**.NET Core 1.1**</span></span>

1. <span data-ttu-id="f8924-185">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-185">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="f8924-186">Red Hat Enterprise Linux yükleme bilgileri en son .NET Core 1.1 için bkz: [.NET Core 1.1 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="f8924-186">For the latest .NET Core 1.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span></span>
     
<span data-ttu-id="f8924-187">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-187">**.NET Core 1.0**</span></span>

1. <span data-ttu-id="f8924-188">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-188">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="f8924-189">Red Hat Enterprise Linux yükleme bilgileri en son .NET Core 1.0 için bkz: [.NET Core 1.0 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="f8924-189">For the latest .NET Core 1.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span></span>

<span data-ttu-id="f8924-190">Red Hat .NET kanal erişim kayıt Yardım için bkz: [.NET Core 1.1 Başlarken Kılavuzu, bölüm 1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) Red Hat hızında.</span><span class="sxs-lookup"><span data-stu-id="f8924-190">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a><span data-ttu-id="f8924-191">.NET Core Ubuntu ve Linux Naneli dağıtımları/için desteklenen sürümleri (64 bit) yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-191">Install .NET Core for supported Ubuntu and Linux Mint distributions/versions (64 bit)</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-192">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-192">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="f8924-193">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-193">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-194">.NET Core üzerinde 2.x desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-194">Install .NET Core 2.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

<span data-ttu-id="f8924-195">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-195">**.NET Core 2.0**</span></span>

|<span data-ttu-id="f8924-196">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-196">Runtimes / SDKs</span></span>          |<span data-ttu-id="f8924-197">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="f8924-197">Ubuntu 17.10</span></span>  |<span data-ttu-id="f8924-198">Ubuntu 16.04 / Linux Naneli 18</span><span class="sxs-lookup"><span data-stu-id="f8924-198">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="f8924-199">Ubuntu 14.04 / Linux Naneli 17</span><span class="sxs-lookup"><span data-stu-id="f8924-199">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|--------------|----------------------------|----------------------------|
|<span data-ttu-id="f8924-200">.NET çekirdeği çalışma zamanı 2.0.6</span><span class="sxs-lookup"><span data-stu-id="f8924-200">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="f8924-201">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-201">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[<span data-ttu-id="f8924-202">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-202">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[<span data-ttu-id="f8924-203">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-203">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|<span data-ttu-id="f8924-204">.NET çekirdeği çalışma zamanı 2.0.5</span><span class="sxs-lookup"><span data-stu-id="f8924-204">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="f8924-205">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-205">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[<span data-ttu-id="f8924-206">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-206">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[<span data-ttu-id="f8924-207">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-207">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|<span data-ttu-id="f8924-208">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="f8924-208">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="f8924-209">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-209">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[<span data-ttu-id="f8924-210">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-210">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[<span data-ttu-id="f8924-211">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-211">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|<span data-ttu-id="f8924-212">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="f8924-212">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="f8924-213">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-213">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[<span data-ttu-id="f8924-214">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-214">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[<span data-ttu-id="f8924-215">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-215">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |

<span data-ttu-id="f8924-216">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-216">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f8924-217">.NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="f8924-217">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="f8924-218">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-218">Runtimes / SDKs</span></span>                  |<span data-ttu-id="f8924-219">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="f8924-219">Ubuntu 17.10</span></span>    |<span data-ttu-id="f8924-220">Ubuntu 16.04 / Linux Naneli 18</span><span class="sxs-lookup"><span data-stu-id="f8924-220">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="f8924-221">Ubuntu 14.04 / Linux Naneli 17</span><span class="sxs-lookup"><span data-stu-id="f8924-221">Ubuntu 14.04 / Linux Mint 17</span></span>|
|---------------------------------|----------------|----------------------------|----------------------------|
|<span data-ttu-id="f8924-222">.NET çalışma zamanı 2.1.0-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-222">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="f8924-223">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-223">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[<span data-ttu-id="f8924-224">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-224">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[<span data-ttu-id="f8924-225">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-225">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|<span data-ttu-id="f8924-226">.NET SDK 2.1.300-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-226">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="f8924-227">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-227">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[<span data-ttu-id="f8924-228">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-228">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[<span data-ttu-id="f8924-229">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-229">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-230">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-230">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="f8924-231">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-232">.NET Core üzerinde 1.x desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-232">Install .NET Core 1.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

| <span data-ttu-id="f8924-233">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-233">Runtimes / SDKs</span></span>         |<span data-ttu-id="f8924-234">Ubuntu 16.04 / Linux Naneli 18</span><span class="sxs-lookup"><span data-stu-id="f8924-234">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="f8924-235">Ubuntu 14.04 / Linux Naneli 17</span><span class="sxs-lookup"><span data-stu-id="f8924-235">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|----------------------------|----------------------------|
|<span data-ttu-id="f8924-236">.NET çekirdeği çalışma zamanı 1.1.7</span><span class="sxs-lookup"><span data-stu-id="f8924-236">.NET Core Runtime 1.1.7</span></span>  |[<span data-ttu-id="f8924-237">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-237">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-238">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-238">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-239">.NET çekirdeği çalışma zamanı 1.1.6</span><span class="sxs-lookup"><span data-stu-id="f8924-239">.NET Core Runtime 1.1.6</span></span>  |[<span data-ttu-id="f8924-240">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-240">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-241">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-241">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-242">.NET çekirdeği çalışma zamanı 1.0.10</span><span class="sxs-lookup"><span data-stu-id="f8924-242">.NET Core Runtime 1.0.10</span></span> |[<span data-ttu-id="f8924-243">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-243">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-244">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-244">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-245">.NET çekirdeği çalışma zamanı 1.0.9</span><span class="sxs-lookup"><span data-stu-id="f8924-245">.NET Core Runtime 1.0.9</span></span>  |[<span data-ttu-id="f8924-246">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-246">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-247">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-247">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-248">.NET core SDK 1.1.8</span><span class="sxs-lookup"><span data-stu-id="f8924-248">.NET Core SDK 1.1.8</span></span>      |[<span data-ttu-id="f8924-249">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-249">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-250">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-250">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-251">.NET core SDK 1.1.7</span><span class="sxs-lookup"><span data-stu-id="f8924-251">.NET Core SDK 1.1.7</span></span>      |[<span data-ttu-id="f8924-252">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-252">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-253">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-253">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-254">.NET core SDK 1.0.4</span><span class="sxs-lookup"><span data-stu-id="f8924-254">.NET Core SDK 1.0.4</span></span>      |[<span data-ttu-id="f8924-255">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-255">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-256">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-256">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="f8924-257">.NET core SDK 1.0.1</span><span class="sxs-lookup"><span data-stu-id="f8924-257">.NET Core SDK 1.0.1</span></span>      |[<span data-ttu-id="f8924-258">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-258">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="f8924-259">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-259">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a><span data-ttu-id="f8924-260">.NET Core Debian için desteklenen sürümleri (64 bit) yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-260">Install .NET Core for supported Debian versions (64 bit)</span></span>

<span data-ttu-id="f8924-261">.NET Core desteklenen Debian sürümlerinde (64 bit) yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="f8924-261">To install .NET Core on supported Debian versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="f8924-262">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8924-262">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-263">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-263">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="f8924-264">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-264">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-265">.NET Core üzerinde 2.x desteklenen Debian sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-265">Install .NET Core 2.x on supported Debian versions (64 bit):</span></span>

<span data-ttu-id="f8924-266">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-266">**.NET Core 2.0**</span></span>

|<span data-ttu-id="f8924-267">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-267">Runtimes / SDKs</span></span>          |<span data-ttu-id="f8924-268">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f8924-268">Debian 9</span></span>       |<span data-ttu-id="f8924-269">Debian 8</span><span class="sxs-lookup"><span data-stu-id="f8924-269">Debian 8</span></span>       |
|-------------------------|---------------|---------------|
|<span data-ttu-id="f8924-270">.NET çekirdeği çalışma zamanı 2.0.6</span><span class="sxs-lookup"><span data-stu-id="f8924-270">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="f8924-271">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-271">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[<span data-ttu-id="f8924-272">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-272">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|<span data-ttu-id="f8924-273">.NET çekirdeği çalışma zamanı 2.0.5</span><span class="sxs-lookup"><span data-stu-id="f8924-273">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="f8924-274">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-274">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[<span data-ttu-id="f8924-275">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-275">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|<span data-ttu-id="f8924-276">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="f8924-276">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="f8924-277">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-277">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[<span data-ttu-id="f8924-278">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-278">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|<span data-ttu-id="f8924-279">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="f8924-279">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="f8924-280">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-280">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[<span data-ttu-id="f8924-281">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-281">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |

<span data-ttu-id="f8924-282">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-282">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f8924-283">.NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="f8924-283">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="f8924-284">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-284">Runtimes / SDKs</span></span>                  |<span data-ttu-id="f8924-285">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f8924-285">Debian 9</span></span>       |<span data-ttu-id="f8924-286">Debian 8</span><span class="sxs-lookup"><span data-stu-id="f8924-286">Debian 8</span></span>       |
|---------------------------------|---------------|---------------|
|<span data-ttu-id="f8924-287">.NET çalışma zamanı 2.1.0-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-287">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="f8924-288">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-288">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[<span data-ttu-id="f8924-289">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-289">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|<span data-ttu-id="f8924-290">.NET SDK 2.1.300-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-290">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="f8924-291">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-291">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[<span data-ttu-id="f8924-292">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-292">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-293">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-293">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="f8924-294">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-294">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-295">.NET yüklemek 1.x Debian 9 veya Debian 8 Çekirdek:</span><span class="sxs-lookup"><span data-stu-id="f8924-295">Install .NET Core 1.x on Debian 9 or Debian 8:</span></span>

* <span data-ttu-id="f8924-296">.NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-296">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-297">.NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-297">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-298">.NET çekirdeği çalışma zamanı 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-298">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-299">.NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-299">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-300">.NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-300">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-301">.NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-301">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-302">.NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-302">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="f8924-303">.NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-303">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a><span data-ttu-id="f8924-304">.NET Core Fedora için desteklenen sürümleri (64 bit) yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-304">Install .NET Core for supported Fedora versions (64 bit)</span></span>

<span data-ttu-id="f8924-305">.NET Core üzerinde desteklenen Fedora sürümlerini yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="f8924-305">To install .NET Core on supported Fedora versions:</span></span>

> [!NOTE]
> <span data-ttu-id="f8924-306">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8924-306">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-307">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-307">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="f8924-308">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-308">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-309">.NET Core üzerinde 2.x desteklenen Fedora sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-309">Install .NET Core 2.x on supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="f8924-310">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-310">**.NET Core 2.0**</span></span>

|<span data-ttu-id="f8924-311">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-311">Runtimes / SDKs</span></span>          |<span data-ttu-id="f8924-312">Fedora 26 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="f8924-312">Fedora 26 or later</span></span> |<span data-ttu-id="f8924-313">Fedora 25 veya önceki</span><span class="sxs-lookup"><span data-stu-id="f8924-313">Fedora 25 or previous</span></span> |
|-------------------------|-------------------|----------------------|
|<span data-ttu-id="f8924-314">.NET çekirdeği çalışma zamanı 2.0.6</span><span class="sxs-lookup"><span data-stu-id="f8924-314">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="f8924-315">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-315">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[<span data-ttu-id="f8924-316">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-316">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|<span data-ttu-id="f8924-317">.NET çekirdeği çalışma zamanı 2.0.5</span><span class="sxs-lookup"><span data-stu-id="f8924-317">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="f8924-318">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-318">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[<span data-ttu-id="f8924-319">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-319">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|<span data-ttu-id="f8924-320">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="f8924-320">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="f8924-321">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-321">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[<span data-ttu-id="f8924-322">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-322">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|<span data-ttu-id="f8924-323">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="f8924-323">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="f8924-324">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-324">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[<span data-ttu-id="f8924-325">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-325">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

<span data-ttu-id="f8924-326">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-326">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f8924-327">.NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="f8924-327">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="f8924-328">Çalışma zamanları / SDK'ları</span><span class="sxs-lookup"><span data-stu-id="f8924-328">Runtimes / SDKs</span></span>                  |<span data-ttu-id="f8924-329">Fedora 26 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="f8924-329">Fedora 26 or later</span></span> |<span data-ttu-id="f8924-330">Fedora 25 veya önceki</span><span class="sxs-lookup"><span data-stu-id="f8924-330">Fedora 25 or previous</span></span> |
|---------------------------------|-------------------|----------------------|
|<span data-ttu-id="f8924-331">.NET çalışma zamanı 2.1.0-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-331">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="f8924-332">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-332">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)       |[<span data-ttu-id="f8924-333">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-333">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview1)           |        |
|<span data-ttu-id="f8924-334">.NET SDK 2.1.300-preview1 çekirdek</span><span class="sxs-lookup"><span data-stu-id="f8924-334">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="f8924-335">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-335">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview1)       |[<span data-ttu-id="f8924-336">Bağlantı yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-336">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-337">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-337">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="f8924-338">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-338">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-339">.NET Core desteklenen 1.x Fedora sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-339">Install .NET Core 1.x supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="f8924-340">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="f8924-340">**Fedora 24**</span></span>

* <span data-ttu-id="f8924-341">.NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-341">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="f8924-342">.NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-342">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="f8924-343">.NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-343">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="f8924-344">.NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-344">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="f8924-345">.NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-345">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

<span data-ttu-id="f8924-346">**Fedora 23**</span><span class="sxs-lookup"><span data-stu-id="f8924-346">**Fedora 23**</span></span>

* <span data-ttu-id="f8924-347">.NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-347">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="f8924-348">.NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-348">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="f8924-349">.NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-349">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a><span data-ttu-id="f8924-350">.NET Core desteklenen CentOS ve Oracle Linux için yükleme dağıtımları/sürümleri (64 bit)</span><span class="sxs-lookup"><span data-stu-id="f8924-350">Install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit)</span></span>

<span data-ttu-id="f8924-351">Yüklemek için .NET Core desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):</span><span class="sxs-lookup"><span data-stu-id="f8924-351">To install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="f8924-352">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f8924-352">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-353">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-353">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="f8924-354">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-354">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-355">.NET Core yükleme 2.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):</span><span class="sxs-lookup"><span data-stu-id="f8924-355">Install .NET Core 2.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

<span data-ttu-id="f8924-356">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-356">**.NET Core 2.0**</span></span>

* <span data-ttu-id="f8924-357">.NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="f8924-357">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span></span>
* <span data-ttu-id="f8924-358">.NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="f8924-358">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span></span>
* <span data-ttu-id="f8924-359">.NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="f8924-359">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span></span>
* <span data-ttu-id="f8924-360">.NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="f8924-360">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span></span>
 
<span data-ttu-id="f8924-361">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-361">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f8924-362">.NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="f8924-362">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview/).</span></span>

* <span data-ttu-id="f8924-363">.NET çekirdeği çalışma zamanı 2.1.0-preview1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="f8924-363">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="f8924-364">.NET core SDK 2.1.300-preview1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="f8924-364">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-365">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-365">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="f8924-366">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-366">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-367">.NET Core yükleme 1.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):</span><span class="sxs-lookup"><span data-stu-id="f8924-367">Install .NET Core 1.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

* <span data-ttu-id="f8924-368">.NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-368">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-369">.NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-369">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-370">.NET çekirdeği çalışma zamanı 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-370">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-371">.NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-371">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-372">.NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-372">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-373">.NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-373">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-374">.NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-374">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="f8924-375">.NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-375">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a><span data-ttu-id="f8924-376">.NET Core SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/için desteklenen sürümleri (64 bit) yükleyin</span><span class="sxs-lookup"><span data-stu-id="f8924-376">Install .NET Core for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit)</span></span>

<span data-ttu-id="f8924-377">.NET Core yüklemek için desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) 2.x için:</span><span class="sxs-lookup"><span data-stu-id="f8924-377">To install .NET Core 2.x for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f8924-378">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="f8924-378">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="f8924-379">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-379">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-380">.NET Core üzerinde 2.x desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-380">Install .NET Core 2.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="f8924-381">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="f8924-381">**.NET Core 2.0**</span></span>

* <span data-ttu-id="f8924-382">.NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="f8924-382">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span></span>
* <span data-ttu-id="f8924-383">.NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="f8924-383">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span></span>
* <span data-ttu-id="f8924-384">.NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="f8924-384">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span></span>
* <span data-ttu-id="f8924-385">.NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="f8924-385">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span></span>
 
<span data-ttu-id="f8924-386">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="f8924-386">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f8924-387">.NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="f8924-387">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

* <span data-ttu-id="f8924-388">.NET çekirdeği çalışma zamanı 2.1.0-preview1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="f8924-388">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="f8924-389">.NET core SDK 2.1.300-preview1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="f8924-389">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8924-390">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8924-390">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="f8924-391">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="f8924-391">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="f8924-392">.NET Core üzerinde 1.x desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="f8924-392">Install .NET Core 1.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="f8924-393">**SUSE Linux Enterprise Server 13.2**</span><span class="sxs-lookup"><span data-stu-id="f8924-393">**SUSE Linux Enterprise Server 13.2**</span></span>

* <span data-ttu-id="f8924-394">.NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-394">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="f8924-395">.NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-395">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="f8924-396">.NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-396">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>

<span data-ttu-id="f8924-397">**openSUSE 24**</span><span class="sxs-lookup"><span data-stu-id="f8924-397">**openSUSE 24**</span></span>

* <span data-ttu-id="f8924-398">.NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-398">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span></span>
* <span data-ttu-id="f8924-399">.NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="f8924-399">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span></span>

---

> [!IMPORTANT]
> <span data-ttu-id="f8924-400">Desteklenen bir Linux dağıtım/sürümünde .NET Core yükleme sorunları varsa, yüklü dağıtımları/sürümü için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="f8924-400">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>
> * [<span data-ttu-id="f8924-401">.NET core 2.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f8924-401">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [<span data-ttu-id="f8924-402">.NET core 2.0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f8924-402">.NET Core 2.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [<span data-ttu-id="f8924-403">.NET core 1.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f8924-403">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [<span data-ttu-id="f8924-404">.NET core 1.0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f8924-404">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)