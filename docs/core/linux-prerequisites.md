---
title: Linux üzerinde .NET Core önkoşulları
description: Linux makinelerde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen Linux sürümleri ve .NET Core bağımlılıkları.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: 0e798e86fcf88a1b7a67f50c2301e10ad725fad8
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521493"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="501ff-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="501ff-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="501ff-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için gereken bağımlılıklar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="501ff-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="501ff-105">Desteklenen Linux dağıtımları/sürümleri ve aşağıdaki bağımlılıklar, Linux üzerinde .NET Core uygulamaları geliştirmenin iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="501ff-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

- [<span data-ttu-id="501ff-106">En sevdiğiniz düzenleyicinizle komut satırı</span><span class="sxs-lookup"><span data-stu-id="501ff-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="501ff-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="501ff-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="501ff-108">.NET Core SDK paketi üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="501ff-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="501ff-109">Üretim ortamlarına dağıtılan uygulamalar için yalnızca .NET Core çalışma zamanı paketi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="501ff-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="501ff-110">.NET Core çalışma zamanı, uygulamalar ile birlikte bulunan bir dağıtımın parçası olarak dağıtılır, ancak çerçeveye bağımlı dağıtılan uygulamalar için ayrı olarak dağıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="501ff-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="501ff-111">Çerçeveye bağımlı ve kendi kendine içerilen dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="501ff-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="501ff-112">Ayrıca, belirli yönergeler için [kendi Içindeki Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="501ff-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="501ff-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="501ff-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="501ff-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="501ff-114">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="501ff-115">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="501ff-115">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="501ff-116">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="501ff-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="501ff-117">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="501ff-117">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="501ff-118">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir):</span><span class="sxs-lookup"><span data-stu-id="501ff-118">.NET Core 3.0 is supported on the following Linux distributions/versions):</span></span>

> [!NOTE]
> <span data-ttu-id="501ff-119">@No__t_0 sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="501ff-119">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="501ff-120">ATAYAMADı</span><span class="sxs-lookup"><span data-stu-id="501ff-120">OS</span></span>                             | <span data-ttu-id="501ff-121">Version</span><span class="sxs-lookup"><span data-stu-id="501ff-121">Version</span></span>               | <span data-ttu-id="501ff-122">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="501ff-122">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="501ff-123">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-123">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="501ff-124">6 +, 7</span><span class="sxs-lookup"><span data-stu-id="501ff-124">6+, 7</span></span>                 | <span data-ttu-id="501ff-125">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-125">x64</span></span> |
| <span data-ttu-id="501ff-126">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-126">Oracle Linux</span></span>                   | <span data-ttu-id="501ff-127">7</span><span class="sxs-lookup"><span data-stu-id="501ff-127">7</span></span>                     | <span data-ttu-id="501ff-128">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-128">x64</span></span> |
| <span data-ttu-id="501ff-129">CentOS</span><span class="sxs-lookup"><span data-stu-id="501ff-129">CentOS</span></span>                         | <span data-ttu-id="501ff-130">7</span><span class="sxs-lookup"><span data-stu-id="501ff-130">7</span></span>                     | <span data-ttu-id="501ff-131">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-131">x64</span></span> |
| <span data-ttu-id="501ff-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="501ff-132">Fedora</span></span>                         | <span data-ttu-id="501ff-133">29 +</span><span class="sxs-lookup"><span data-stu-id="501ff-133">29+</span></span>                   | <span data-ttu-id="501ff-134">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-134">x64</span></span> |
| <span data-ttu-id="501ff-135">Debian</span><span class="sxs-lookup"><span data-stu-id="501ff-135">Debian</span></span>                         | <span data-ttu-id="501ff-136">9 +</span><span class="sxs-lookup"><span data-stu-id="501ff-136">9+</span></span>                    | <span data-ttu-id="501ff-137">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="501ff-137">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="501ff-138">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="501ff-138">Ubuntu</span></span>                         | <span data-ttu-id="501ff-139">16.04 +</span><span class="sxs-lookup"><span data-stu-id="501ff-139">16.04+</span></span>                | <span data-ttu-id="501ff-140">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="501ff-140">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="501ff-141">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="501ff-141">Linux Mint</span></span>                     | <span data-ttu-id="501ff-142">18 +</span><span class="sxs-lookup"><span data-stu-id="501ff-142">18+</span></span>                   | <span data-ttu-id="501ff-143">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-143">x64</span></span> |
| <span data-ttu-id="501ff-144">openSUSE</span><span class="sxs-lookup"><span data-stu-id="501ff-144">openSUSE</span></span>                       | <span data-ttu-id="501ff-145">15 +</span><span class="sxs-lookup"><span data-stu-id="501ff-145">15+</span></span>                   | <span data-ttu-id="501ff-146">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-146">x64</span></span> |
| <span data-ttu-id="501ff-147">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="501ff-147">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="501ff-148">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="501ff-148">12 SP2+</span></span>               | <span data-ttu-id="501ff-149">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-149">x64</span></span> |
| <span data-ttu-id="501ff-150">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-150">Alpine Linux</span></span>                   | <span data-ttu-id="501ff-151">3.8 +</span><span class="sxs-lookup"><span data-stu-id="501ff-151">3.8+</span></span>                  | <span data-ttu-id="501ff-152">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="501ff-152">x64, ARM64</span></span> |

<span data-ttu-id="501ff-153">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="501ff-153">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="501ff-154">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="501ff-154">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="501ff-155">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="501ff-155">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="501ff-156">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="501ff-156">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="501ff-157">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="501ff-157">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="501ff-158">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span><span class="sxs-lookup"><span data-stu-id="501ff-158">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span></span>

<span data-ttu-id="501ff-159">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="501ff-159">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="501ff-160">@No__t_0 sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="501ff-160">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="501ff-161">ATAYAMADı</span><span class="sxs-lookup"><span data-stu-id="501ff-161">OS</span></span>                             |  <span data-ttu-id="501ff-162">Version</span><span class="sxs-lookup"><span data-stu-id="501ff-162">Version</span></span>                |  <span data-ttu-id="501ff-163">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="501ff-163">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="501ff-164">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-164">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="501ff-165">6, 7</span><span class="sxs-lookup"><span data-stu-id="501ff-165">6, 7</span></span>                   | <span data-ttu-id="501ff-166">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-166">x64</span></span> |
| <span data-ttu-id="501ff-167">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-167">Oracle Linux</span></span>                   |  <span data-ttu-id="501ff-168">7</span><span class="sxs-lookup"><span data-stu-id="501ff-168">7</span></span>                      | <span data-ttu-id="501ff-169">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-169">x64</span></span> |
| <span data-ttu-id="501ff-170">CentOS</span><span class="sxs-lookup"><span data-stu-id="501ff-170">CentOS</span></span>                         |  <span data-ttu-id="501ff-171">7</span><span class="sxs-lookup"><span data-stu-id="501ff-171">7</span></span>                      | <span data-ttu-id="501ff-172">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-172">x64</span></span> |
| <span data-ttu-id="501ff-173">Fedora</span><span class="sxs-lookup"><span data-stu-id="501ff-173">Fedora</span></span>                         |  <span data-ttu-id="501ff-174">29, 30</span><span class="sxs-lookup"><span data-stu-id="501ff-174">29, 30</span></span>                 | <span data-ttu-id="501ff-175">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-175">x64</span></span> |
| <span data-ttu-id="501ff-176">Debian</span><span class="sxs-lookup"><span data-stu-id="501ff-176">Debian</span></span>                         |  <span data-ttu-id="501ff-177">9</span><span class="sxs-lookup"><span data-stu-id="501ff-177">9</span></span>                      | <span data-ttu-id="501ff-178">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="501ff-178">x64, ARM32</span></span> |
| <span data-ttu-id="501ff-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="501ff-179">Ubuntu</span></span>                         |  <span data-ttu-id="501ff-180">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="501ff-180">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="501ff-181">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="501ff-181">x64, ARM32</span></span> |
| <span data-ttu-id="501ff-182">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="501ff-182">Linux Mint</span></span>                     |  <span data-ttu-id="501ff-183">17, 18</span><span class="sxs-lookup"><span data-stu-id="501ff-183">17, 18</span></span>                 | <span data-ttu-id="501ff-184">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-184">x64</span></span> |
| <span data-ttu-id="501ff-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="501ff-185">openSUSE</span></span>                       |  <span data-ttu-id="501ff-186">15 +</span><span class="sxs-lookup"><span data-stu-id="501ff-186">15+</span></span>                    | <span data-ttu-id="501ff-187">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-187">x64</span></span> |
| <span data-ttu-id="501ff-188">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="501ff-188">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="501ff-189">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="501ff-189">12 SP2+</span></span>                | <span data-ttu-id="501ff-190">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-190">x64</span></span> |
| <span data-ttu-id="501ff-191">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-191">Alpine Linux</span></span>                   |  <span data-ttu-id="501ff-192">3.7 +</span><span class="sxs-lookup"><span data-stu-id="501ff-192">3.7+</span></span>                   | <span data-ttu-id="501ff-193">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-193">x64</span></span> |

<span data-ttu-id="501ff-194">.NET Core 2,2 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,2 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="501ff-194">See [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="501ff-195">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="501ff-195">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="501ff-196">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="501ff-196">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="501ff-197">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="501ff-197">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="501ff-198">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="501ff-198">For download links and more information, see [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="501ff-199">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="501ff-199">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

| <span data-ttu-id="501ff-200">ATAYAMADı</span><span class="sxs-lookup"><span data-stu-id="501ff-200">OS</span></span>                             |  <span data-ttu-id="501ff-201">Version</span><span class="sxs-lookup"><span data-stu-id="501ff-201">Version</span></span>                |  <span data-ttu-id="501ff-202">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="501ff-202">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="501ff-203">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-203">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="501ff-204">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="501ff-204">6, 7, 8</span></span>                | <span data-ttu-id="501ff-205">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-205">x64</span></span> |
| <span data-ttu-id="501ff-206">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-206">Oracle Linux</span></span>                   |  <span data-ttu-id="501ff-207">7</span><span class="sxs-lookup"><span data-stu-id="501ff-207">7</span></span>                      | <span data-ttu-id="501ff-208">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-208">x64</span></span> |
| <span data-ttu-id="501ff-209">CentOS</span><span class="sxs-lookup"><span data-stu-id="501ff-209">CentOS</span></span>                         |  <span data-ttu-id="501ff-210">7</span><span class="sxs-lookup"><span data-stu-id="501ff-210">7</span></span>                      | <span data-ttu-id="501ff-211">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-211">x64</span></span> |
| <span data-ttu-id="501ff-212">Fedora</span><span class="sxs-lookup"><span data-stu-id="501ff-212">Fedora</span></span>                         |  <span data-ttu-id="501ff-213">29, 30</span><span class="sxs-lookup"><span data-stu-id="501ff-213">29, 30</span></span>                 | <span data-ttu-id="501ff-214">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-214">x64</span></span> |
| <span data-ttu-id="501ff-215">Debian</span><span class="sxs-lookup"><span data-stu-id="501ff-215">Debian</span></span>                         |  <span data-ttu-id="501ff-216">9</span><span class="sxs-lookup"><span data-stu-id="501ff-216">9</span></span>                      | <span data-ttu-id="501ff-217">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="501ff-217">x64, ARM32</span></span> |
| <span data-ttu-id="501ff-218">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="501ff-218">Ubuntu</span></span>                         |  <span data-ttu-id="501ff-219">16,04, 18,04, 19,04</span><span class="sxs-lookup"><span data-stu-id="501ff-219">16.04, 18.04, 19.04</span></span>    | <span data-ttu-id="501ff-220">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="501ff-220">x64, ARM32</span></span> |
| <span data-ttu-id="501ff-221">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="501ff-221">Linux Mint</span></span>                     |  <span data-ttu-id="501ff-222">17, 18</span><span class="sxs-lookup"><span data-stu-id="501ff-222">17, 18</span></span>                 | <span data-ttu-id="501ff-223">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-223">x64</span></span> |
| <span data-ttu-id="501ff-224">openSUSE</span><span class="sxs-lookup"><span data-stu-id="501ff-224">openSUSE</span></span>                       |  <span data-ttu-id="501ff-225">42.3 +</span><span class="sxs-lookup"><span data-stu-id="501ff-225">42.3+</span></span>                  | <span data-ttu-id="501ff-226">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-226">x64</span></span> |
| <span data-ttu-id="501ff-227">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="501ff-227">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="501ff-228">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="501ff-228">12 SP2+</span></span>                | <span data-ttu-id="501ff-229">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-229">x64</span></span> |
| <span data-ttu-id="501ff-230">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="501ff-230">Alpine Linux</span></span>                   |  <span data-ttu-id="501ff-231">3.7 +</span><span class="sxs-lookup"><span data-stu-id="501ff-231">3.7+</span></span>                   | <span data-ttu-id="501ff-232">X64</span><span class="sxs-lookup"><span data-stu-id="501ff-232">x64</span></span> |

<span data-ttu-id="501ff-233">.NET Core 2,1 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,1 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="501ff-233">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="501ff-234">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="501ff-234">Linux distribution dependencies</span></span>

<span data-ttu-id="501ff-235">Aşağıdakiler örnek olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="501ff-235">The following are intended to be examples.</span></span> <span data-ttu-id="501ff-236">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="501ff-236">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="501ff-237">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="501ff-237">Ubuntu</span></span>

<span data-ttu-id="501ff-238">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="501ff-238">Ubuntu distributions require the following libraries installed:</span></span>

- <span data-ttu-id="501ff-239">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="501ff-239">liblttng-ust0</span></span>
- <span data-ttu-id="501ff-240">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-240">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="501ff-241">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-241">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="501ff-242">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="501ff-242">libssl1.0.0</span></span>
- <span data-ttu-id="501ff-243">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="501ff-243">libkrb5-3</span></span>
- <span data-ttu-id="501ff-244">zlib1g</span><span class="sxs-lookup"><span data-stu-id="501ff-244">zlib1g</span></span>
- <span data-ttu-id="501ff-245">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-245">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="501ff-246">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-246">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="501ff-247">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-247">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="501ff-248">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="501ff-248">libicu60 (for 18.x)</span></span>

<span data-ttu-id="501ff-249">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="501ff-249">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="501ff-250">libunwind8</span><span class="sxs-lookup"><span data-stu-id="501ff-250">libunwind8</span></span>
- <span data-ttu-id="501ff-251">libuuid1</span><span class="sxs-lookup"><span data-stu-id="501ff-251">libuuid1</span></span>

<span data-ttu-id="501ff-252">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="501ff-252">For .NET Core applications that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

* <span data-ttu-id="501ff-253">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="501ff-253">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="501ff-254">Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="501ff-254">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="501ff-255">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="501ff-255">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="501ff-256">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="501ff-256">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="501ff-257">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="501ff-257">CentOS and Fedora</span></span>

<span data-ttu-id="501ff-258">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="501ff-258">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="501ff-259">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="501ff-259">lttng-ust</span></span>
- <span data-ttu-id="501ff-260">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="501ff-260">libcurl</span></span>
- <span data-ttu-id="501ff-261">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="501ff-261">openssl-libs</span></span>
- <span data-ttu-id="501ff-262">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="501ff-262">krb5-libs</span></span>
- <span data-ttu-id="501ff-263">libıu</span><span class="sxs-lookup"><span data-stu-id="501ff-263">libicu</span></span>
- <span data-ttu-id="501ff-264">zlib</span><span class="sxs-lookup"><span data-stu-id="501ff-264">zlib</span></span>

<span data-ttu-id="501ff-265">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, COMPAT-openssl10 yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="501ff-265">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="501ff-266">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="501ff-266">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="501ff-267">librüzgar</span><span class="sxs-lookup"><span data-stu-id="501ff-267">libunwind</span></span>
- <span data-ttu-id="501ff-268">libuuid</span><span class="sxs-lookup"><span data-stu-id="501ff-268">libuuid</span></span>

<span data-ttu-id="501ff-269">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="501ff-269">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="501ff-270">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="501ff-270">For .NET Core applications that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

* <span data-ttu-id="501ff-271">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="501ff-271">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="501ff-272">CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="501ff-272">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="501ff-273">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="501ff-273">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="501ff-274">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="501ff-274">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="501ff-275">Yerel yükleyicilerle .NET Core bağımlılıklarını yükleme</span><span class="sxs-lookup"><span data-stu-id="501ff-275">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="501ff-276">.NET Core yerel yükleyicileri desteklenen Linux dağıtımları/sürümleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="501ff-276">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="501ff-277">Yerel yükleyiciler sunucuya yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="501ff-277">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="501ff-278">Yerel bir yükleyiciyi kullanmanın avantajı, tüm .NET Core yerel bağımlılıklarının yüklü olması.</span><span class="sxs-lookup"><span data-stu-id="501ff-278">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="501ff-279">Yerel yükleyiciler Ayrıca sistem genelinde .NET Core SDK de yükler.</span><span class="sxs-lookup"><span data-stu-id="501ff-279">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="501ff-280">Linux 'ta iki yükleyici paketi seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="501ff-280">On Linux, there are two installer package choices:</span></span>

- <span data-ttu-id="501ff-281">Bir akış tabanlı Paket Yöneticisi, Ubuntu için apt-get veya CentOS/RHEL için de rivı kullanma.</span><span class="sxs-lookup"><span data-stu-id="501ff-281">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
- <span data-ttu-id="501ff-282">Paketlerin kendisini, DEB veya RPM 'yi kullanma.</span><span class="sxs-lookup"><span data-stu-id="501ff-282">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="501ff-283">.NET Core yükleyici betiği ile betik yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="501ff-283">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="501ff-284">[DotNet-install betikleri](./tools/dotnet-install-script.md) , CLI araç zinciri ve paylaşılan çalışma zamanının yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="501ff-284">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="501ff-285">Betiği <https://dot.net/v1/dotnet-install.sh> ' dan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="501ff-285">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="501ff-286">Komut dosyası, şu anda .NET Core 1,1 olan en son "LTS" sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="501ff-286">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="501ff-287">.NET Core 2,1 yüklemek için betiği aşağıdaki anahtarla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="501ff-287">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="501ff-288">Yükleyici Bash betiği, Otomasyon senaryolarında ve yönetici olmayan yüklemelerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="501ff-288">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="501ff-289">Bu betik Ayrıca PowerShell anahtarlarını okur, bu nedenle Linux/OS X sistemlerinde komut dosyasıyla kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="501ff-289">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="501ff-290">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="501ff-290">Troubleshoot</span></span>

<span data-ttu-id="501ff-291">Desteklenen bir Linux dağıtımında/sürümünde .NET Core yüklemesiyle ilgili sorunlar yaşıyorsanız, yüklü dağıtımlarınız/sürümleriniz için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="501ff-291">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

- [<span data-ttu-id="501ff-292">.NET Core 3,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="501ff-292">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
- [<span data-ttu-id="501ff-293">.NET Core 2,2 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="501ff-293">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
- [<span data-ttu-id="501ff-294">.NET Core 2,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="501ff-294">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
- [<span data-ttu-id="501ff-295">.NET Core 1,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="501ff-295">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
- [<span data-ttu-id="501ff-296">.NET Core 1,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="501ff-296">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
