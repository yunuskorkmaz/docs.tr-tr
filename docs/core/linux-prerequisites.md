---
title: Linux üzerinde .NET Core önkoşulları
description: Desteklenen Linux sürümleri ve .NET Core bağımlılıklarının geliştirmek, dağıtmak ve .NET Core uygulamaları Linux makinelerinde çalışır.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 7a2b0b3af97500ab0988e5de7a44713a8c05ccb9
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656056"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="1df42-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="1df42-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="1df42-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1df42-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="1df42-105">Desteklenen Linux dağıtımları/sürümleri ve bağımlılıklarını izleyen iki yolu Linux üzerinde .NET Core uygulamaları geliştirmek için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="1df42-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="1df42-106">Sık kullandığınız düzenleyicinizi ile komut satırı</span><span class="sxs-lookup"><span data-stu-id="1df42-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="1df42-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1df42-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="1df42-108">.NET Core SDK paketini üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1df42-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="1df42-109">Yalnızca .NET Core çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1df42-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="1df42-110">.NET Core çalışma zamanı ile uygulamaları kendi içinde bir dağıtımının parçası olarak dağıtılan, Framework bağımlı uygulamaları ayrı ayrı dağıtılsa için ancak, dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1df42-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="1df42-111">Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="1df42-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="1df42-112">Ayrıca bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="1df42-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="1df42-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="1df42-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1df42-114">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="1df42-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="1df42-115">.NET core 2.x tek bir işletim sistemi olarak Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1df42-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="1df42-116">Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.</span><span class="sxs-lookup"><span data-stu-id="1df42-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="1df42-117">Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="1df42-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="1df42-118">.NET core 2.x, aşağıdaki Linux dağıtımları/sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="1df42-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="1df42-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-120">CentOS 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="1df42-121">Oracle Linux 7 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="1df42-122">Fedora 28, 27 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="1df42-123">Debian 9 (64 bit `arm32`), 8,7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-124">Ubuntu 18.04 (64 bit `arm32`), 16.04, 14.04 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-125">Linux Naneli 18, 17 - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-126">openSUSE 42.3 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="1df42-128">Alpine Linux 3.7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="1df42-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="1df42-129">Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="1df42-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1df42-130">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="1df42-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1df42-131">Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="1df42-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="1df42-132">.NET core 1.x aşağıdaki Linux 64-bit üzerinde desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1df42-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="1df42-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="1df42-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="1df42-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1df42-134">CentOS 7</span></span>
* <span data-ttu-id="1df42-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="1df42-135">Oracle Linux 7</span></span>
* <span data-ttu-id="1df42-136">27 fedora 28 (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="1df42-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="1df42-137">Debian 8.2 veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="1df42-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="1df42-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="1df42-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="1df42-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="1df42-139">Linux Mint 17</span></span>
* <span data-ttu-id="1df42-140">openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="1df42-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="1df42-141">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="1df42-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="1df42-142">.NET core 3.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="1df42-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="1df42-143">.NET core 3.0 Önizleme 1, tek bir işletim sistemi Linux değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1df42-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="1df42-144">Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.</span><span class="sxs-lookup"><span data-stu-id="1df42-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="1df42-145">Daha fazla bilgi ve indirme bağlantıları [.NET Core 3.0 indirir](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="1df42-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="1df42-146">.NET core 3.0 Önizleme 1, aşağıdaki Linux dağıtımları/sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1df42-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="1df42-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="1df42-147">OS</span></span>                            | <span data-ttu-id="1df42-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1df42-148">Version</span></span>               | <span data-ttu-id="1df42-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="1df42-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="1df42-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="1df42-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="1df42-151">6</span><span class="sxs-lookup"><span data-stu-id="1df42-151">6</span></span>                     | <span data-ttu-id="1df42-152">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-152">x64</span></span>
<span data-ttu-id="1df42-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="1df42-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="1df42-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="1df42-154">CentOS</span></span><br><span data-ttu-id="1df42-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="1df42-155">Oracle Linux</span></span>  | <span data-ttu-id="1df42-156">7</span><span class="sxs-lookup"><span data-stu-id="1df42-156">7</span></span>                     | <span data-ttu-id="1df42-157">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-157">x64</span></span>
<span data-ttu-id="1df42-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="1df42-158">Fedora</span></span>                        | <span data-ttu-id="1df42-159">28</span><span class="sxs-lookup"><span data-stu-id="1df42-159">28</span></span>                    | <span data-ttu-id="1df42-160">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-160">x64</span></span>
<span data-ttu-id="1df42-161">Debian</span><span class="sxs-lookup"><span data-stu-id="1df42-161">Debian</span></span>                        | <span data-ttu-id="1df42-162">9</span><span class="sxs-lookup"><span data-stu-id="1df42-162">9</span></span>                     | <span data-ttu-id="1df42-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="1df42-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="1df42-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1df42-164">Ubuntu</span></span>                        | <span data-ttu-id="1df42-165">16.04 +, 18.04 +</span><span class="sxs-lookup"><span data-stu-id="1df42-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="1df42-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="1df42-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="1df42-167">Linux Naneli</span><span class="sxs-lookup"><span data-stu-id="1df42-167">Linux Mint</span></span>                    | <span data-ttu-id="1df42-168">18</span><span class="sxs-lookup"><span data-stu-id="1df42-168">18</span></span>                    | <span data-ttu-id="1df42-169">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-169">x64</span></span>
<span data-ttu-id="1df42-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1df42-170">openSUSE</span></span>                      | <span data-ttu-id="1df42-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="1df42-171">42.3+</span></span>                 | <span data-ttu-id="1df42-172">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-172">x64</span></span>
<span data-ttu-id="1df42-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="1df42-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="1df42-174">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="1df42-174">12 SP2+</span></span>               | <span data-ttu-id="1df42-175">X64</span><span class="sxs-lookup"><span data-stu-id="1df42-175">x64</span></span>
<span data-ttu-id="1df42-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="1df42-176">Alpine Linux</span></span>                  | <span data-ttu-id="1df42-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="1df42-177">3.8+</span></span>                  | <span data-ttu-id="1df42-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="1df42-178">x64, ARM64</span></span>

<span data-ttu-id="1df42-179">\* ARM32 ve ARM64 desteği 9 Debian ve Ubuntu 16.04 başlatır.</span><span class="sxs-lookup"><span data-stu-id="1df42-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="1df42-180">Bu dağıtım paketlerini önceki sürümlerinde, ARM yongalarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1df42-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="1df42-181">Bkz: [.NET Core 3.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tam listesi .NET Core 3.0, desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.</span><span class="sxs-lookup"><span data-stu-id="1df42-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="1df42-182">ARM64'te .NET Core 3.0 yükleme hakkında daha fazla bilgi için bkz. [Linux ARM64 üzerinde .NET Core 3.0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="1df42-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>



---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="1df42-183">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="1df42-183">Linux distribution dependencies</span></span>

<span data-ttu-id="1df42-184">Aşağıdaki örnekler olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1df42-184">The following are intended to be examples.</span></span> <span data-ttu-id="1df42-185">Adları ve tam sürümünü, tercih ettiğiniz Linux dağıtımı biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="1df42-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="1df42-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1df42-186">Ubuntu</span></span>

<span data-ttu-id="1df42-187">Ubuntu dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1df42-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="1df42-188">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="1df42-188">liblttng-ust0</span></span>
* <span data-ttu-id="1df42-189">libcurl3</span><span class="sxs-lookup"><span data-stu-id="1df42-189">libcurl3</span></span>
* <span data-ttu-id="1df42-190">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="1df42-190">libssl1.0.0</span></span>
* <span data-ttu-id="1df42-191">libkrb5 3</span><span class="sxs-lookup"><span data-stu-id="1df42-191">libkrb5-3</span></span>
* <span data-ttu-id="1df42-192">zlib1g</span><span class="sxs-lookup"><span data-stu-id="1df42-192">zlib1g</span></span>
* <span data-ttu-id="1df42-193">libicu52 (için 14.x)</span><span class="sxs-lookup"><span data-stu-id="1df42-193">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="1df42-194">libicu55 (için 16.x)</span><span class="sxs-lookup"><span data-stu-id="1df42-194">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="1df42-195">libicu57 (için 17.x)</span><span class="sxs-lookup"><span data-stu-id="1df42-195">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="1df42-196">libicu60 (için 18.x)</span><span class="sxs-lookup"><span data-stu-id="1df42-196">libicu60 (for 18.x)</span></span>

<span data-ttu-id="1df42-197">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="1df42-197">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="1df42-198">libunwind8</span><span class="sxs-lookup"><span data-stu-id="1df42-198">libunwind8</span></span>
* <span data-ttu-id="1df42-199">libuuid1</span><span class="sxs-lookup"><span data-stu-id="1df42-199">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="1df42-200">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="1df42-200">CentOS and Fedora</span></span>

<span data-ttu-id="1df42-201">CentOS dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1df42-201">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="1df42-202">ust lttng</span><span class="sxs-lookup"><span data-stu-id="1df42-202">lttng-ust</span></span>
* <span data-ttu-id="1df42-203">libcurl</span><span class="sxs-lookup"><span data-stu-id="1df42-203">libcurl</span></span>
* <span data-ttu-id="1df42-204">openssl kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="1df42-204">openssl-libs</span></span>
* <span data-ttu-id="1df42-205">krb5 kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="1df42-205">krb5-libs</span></span>
* <span data-ttu-id="1df42-206">libicu</span><span class="sxs-lookup"><span data-stu-id="1df42-206">libicu</span></span>
* <span data-ttu-id="1df42-207">Zlib</span><span class="sxs-lookup"><span data-stu-id="1df42-207">zlib</span></span>

<span data-ttu-id="1df42-208">Fedora kullanıcılar: Varsa, openssl'ın sürümü > = 1.1 compat openssl10'ı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1df42-208">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="1df42-209">Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="1df42-209">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="1df42-210">libunwind</span><span class="sxs-lookup"><span data-stu-id="1df42-210">libunwind</span></span>
* <span data-ttu-id="1df42-211">libuuid</span><span class="sxs-lookup"><span data-stu-id="1df42-211">libuuid</span></span>

<span data-ttu-id="1df42-212">Bağımlılıklar hakkında daha fazla bilgi için bkz. [Self-contained Linux uygulamalarını](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="1df42-212">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="1df42-213">Yerel yükleyicilerden ile .NET Core Bağımlılıkların yüklenmesi</span><span class="sxs-lookup"><span data-stu-id="1df42-213">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="1df42-214">Desteklenen Linux dağıtımları/sürümleri .NET core için yerel yükleyicilerden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1df42-214">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="1df42-215">Yerel yükleyicilerden sunucusuna (sudo) yönetici erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1df42-215">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="1df42-216">Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıkları yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="1df42-216">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="1df42-217">Yerel yükleyiciler, .NET Core SDK'sı sistem genelinde da yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1df42-217">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="1df42-218">Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="1df42-218">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="1df42-219">CentOS/RHEL Ubuntu için apt-get veya yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1df42-219">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="1df42-220">Paketleri kendileri DEB veya RPM kullanma.</span><span class="sxs-lookup"><span data-stu-id="1df42-220">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="1df42-221">.NET Core Yükleyici komut dosyasını yükler betik oluşturma</span><span class="sxs-lookup"><span data-stu-id="1df42-221">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="1df42-222">[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI araç zinciri ve paylaşılan çalışma zamanı'nın bir yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1df42-222">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="1df42-223">Betikten indirebileceğiniz [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="1df42-223">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="1df42-224">Şu anda .NET Core 1.1 olan en son "LTS" sürümünü yüklemek için betik Varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="1df42-224">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="1df42-225">.NET Core 2.1 yüklemek için aşağıdaki geçiş betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1df42-225">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="1df42-226">Yükleyici bash betiğini Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1df42-226">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="1df42-227">Linux/OS X sistemleri komut ile kullanılabilmesi için bu betiği ayrıca PowerShell anahtarları okur.</span><span class="sxs-lookup"><span data-stu-id="1df42-227">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="1df42-228">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1df42-228">Troubleshoot</span></span>

<span data-ttu-id="1df42-229">Desteklenen bir Linux dağıtımı/sürümünde .NET Core yüklemesi ile ilgili sorunlar varsa, yüklü, dağıtımları/sürümleri için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="1df42-229">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="1df42-230">.NET core bilinen sorunları 3.0</span><span class="sxs-lookup"><span data-stu-id="1df42-230">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="1df42-231">.NET core bilinen sorunları 2.2</span><span class="sxs-lookup"><span data-stu-id="1df42-231">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="1df42-232">.NET core 2.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="1df42-232">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="1df42-233">.NET core 1.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="1df42-233">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="1df42-234">.NET core 1.0, bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="1df42-234">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
