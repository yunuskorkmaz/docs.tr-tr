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
ms.openlocfilehash: 04fdf26e150e6d489c0641588563f69f24835615
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="bbca8-104">.NET Core Linux önkoşulları</span><span class="sxs-lookup"><span data-stu-id="bbca8-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="bbca8-105">Bu makalede Linux'ta .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="bbca8-106">Desteklenen Linux dağıtımları/sürümleri ve izleyin bağımlılıkları Linux'ta .NET Core uygulama geliştirme iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="bbca8-107">Tercih ettiğiniz Düzenleyicisi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="bbca8-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="bbca8-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bbca8-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="bbca8-109">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="bbca8-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-110">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bbca8-111">.NET core 2.0 tek bir işletim sistemi Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="bbca8-112">Bir tek desteklenen Linux distro'lar Linux yapı (her yonga Mimarisi) yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbca8-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="bbca8-113">NET çekirdek 2.x, aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bbca8-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="bbca8-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="bbca8-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-115">CentOS 7</span></span>
 * <span data-ttu-id="bbca8-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="bbca8-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="bbca8-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="bbca8-118">Debian 8,7 veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="bbca8-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="bbca8-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="bbca8-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="bbca8-120">Linux Naneli 18, Linux Naneli 17</span><span class="sxs-lookup"><span data-stu-id="bbca8-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="bbca8-121">openSUSE 42,2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bbca8-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="bbca8-122">SUSE Enterprise Linux (SLES) 12 SP2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bbca8-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="bbca8-123">Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="bbca8-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-124">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bbca8-125">.NET core 1.x aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bbca8-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="bbca8-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="bbca8-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-127">CentOS 7</span></span>
* <span data-ttu-id="bbca8-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bbca8-128">Oracle Linux 7</span></span>
* <span data-ttu-id="bbca8-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="bbca8-129">Fedora 24</span></span>
* <span data-ttu-id="bbca8-130">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bbca8-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="bbca8-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="bbca8-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="bbca8-132">Ubuntu 16.10 .NET Core 1.1 en son düzeltme eki sürümü tarafından desteklenen</span><span class="sxs-lookup"><span data-stu-id="bbca8-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="bbca8-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bbca8-133">Linux Mint 17</span></span>
* <span data-ttu-id="bbca8-134">openSUSE 42,1 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="bbca8-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="bbca8-135">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.</span><span class="sxs-lookup"><span data-stu-id="bbca8-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="bbca8-136">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="bbca8-136">Linux distribution dependencies</span></span>

<span data-ttu-id="bbca8-137">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bbca8-137">The following are intended to be examples.</span></span> <span data-ttu-id="bbca8-138">Tam sürümünü ve adları, seçim Linux dağıtımını biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="bbca8-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bbca8-139">Ubuntu</span></span>

<span data-ttu-id="bbca8-140">Ubuntu dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bbca8-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="bbca8-141">libunwind8</span></span>
* <span data-ttu-id="bbca8-142">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="bbca8-142">liblttng-ust0</span></span>
* <span data-ttu-id="bbca8-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="bbca8-143">libcurl3</span></span>
* <span data-ttu-id="bbca8-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="bbca8-144">libssl1.0.0</span></span>
* <span data-ttu-id="bbca8-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="bbca8-145">libuuid1</span></span>
* <span data-ttu-id="bbca8-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="bbca8-146">libkrb5</span></span>
* <span data-ttu-id="bbca8-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="bbca8-147">zlib1g</span></span>
* <span data-ttu-id="bbca8-148">libicu52 (için 14.X)</span><span class="sxs-lookup"><span data-stu-id="bbca8-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="bbca8-149">libicu55 (için 16.X)</span><span class="sxs-lookup"><span data-stu-id="bbca8-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="bbca8-150">libicu57 (için 17.X)</span><span class="sxs-lookup"><span data-stu-id="bbca8-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="bbca8-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="bbca8-151">CentOS</span></span>

<span data-ttu-id="bbca8-152">CentOS dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bbca8-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="bbca8-153">libunwind</span></span>
* <span data-ttu-id="bbca8-154">lttng hakkınızın</span><span class="sxs-lookup"><span data-stu-id="bbca8-154">lttng-ust</span></span>
* <span data-ttu-id="bbca8-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="bbca8-155">libcurl</span></span>
* <span data-ttu-id="bbca8-156">openssl kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="bbca8-156">openssl-libs</span></span>
* <span data-ttu-id="bbca8-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="bbca8-157">libuuid</span></span>
* <span data-ttu-id="bbca8-158">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="bbca8-158">krb5-libs</span></span>
* <span data-ttu-id="bbca8-159">libicu</span><span class="sxs-lookup"><span data-stu-id="bbca8-159">libicu</span></span>
* <span data-ttu-id="bbca8-160">Zlib</span><span class="sxs-lookup"><span data-stu-id="bbca8-160">zlib</span></span>

<span data-ttu-id="bbca8-161">Bağımlılıklar hakkında daha fazla bilgi için bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="bbca8-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="bbca8-162">.NET Core bağımlılıkları ile yerel yükleyicileri yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="bbca8-163">Desteklenen Linux dağıtımları/sürümleri .NET core yerel yükleyicileri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="bbca8-164">Yerel yükleyicileri sunucusuna yönetici (sudo) erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="bbca8-165">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıklarını yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="bbca8-166">Yerel yükleyicileri ayrıca .NET Core SDK sistem genelinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="bbca8-167">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="bbca8-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="bbca8-168">Get apt Ubuntu için veya yum gibi bir akış tabanlı Paket Yöneticisi CentOS/RHEL için kullanma.</span><span class="sxs-lookup"><span data-stu-id="bbca8-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="bbca8-169">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="bbca8-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="bbca8-170">.NET Core Yükleyici komut dosyasıyla yükler komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbca8-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="bbca8-171">`dotnet-install` Komut dosyaları, CLI zincirinin ve paylaşılan çalışma zamanı yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbca8-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="bbca8-172">Komut dosyasını indirebilirsiniz: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="bbca8-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="bbca8-173">Yükleyici bash betik Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbca8-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="bbca8-174">Linux/OS X sistemleri komut ile kullanılabilmesi için bu komut dosyası ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="bbca8-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbca8-175">Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="bbca8-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bbca8-176">Red Hat Enterprise Linux (RHEL) 7 .NET Core yükleyin</span><span class="sxs-lookup"><span data-stu-id="bbca8-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="bbca8-177">.NET Core üzerinde RHEL 7 yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="bbca8-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="bbca8-178">RHEL 7 abonelik altında kullanılabilir Red Hat .NET kanal etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="bbca8-179">Red Hat Enterprise 7 Server için kullanın:</span><span class="sxs-lookup"><span data-stu-id="bbca8-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="bbca8-180">Red Hat Enterprise 7 için iş istasyonu, kullanın:</span><span class="sxs-lookup"><span data-stu-id="bbca8-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="bbca8-181">Red Hat Enterprise 7 HPC işlem düğümü için kullanın:</span><span class="sxs-lookup"><span data-stu-id="bbca8-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="bbca8-182">Scl aracını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="bbca8-183">.NET Core yükleyin</span><span class="sxs-lookup"><span data-stu-id="bbca8-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-184">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bbca8-185">.NET Core 2.0 yükleme SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="bbca8-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="bbca8-186">.NET Core 2.0 SDK/Runtime ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-187">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bbca8-188">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="bbca8-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="bbca8-189">.NET Core 1.1 yüklemek SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="bbca8-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="bbca8-190">.NET Core 1.1 SDK ve çalışma zamanı, ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="bbca8-191">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="bbca8-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="bbca8-192">.NET yüklemek çekirdek 1.0 SDK ve çalışma zamanı:</span><span class="sxs-lookup"><span data-stu-id="bbca8-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="bbca8-193">.NET Core 1.0 SDK ve çalışma zamanı, ortamınız için etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="bbca8-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="bbca8-194">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="bbca8-195">Red Hat .NET kanal erişim kayıt Yardım için bkz: [.NET Core 1.1 Başlarken Kılavuzu, bölüm 1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) Red Hat hızında.</span><span class="sxs-lookup"><span data-stu-id="bbca8-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="bbca8-196">.NET Core Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 ve Linux Naneli 17, Linux Naneli 18 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="bbca8-197">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-198">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bbca8-199">Microsoft Product anahtarı güvenilir olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="bbca8-200">Akış istediğiniz sürümü konak paketini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="bbca8-201">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="bbca8-201">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="bbca8-202">**Ubuntu 16.04 / Linux Naneli 18**</span><span class="sxs-lookup"><span data-stu-id="bbca8-202">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="bbca8-203">**Ubuntu 14.04 / Linux Naneli 17**</span><span class="sxs-lookup"><span data-stu-id="bbca8-203">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="bbca8-204">.NET Core yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-204">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="bbca8-205">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-205">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-206">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-206">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bbca8-207">Akış istediğiniz sürümü konak paketini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-207">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="bbca8-208">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="bbca8-208">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="bbca8-209">**Ubuntu 16.04 / Linux Naneli 18**</span><span class="sxs-lookup"><span data-stu-id="bbca8-209">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="bbca8-210">**Ubuntu 14.04 / Linux Naneli 17**</span><span class="sxs-lookup"><span data-stu-id="bbca8-210">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="bbca8-211">.NET yüklemek Ubuntu ya da Linux Naneli 1.x Çekirdek:</span><span class="sxs-lookup"><span data-stu-id="bbca8-211">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="bbca8-212">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-212">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="bbca8-213">.NET Core Debian 8 veya Debian 9 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-213">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="bbca8-214">.NET Core Debian 8 veya Debian 9 (64 bit) yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="bbca8-214">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="bbca8-215">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-215">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bbca8-216">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-216">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-217">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-217">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bbca8-218">Sistem bileşenlerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-218">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="bbca8-219">Güvenilen Microsoft Product anahtarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-219">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="bbca8-220">Microsoft Product akışı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-220">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="bbca8-221">**Debian 9 (Esnetme)**</span><span class="sxs-lookup"><span data-stu-id="bbca8-221">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="bbca8-222">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="bbca8-222">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="bbca8-223">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-223">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="bbca8-224">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-224">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="bbca8-225">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-225">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-226">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-226">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bbca8-227">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-227">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="bbca8-228">.NET Core SDK ikili dosyaları (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-228">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="bbca8-229">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-229">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bbca8-230">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-230">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="bbca8-231">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-231">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="bbca8-232">.NET Core Fedora 24, Fedora 25 veya Fedora 26 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-232">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="bbca8-233">.NET Core yüklemek için Fedora 26 veya Fedora 25 veya .NET Core 2.x 1.x Fedora 24 üzerinde:</span><span class="sxs-lookup"><span data-stu-id="bbca8-233">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="bbca8-234">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-234">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bbca8-235">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-235">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-236">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bbca8-237">**Fedora 26 veya Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="bbca8-237">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="bbca8-238">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-238">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bbca8-239">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-239">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="bbca8-240">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-240">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bbca8-241">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-241">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-242">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-242">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bbca8-243">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="bbca8-243">**Fedora 24**</span></span>

2. <span data-ttu-id="bbca8-244">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-244">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="bbca8-245">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-245">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="bbca8-246">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-246">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bbca8-247">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-247">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="bbca8-248">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-248">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="bbca8-249">.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-249">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="bbca8-250">.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="bbca8-250">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="bbca8-251">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-251">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bbca8-252">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-252">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-253">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-253">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bbca8-254">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-254">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bbca8-255">Microsoft Product akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-255">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="bbca8-256">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-256">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bbca8-257">DotNet YOLUNUZU ekleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-257">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-258">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-258">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bbca8-259">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-259">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="bbca8-260">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-260">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="bbca8-261">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-261">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bbca8-262">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-262">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="bbca8-263">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-263">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="bbca8-264">.NET Core SUSE Linux Enterprise Server (64 bit) için yükleme</span><span class="sxs-lookup"><span data-stu-id="bbca8-264">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="bbca8-265">.NET Core yüklemek için 2.x için SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span><span class="sxs-lookup"><span data-stu-id="bbca8-265">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="bbca8-266">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-266">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bbca8-267">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-267">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="bbca8-268">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-268">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="bbca8-269">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-269">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="bbca8-270">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-270">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="bbca8-271">.NET Core (64 bit) openSUSE için yükleyin</span><span class="sxs-lookup"><span data-stu-id="bbca8-271">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="bbca8-272">.NET Core yüklemek için openSUSE veya .NET Core 2.x 1.x openSUSE (64 bit) için:</span><span class="sxs-lookup"><span data-stu-id="bbca8-272">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="bbca8-273">Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.</span><span class="sxs-lookup"><span data-stu-id="bbca8-273">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bbca8-274">Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bbca8-274">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bbca8-275">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-275">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bbca8-276">Microsoft imza anahtarı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-276">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bbca8-277">Dotnet ürün akışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-277">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="bbca8-278">.NET Core SDK yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-278">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bbca8-279">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-279">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bbca8-280">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="bbca8-280">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bbca8-281">Önkoşullar alın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-281">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="bbca8-282">.NET Core SDK ikili (tarball) indirin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-282">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="bbca8-283">.NET Core SDK ikili dosyaları ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="bbca8-283">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bbca8-284">DotNet YOLUNU ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbca8-284">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="bbca8-285">Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-285">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="bbca8-286">Desteklenen bir Linux dağıtım/sürümünde .NET Core 2.x yükleme sorunları varsa başvurun [2.0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü dağıtımları/sürümü için konu.</span><span class="sxs-lookup"><span data-stu-id="bbca8-286">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="bbca8-287">Desteklenen bir Linux dağıtım/sürümünde .NET Core 1.x yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) yüklü dağıtımları konuları / sürümleri.</span><span class="sxs-lookup"><span data-stu-id="bbca8-287">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
