---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları-.NET Core
description: Windows, Linux ve macOS 'ta .NET Core SDK ve çalışma zamanı yüklemek için işletim sistemi ve CPU mimarisi ön koşullarını ayrıntılı olarak izleyin.
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451103"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="0e78f-103">.NET Core bağımlılıkları ve gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="0e78f-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="0e78f-104">Bu makalede .NET Core tarafından desteklenen işletim sistemleri ve CPU mimarisinin ayrıntıları verilir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="0e78f-105">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="0e78f-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="0e78f-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e78f-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0e78f-107">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-108">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-109">OS</span></span>                            | <span data-ttu-id="0e78f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-110">Version</span></span>                        | <span data-ttu-id="0e78f-111">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0e78f-112">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="0e78f-112">Windows Client</span></span>                | <span data-ttu-id="0e78f-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0e78f-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0e78f-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-114">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-115">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="0e78f-115">Windows 10 Client</span></span>             | <span data-ttu-id="0e78f-116">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-116">Version 1607+</span></span>                  | <span data-ttu-id="0e78f-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-117">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0e78f-118">Windows Server</span></span>                | <span data-ttu-id="0e78f-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-119">2012 R2+</span></span>                       | <span data-ttu-id="0e78f-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-120">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-121">Nano sunucu</span><span class="sxs-lookup"><span data-stu-id="0e78f-121">Nano Server</span></span>                   | <span data-ttu-id="0e78f-122">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-122">Version 1803+</span></span>                  | <span data-ttu-id="0e78f-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-123">x64, ARM32</span></span>      |

<span data-ttu-id="0e78f-124">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="0e78f-125">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0e78f-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="0e78f-126">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-127">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-128">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-128">OS</span></span>                            | <span data-ttu-id="0e78f-129">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-129">Version</span></span>                        | <span data-ttu-id="0e78f-130">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0e78f-131">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="0e78f-131">Windows Client</span></span>                | <span data-ttu-id="0e78f-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0e78f-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0e78f-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-133">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-134">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="0e78f-134">Windows 10 Client</span></span>             | <span data-ttu-id="0e78f-135">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-135">Version 1607+</span></span>                  | <span data-ttu-id="0e78f-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-136">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0e78f-137">Windows Server</span></span>                | <span data-ttu-id="0e78f-138">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="0e78f-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-139">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-140">Nano sunucu</span><span class="sxs-lookup"><span data-stu-id="0e78f-140">Nano Server</span></span>                   | <span data-ttu-id="0e78f-141">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-141">Version 1803+</span></span>                   | <span data-ttu-id="0e78f-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-142">x64, ARM32</span></span>      |

<span data-ttu-id="0e78f-143">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0e78f-144">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e78f-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0e78f-145">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-146">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-147">OS</span></span>                            | <span data-ttu-id="0e78f-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-148">Version</span></span>                        | <span data-ttu-id="0e78f-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0e78f-150">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="0e78f-150">Windows Client</span></span>                | <span data-ttu-id="0e78f-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0e78f-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0e78f-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-152">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-153">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="0e78f-153">Windows 10 Client</span></span>             | <span data-ttu-id="0e78f-154">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-154">Version 1607+</span></span>                  | <span data-ttu-id="0e78f-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-155">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0e78f-156">Windows Server</span></span>                | <span data-ttu-id="0e78f-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="0e78f-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0e78f-158">x64, x86</span></span>        |
| <span data-ttu-id="0e78f-159">Nano sunucu</span><span class="sxs-lookup"><span data-stu-id="0e78f-159">Nano Server</span></span>                   | <span data-ttu-id="0e78f-160">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-160">Version 1803+</span></span>                  | <span data-ttu-id="0e78f-161">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-161">x64,</span></span>            |

<span data-ttu-id="0e78f-162">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="0e78f-163">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0e78f-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="0e78f-164">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="0e78f-165">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="0e78f-165">Windows 7 SP1</span></span>
- <span data-ttu-id="0e78f-166">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="0e78f-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="0e78f-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0e78f-167">Windows 8.1</span></span>
- <span data-ttu-id="0e78f-168">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0e78f-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="0e78f-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0e78f-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="0e78f-170">Aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0e78f-170">Install the following:</span></span>

- <span data-ttu-id="0e78f-171">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="0e78f-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="0e78f-172">KB2533623</span><span class="sxs-lookup"><span data-stu-id="0e78f-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="0e78f-173">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="0e78f-174">*API-MS-Win-CRT-Runtime-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e78f-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="0e78f-175">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="0e78f-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="0e78f-176">\- veya-</span><span class="sxs-lookup"><span data-stu-id="0e78f-176">\- or -</span></span>
>
> <span data-ttu-id="0e78f-177">*Hostfxr. dll* kitaplığı bulundu, ancak *C:\\\<path_to_app >\\hostfxr. dll* ' den yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="0e78f-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="0e78f-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e78f-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0e78f-179">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="0e78f-180">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="0e78f-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0e78f-181">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-182">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-183">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-183">OS</span></span>                             | <span data-ttu-id="0e78f-184">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-184">Version</span></span>               | <span data-ttu-id="0e78f-185">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="0e78f-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="0e78f-187">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="0e78f-187">6, 7, 8</span></span>               | <span data-ttu-id="0e78f-188">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-188">x64</span></span> |
| <span data-ttu-id="0e78f-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="0e78f-189">CentOS</span></span>                         | <span data-ttu-id="0e78f-190">7 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-190">7+</span></span>                    | <span data-ttu-id="0e78f-191">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-191">x64</span></span> |
| <span data-ttu-id="0e78f-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-192">Oracle Linux</span></span>                   | <span data-ttu-id="0e78f-193">7 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-193">7+</span></span>                    | <span data-ttu-id="0e78f-194">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-194">x64</span></span> |
| <span data-ttu-id="0e78f-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="0e78f-195">Fedora</span></span>                         | <span data-ttu-id="0e78f-196">29 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-196">29+</span></span>                   | <span data-ttu-id="0e78f-197">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-197">x64</span></span> |
| <span data-ttu-id="0e78f-198">Debian</span><span class="sxs-lookup"><span data-stu-id="0e78f-198">Debian</span></span>                         | <span data-ttu-id="0e78f-199">9 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-199">9+</span></span>                    | <span data-ttu-id="0e78f-200">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0e78f-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0e78f-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0e78f-201">Ubuntu</span></span>                         | <span data-ttu-id="0e78f-202">16.04 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-202">16.04+</span></span>                | <span data-ttu-id="0e78f-203">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0e78f-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0e78f-204">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="0e78f-204">Linux Mint</span></span>                     | <span data-ttu-id="0e78f-205">18 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-205">18+</span></span>                   | <span data-ttu-id="0e78f-206">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-206">x64</span></span> |
| <span data-ttu-id="0e78f-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0e78f-207">openSUSE</span></span>                       | <span data-ttu-id="0e78f-208">15 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-208">15+</span></span>                   | <span data-ttu-id="0e78f-209">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-209">x64</span></span> |
| <span data-ttu-id="0e78f-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0e78f-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="0e78f-211">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-211">12 SP2+</span></span>               | <span data-ttu-id="0e78f-212">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-212">x64</span></span> |
| <span data-ttu-id="0e78f-213">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-213">Alpine Linux</span></span>                   | <span data-ttu-id="0e78f-214">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-214">3.8+</span></span>                  | <span data-ttu-id="0e78f-215">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="0e78f-215">x64, ARM64</span></span> |

<span data-ttu-id="0e78f-216">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="0e78f-217">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="0e78f-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="0e78f-218">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0e78f-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="0e78f-219">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="0e78f-220">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="0e78f-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0e78f-221">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-222">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-223">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-223">OS</span></span>                             |  <span data-ttu-id="0e78f-224">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-224">Version</span></span>                |  <span data-ttu-id="0e78f-225">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="0e78f-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="0e78f-227">6, 7</span><span class="sxs-lookup"><span data-stu-id="0e78f-227">6, 7</span></span>                   | <span data-ttu-id="0e78f-228">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-228">x64</span></span> |
| <span data-ttu-id="0e78f-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="0e78f-229">CentOS</span></span>                         |  <span data-ttu-id="0e78f-230">7</span><span class="sxs-lookup"><span data-stu-id="0e78f-230">7</span></span>                      | <span data-ttu-id="0e78f-231">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-231">x64</span></span> |
| <span data-ttu-id="0e78f-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-232">Oracle Linux</span></span>                   |  <span data-ttu-id="0e78f-233">7</span><span class="sxs-lookup"><span data-stu-id="0e78f-233">7</span></span>                      | <span data-ttu-id="0e78f-234">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-234">x64</span></span> |
| <span data-ttu-id="0e78f-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="0e78f-235">Fedora</span></span>                         |  <span data-ttu-id="0e78f-236">29, 30</span><span class="sxs-lookup"><span data-stu-id="0e78f-236">29, 30</span></span>                 | <span data-ttu-id="0e78f-237">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-237">x64</span></span> |
| <span data-ttu-id="0e78f-238">Debian</span><span class="sxs-lookup"><span data-stu-id="0e78f-238">Debian</span></span>                         |  <span data-ttu-id="0e78f-239">9</span><span class="sxs-lookup"><span data-stu-id="0e78f-239">9</span></span>                      | <span data-ttu-id="0e78f-240">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-240">x64, ARM32</span></span> |
| <span data-ttu-id="0e78f-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0e78f-241">Ubuntu</span></span>                         |  <span data-ttu-id="0e78f-242">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="0e78f-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="0e78f-243">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-243">x64, ARM32</span></span> |
| <span data-ttu-id="0e78f-244">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="0e78f-244">Linux Mint</span></span>                     |  <span data-ttu-id="0e78f-245">17, 18</span><span class="sxs-lookup"><span data-stu-id="0e78f-245">17, 18</span></span>                 | <span data-ttu-id="0e78f-246">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-246">x64</span></span> |
| <span data-ttu-id="0e78f-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0e78f-247">openSUSE</span></span>                       |  <span data-ttu-id="0e78f-248">15 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-248">15+</span></span>                    | <span data-ttu-id="0e78f-249">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-249">x64</span></span> |
| <span data-ttu-id="0e78f-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0e78f-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="0e78f-251">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-251">12 SP2+</span></span>                | <span data-ttu-id="0e78f-252">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-252">x64</span></span> |
| <span data-ttu-id="0e78f-253">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-253">Alpine Linux</span></span>                   |  <span data-ttu-id="0e78f-254">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-254">3.8+</span></span>                   | <span data-ttu-id="0e78f-255">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-255">x64</span></span> |

<span data-ttu-id="0e78f-256">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0e78f-257">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e78f-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0e78f-258">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="0e78f-259">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="0e78f-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0e78f-260">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-261">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-262">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0e78f-262">OS</span></span>                             |  <span data-ttu-id="0e78f-263">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0e78f-263">Version</span></span>                |  <span data-ttu-id="0e78f-264">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="0e78f-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="0e78f-266">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="0e78f-266">6, 7, 8</span></span>                | <span data-ttu-id="0e78f-267">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-267">x64</span></span> |
| <span data-ttu-id="0e78f-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="0e78f-268">CentOS</span></span>                         |  <span data-ttu-id="0e78f-269">7 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-269">7+</span></span>                     | <span data-ttu-id="0e78f-270">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-270">x64</span></span> |
| <span data-ttu-id="0e78f-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-271">Oracle Linux</span></span>                   |  <span data-ttu-id="0e78f-272">7 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-272">7+</span></span>                     | <span data-ttu-id="0e78f-273">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-273">x64</span></span> |
| <span data-ttu-id="0e78f-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="0e78f-274">Fedora</span></span>                         |  <span data-ttu-id="0e78f-275">29 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-275">29+</span></span>                    | <span data-ttu-id="0e78f-276">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-276">x64</span></span> |
| <span data-ttu-id="0e78f-277">Debian</span><span class="sxs-lookup"><span data-stu-id="0e78f-277">Debian</span></span>                         |  <span data-ttu-id="0e78f-278">9</span><span class="sxs-lookup"><span data-stu-id="0e78f-278">9</span></span>                      | <span data-ttu-id="0e78f-279">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-279">x64, ARM32</span></span> |
| <span data-ttu-id="0e78f-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0e78f-280">Ubuntu</span></span>                         |  <span data-ttu-id="0e78f-281">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="0e78f-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="0e78f-282">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0e78f-282">x64, ARM32</span></span> |
| <span data-ttu-id="0e78f-283">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="0e78f-283">Linux Mint</span></span>                     |  <span data-ttu-id="0e78f-284">17 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-284">17+</span></span>                    | <span data-ttu-id="0e78f-285">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-285">x64</span></span> |
| <span data-ttu-id="0e78f-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0e78f-286">openSUSE</span></span>                       |  <span data-ttu-id="0e78f-287">15 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-287">15+</span></span>                    | <span data-ttu-id="0e78f-288">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-288">x64</span></span> |
| <span data-ttu-id="0e78f-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0e78f-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="0e78f-290">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-290">12 SP2+</span></span>                | <span data-ttu-id="0e78f-291">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-291">x64</span></span> |
| <span data-ttu-id="0e78f-292">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="0e78f-292">Alpine Linux</span></span>                   |  <span data-ttu-id="0e78f-293">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0e78f-293">3.8+</span></span>                   | <span data-ttu-id="0e78f-294">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-294">x64</span></span> |

<span data-ttu-id="0e78f-295">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="0e78f-296">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="0e78f-296">Linux distribution dependencies</span></span>

<span data-ttu-id="0e78f-297">Linux dağıtımına bağlı olarak ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e78f-298">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="0e78f-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0e78f-299">Ubuntu</span></span>

<span data-ttu-id="0e78f-300">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="0e78f-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="0e78f-301">liblttng-ust0</span></span>
- <span data-ttu-id="0e78f-302">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="0e78f-303">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="0e78f-304">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="0e78f-304">libssl1.0.0</span></span>
- <span data-ttu-id="0e78f-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="0e78f-305">libkrb5-3</span></span>
- <span data-ttu-id="0e78f-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="0e78f-306">zlib1g</span></span>
- <span data-ttu-id="0e78f-307">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="0e78f-308">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="0e78f-309">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="0e78f-310">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="0e78f-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="0e78f-311">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="0e78f-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="0e78f-312">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="0e78f-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="0e78f-313">Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="0e78f-314">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e78f-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="0e78f-315">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="0e78f-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="0e78f-316">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="0e78f-316">CentOS and Fedora</span></span>

<span data-ttu-id="0e78f-317">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="0e78f-318">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="0e78f-318">lttng-ust</span></span>
- <span data-ttu-id="0e78f-319">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="0e78f-319">libcurl</span></span>
- <span data-ttu-id="0e78f-320">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="0e78f-320">openssl-libs</span></span>
- <span data-ttu-id="0e78f-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="0e78f-321">krb5-libs</span></span>
- <span data-ttu-id="0e78f-322">libıu</span><span class="sxs-lookup"><span data-stu-id="0e78f-322">libicu</span></span>
- <span data-ttu-id="0e78f-323">zlib</span><span class="sxs-lookup"><span data-stu-id="0e78f-323">zlib</span></span>

<span data-ttu-id="0e78f-324">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="0e78f-325">.NET Core 2,0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="0e78f-326">librüzgar</span><span class="sxs-lookup"><span data-stu-id="0e78f-326">libunwind</span></span>
- <span data-ttu-id="0e78f-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="0e78f-327">libuuid</span></span>

<span data-ttu-id="0e78f-328">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="0e78f-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="0e78f-329">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="0e78f-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="0e78f-330">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="0e78f-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="0e78f-331">CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="0e78f-332">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e78f-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="0e78f-333">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="0e78f-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="0e78f-334">.NET Core aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0e78f-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="0e78f-335">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e78f-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0e78f-336">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="0e78f-336">.NET Core Version</span></span> | <span data-ttu-id="0e78f-337">Mac OS</span><span class="sxs-lookup"><span data-stu-id="0e78f-337">macOS</span></span>                 | <span data-ttu-id="0e78f-338">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="0e78f-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="0e78f-339">3,0</span><span class="sxs-lookup"><span data-stu-id="0e78f-339">3.0</span></span>               | <span data-ttu-id="0e78f-340">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="0e78f-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0e78f-341">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-341">x64</span></span> | [<span data-ttu-id="0e78f-342">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="0e78f-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="0e78f-343">2.2</span><span class="sxs-lookup"><span data-stu-id="0e78f-343">2.2</span></span>               | <span data-ttu-id="0e78f-344">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="0e78f-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="0e78f-345">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-345">x64</span></span> | [<span data-ttu-id="0e78f-346">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="0e78f-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="0e78f-347">2.1</span><span class="sxs-lookup"><span data-stu-id="0e78f-347">2.1</span></span>               | <span data-ttu-id="0e78f-348">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="0e78f-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="0e78f-349">x64</span><span class="sxs-lookup"><span data-stu-id="0e78f-349">x64</span></span> | [<span data-ttu-id="0e78f-350">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="0e78f-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="0e78f-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="0e78f-351">libgdiplus</span></span>

<span data-ttu-id="0e78f-352">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0e78f-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="0e78f-353">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e78f-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="0e78f-354">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="0e78f-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="0e78f-355">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0e78f-355">Next steps</span></span>

- <span data-ttu-id="0e78f-356">Uygulama geliştirmek ve çalıştırmak için, [.NET Core SDK](sdk.md) (çalışma zamanını içerir).</span><span class="sxs-lookup"><span data-stu-id="0e78f-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="0e78f-357">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma zamanı](runtime.md)'nı yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="0e78f-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
