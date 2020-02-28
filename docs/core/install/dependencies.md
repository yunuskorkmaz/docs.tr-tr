---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları-.NET Core
description: Windows, Linux ve macOS 'ta .NET Core SDK ve çalışma zamanı yüklemek için işletim sistemi ve CPU mimarisi ön koşullarını ayrıntılı olarak izleyin.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157822"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="038f3-103">.NET Core bağımlılıkları ve gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="038f3-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="038f3-104">Bu makalede .NET Core tarafından desteklenen işletim sistemleri ve CPU mimarisinin ayrıntıları verilir.</span><span class="sxs-lookup"><span data-stu-id="038f3-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="038f3-105">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="038f3-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="038f3-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="038f3-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="038f3-107">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-108">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-109">OS</span></span>                            | <span data-ttu-id="038f3-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-110">Version</span></span>                        | <span data-ttu-id="038f3-111">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="038f3-112">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-112">Windows Client</span></span>                | <span data-ttu-id="038f3-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="038f3-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="038f3-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-114">x64, x86</span></span>        |
| <span data-ttu-id="038f3-115">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-115">Windows 10 Client</span></span>             | <span data-ttu-id="038f3-116">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="038f3-116">Version 1607+</span></span>                  | <span data-ttu-id="038f3-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-117">x64, x86</span></span>        |
| <span data-ttu-id="038f3-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="038f3-118">Windows Server</span></span>                | <span data-ttu-id="038f3-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-119">2012 R2+</span></span>                       | <span data-ttu-id="038f3-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-120">x64, x86</span></span>        |
| <span data-ttu-id="038f3-121">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="038f3-121">Nano Server</span></span>                   | <span data-ttu-id="038f3-122">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="038f3-122">Version 1803+</span></span>                  | <span data-ttu-id="038f3-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-123">x64, ARM32</span></span>      |

<span data-ttu-id="038f3-124">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="038f3-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="038f3-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="038f3-126">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-127">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-128">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-128">OS</span></span>                            | <span data-ttu-id="038f3-129">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-129">Version</span></span>                        | <span data-ttu-id="038f3-130">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="038f3-131">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-131">Windows Client</span></span>                | <span data-ttu-id="038f3-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="038f3-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="038f3-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-133">x64, x86</span></span>        |
| <span data-ttu-id="038f3-134">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-134">Windows 10 Client</span></span>             | <span data-ttu-id="038f3-135">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="038f3-135">Version 1607+</span></span>                  | <span data-ttu-id="038f3-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-136">x64, x86</span></span>        |
| <span data-ttu-id="038f3-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="038f3-137">Windows Server</span></span>                | <span data-ttu-id="038f3-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-138">2012 R2+</span></span>                       | <span data-ttu-id="038f3-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-139">x64, x86</span></span>        |
| <span data-ttu-id="038f3-140">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="038f3-140">Nano Server</span></span>                   | <span data-ttu-id="038f3-141">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="038f3-141">Version 1803+</span></span>                  | <span data-ttu-id="038f3-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-142">x64, ARM32</span></span>      |

<span data-ttu-id="038f3-143">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="038f3-144">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="038f3-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="038f3-145">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-146">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-147">OS</span></span>                            | <span data-ttu-id="038f3-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-148">Version</span></span>                        | <span data-ttu-id="038f3-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="038f3-150">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-150">Windows Client</span></span>                | <span data-ttu-id="038f3-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="038f3-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="038f3-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-152">x64, x86</span></span>        |
| <span data-ttu-id="038f3-153">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-153">Windows 10 Client</span></span>             | <span data-ttu-id="038f3-154">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="038f3-154">Version 1607+</span></span>                  | <span data-ttu-id="038f3-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-155">x64, x86</span></span>        |
| <span data-ttu-id="038f3-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="038f3-156">Windows Server</span></span>                | <span data-ttu-id="038f3-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="038f3-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="038f3-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-158">x64, x86</span></span>        |
| <span data-ttu-id="038f3-159">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="038f3-159">Nano Server</span></span>                   | <span data-ttu-id="038f3-160">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="038f3-160">Version 1803+</span></span>                   | <span data-ttu-id="038f3-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-161">x64, ARM32</span></span>      |

<span data-ttu-id="038f3-162">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="038f3-163">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="038f3-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="038f3-164">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-165">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-166">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-166">OS</span></span>                            | <span data-ttu-id="038f3-167">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-167">Version</span></span>                        | <span data-ttu-id="038f3-168">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="038f3-169">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-169">Windows Client</span></span>                | <span data-ttu-id="038f3-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="038f3-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="038f3-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-171">x64, x86</span></span>        |
| <span data-ttu-id="038f3-172">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="038f3-172">Windows 10 Client</span></span>             | <span data-ttu-id="038f3-173">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="038f3-173">Version 1607+</span></span>                  | <span data-ttu-id="038f3-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-174">x64, x86</span></span>        |
| <span data-ttu-id="038f3-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="038f3-175">Windows Server</span></span>                | <span data-ttu-id="038f3-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="038f3-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="038f3-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="038f3-177">x64, x86</span></span>        |
| <span data-ttu-id="038f3-178">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="038f3-178">Nano Server</span></span>                   | <span data-ttu-id="038f3-179">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="038f3-179">Version 1803+</span></span>                  | <span data-ttu-id="038f3-180">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-180">x64,</span></span>            |

<span data-ttu-id="038f3-181">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="038f3-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="038f3-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="038f3-183">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="038f3-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="038f3-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="038f3-184">Windows 7 SP1</span></span>
- <span data-ttu-id="038f3-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="038f3-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="038f3-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="038f3-186">Windows 8.1</span></span>
- <span data-ttu-id="038f3-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="038f3-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="038f3-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="038f3-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="038f3-189">Aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="038f3-189">Install the following:</span></span>

- <span data-ttu-id="038f3-190">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="038f3-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="038f3-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="038f3-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="038f3-192">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="038f3-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="038f3-193">*API-MS-Win-CRT-Runtime-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="038f3-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="038f3-194">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="038f3-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="038f3-195">\- veya-</span><span class="sxs-lookup"><span data-stu-id="038f3-195">\- or -</span></span>
>
> <span data-ttu-id="038f3-196">*Hostfxr. dll* kitaplığı bulundu, ancak *C:\\\<path_to_app >\\hostfxr. dll* ' den yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="038f3-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="038f3-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="038f3-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="038f3-198">.NET Core 3,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="038f3-199">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="038f3-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="038f3-200">.NET Core 3,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-201">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-202">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-202">OS</span></span>                             | <span data-ttu-id="038f3-203">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-203">Version</span></span>               | <span data-ttu-id="038f3-204">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="038f3-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="038f3-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="038f3-206">6, 7, 8</span></span>               | <span data-ttu-id="038f3-207">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-207">x64</span></span> |
| <span data-ttu-id="038f3-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="038f3-208">CentOS</span></span>                         | <span data-ttu-id="038f3-209">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-209">7+</span></span>                    | <span data-ttu-id="038f3-210">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-210">x64</span></span> |
| <span data-ttu-id="038f3-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-211">Oracle Linux</span></span>                   | <span data-ttu-id="038f3-212">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-212">7+</span></span>                    | <span data-ttu-id="038f3-213">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-213">x64</span></span> |
| <span data-ttu-id="038f3-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="038f3-214">Fedora</span></span>                         | <span data-ttu-id="038f3-215">29 +</span><span class="sxs-lookup"><span data-stu-id="038f3-215">29+</span></span>                   | <span data-ttu-id="038f3-216">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-216">x64</span></span> |
| <span data-ttu-id="038f3-217">Debian</span><span class="sxs-lookup"><span data-stu-id="038f3-217">Debian</span></span>                         | <span data-ttu-id="038f3-218">9 +</span><span class="sxs-lookup"><span data-stu-id="038f3-218">9+</span></span>                    | <span data-ttu-id="038f3-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="038f3-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="038f3-220">Ubuntu</span></span>                         | <span data-ttu-id="038f3-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="038f3-221">16.04+</span></span>                | <span data-ttu-id="038f3-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="038f3-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="038f3-223">Linux Mint</span></span>                     | <span data-ttu-id="038f3-224">18 +</span><span class="sxs-lookup"><span data-stu-id="038f3-224">18+</span></span>                   | <span data-ttu-id="038f3-225">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-225">x64</span></span> |
| <span data-ttu-id="038f3-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="038f3-226">openSUSE</span></span>                       | <span data-ttu-id="038f3-227">15 +</span><span class="sxs-lookup"><span data-stu-id="038f3-227">15+</span></span>                   | <span data-ttu-id="038f3-228">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-228">x64</span></span> |
| <span data-ttu-id="038f3-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="038f3-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="038f3-230">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-230">12 SP2+</span></span>               | <span data-ttu-id="038f3-231">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-231">x64</span></span> |
| <span data-ttu-id="038f3-232">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-232">Alpine Linux</span></span>                   | <span data-ttu-id="038f3-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="038f3-233">3.10+</span></span>                 | <span data-ttu-id="038f3-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-234">x64, ARM64</span></span> |

<span data-ttu-id="038f3-235">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="038f3-236">.NET Core 3,1 ' i ARM64 üzerinde yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="038f3-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="038f3-237">ARM64 desteği Linux Kernel 4,14 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="038f3-238">Bazı Linux dağıtımları, diğerleri bu gereksinimi karşılar.</span><span class="sxs-lookup"><span data-stu-id="038f3-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="038f3-239">Örneğin, Ubuntu 18,04 desteklenir, ancak Ubuntu 16,04 değildir.</span><span class="sxs-lookup"><span data-stu-id="038f3-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="038f3-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="038f3-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="038f3-241">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="038f3-242">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="038f3-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="038f3-243">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-244">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-245">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-245">OS</span></span>                             | <span data-ttu-id="038f3-246">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-246">Version</span></span>               | <span data-ttu-id="038f3-247">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="038f3-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="038f3-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="038f3-249">6, 7, 8</span></span>               | <span data-ttu-id="038f3-250">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-250">x64</span></span> |
| <span data-ttu-id="038f3-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="038f3-251">CentOS</span></span>                         | <span data-ttu-id="038f3-252">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-252">7+</span></span>                    | <span data-ttu-id="038f3-253">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-253">x64</span></span> |
| <span data-ttu-id="038f3-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-254">Oracle Linux</span></span>                   | <span data-ttu-id="038f3-255">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-255">7+</span></span>                    | <span data-ttu-id="038f3-256">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-256">x64</span></span> |
| <span data-ttu-id="038f3-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="038f3-257">Fedora</span></span>                         | <span data-ttu-id="038f3-258">29 +</span><span class="sxs-lookup"><span data-stu-id="038f3-258">29+</span></span>                   | <span data-ttu-id="038f3-259">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-259">x64</span></span> |
| <span data-ttu-id="038f3-260">Debian</span><span class="sxs-lookup"><span data-stu-id="038f3-260">Debian</span></span>                         | <span data-ttu-id="038f3-261">9 +</span><span class="sxs-lookup"><span data-stu-id="038f3-261">9+</span></span>                    | <span data-ttu-id="038f3-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="038f3-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="038f3-263">Ubuntu</span></span>                         | <span data-ttu-id="038f3-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="038f3-264">16.04+</span></span>                | <span data-ttu-id="038f3-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="038f3-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="038f3-266">Linux Mint</span></span>                     | <span data-ttu-id="038f3-267">18 +</span><span class="sxs-lookup"><span data-stu-id="038f3-267">18+</span></span>                   | <span data-ttu-id="038f3-268">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-268">x64</span></span> |
| <span data-ttu-id="038f3-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="038f3-269">openSUSE</span></span>                       | <span data-ttu-id="038f3-270">15 +</span><span class="sxs-lookup"><span data-stu-id="038f3-270">15+</span></span>                   | <span data-ttu-id="038f3-271">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-271">x64</span></span> |
| <span data-ttu-id="038f3-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="038f3-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="038f3-273">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-273">12 SP2+</span></span>               | <span data-ttu-id="038f3-274">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-274">x64</span></span> |
| <span data-ttu-id="038f3-275">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-275">Alpine Linux</span></span>                   | <span data-ttu-id="038f3-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="038f3-276">3.8+</span></span>                  | <span data-ttu-id="038f3-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="038f3-277">x64, ARM64</span></span> |

<span data-ttu-id="038f3-278">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="038f3-279">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="038f3-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="038f3-280">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="038f3-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="038f3-281">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="038f3-282">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="038f3-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="038f3-283">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-284">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-285">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-285">OS</span></span>                             |  <span data-ttu-id="038f3-286">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-286">Version</span></span>                |  <span data-ttu-id="038f3-287">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="038f3-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="038f3-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="038f3-289">6, 7</span></span>                   | <span data-ttu-id="038f3-290">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-290">x64</span></span> |
| <span data-ttu-id="038f3-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="038f3-291">CentOS</span></span>                         |  <span data-ttu-id="038f3-292">7</span><span class="sxs-lookup"><span data-stu-id="038f3-292">7</span></span>                      | <span data-ttu-id="038f3-293">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-293">x64</span></span> |
| <span data-ttu-id="038f3-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-294">Oracle Linux</span></span>                   |  <span data-ttu-id="038f3-295">7</span><span class="sxs-lookup"><span data-stu-id="038f3-295">7</span></span>                      | <span data-ttu-id="038f3-296">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-296">x64</span></span> |
| <span data-ttu-id="038f3-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="038f3-297">Fedora</span></span>                         |  <span data-ttu-id="038f3-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="038f3-298">29, 30</span></span>                 | <span data-ttu-id="038f3-299">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-299">x64</span></span> |
| <span data-ttu-id="038f3-300">Debian</span><span class="sxs-lookup"><span data-stu-id="038f3-300">Debian</span></span>                         |  <span data-ttu-id="038f3-301">9</span><span class="sxs-lookup"><span data-stu-id="038f3-301">9</span></span>                      | <span data-ttu-id="038f3-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-302">x64, ARM32</span></span> |
| <span data-ttu-id="038f3-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="038f3-303">Ubuntu</span></span>                         |  <span data-ttu-id="038f3-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="038f3-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="038f3-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-305">x64, ARM32</span></span> |
| <span data-ttu-id="038f3-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="038f3-306">Linux Mint</span></span>                     |  <span data-ttu-id="038f3-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="038f3-307">17, 18</span></span>                 | <span data-ttu-id="038f3-308">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-308">x64</span></span> |
| <span data-ttu-id="038f3-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="038f3-309">openSUSE</span></span>                       |  <span data-ttu-id="038f3-310">15 +</span><span class="sxs-lookup"><span data-stu-id="038f3-310">15+</span></span>                    | <span data-ttu-id="038f3-311">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-311">x64</span></span> |
| <span data-ttu-id="038f3-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="038f3-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="038f3-313">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-313">12 SP2+</span></span>                | <span data-ttu-id="038f3-314">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-314">x64</span></span> |
| <span data-ttu-id="038f3-315">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-315">Alpine Linux</span></span>                   |  <span data-ttu-id="038f3-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="038f3-316">3.8+</span></span>                   | <span data-ttu-id="038f3-317">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-317">x64</span></span> |

<span data-ttu-id="038f3-318">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="038f3-319">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="038f3-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="038f3-320">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="038f3-321">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="038f3-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="038f3-322">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-323">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-324">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="038f3-324">OS</span></span>                             |  <span data-ttu-id="038f3-325">Sürüm</span><span class="sxs-lookup"><span data-stu-id="038f3-325">Version</span></span>                |  <span data-ttu-id="038f3-326">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="038f3-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="038f3-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="038f3-328">6, 7, 8</span></span>                | <span data-ttu-id="038f3-329">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-329">x64</span></span> |
| <span data-ttu-id="038f3-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="038f3-330">CentOS</span></span>                         |  <span data-ttu-id="038f3-331">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-331">7+</span></span>                     | <span data-ttu-id="038f3-332">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-332">x64</span></span> |
| <span data-ttu-id="038f3-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-333">Oracle Linux</span></span>                   |  <span data-ttu-id="038f3-334">7 +</span><span class="sxs-lookup"><span data-stu-id="038f3-334">7+</span></span>                     | <span data-ttu-id="038f3-335">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-335">x64</span></span> |
| <span data-ttu-id="038f3-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="038f3-336">Fedora</span></span>                         |  <span data-ttu-id="038f3-337">29 +</span><span class="sxs-lookup"><span data-stu-id="038f3-337">29+</span></span>                    | <span data-ttu-id="038f3-338">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-338">x64</span></span> |
| <span data-ttu-id="038f3-339">Debian</span><span class="sxs-lookup"><span data-stu-id="038f3-339">Debian</span></span>                         |  <span data-ttu-id="038f3-340">9</span><span class="sxs-lookup"><span data-stu-id="038f3-340">9</span></span>                      | <span data-ttu-id="038f3-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-341">x64, ARM32</span></span> |
| <span data-ttu-id="038f3-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="038f3-342">Ubuntu</span></span>                         |  <span data-ttu-id="038f3-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="038f3-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="038f3-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="038f3-344">x64, ARM32</span></span> |
| <span data-ttu-id="038f3-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="038f3-345">Linux Mint</span></span>                     |  <span data-ttu-id="038f3-346">17 +</span><span class="sxs-lookup"><span data-stu-id="038f3-346">17+</span></span>                    | <span data-ttu-id="038f3-347">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-347">x64</span></span> |
| <span data-ttu-id="038f3-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="038f3-348">openSUSE</span></span>                       |  <span data-ttu-id="038f3-349">15 +</span><span class="sxs-lookup"><span data-stu-id="038f3-349">15+</span></span>                    | <span data-ttu-id="038f3-350">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-350">x64</span></span> |
| <span data-ttu-id="038f3-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="038f3-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="038f3-352">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="038f3-352">12 SP2+</span></span>                | <span data-ttu-id="038f3-353">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-353">x64</span></span> |
| <span data-ttu-id="038f3-354">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="038f3-354">Alpine Linux</span></span>                   |  <span data-ttu-id="038f3-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="038f3-355">3.8+</span></span>                   | <span data-ttu-id="038f3-356">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-356">x64</span></span> |

<span data-ttu-id="038f3-357">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="038f3-358">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="038f3-358">Linux distribution dependencies</span></span>

<span data-ttu-id="038f3-359">Linux dağıtımına bağlı olarak ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="038f3-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="038f3-360">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="038f3-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="038f3-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="038f3-361">Ubuntu</span></span>

<span data-ttu-id="038f3-362">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="038f3-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="038f3-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="038f3-363">liblttng-ust0</span></span>
- <span data-ttu-id="038f3-364">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="038f3-365">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="038f3-366">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="038f3-366">libssl1.0.0</span></span>
- <span data-ttu-id="038f3-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="038f3-367">libkrb5-3</span></span>
- <span data-ttu-id="038f3-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="038f3-368">zlib1g</span></span>
- <span data-ttu-id="038f3-369">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="038f3-370">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="038f3-371">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="038f3-372">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="038f3-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="038f3-373">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="038f3-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="038f3-374">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="038f3-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="038f3-375">Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="038f3-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="038f3-376">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="038f3-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="038f3-377">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="038f3-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="038f3-378">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="038f3-378">CentOS and Fedora</span></span>

<span data-ttu-id="038f3-379">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="038f3-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="038f3-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="038f3-380">lttng-ust</span></span>
- <span data-ttu-id="038f3-381">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="038f3-381">libcurl</span></span>
- <span data-ttu-id="038f3-382">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="038f3-382">openssl-libs</span></span>
- <span data-ttu-id="038f3-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="038f3-383">krb5-libs</span></span>
- <span data-ttu-id="038f3-384">libıu</span><span class="sxs-lookup"><span data-stu-id="038f3-384">libicu</span></span>
- <span data-ttu-id="038f3-385">zlib</span><span class="sxs-lookup"><span data-stu-id="038f3-385">zlib</span></span>

<span data-ttu-id="038f3-386">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="038f3-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="038f3-387">.NET Core 2,0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="038f3-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="038f3-388">librüzgar</span><span class="sxs-lookup"><span data-stu-id="038f3-388">libunwind</span></span>
- <span data-ttu-id="038f3-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="038f3-389">libuuid</span></span>

<span data-ttu-id="038f3-390">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="038f3-391">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="038f3-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="038f3-392">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="038f3-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="038f3-393">CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="038f3-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="038f3-394">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="038f3-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="038f3-395">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="038f3-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="038f3-396">.NET Core aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="038f3-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="038f3-397">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="038f3-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="038f3-398">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="038f3-398">.NET Core Version</span></span> | <span data-ttu-id="038f3-399">macOS</span><span class="sxs-lookup"><span data-stu-id="038f3-399">macOS</span></span>                 | <span data-ttu-id="038f3-400">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="038f3-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="038f3-401">3.1</span><span class="sxs-lookup"><span data-stu-id="038f3-401">3.1</span></span>               | <span data-ttu-id="038f3-402">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="038f3-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="038f3-403">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-403">x64</span></span> | [<span data-ttu-id="038f3-404">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="038f3-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="038f3-405">3.0</span><span class="sxs-lookup"><span data-stu-id="038f3-405">3.0</span></span>               | <span data-ttu-id="038f3-406">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="038f3-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="038f3-407">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-407">x64</span></span> | [<span data-ttu-id="038f3-408">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="038f3-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="038f3-409">2.2</span><span class="sxs-lookup"><span data-stu-id="038f3-409">2.2</span></span>               | <span data-ttu-id="038f3-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="038f3-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="038f3-411">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-411">x64</span></span> | [<span data-ttu-id="038f3-412">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="038f3-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="038f3-413">2.1</span><span class="sxs-lookup"><span data-stu-id="038f3-413">2.1</span></span>               | <span data-ttu-id="038f3-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="038f3-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="038f3-415">x64</span><span class="sxs-lookup"><span data-stu-id="038f3-415">x64</span></span> | [<span data-ttu-id="038f3-416">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="038f3-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="038f3-417">MacOS Catalina (sürüm 10,15) ile başlayarak, geliştirici KIMLIĞIYLE dağıtılan 1 Haziran 2019 ' den sonra oluşturulan tüm yazılımlar, dikkat edilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="038f3-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="038f3-418">Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="038f3-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="038f3-419">.NET Core (çalışma zamanı ve SDK) yükleyicileri 3,1, 3,0 ve 2,1 sürümleri, 18 Şubat 2020 tarihinden itibaren giderilmiş.</span><span class="sxs-lookup"><span data-stu-id="038f3-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="038f3-420">Önceki yayınlanmış sürümler yok.</span><span class="sxs-lookup"><span data-stu-id="038f3-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="038f3-421">Desteklenmeyen bir uygulama çalıştırırsanız aşağıdaki görüntüye benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="038f3-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarleştirme uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="038f3-423">Zorunlu kılınma 'nın .NET Core 'u (ve .NET Core uygulamalarınızı) nasıl etkilediği hakkında daha fazla bilgi için bkz. [macOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="038f3-424">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="038f3-424">libgdiplus</span></span>

<span data-ttu-id="038f3-425">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="038f3-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="038f3-426">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="038f3-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="038f3-427">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="038f3-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="038f3-428">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="038f3-428">Next steps</span></span>

- <span data-ttu-id="038f3-429">Uygulama geliştirmek ve çalıştırmak için, [.NET Core SDK](sdk.md) (çalışma zamanını içerir).</span><span class="sxs-lookup"><span data-stu-id="038f3-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="038f3-430">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma zamanı](runtime.md)'nı yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="038f3-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
