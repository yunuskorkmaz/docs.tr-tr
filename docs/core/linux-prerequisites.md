---
title: Linux üzerinde .NET Core önkoşulları
description: Desteklenen Linux sürümleri ve .NET Core bağımlılıklarının geliştirmek, dağıtmak ve .NET Core uygulamaları Linux makinelerinde çalışır.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 0bd3287535ba2c398f6577890d1d39f42a806364
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614511"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="f48d6-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="f48d6-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="f48d6-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="f48d6-105">Desteklenen Linux dağıtımları/sürümleri ve bağımlılıklarını izleyen iki yolu Linux üzerinde .NET Core uygulamaları geliştirmek için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="f48d6-106">Sık kullandığınız düzenleyicinizi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="f48d6-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="f48d6-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f48d6-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="f48d6-108">.NET Core SDK paketini üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="f48d6-109">Yalnızca .NET Core çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="f48d6-110">.NET Core çalışma zamanı ile uygulamaları kendi içinde bir dağıtımının parçası olarak dağıtılan, Framework bağımlı uygulamaları ayrı ayrı dağıtılsa için ancak, dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="f48d6-111">Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f48d6-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="f48d6-112">Ayrıca bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="f48d6-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="f48d6-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="f48d6-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f48d6-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f48d6-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f48d6-115">.NET core 2.x tek bir işletim sistemi olarak Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="f48d6-116">Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.</span><span class="sxs-lookup"><span data-stu-id="f48d6-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="f48d6-117">Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="f48d6-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="f48d6-118">.NET core 2.x, aşağıdaki Linux dağıtımları/sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="f48d6-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-120">CentOS 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="f48d6-121">Oracle Linux 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="f48d6-122">Fedora 28, 27 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="f48d6-123">Debian 9 (64 bit `arm32`), 8,7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-124">Ubuntu 18.04 (64 bit `arm32`), 16.04, 14.04 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-125">Linux Naneli 18, 17 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-126">openSUSE 42.3 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="f48d6-128">Alpine Linux 3.7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="f48d6-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="f48d6-129">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="f48d6-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f48d6-130">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f48d6-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f48d6-131">Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="f48d6-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="f48d6-132">.NET core 1.x aşağıdaki Linux 64-bit üzerinde desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f48d6-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="f48d6-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="f48d6-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="f48d6-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f48d6-134">CentOS 7</span></span>
* <span data-ttu-id="f48d6-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="f48d6-135">Oracle Linux 7</span></span>
* <span data-ttu-id="f48d6-136">27 fedora 28 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="f48d6-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="f48d6-137">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f48d6-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="f48d6-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="f48d6-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="f48d6-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="f48d6-139">Linux Mint 17</span></span>
* <span data-ttu-id="f48d6-140">openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="f48d6-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="f48d6-141">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="f48d6-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="f48d6-142">.NET core 3.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="f48d6-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="f48d6-143">.NET core 3.0 Önizleme 1, tek bir işletim sistemi Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="f48d6-144">Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.</span><span class="sxs-lookup"><span data-stu-id="f48d6-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="f48d6-145">Daha fazla bilgi ve indirme bağlantıları [.NET Core 3.0 indirir](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="f48d6-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="f48d6-146">.NET core 3.0 Önizleme 1, aşağıdaki Linux dağıtımları/sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="f48d6-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f48d6-147">OS</span></span>                            | <span data-ttu-id="f48d6-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f48d6-148">Version</span></span>               | <span data-ttu-id="f48d6-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="f48d6-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="f48d6-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="f48d6-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="f48d6-151">6</span><span class="sxs-lookup"><span data-stu-id="f48d6-151">6</span></span>                     | <span data-ttu-id="f48d6-152">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-152">x64</span></span>
<span data-ttu-id="f48d6-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="f48d6-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="f48d6-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="f48d6-154">CentOS</span></span><br><span data-ttu-id="f48d6-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="f48d6-155">Oracle Linux</span></span>  | <span data-ttu-id="f48d6-156">7</span><span class="sxs-lookup"><span data-stu-id="f48d6-156">7</span></span>                     | <span data-ttu-id="f48d6-157">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-157">x64</span></span>
<span data-ttu-id="f48d6-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="f48d6-158">Fedora</span></span>                        | <span data-ttu-id="f48d6-159">28</span><span class="sxs-lookup"><span data-stu-id="f48d6-159">28</span></span>                    | <span data-ttu-id="f48d6-160">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-160">x64</span></span>
<span data-ttu-id="f48d6-161">Debian</span><span class="sxs-lookup"><span data-stu-id="f48d6-161">Debian</span></span>                        | <span data-ttu-id="f48d6-162">9</span><span class="sxs-lookup"><span data-stu-id="f48d6-162">9</span></span>                     | <span data-ttu-id="f48d6-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="f48d6-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="f48d6-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f48d6-164">Ubuntu</span></span>                        | <span data-ttu-id="f48d6-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="f48d6-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="f48d6-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="f48d6-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="f48d6-167">Linux Naneli</span><span class="sxs-lookup"><span data-stu-id="f48d6-167">Linux Mint</span></span>                    | <span data-ttu-id="f48d6-168">18</span><span class="sxs-lookup"><span data-stu-id="f48d6-168">18</span></span>                    | <span data-ttu-id="f48d6-169">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-169">x64</span></span>
<span data-ttu-id="f48d6-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f48d6-170">openSUSE</span></span>                      | <span data-ttu-id="f48d6-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="f48d6-171">42.3+</span></span>                 | <span data-ttu-id="f48d6-172">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-172">x64</span></span>
<span data-ttu-id="f48d6-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="f48d6-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="f48d6-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="f48d6-174">12 SP2+</span></span>               | <span data-ttu-id="f48d6-175">X64</span><span class="sxs-lookup"><span data-stu-id="f48d6-175">x64</span></span>
<span data-ttu-id="f48d6-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="f48d6-176">Alpine Linux</span></span>                  | <span data-ttu-id="f48d6-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="f48d6-177">3.8+</span></span>                  | <span data-ttu-id="f48d6-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="f48d6-178">x64, ARM64</span></span>

<span data-ttu-id="f48d6-179">\* ARM32 ve ARM64 desteği 9 Debian ve Ubuntu 16.04 başlatır.</span><span class="sxs-lookup"><span data-stu-id="f48d6-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="f48d6-180">Bu dağıtım paketlerini önceki sürümlerinde, ARM yongalarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f48d6-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="f48d6-181">Bkz: [.NET Core 3.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tam listesi .NET Core 3.0, desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="f48d6-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="f48d6-182">ARM64'te .NET Core 3.0 yükleme hakkında daha fazla bilgi için bkz. [Linux ARM64 üzerinde .NET Core 3.0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="f48d6-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="f48d6-183">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="f48d6-183">Linux distribution dependencies</span></span>

<span data-ttu-id="f48d6-184">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f48d6-184">The following are intended to be examples.</span></span> <span data-ttu-id="f48d6-185">Adları ve tam sürümünü, tercih ettiğiniz Linux dağıtımı biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="f48d6-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f48d6-186">Ubuntu</span></span>

<span data-ttu-id="f48d6-187">Ubuntu dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="f48d6-188">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="f48d6-188">liblttng-ust0</span></span>
* <span data-ttu-id="f48d6-189">libcurl3 (için 14.x ve 16.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="f48d6-190">libcurl4 (için 18.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="f48d6-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="f48d6-191">libssl1.0.0</span></span>
* <span data-ttu-id="f48d6-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="f48d6-192">libkrb5-3</span></span>
* <span data-ttu-id="f48d6-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="f48d6-193">zlib1g</span></span>
* <span data-ttu-id="f48d6-194">libicu52 (için 14.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="f48d6-195">libicu55 (için 16.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="f48d6-196">libicu57 (için 17.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="f48d6-197">libicu60 (için 18.x)</span><span class="sxs-lookup"><span data-stu-id="f48d6-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="f48d6-198">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="f48d6-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="f48d6-199">libunwind8</span></span>
* <span data-ttu-id="f48d6-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="f48d6-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="f48d6-201">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="f48d6-201">CentOS and Fedora</span></span>

<span data-ttu-id="f48d6-202">CentOS dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="f48d6-203">ust lttng</span><span class="sxs-lookup"><span data-stu-id="f48d6-203">lttng-ust</span></span>
* <span data-ttu-id="f48d6-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="f48d6-204">libcurl</span></span>
* <span data-ttu-id="f48d6-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="f48d6-205">openssl-libs</span></span>
* <span data-ttu-id="f48d6-206">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="f48d6-206">krb5-libs</span></span>
* <span data-ttu-id="f48d6-207">libicu</span><span class="sxs-lookup"><span data-stu-id="f48d6-207">libicu</span></span>
* <span data-ttu-id="f48d6-208">zlib</span><span class="sxs-lookup"><span data-stu-id="f48d6-208">zlib</span></span>

<span data-ttu-id="f48d6-209">Fedora kullanıcılar: Varsa, openssl'ın sürümü > = 1.1 compat openssl10'ı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="f48d6-210">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="f48d6-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="f48d6-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="f48d6-211">libunwind</span></span>
* <span data-ttu-id="f48d6-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="f48d6-212">libuuid</span></span>

<span data-ttu-id="f48d6-213">Bağımlılıklar hakkında daha fazla bilgi için bkz. [Self-contained Linux uygulamalarını](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f48d6-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="f48d6-214">Yerel yükleyicilerden ile .NET Core Bağımlılıkların yüklenmesi</span><span class="sxs-lookup"><span data-stu-id="f48d6-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="f48d6-215">Desteklenen Linux dağıtımları/sürümleri .NET core için yerel yükleyicilerden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="f48d6-216">Yerel yükleyicilerden sunucusuna (sudo) yönetici erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="f48d6-217">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıkları yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="f48d6-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="f48d6-218">Yerel yükleyiciler, .NET Core SDK'sı sistem genelinde da yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f48d6-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="f48d6-219">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="f48d6-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="f48d6-220">CentOS/RHEL Ubuntu için apt-get veya yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f48d6-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="f48d6-221">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="f48d6-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="f48d6-222">.NET Core Yükleyici komut dosyasını yükler betik oluşturma</span><span class="sxs-lookup"><span data-stu-id="f48d6-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="f48d6-223">[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI araç zinciri ve paylaşılan çalışma zamanı'nın bir yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f48d6-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="f48d6-224">Betikten indirebileceğiniz <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="f48d6-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="f48d6-225">Şu anda .NET Core 1.1 olan en son "LTS" sürümünü yüklemek için betik Varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="f48d6-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="f48d6-226">.NET Core 2.1 yüklemek için aşağıdaki geçiş betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f48d6-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="f48d6-227">Yükleyici bash betiğini Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f48d6-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="f48d6-228">Linux/OS X sistemleri komut ile kullanılabilmesi için bu betiği ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="f48d6-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="f48d6-229">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f48d6-229">Troubleshoot</span></span>

<span data-ttu-id="f48d6-230">Desteklenen bir Linux dağıtımı/sürümünde .NET Core yüklemesi ile ilgili sorunlar varsa, yüklü, dağıtımları/sürümleri için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="f48d6-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="f48d6-231">.NET core bilinen sorunları 3.0</span><span class="sxs-lookup"><span data-stu-id="f48d6-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="f48d6-232">.NET core bilinen sorunları 2.2</span><span class="sxs-lookup"><span data-stu-id="f48d6-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="f48d6-233">.NET core 2.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f48d6-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="f48d6-234">.NET core 1.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f48d6-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="f48d6-235">.NET core 1.0, bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="f48d6-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
