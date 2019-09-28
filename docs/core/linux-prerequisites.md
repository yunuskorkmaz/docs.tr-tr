---
title: Linux üzerinde .NET Core önkoşulları
description: Linux makinelerde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen Linux sürümleri ve .NET Core bağımlılıkları.
author: leecow
ms.author: leecow
ms.date: 09/25/2019
ms.openlocfilehash: 4c5d79459c9d69111ca6452d9305f0deb37212b8
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591695"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="7d28e-103">Linux üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="7d28e-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="7d28e-104">Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için gereken bağımlılıklar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="7d28e-105">Desteklenen Linux dağıtımları/sürümleri ve aşağıdaki bağımlılıklar, Linux üzerinde .NET Core uygulamaları geliştirmenin iki yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="7d28e-106">En sevdiğiniz düzenleyicinizle komut satırı</span><span class="sxs-lookup"><span data-stu-id="7d28e-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="7d28e-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7d28e-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="7d28e-108">.NET Core SDK paketi üretim sunucuları/ortamları için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="7d28e-109">Üretim ortamlarına dağıtılan uygulamalar için yalnızca .NET Core çalışma zamanı paketi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="7d28e-110">.NET Core çalışma zamanı, uygulamalar ile birlikte bulunan bir dağıtımın parçası olarak dağıtılır, ancak çerçeveye bağımlı dağıtılan uygulamalar için ayrı olarak dağıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="7d28e-111">Çerçeveye bağımlı ve kendi kendine içerilen dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7d28e-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="7d28e-112">Ayrıca, belirli yönergeler için [kendi Içindeki Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="7d28e-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="7d28e-113">Desteklenen Linux sürümleri</span><span class="sxs-lookup"><span data-stu-id="7d28e-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="7d28e-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7d28e-114">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7d28e-115">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-115">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="7d28e-116">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="7d28e-117">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="7d28e-117">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="7d28e-118">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir):</span><span class="sxs-lookup"><span data-stu-id="7d28e-118">.NET Core 3.0 is supported on the following Linux distributions/versions):</span></span>

> [!NOTE]
> <span data-ttu-id="7d28e-119">@No__t-0 simgesi en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d28e-119">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7d28e-120">OS</span><span class="sxs-lookup"><span data-stu-id="7d28e-120">OS</span></span>                             | <span data-ttu-id="7d28e-121">Version</span><span class="sxs-lookup"><span data-stu-id="7d28e-121">Version</span></span>               | <span data-ttu-id="7d28e-122">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="7d28e-122">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="7d28e-123">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-123">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="7d28e-124">6 +, 7</span><span class="sxs-lookup"><span data-stu-id="7d28e-124">6+, 7</span></span>                 | <span data-ttu-id="7d28e-125">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-125">x64</span></span> |
| <span data-ttu-id="7d28e-126">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-126">Oracle Linux</span></span>                   | <span data-ttu-id="7d28e-127">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-127">7</span></span>                     | <span data-ttu-id="7d28e-128">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-128">x64</span></span> |
| <span data-ttu-id="7d28e-129">CentOS</span><span class="sxs-lookup"><span data-stu-id="7d28e-129">CentOS</span></span>                         | <span data-ttu-id="7d28e-130">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-130">7</span></span>                     | <span data-ttu-id="7d28e-131">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-131">x64</span></span> |
| <span data-ttu-id="7d28e-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="7d28e-132">Fedora</span></span>                         | <span data-ttu-id="7d28e-133">29 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-133">29+</span></span>                   | <span data-ttu-id="7d28e-134">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-134">x64</span></span> |
| <span data-ttu-id="7d28e-135">Debian</span><span class="sxs-lookup"><span data-stu-id="7d28e-135">Debian</span></span>                         | <span data-ttu-id="7d28e-136">9 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-136">9+</span></span>                    | <span data-ttu-id="7d28e-137">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="7d28e-137">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7d28e-138">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7d28e-138">Ubuntu</span></span>                         | <span data-ttu-id="7d28e-139">16.04 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-139">16.04+</span></span>                | <span data-ttu-id="7d28e-140">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="7d28e-140">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7d28e-141">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7d28e-141">Linux Mint</span></span>                     | <span data-ttu-id="7d28e-142">18 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-142">18+</span></span>                   | <span data-ttu-id="7d28e-143">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-143">x64</span></span> |
| <span data-ttu-id="7d28e-144">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7d28e-144">openSUSE</span></span>                       | <span data-ttu-id="7d28e-145">15 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-145">15+</span></span>                   | <span data-ttu-id="7d28e-146">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-146">x64</span></span> |
| <span data-ttu-id="7d28e-147">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7d28e-147">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="7d28e-148">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-148">12 SP2+</span></span>               | <span data-ttu-id="7d28e-149">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-149">x64</span></span> |
| <span data-ttu-id="7d28e-150">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-150">Alpine Linux</span></span>                   | <span data-ttu-id="7d28e-151">3.8 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-151">3.8+</span></span>                  | <span data-ttu-id="7d28e-152">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="7d28e-152">x64, ARM64</span></span> |

<span data-ttu-id="7d28e-153">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="7d28e-153">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="7d28e-154">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="7d28e-154">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="7d28e-155">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="7d28e-155">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7d28e-156">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-156">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="7d28e-157">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-157">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7d28e-158">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span><span class="sxs-lookup"><span data-stu-id="7d28e-158">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span></span>

<span data-ttu-id="7d28e-159">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-159">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="7d28e-160">@No__t-0 simgesi en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d28e-160">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7d28e-161">OS</span><span class="sxs-lookup"><span data-stu-id="7d28e-161">OS</span></span>                             |  <span data-ttu-id="7d28e-162">Version</span><span class="sxs-lookup"><span data-stu-id="7d28e-162">Version</span></span>                |  <span data-ttu-id="7d28e-163">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="7d28e-163">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="7d28e-164">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-164">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="7d28e-165">6, 7</span><span class="sxs-lookup"><span data-stu-id="7d28e-165">6, 7</span></span>                   | <span data-ttu-id="7d28e-166">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-166">x64</span></span> |
| <span data-ttu-id="7d28e-167">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-167">Oracle Linux</span></span>                   |  <span data-ttu-id="7d28e-168">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-168">7</span></span>                      | <span data-ttu-id="7d28e-169">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-169">x64</span></span> |
| <span data-ttu-id="7d28e-170">CentOS</span><span class="sxs-lookup"><span data-stu-id="7d28e-170">CentOS</span></span>                         |  <span data-ttu-id="7d28e-171">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-171">7</span></span>                      | <span data-ttu-id="7d28e-172">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-172">x64</span></span> |
| <span data-ttu-id="7d28e-173">Fedora</span><span class="sxs-lookup"><span data-stu-id="7d28e-173">Fedora</span></span>                         |  <span data-ttu-id="7d28e-174">29, 30</span><span class="sxs-lookup"><span data-stu-id="7d28e-174">29, 30</span></span>                 | <span data-ttu-id="7d28e-175">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-175">x64</span></span> |
| <span data-ttu-id="7d28e-176">Debian</span><span class="sxs-lookup"><span data-stu-id="7d28e-176">Debian</span></span>                         |  <span data-ttu-id="7d28e-177">9</span><span class="sxs-lookup"><span data-stu-id="7d28e-177">9</span></span>                      | <span data-ttu-id="7d28e-178">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="7d28e-178">x64, ARM32</span></span> |
| <span data-ttu-id="7d28e-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7d28e-179">Ubuntu</span></span>                         |  <span data-ttu-id="7d28e-180">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="7d28e-180">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="7d28e-181">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="7d28e-181">x64, ARM32</span></span> |
| <span data-ttu-id="7d28e-182">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7d28e-182">Linux Mint</span></span>                     |  <span data-ttu-id="7d28e-183">17, 18</span><span class="sxs-lookup"><span data-stu-id="7d28e-183">17, 18</span></span>                 | <span data-ttu-id="7d28e-184">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-184">x64</span></span> |
| <span data-ttu-id="7d28e-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7d28e-185">openSUSE</span></span>                       |  <span data-ttu-id="7d28e-186">15 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-186">15+</span></span>                    | <span data-ttu-id="7d28e-187">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-187">x64</span></span> |
| <span data-ttu-id="7d28e-188">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7d28e-188">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="7d28e-189">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-189">12 SP2+</span></span>                | <span data-ttu-id="7d28e-190">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-190">x64</span></span> |
| <span data-ttu-id="7d28e-191">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-191">Alpine Linux</span></span>                   |  <span data-ttu-id="7d28e-192">3.7 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-192">3.7+</span></span>                   | <span data-ttu-id="7d28e-193">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-193">x64</span></span> |

<span data-ttu-id="7d28e-194">.NET Core 2,2 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,2 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="7d28e-194">See [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7d28e-195">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="7d28e-195">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7d28e-196">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-196">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="7d28e-197">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-197">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7d28e-198">İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="7d28e-198">For download links and more information, see [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="7d28e-199">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-199">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

| <span data-ttu-id="7d28e-200">OS</span><span class="sxs-lookup"><span data-stu-id="7d28e-200">OS</span></span>                             |  <span data-ttu-id="7d28e-201">Version</span><span class="sxs-lookup"><span data-stu-id="7d28e-201">Version</span></span>                |  <span data-ttu-id="7d28e-202">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="7d28e-202">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="7d28e-203">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-203">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="7d28e-204">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="7d28e-204">6, 7, 8</span></span>                | <span data-ttu-id="7d28e-205">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-205">x64</span></span> |
| <span data-ttu-id="7d28e-206">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-206">Oracle Linux</span></span>                   |  <span data-ttu-id="7d28e-207">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-207">7</span></span>                      | <span data-ttu-id="7d28e-208">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-208">x64</span></span> |
| <span data-ttu-id="7d28e-209">CentOS</span><span class="sxs-lookup"><span data-stu-id="7d28e-209">CentOS</span></span>                         |  <span data-ttu-id="7d28e-210">7</span><span class="sxs-lookup"><span data-stu-id="7d28e-210">7</span></span>                      | <span data-ttu-id="7d28e-211">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-211">x64</span></span> |
| <span data-ttu-id="7d28e-212">Fedora</span><span class="sxs-lookup"><span data-stu-id="7d28e-212">Fedora</span></span>                         |  <span data-ttu-id="7d28e-213">29, 30</span><span class="sxs-lookup"><span data-stu-id="7d28e-213">29, 30</span></span>                 | <span data-ttu-id="7d28e-214">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-214">x64</span></span> |
| <span data-ttu-id="7d28e-215">Debian</span><span class="sxs-lookup"><span data-stu-id="7d28e-215">Debian</span></span>                         |  <span data-ttu-id="7d28e-216">9</span><span class="sxs-lookup"><span data-stu-id="7d28e-216">9</span></span>                      | <span data-ttu-id="7d28e-217">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="7d28e-217">x64, ARM32</span></span> |
| <span data-ttu-id="7d28e-218">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7d28e-218">Ubuntu</span></span>                         |  <span data-ttu-id="7d28e-219">16,04, 18,04, 19,04</span><span class="sxs-lookup"><span data-stu-id="7d28e-219">16.04, 18.04, 19.04</span></span>    | <span data-ttu-id="7d28e-220">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="7d28e-220">x64, ARM32</span></span> |
| <span data-ttu-id="7d28e-221">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7d28e-221">Linux Mint</span></span>                     |  <span data-ttu-id="7d28e-222">17, 18</span><span class="sxs-lookup"><span data-stu-id="7d28e-222">17, 18</span></span>                 | <span data-ttu-id="7d28e-223">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-223">x64</span></span> |
| <span data-ttu-id="7d28e-224">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7d28e-224">openSUSE</span></span>                       |  <span data-ttu-id="7d28e-225">42.3 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-225">42.3+</span></span>                  | <span data-ttu-id="7d28e-226">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-226">x64</span></span> |
| <span data-ttu-id="7d28e-227">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7d28e-227">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="7d28e-228">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-228">12 SP2+</span></span>                | <span data-ttu-id="7d28e-229">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-229">x64</span></span> |
| <span data-ttu-id="7d28e-230">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="7d28e-230">Alpine Linux</span></span>                   |  <span data-ttu-id="7d28e-231">3.7 +</span><span class="sxs-lookup"><span data-stu-id="7d28e-231">3.7+</span></span>                   | <span data-ttu-id="7d28e-232">X64</span><span class="sxs-lookup"><span data-stu-id="7d28e-232">x64</span></span> |

<span data-ttu-id="7d28e-233">.NET Core 2,1 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,1 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="7d28e-233">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="7d28e-234">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="7d28e-234">Linux distribution dependencies</span></span>

<span data-ttu-id="7d28e-235">Aşağıdakiler örnek olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-235">The following are intended to be examples.</span></span> <span data-ttu-id="7d28e-236">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-236">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="7d28e-237">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7d28e-237">Ubuntu</span></span>

<span data-ttu-id="7d28e-238">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-238">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7d28e-239">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="7d28e-239">liblttng-ust0</span></span>
* <span data-ttu-id="7d28e-240">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-240">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="7d28e-241">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-241">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="7d28e-242">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="7d28e-242">libssl1.0.0</span></span>
* <span data-ttu-id="7d28e-243">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="7d28e-243">libkrb5-3</span></span>
* <span data-ttu-id="7d28e-244">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7d28e-244">zlib1g</span></span>
* <span data-ttu-id="7d28e-245">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-245">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="7d28e-246">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-246">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="7d28e-247">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-247">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="7d28e-248">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="7d28e-248">libicu60 (for 18.x)</span></span>

<span data-ttu-id="7d28e-249">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-249">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="7d28e-250">libunwind8</span><span class="sxs-lookup"><span data-stu-id="7d28e-250">libunwind8</span></span>
* <span data-ttu-id="7d28e-251">libuuid1</span><span class="sxs-lookup"><span data-stu-id="7d28e-251">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="7d28e-252">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="7d28e-252">CentOS and Fedora</span></span>

<span data-ttu-id="7d28e-253">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-253">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="7d28e-254">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="7d28e-254">lttng-ust</span></span>
* <span data-ttu-id="7d28e-255">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="7d28e-255">libcurl</span></span>
* <span data-ttu-id="7d28e-256">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="7d28e-256">openssl-libs</span></span>
* <span data-ttu-id="7d28e-257">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="7d28e-257">krb5-libs</span></span>
* <span data-ttu-id="7d28e-258">libıu</span><span class="sxs-lookup"><span data-stu-id="7d28e-258">libicu</span></span>
* <span data-ttu-id="7d28e-259">zlib</span><span class="sxs-lookup"><span data-stu-id="7d28e-259">zlib</span></span>

<span data-ttu-id="7d28e-260">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 ise, COMPAT-openssl10 ' ı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-260">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="7d28e-261">.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="7d28e-261">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="7d28e-262">librüzgar</span><span class="sxs-lookup"><span data-stu-id="7d28e-262">libunwind</span></span>
* <span data-ttu-id="7d28e-263">libuuid</span><span class="sxs-lookup"><span data-stu-id="7d28e-263">libuuid</span></span>

<span data-ttu-id="7d28e-264">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="7d28e-264">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="7d28e-265">Yerel yükleyicilerle .NET Core bağımlılıklarını yükleme</span><span class="sxs-lookup"><span data-stu-id="7d28e-265">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="7d28e-266">.NET Core yerel yükleyicileri desteklenen Linux dağıtımları/sürümleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-266">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="7d28e-267">Yerel yükleyiciler sunucuya yönetici (sudo) erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-267">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="7d28e-268">Yerel bir yükleyiciyi kullanmanın avantajı, tüm .NET Core yerel bağımlılıklarının yüklü olması.</span><span class="sxs-lookup"><span data-stu-id="7d28e-268">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="7d28e-269">Yerel yükleyiciler Ayrıca sistem genelinde .NET Core SDK de yükler.</span><span class="sxs-lookup"><span data-stu-id="7d28e-269">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="7d28e-270">Linux 'ta iki yükleyici paketi seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="7d28e-270">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="7d28e-271">Bir akış tabanlı Paket Yöneticisi, Ubuntu için apt-get veya CentOS/RHEL için de rivı kullanma.</span><span class="sxs-lookup"><span data-stu-id="7d28e-271">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="7d28e-272">Paketlerin kendisini, DEB veya RPM 'yi kullanma.</span><span class="sxs-lookup"><span data-stu-id="7d28e-272">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="7d28e-273">.NET Core yükleyici betiği ile betik yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="7d28e-273">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="7d28e-274">[DotNet-install betikleri](./tools/dotnet-install-script.md) , CLI araç zinciri ve paylaşılan çalışma zamanının yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-274">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="7d28e-275">Betiği konumundan <https://dot.net/v1/dotnet-install.sh>indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d28e-275">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="7d28e-276">Komut dosyası, şu anda .NET Core 1,1 olan en son "LTS" sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="7d28e-276">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="7d28e-277">.NET Core 2,1 yüklemek için betiği aşağıdaki anahtarla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7d28e-277">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="7d28e-278">Yükleyici Bash betiği, Otomasyon senaryolarında ve yönetici olmayan yüklemelerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d28e-278">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="7d28e-279">Bu betik Ayrıca PowerShell anahtarlarını okur, bu nedenle Linux/OS X sistemlerinde komut dosyasıyla kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="7d28e-279">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="7d28e-280">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="7d28e-280">Troubleshoot</span></span>

<span data-ttu-id="7d28e-281">Desteklenen bir Linux dağıtımında/sürümünde .NET Core yüklemesiyle ilgili sorunlar yaşıyorsanız, yüklü dağıtımlarınız/sürümleriniz için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="7d28e-281">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="7d28e-282">.NET Core 3,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7d28e-282">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="7d28e-283">.NET Core 2,2 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7d28e-283">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="7d28e-284">.NET Core 2,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7d28e-284">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="7d28e-285">.NET Core 1,1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7d28e-285">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="7d28e-286">.NET Core 1,0 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="7d28e-286">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
