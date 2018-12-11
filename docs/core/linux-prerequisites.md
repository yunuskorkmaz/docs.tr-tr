---
title: Linux üzerinde .NET Core önkoşulları
description: Desteklenen Linux sürümleri ve .NET Core bağımlılıklarının geliştirmek, dağıtmak ve .NET Core uygulamaları Linux makinelerinde çalışır.
author: thraka
ms.author: adegeo
ms.date: 12/03/2018
ms.openlocfilehash: e250158d10c6a03535f4e693e74954747f860a3c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148345"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="7f631-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="7f631-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="7f631-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f631-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="7f631-105">Desteklenen Linux dağıtımları/sürümleri ve bağımlılıklarını izleyen iki yolu Linux üzerinde .NET Core uygulamaları geliştirmek için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7f631-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="7f631-106">Sık kullandığınız düzenleyicinizi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="7f631-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="7f631-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7f631-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="7f631-108">.NET Core SDK paketini üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f631-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="7f631-109">Yalnızca .NET Core çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f631-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="7f631-110">.NET Core çalışma zamanı ile uygulamaları kendi içinde bir dağıtımının parçası olarak dağıtılan, Framework bağımlı uygulamaları ayrı ayrı dağıtılsa için ancak, dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f631-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="7f631-111">Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f631-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="7f631-112">Ayrıca bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="7f631-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="7f631-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="7f631-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7f631-114">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="7f631-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7f631-115">.NET core 2.x tek bir işletim sistemi olarak Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7f631-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="7f631-116">Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f631-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="7f631-117">Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="7f631-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="7f631-118">.NET core 2.x, aşağıdaki Linux dağıtımları/sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7f631-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="7f631-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-120">CentOS 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="7f631-121">Oracle Linux 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="7f631-122">Fedora 28, 27 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="7f631-123">Debian 9 (64 bit `arm32`), 8,7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-124">Ubuntu 18.04 (64 bit `arm32`), 16.04, 14.04 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-125">Linux Naneli 18, 17 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-126">openSUSE 42.3 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="7f631-128">Alpine Linux 3.7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="7f631-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="7f631-129">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="7f631-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7f631-130">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7f631-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7f631-131">Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="7f631-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="7f631-132">.NET core 1.x aşağıdaki Linux 64-bit üzerinde desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7f631-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="7f631-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7f631-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="7f631-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7f631-134">CentOS 7</span></span>
* <span data-ttu-id="7f631-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7f631-135">Oracle Linux 7</span></span>
* <span data-ttu-id="7f631-136">27 fedora 28 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="7f631-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="7f631-137">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="7f631-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="7f631-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="7f631-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="7f631-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="7f631-139">Linux Mint 17</span></span>
* <span data-ttu-id="7f631-140">openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="7f631-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="7f631-141">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="7f631-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="7f631-142">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="7f631-142">Linux distribution dependencies</span></span>

<span data-ttu-id="7f631-143">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f631-143">The following are intended to be examples.</span></span> <span data-ttu-id="7f631-144">Adları ve tam sürümünü, tercih ettiğiniz Linux dağıtımı biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="7f631-144">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="7f631-145">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7f631-145">Ubuntu</span></span>

<span data-ttu-id="7f631-146">Ubuntu dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7f631-146">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7f631-147">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="7f631-147">liblttng-ust0</span></span>
* <span data-ttu-id="7f631-148">libcurl3</span><span class="sxs-lookup"><span data-stu-id="7f631-148">libcurl3</span></span>
* <span data-ttu-id="7f631-149">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="7f631-149">libssl1.0.0</span></span>
* <span data-ttu-id="7f631-150">libkrb5 3</span><span class="sxs-lookup"><span data-stu-id="7f631-150">libkrb5-3</span></span>
* <span data-ttu-id="7f631-151">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7f631-151">zlib1g</span></span>
* <span data-ttu-id="7f631-152">libicu52 (için 14.x)</span><span class="sxs-lookup"><span data-stu-id="7f631-152">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="7f631-153">libicu55 (için 16.x)</span><span class="sxs-lookup"><span data-stu-id="7f631-153">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="7f631-154">libicu57 (için 17.x)</span><span class="sxs-lookup"><span data-stu-id="7f631-154">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="7f631-155">libicu60 (için 18.x)</span><span class="sxs-lookup"><span data-stu-id="7f631-155">libicu60 (for 18.x)</span></span>

<span data-ttu-id="7f631-156">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7f631-156">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="7f631-157">libunwind8</span><span class="sxs-lookup"><span data-stu-id="7f631-157">libunwind8</span></span>
* <span data-ttu-id="7f631-158">libuuid1</span><span class="sxs-lookup"><span data-stu-id="7f631-158">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="7f631-159">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="7f631-159">CentOS and Fedora</span></span>

<span data-ttu-id="7f631-160">CentOS dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7f631-160">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7f631-161">ust lttng</span><span class="sxs-lookup"><span data-stu-id="7f631-161">lttng-ust</span></span>
* <span data-ttu-id="7f631-162">libcurl</span><span class="sxs-lookup"><span data-stu-id="7f631-162">libcurl</span></span>
* <span data-ttu-id="7f631-163">openssl kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="7f631-163">openssl-libs</span></span>
* <span data-ttu-id="7f631-164">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="7f631-164">krb5-libs</span></span>
* <span data-ttu-id="7f631-165">libicu</span><span class="sxs-lookup"><span data-stu-id="7f631-165">libicu</span></span>
* <span data-ttu-id="7f631-166">Zlib</span><span class="sxs-lookup"><span data-stu-id="7f631-166">zlib</span></span>

<span data-ttu-id="7f631-167">Fedora kullanıcılar: Varsa, openssl'ın sürümü > = 1.1 compat openssl10'ı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f631-167">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="7f631-168">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7f631-168">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="7f631-169">libunwind</span><span class="sxs-lookup"><span data-stu-id="7f631-169">libunwind</span></span>
* <span data-ttu-id="7f631-170">libuuid</span><span class="sxs-lookup"><span data-stu-id="7f631-170">libuuid</span></span>

<span data-ttu-id="7f631-171">Bağımlılıklar hakkında daha fazla bilgi için bkz. [Self-contained Linux uygulamalarını](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="7f631-171">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="7f631-172">Yerel yükleyicilerden ile .NET Core Bağımlılıkların yüklenmesi</span><span class="sxs-lookup"><span data-stu-id="7f631-172">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="7f631-173">Desteklenen Linux dağıtımları/sürümleri .NET core için yerel yükleyicilerden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f631-173">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="7f631-174">Yerel yükleyicilerden sunucusuna (sudo) yönetici erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7f631-174">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="7f631-175">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıkları yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="7f631-175">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="7f631-176">Yerel yükleyiciler, .NET Core SDK'sı sistem genelinde da yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f631-176">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="7f631-177">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="7f631-177">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="7f631-178">CentOS/RHEL Ubuntu için apt-get veya yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7f631-178">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="7f631-179">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="7f631-179">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="7f631-180">.NET Core Yükleyici komut dosyasını yükler betik oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f631-180">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="7f631-181">[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI araç zinciri ve paylaşılan çalışma zamanı'nın bir yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f631-181">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="7f631-182">Betikten indirebileceğiniz [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="7f631-182">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="7f631-183">Şu anda .NET Core 1.1 olan en son "LTS" sürümünü yüklemek için betik Varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="7f631-183">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="7f631-184">.NET Core 2.1 yüklemek için aşağıdaki geçiş betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7f631-184">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="7f631-185">Yükleyici bash betiğini Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f631-185">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="7f631-186">Linux/OS X sistemleri komut ile kullanılabilmesi için bu betiği ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="7f631-186">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="7f631-187">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="7f631-187">Troubleshoot</span></span>

<span data-ttu-id="7f631-188">Desteklenen bir Linux dağıtımı/sürümünde .NET Core yüklemesi ile ilgili sorunlar varsa, yüklü, dağıtımları/sürümleri için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="7f631-188">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="7f631-189">.NET core bilinen sorunları 3.0</span><span class="sxs-lookup"><span data-stu-id="7f631-189">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="7f631-190">.NET core bilinen sorunları 2.2</span><span class="sxs-lookup"><span data-stu-id="7f631-190">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="7f631-191">.NET core 2.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7f631-191">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="7f631-192">.NET core 1.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7f631-192">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="7f631-193">.NET core 1.0, bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7f631-193">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
