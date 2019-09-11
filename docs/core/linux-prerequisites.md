---
title: Linux üzerinde .NET Core önkoşulları
description: Linux makinelerde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen Linux sürümleri ve .NET Core bağımlılıkları.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: ad1ab42bcf66e32a45351ae2b6156251c9d0dc1f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849064"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="477ef-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="477ef-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="477ef-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için gereken bağımlılıklar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="477ef-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="477ef-105">Desteklenen Linux dağıtımları/sürümleri ve aşağıdaki bağımlılıklar, Linux üzerinde .NET Core uygulamaları geliştirmenin iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="477ef-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="477ef-106">En sevdiğiniz düzenleyicinizle komut satırı</span><span class="sxs-lookup"><span data-stu-id="477ef-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="477ef-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="477ef-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="477ef-108">.NET Core SDK paketi üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="477ef-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="477ef-109">Üretim ortamlarına dağıtılan uygulamalar için yalnızca .NET Core çalışma zamanı paketi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="477ef-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="477ef-110">.NET Core çalışma zamanı, uygulamalar ile birlikte bulunan bir dağıtımın parçası olarak dağıtılır, ancak çerçeveye bağımlı dağıtılan uygulamalar için ayrı olarak dağıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="477ef-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="477ef-111">Çerçeveye bağımlı ve kendi kendine içerilen dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="477ef-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="477ef-112">Ayrıca, belirli yönergeler için [kendi Içindeki Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="477ef-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="477ef-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="477ef-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="477ef-114">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="477ef-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="477ef-115">.NET Core 2. x, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="477ef-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="477ef-116">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="477ef-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="477ef-117">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="477ef-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="477ef-118">.NET Core 2. x, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="477ef-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="477ef-119">Red Hat Enterprise Linux 7, 6-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-120">CentOS 7-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="477ef-121">Oracle Linux 7-64 bit (`x86_64` veya) `amd64`</span><span class="sxs-lookup"><span data-stu-id="477ef-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="477ef-122">Fedora 28, 27-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="477ef-123">9 (64-bit, `arm32`), 8,7 veya sonraki sürümler-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-124">Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-125">Linux Mint 18, 17-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-126">openSUSE 42,3 veya sonraki sürümleri-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-127">Suse Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="477ef-128">Alp Linux 3,7 veya sonraki sürümleri-64-bit (`x86_64` veya `amd64`)</span><span class="sxs-lookup"><span data-stu-id="477ef-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="477ef-129">.NET Core 2,1 ve .NET Core 2,2 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 2,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) işletim sistemi sürümleri ve [.NET Core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) ' ne bakın Köprü.</span><span class="sxs-lookup"><span data-stu-id="477ef-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="477ef-130">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="477ef-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="477ef-131">İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 1,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.1) veya [.NET Core 1,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="477ef-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="477ef-132">.NET Core 1. x, aşağıdaki Linux 64-bit (`x86_64` veya `amd64`) dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="477ef-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="477ef-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="477ef-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="477ef-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="477ef-134">CentOS 7</span></span>
* <span data-ttu-id="477ef-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="477ef-135">Oracle Linux 7</span></span>
* <span data-ttu-id="477ef-136">Fedora 28 (.NET Core 1,1), 27</span><span class="sxs-lookup"><span data-stu-id="477ef-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="477ef-137">8,2 veya sonraki sürümlerini kaldırma</span><span class="sxs-lookup"><span data-stu-id="477ef-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="477ef-138">Ubuntu 18,04 (.NET Core 1,1), 16,04, 14,04</span><span class="sxs-lookup"><span data-stu-id="477ef-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="477ef-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="477ef-139">Linux Mint 17</span></span>
* <span data-ttu-id="477ef-140">openSUSE 42,3 veya sonraki sürümleri (.NET Core 1,1)</span><span class="sxs-lookup"><span data-stu-id="477ef-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="477ef-141">.NET Core 1. x desteklenen işletim sistemlerinin tüm listesi için bkz. .NET Core [1.](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) x tarafından desteklenen işletim sistemleri, destek sistemi sürümlerinin dışında ve yaşam döngüsü ilkesi bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="477ef-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="477ef-142">.NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="477ef-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="477ef-143">.NET Core 3,0 Preview 1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="477ef-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="477ef-144">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="477ef-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="477ef-145">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="477ef-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="477ef-146">.NET Core 3,0 Preview 1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="477ef-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="477ef-147">OS</span><span class="sxs-lookup"><span data-stu-id="477ef-147">OS</span></span>                            | <span data-ttu-id="477ef-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="477ef-148">Version</span></span>               | <span data-ttu-id="477ef-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="477ef-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="477ef-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="477ef-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="477ef-151">6</span><span class="sxs-lookup"><span data-stu-id="477ef-151">6</span></span>                     | <span data-ttu-id="477ef-152">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-152">x64</span></span>
<span data-ttu-id="477ef-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="477ef-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="477ef-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="477ef-154">CentOS</span></span><br><span data-ttu-id="477ef-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="477ef-155">Oracle Linux</span></span>  | <span data-ttu-id="477ef-156">7</span><span class="sxs-lookup"><span data-stu-id="477ef-156">7</span></span>                     | <span data-ttu-id="477ef-157">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-157">x64</span></span>
<span data-ttu-id="477ef-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="477ef-158">Fedora</span></span>                        | <span data-ttu-id="477ef-159">28</span><span class="sxs-lookup"><span data-stu-id="477ef-159">28</span></span>                    | <span data-ttu-id="477ef-160">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-160">x64</span></span>
<span data-ttu-id="477ef-161">Debian</span><span class="sxs-lookup"><span data-stu-id="477ef-161">Debian</span></span>                        | <span data-ttu-id="477ef-162">9</span><span class="sxs-lookup"><span data-stu-id="477ef-162">9</span></span>                     | <span data-ttu-id="477ef-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="477ef-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="477ef-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="477ef-164">Ubuntu</span></span>                        | <span data-ttu-id="477ef-165">16.04 +, 18.04 +</span><span class="sxs-lookup"><span data-stu-id="477ef-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="477ef-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="477ef-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="477ef-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="477ef-167">Linux Mint</span></span>                    | <span data-ttu-id="477ef-168">18</span><span class="sxs-lookup"><span data-stu-id="477ef-168">18</span></span>                    | <span data-ttu-id="477ef-169">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-169">x64</span></span>
<span data-ttu-id="477ef-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="477ef-170">openSUSE</span></span>                      | <span data-ttu-id="477ef-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="477ef-171">42.3+</span></span>                 | <span data-ttu-id="477ef-172">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-172">x64</span></span>
<span data-ttu-id="477ef-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="477ef-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="477ef-174">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="477ef-174">12 SP2+</span></span>               | <span data-ttu-id="477ef-175">X64</span><span class="sxs-lookup"><span data-stu-id="477ef-175">x64</span></span>
<span data-ttu-id="477ef-176">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="477ef-176">Alpine Linux</span></span>                  | <span data-ttu-id="477ef-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="477ef-177">3.8+</span></span>                  | <span data-ttu-id="477ef-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="477ef-178">x64, ARM64</span></span>

<span data-ttu-id="477ef-179">\*ARM32 ve ARM64 desteği, de, 9 ve Ubuntu 16,04 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="477ef-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="477ef-180">Bu detrolar 'ın önceki sürümleri ARM yongalarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="477ef-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="477ef-181">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="477ef-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="477ef-182">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="477ef-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="477ef-183">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="477ef-183">Linux distribution dependencies</span></span>

<span data-ttu-id="477ef-184">Aşağıdakiler örnek olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="477ef-184">The following are intended to be examples.</span></span> <span data-ttu-id="477ef-185">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="477ef-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="477ef-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="477ef-186">Ubuntu</span></span>

<span data-ttu-id="477ef-187">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="477ef-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="477ef-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="477ef-188">liblttng-ust0</span></span>
* <span data-ttu-id="477ef-189">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="477ef-190">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="477ef-191">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="477ef-191">libssl1.0.0</span></span>
* <span data-ttu-id="477ef-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="477ef-192">libkrb5-3</span></span>
* <span data-ttu-id="477ef-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="477ef-193">zlib1g</span></span>
* <span data-ttu-id="477ef-194">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="477ef-195">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="477ef-196">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="477ef-197">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="477ef-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="477ef-198">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="477ef-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="477ef-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="477ef-199">libunwind8</span></span>
* <span data-ttu-id="477ef-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="477ef-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="477ef-201">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="477ef-201">CentOS and Fedora</span></span>

<span data-ttu-id="477ef-202">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="477ef-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="477ef-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="477ef-203">lttng-ust</span></span>
* <span data-ttu-id="477ef-204">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="477ef-204">libcurl</span></span>
* <span data-ttu-id="477ef-205">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="477ef-205">openssl-libs</span></span>
* <span data-ttu-id="477ef-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="477ef-206">krb5-libs</span></span>
* <span data-ttu-id="477ef-207">libıu</span><span class="sxs-lookup"><span data-stu-id="477ef-207">libicu</span></span>
* <span data-ttu-id="477ef-208">zlib</span><span class="sxs-lookup"><span data-stu-id="477ef-208">zlib</span></span>

<span data-ttu-id="477ef-209">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 ise, COMPAT-openssl10 ' ı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="477ef-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="477ef-210">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="477ef-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="477ef-211">librüzgar</span><span class="sxs-lookup"><span data-stu-id="477ef-211">libunwind</span></span>
* <span data-ttu-id="477ef-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="477ef-212">libuuid</span></span>

<span data-ttu-id="477ef-213">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="477ef-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="477ef-214">Yerel yükleyicilerle .NET Core bağımlılıklarını yükleme</span><span class="sxs-lookup"><span data-stu-id="477ef-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="477ef-215">.NET Core yerel yükleyicileri desteklenen Linux dağıtımları/sürümleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="477ef-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="477ef-216">Yerel yükleyiciler sunucuya yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="477ef-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="477ef-217">Yerel bir yükleyiciyi kullanmanın avantajı, tüm .NET Core yerel bağımlılıklarının yüklü olması.</span><span class="sxs-lookup"><span data-stu-id="477ef-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="477ef-218">Yerel yükleyiciler Ayrıca sistem genelinde .NET Core SDK de yükler.</span><span class="sxs-lookup"><span data-stu-id="477ef-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="477ef-219">Linux 'ta iki yükleyici paketi seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="477ef-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="477ef-220">Bir akış tabanlı Paket Yöneticisi, Ubuntu için apt-get veya CentOS/RHEL için de rivı kullanma.</span><span class="sxs-lookup"><span data-stu-id="477ef-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="477ef-221">Paketlerin kendisini, DEB veya RPM 'yi kullanma.</span><span class="sxs-lookup"><span data-stu-id="477ef-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="477ef-222">.NET Core yükleyici betiği ile betik yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="477ef-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="477ef-223">[DotNet-install betikleri](./tools/dotnet-install-script.md) , CLI araç zinciri ve paylaşılan çalışma zamanının yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="477ef-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="477ef-224">Betiği konumundan <https://dot.net/v1/dotnet-install.sh>indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="477ef-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="477ef-225">Komut dosyası, şu anda .NET Core 1,1 olan en son "LTS" sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="477ef-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="477ef-226">.NET Core 2,1 yüklemek için betiği aşağıdaki anahtarla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="477ef-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="477ef-227">Yükleyici Bash betiği, Otomasyon senaryolarında ve yönetici olmayan yüklemelerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="477ef-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="477ef-228">Bu betik Ayrıca PowerShell anahtarlarını okur, bu nedenle Linux/OS X sistemlerinde komut dosyasıyla kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="477ef-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="477ef-229">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="477ef-229">Troubleshoot</span></span>

<span data-ttu-id="477ef-230">Desteklenen bir Linux dağıtımında/sürümünde .NET Core yüklemesiyle ilgili sorunlar yaşıyorsanız, yüklü dağıtımlarınız/sürümleriniz için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="477ef-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="477ef-231">.NET Core 3,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="477ef-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="477ef-232">.NET Core 2,2 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="477ef-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="477ef-233">.NET Core 2,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="477ef-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="477ef-234">.NET Core 1,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="477ef-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="477ef-235">.NET Core 1,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="477ef-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
