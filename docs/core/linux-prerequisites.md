---
title: ".NET Core Linux önkoşulları"
description: "Desteklenen Linux sürümleri ve geliştirmek, dağıtmak ve Linux makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları."
keywords: .NET, .NET core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: ec08d9fa3ad672400b61c269da0c6a70ed9ef2f5
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="31a00-104">.NET Core Linux önkoşulları</span><span class="sxs-lookup"><span data-stu-id="31a00-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="31a00-105">Bu makalede Linux'ta .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31a00-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="31a00-106">Desteklenen Linux dağıtımları/sürümleri ve izleyin bağımlılıkları Linux'ta .NET Core uygulama geliştirme iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="31a00-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="31a00-107">Tercih ettiğiniz Düzenleyicisi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="31a00-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="31a00-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="31a00-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="31a00-109">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="31a00-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-110">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="31a00-111">.NET core 2.0 tek bir işletim sistemi Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="31a00-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="31a00-112">Bir tek desteklenen Linux distro'lar Linux yapı (her yonga Mimarisi) yoktur.</span><span class="sxs-lookup"><span data-stu-id="31a00-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="31a00-113">NET çekirdek 2.x, aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="31a00-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="31a00-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="31a00-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="31a00-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="31a00-115">CentOS 7</span></span>
 * <span data-ttu-id="31a00-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="31a00-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="31a00-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="31a00-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="31a00-118">Debian 8,7 veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="31a00-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="31a00-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="31a00-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="31a00-120">Linux Naneli 18, Linux Naneli 17</span><span class="sxs-lookup"><span data-stu-id="31a00-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="31a00-121">openSUSE 42,2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="31a00-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="31a00-122">SUSE Enterprise Linux (SLES) 12 SP2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="31a00-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="31a00-123">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="31a00-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-124">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="31a00-125">.NET core 1.x aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="31a00-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="31a00-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="31a00-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="31a00-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="31a00-127">CentOS 7</span></span>
* <span data-ttu-id="31a00-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="31a00-128">Oracle Linux 7</span></span>
* <span data-ttu-id="31a00-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="31a00-129">Fedora 24</span></span>
* <span data-ttu-id="31a00-130">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="31a00-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="31a00-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="31a00-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="31a00-132">Ubuntu 16.10 .NET Core 1.1 en son düzeltme eki sürümü tarafından desteklenen</span><span class="sxs-lookup"><span data-stu-id="31a00-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="31a00-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="31a00-133">Linux Mint 17</span></span>
* <span data-ttu-id="31a00-134">openSUSE 42,1 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="31a00-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="31a00-135">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="31a00-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="31a00-136">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="31a00-136">Linux distribution dependencies</span></span>

<span data-ttu-id="31a00-137">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31a00-137">The following are intended to be examples.</span></span> <span data-ttu-id="31a00-138">Tam sürümünü ve adları, seçim Linux dağıtımını biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="31a00-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="31a00-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="31a00-139">Ubuntu</span></span>

<span data-ttu-id="31a00-140">Ubuntu dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="31a00-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="31a00-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="31a00-141">libunwind8</span></span>
* <span data-ttu-id="31a00-142">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="31a00-142">liblttng-ust0</span></span>
* <span data-ttu-id="31a00-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="31a00-143">libcurl3</span></span>
* <span data-ttu-id="31a00-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="31a00-144">libssl1.0.0</span></span>
* <span data-ttu-id="31a00-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="31a00-145">libuuid1</span></span>
* <span data-ttu-id="31a00-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="31a00-146">libkrb5</span></span>
* <span data-ttu-id="31a00-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="31a00-147">zlib1g</span></span>
* <span data-ttu-id="31a00-148">libicu52 (için 14.X)</span><span class="sxs-lookup"><span data-stu-id="31a00-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="31a00-149">libicu55 (için 16.X)</span><span class="sxs-lookup"><span data-stu-id="31a00-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="31a00-150">libicu57 (için 17.X)</span><span class="sxs-lookup"><span data-stu-id="31a00-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="31a00-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="31a00-151">CentOS</span></span>

<span data-ttu-id="31a00-152">CentOS dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="31a00-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="31a00-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="31a00-153">libunwind</span></span>
* <span data-ttu-id="31a00-154">lttng hakkınızın</span><span class="sxs-lookup"><span data-stu-id="31a00-154">lttng-ust</span></span>
* <span data-ttu-id="31a00-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="31a00-155">libcurl</span></span>
* <span data-ttu-id="31a00-156">openssl kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="31a00-156">openssl-libs</span></span>
* <span data-ttu-id="31a00-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="31a00-157">libuuid</span></span>
* <span data-ttu-id="31a00-158">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="31a00-158">krb5-libs</span></span>
* <span data-ttu-id="31a00-159">libicu</span><span class="sxs-lookup"><span data-stu-id="31a00-159">libicu</span></span>
* <span data-ttu-id="31a00-160">Zlib</span><span class="sxs-lookup"><span data-stu-id="31a00-160">zlib</span></span>

<span data-ttu-id="31a00-161">Bağımlılıklar hakkında daha fazla bilgi için bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="31a00-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="31a00-162">.NET Core bağımlılıkları ile yerel yükleyicileri yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="31a00-163">Desteklenen Linux dağıtımları/sürümleri .NET core yerel yükleyicileri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31a00-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="31a00-164">Yerel yükleyicileri sunucusuna yönetici (sudo) erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="31a00-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="31a00-165">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıklarını yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="31a00-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="31a00-166">Yerel yükleyicileri ayrıca .NET Core SDK sistem genelinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="31a00-167">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="31a00-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="31a00-168">Get apt Ubuntu için veya yum gibi bir akış tabanlı Paket Yöneticisi CentOS/RHEL için kullanma.</span><span class="sxs-lookup"><span data-stu-id="31a00-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="31a00-169">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="31a00-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="31a00-170">.NET Core Yükleyici komut dosyasıyla yükler komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="31a00-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="31a00-171">`dotnet-install` Komut dosyaları, CLI zincirinin ve paylaşılan çalışma zamanı yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31a00-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="31a00-172">Komut dosyasını indirebilirsiniz: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="31a00-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="31a00-173">Yükleyici bash betik Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31a00-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="31a00-174">Linux/OS X sistemleri komut ile kullanılabilmesi için bu komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="31a00-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31a00-175">Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="31a00-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="31a00-176">Red Hat Enterprise Linux (RHEL) 7 .NET Core yükleyin</span><span class="sxs-lookup"><span data-stu-id="31a00-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="31a00-177">.NET Core üzerinde RHEL 7 yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="31a00-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="31a00-178">RHEL 7 abonelik altında kullanılabilir Red Hat .NET kanal etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="31a00-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="31a00-179">Red Hat Enterprise 7 Server için kullanın:</span><span class="sxs-lookup"><span data-stu-id="31a00-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="31a00-180">Red Hat Enterprise 7 için iş istasyonu, kullanın:</span><span class="sxs-lookup"><span data-stu-id="31a00-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="31a00-181">Red Hat Enterprise 7 HPC işlem düğümü için kullanın:</span><span class="sxs-lookup"><span data-stu-id="31a00-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="31a00-182">Scl aracını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="31a00-183">.NET Core yükleyin</span><span class="sxs-lookup"><span data-stu-id="31a00-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-184">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="31a00-185">.NET Core 2.0 yükleme SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="31a00-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="31a00-186">.NET Core 2.0 SDK/Runtime ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="31a00-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-187">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="31a00-188">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="31a00-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="31a00-189">.NET Core 1.1 yüklemek SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="31a00-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="31a00-190">.NET Core 1.1 SDK ve çalışma zamanı, ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="31a00-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="31a00-191">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="31a00-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="31a00-192">.NET yüklemek çekirdek 1.0 SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="31a00-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="31a00-193">.NET Core 1.0 SDK ve çalışma zamanı, ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="31a00-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="31a00-194">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="31a00-195">Red Hat .NET kanal erişim kayıt Yardım için bkz: [.NET Core 1.1 Başlarken Kılavuzu, bölüm 1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) Red Hat hızında.</span><span class="sxs-lookup"><span data-stu-id="31a00-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="31a00-196">.NET Core Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 ve Linux Naneli 17, Linux Naneli 18 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="31a00-197">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-198">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="31a00-199">Microsoft Product anahtarı güvenilir olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="31a00-200">Akış istediğiniz sürümü konak paketini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="31a00-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="31a00-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="31a00-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="31a00-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="31a00-203">**Ubuntu 16.04 / Linux Naneli 18**</span><span class="sxs-lookup"><span data-stu-id="31a00-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="31a00-204">**Ubuntu 14.04 / Linux Naneli 17**</span><span class="sxs-lookup"><span data-stu-id="31a00-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="31a00-205">.NET Core yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. <span data-ttu-id="31a00-206">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-207">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="31a00-208">Akış istediğiniz sürümü konak paketini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="31a00-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="31a00-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="31a00-210">**Ubuntu 16.04 / Linux Naneli 18**</span><span class="sxs-lookup"><span data-stu-id="31a00-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="31a00-211">**Ubuntu 14.04 / Linux Naneli 17**</span><span class="sxs-lookup"><span data-stu-id="31a00-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="31a00-212">.NET yüklemek Ubuntu ya da Linux Naneli 1.x Çekirdek:</span><span class="sxs-lookup"><span data-stu-id="31a00-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="31a00-213">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="31a00-214">.NET Core Debian 8 veya Debian 9 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="31a00-215">.NET Core Debian 8 veya Debian 9 (64 bit) yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="31a00-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="31a00-216">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="31a00-217">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31a00-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-218">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="31a00-219">Sistem bileşenlerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="31a00-220">Güvenilen Microsoft Product anahtarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="31a00-221">Microsoft Product akışı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="31a00-222">**Debian 9 (Esnetme)**</span><span class="sxs-lookup"><span data-stu-id="31a00-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="31a00-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="31a00-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="31a00-224">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="31a00-225">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="31a00-226">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-227">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="31a00-228">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="31a00-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="31a00-229">.NET Core SDK ikili dosyaları (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="31a00-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="31a00-230">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="31a00-231">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="31a00-232">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="31a00-233">.NET Core Fedora 24, Fedora 25 veya Fedora 26 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="31a00-234">.NET Core yüklemek için Fedora 26 veya Fedora 25 veya .NET Core 2.x 1.x Fedora 24 üzerinde:</span><span class="sxs-lookup"><span data-stu-id="31a00-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="31a00-235">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="31a00-236">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31a00-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-237">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="31a00-238">**Fedora 26 veya Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="31a00-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="31a00-239">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="31a00-240">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="31a00-241">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="31a00-242">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-243">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="31a00-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="31a00-244">**Fedora 24**</span></span>

2. <span data-ttu-id="31a00-245">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="31a00-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="31a00-246">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="31a00-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="31a00-247">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="31a00-248">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="31a00-249">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="31a00-250">.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="31a00-251">.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="31a00-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="31a00-252">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="31a00-253">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31a00-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-254">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="31a00-255">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="31a00-256">Microsoft Product akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="31a00-257">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="31a00-258">DotNet YOLUNUZU ekleme</span><span class="sxs-lookup"><span data-stu-id="31a00-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-259">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="31a00-260">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="31a00-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="31a00-261">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="31a00-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="31a00-262">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="31a00-263">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="31a00-264">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="31a00-265">.NET Core SUSE Linux Enterprise Server (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="31a00-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="31a00-266">.NET Core yüklemek için 2.x için SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span><span class="sxs-lookup"><span data-stu-id="31a00-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="31a00-267">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="31a00-268">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="31a00-269">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="31a00-270">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="31a00-271">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="31a00-272">.NET Core (64 bit) openSUSE için yükleyin</span><span class="sxs-lookup"><span data-stu-id="31a00-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="31a00-273">.NET Core yüklemek için openSUSE veya .NET Core 2.x 1.x openSUSE (64 bit) için:</span><span class="sxs-lookup"><span data-stu-id="31a00-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="31a00-274">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="31a00-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="31a00-275">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31a00-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31a00-276">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="31a00-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="31a00-277">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="31a00-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="31a00-278">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="31a00-279">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="31a00-280">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31a00-281">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="31a00-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="31a00-282">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="31a00-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="31a00-283">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="31a00-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="31a00-284">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="31a00-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="31a00-285">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="31a00-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="31a00-286">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="31a00-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="31a00-287">Desteklenen bir Linux dağıtım/sürümünde .NET Core 2.x yükleme sorunları varsa başvurun [2.0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü dağıtımları/sürümü için konu.</span><span class="sxs-lookup"><span data-stu-id="31a00-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="31a00-288">Desteklenen bir Linux dağıtım/sürümünde .NET Core 1.x yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) yüklü dağıtımları konuları / sürümleri.</span><span class="sxs-lookup"><span data-stu-id="31a00-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
