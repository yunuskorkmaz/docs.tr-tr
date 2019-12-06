---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları-.NET Core
description: Windows, Linux ve macOS 'ta .NET Core SDK ve çalışma zamanı yüklemek için işletim sistemi ve CPU mimarisi ön koşullarını ayrıntılı olarak izleyin.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a535048fc8756b55068098ad61fdc37fc8c1f04e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837005"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="d0f26-103">.NET Core bağımlılıkları ve gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="d0f26-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="d0f26-104">Bu makalede .NET Core tarafından desteklenen işletim sistemleri ve CPU mimarisinin ayrıntıları verilir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d0f26-105">Supported operating systems</span><span class="sxs-lookup"><span data-stu-id="d0f26-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="d0f26-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="d0f26-107">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-108">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-109">OS</span></span>                            | <span data-ttu-id="d0f26-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-110">Version</span></span>                        | <span data-ttu-id="d0f26-111">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d0f26-112">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="d0f26-112">Windows Client</span></span>                | <span data-ttu-id="d0f26-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d0f26-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-114">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-115">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="d0f26-115">Windows 10 Client</span></span>             | <span data-ttu-id="d0f26-116">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-116">Version 1607+</span></span>                  | <span data-ttu-id="d0f26-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-117">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d0f26-118">Windows Server</span></span>                | <span data-ttu-id="d0f26-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-119">2012 R2+</span></span>                       | <span data-ttu-id="d0f26-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-120">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-121">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="d0f26-121">Nano Server</span></span>                   | <span data-ttu-id="d0f26-122">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-122">Version 1803+</span></span>                  | <span data-ttu-id="d0f26-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-123">x64, ARM32</span></span>      |

<span data-ttu-id="d0f26-124">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="d0f26-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d0f26-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="d0f26-126">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-127">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-128">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-128">OS</span></span>                            | <span data-ttu-id="d0f26-129">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-129">Version</span></span>                        | <span data-ttu-id="d0f26-130">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d0f26-131">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="d0f26-131">Windows Client</span></span>                | <span data-ttu-id="d0f26-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d0f26-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-133">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-134">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="d0f26-134">Windows 10 Client</span></span>             | <span data-ttu-id="d0f26-135">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-135">Version 1607+</span></span>                  | <span data-ttu-id="d0f26-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-136">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d0f26-137">Windows Server</span></span>                | <span data-ttu-id="d0f26-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-138">2012 R2+</span></span>                       | <span data-ttu-id="d0f26-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-139">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-140">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="d0f26-140">Nano Server</span></span>                   | <span data-ttu-id="d0f26-141">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-141">Version 1803+</span></span>                  | <span data-ttu-id="d0f26-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-142">x64, ARM32</span></span>      |

<span data-ttu-id="d0f26-143">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="d0f26-144">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="d0f26-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="d0f26-145">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-146">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-147">OS</span></span>                            | <span data-ttu-id="d0f26-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-148">Version</span></span>                        | <span data-ttu-id="d0f26-149">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d0f26-150">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="d0f26-150">Windows Client</span></span>                | <span data-ttu-id="d0f26-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d0f26-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-152">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-153">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="d0f26-153">Windows 10 Client</span></span>             | <span data-ttu-id="d0f26-154">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-154">Version 1607+</span></span>                  | <span data-ttu-id="d0f26-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-155">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d0f26-156">Windows Server</span></span>                | <span data-ttu-id="d0f26-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="d0f26-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-158">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-159">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="d0f26-159">Nano Server</span></span>                   | <span data-ttu-id="d0f26-160">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-160">Version 1803+</span></span>                   | <span data-ttu-id="d0f26-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-161">x64, ARM32</span></span>      |

<span data-ttu-id="d0f26-162">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d0f26-163">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d0f26-164">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-165">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-166">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-166">OS</span></span>                            | <span data-ttu-id="d0f26-167">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-167">Version</span></span>                        | <span data-ttu-id="d0f26-168">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d0f26-169">Windows İstemci</span><span class="sxs-lookup"><span data-stu-id="d0f26-169">Windows Client</span></span>                | <span data-ttu-id="d0f26-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d0f26-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-171">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-172">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="d0f26-172">Windows 10 Client</span></span>             | <span data-ttu-id="d0f26-173">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-173">Version 1607+</span></span>                  | <span data-ttu-id="d0f26-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-174">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d0f26-175">Windows Server</span></span>                | <span data-ttu-id="d0f26-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="d0f26-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d0f26-177">x64, x86</span></span>        |
| <span data-ttu-id="d0f26-178">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="d0f26-178">Nano Server</span></span>                   | <span data-ttu-id="d0f26-179">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-179">Version 1803+</span></span>                  | <span data-ttu-id="d0f26-180">x64</span><span class="sxs-lookup"><span data-stu-id="d0f26-180">x64,</span></span>            |

<span data-ttu-id="d0f26-181">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="d0f26-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d0f26-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="d0f26-183">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="d0f26-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d0f26-184">Windows 7 SP1</span></span>
- <span data-ttu-id="d0f26-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="d0f26-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="d0f26-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d0f26-186">Windows 8.1</span></span>
- <span data-ttu-id="d0f26-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d0f26-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="d0f26-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d0f26-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="d0f26-189">Aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="d0f26-189">Install the following:</span></span>

- <span data-ttu-id="d0f26-190">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="d0f26-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="d0f26-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="d0f26-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="d0f26-192">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="d0f26-193">*API-MS-Win-CRT-Runtime-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d0f26-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="d0f26-194">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="d0f26-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="d0f26-195">\- veya -</span><span class="sxs-lookup"><span data-stu-id="d0f26-195">\- or -</span></span>
>
> <span data-ttu-id="d0f26-196">*Hostfxr. dll* kitaplığı bulundu, ancak *C:\\\<path_to_app >\\hostfxr. dll* ' den yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="d0f26-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="d0f26-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="d0f26-198">.NET Core 3,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="d0f26-199">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="d0f26-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d0f26-200">.NET Core 3,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-201">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-202">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-202">OS</span></span>                             | <span data-ttu-id="d0f26-203">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-203">Version</span></span>               | <span data-ttu-id="d0f26-204">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="d0f26-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="d0f26-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d0f26-206">6, 7, 8</span></span>               | <span data-ttu-id="d0f26-207">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-207">x64</span></span> |
| <span data-ttu-id="d0f26-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="d0f26-208">CentOS</span></span>                         | <span data-ttu-id="d0f26-209">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-209">7+</span></span>                    | <span data-ttu-id="d0f26-210">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-210">x64</span></span> |
| <span data-ttu-id="d0f26-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-211">Oracle Linux</span></span>                   | <span data-ttu-id="d0f26-212">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-212">7+</span></span>                    | <span data-ttu-id="d0f26-213">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-213">x64</span></span> |
| <span data-ttu-id="d0f26-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="d0f26-214">Fedora</span></span>                         | <span data-ttu-id="d0f26-215">29 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-215">29+</span></span>                   | <span data-ttu-id="d0f26-216">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-216">x64</span></span> |
| <span data-ttu-id="d0f26-217">Debian</span><span class="sxs-lookup"><span data-stu-id="d0f26-217">Debian</span></span>                         | <span data-ttu-id="d0f26-218">9 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-218">9+</span></span>                    | <span data-ttu-id="d0f26-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d0f26-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d0f26-220">Ubuntu</span></span>                         | <span data-ttu-id="d0f26-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-221">16.04+</span></span>                | <span data-ttu-id="d0f26-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d0f26-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="d0f26-223">Linux Mint</span></span>                     | <span data-ttu-id="d0f26-224">18 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-224">18+</span></span>                   | <span data-ttu-id="d0f26-225">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-225">x64</span></span> |
| <span data-ttu-id="d0f26-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d0f26-226">openSUSE</span></span>                       | <span data-ttu-id="d0f26-227">15 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-227">15+</span></span>                   | <span data-ttu-id="d0f26-228">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-228">x64</span></span> |
| <span data-ttu-id="d0f26-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d0f26-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="d0f26-230">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-230">12 SP2+</span></span>               | <span data-ttu-id="d0f26-231">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-231">x64</span></span> |
| <span data-ttu-id="d0f26-232">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-232">Alpine Linux</span></span>                   | <span data-ttu-id="d0f26-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-233">3.10+</span></span>                 | <span data-ttu-id="d0f26-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-234">x64, ARM64</span></span> |

<span data-ttu-id="d0f26-235">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="d0f26-236">.NET Core 3,1 ' i ARM64 üzerinde yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="d0f26-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0f26-237">ARM64 desteği Linux Kernel 4,14 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="d0f26-238">Bazı Linux dağıtımları, diğerleri bu gereksinimi karşılar.</span><span class="sxs-lookup"><span data-stu-id="d0f26-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="d0f26-239">Örneğin, Ubuntu 18,04 desteklenir, ancak Ubuntu 16,04 değildir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="d0f26-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d0f26-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="d0f26-241">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="d0f26-242">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="d0f26-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d0f26-243">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-244">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-245">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-245">OS</span></span>                             | <span data-ttu-id="d0f26-246">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-246">Version</span></span>               | <span data-ttu-id="d0f26-247">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="d0f26-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="d0f26-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d0f26-249">6, 7, 8</span></span>               | <span data-ttu-id="d0f26-250">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-250">x64</span></span> |
| <span data-ttu-id="d0f26-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="d0f26-251">CentOS</span></span>                         | <span data-ttu-id="d0f26-252">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-252">7+</span></span>                    | <span data-ttu-id="d0f26-253">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-253">x64</span></span> |
| <span data-ttu-id="d0f26-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-254">Oracle Linux</span></span>                   | <span data-ttu-id="d0f26-255">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-255">7+</span></span>                    | <span data-ttu-id="d0f26-256">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-256">x64</span></span> |
| <span data-ttu-id="d0f26-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="d0f26-257">Fedora</span></span>                         | <span data-ttu-id="d0f26-258">29 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-258">29+</span></span>                   | <span data-ttu-id="d0f26-259">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-259">x64</span></span> |
| <span data-ttu-id="d0f26-260">Debian</span><span class="sxs-lookup"><span data-stu-id="d0f26-260">Debian</span></span>                         | <span data-ttu-id="d0f26-261">9 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-261">9+</span></span>                    | <span data-ttu-id="d0f26-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d0f26-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d0f26-263">Ubuntu</span></span>                         | <span data-ttu-id="d0f26-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-264">16.04+</span></span>                | <span data-ttu-id="d0f26-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d0f26-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="d0f26-266">Linux Mint</span></span>                     | <span data-ttu-id="d0f26-267">18 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-267">18+</span></span>                   | <span data-ttu-id="d0f26-268">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-268">x64</span></span> |
| <span data-ttu-id="d0f26-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d0f26-269">openSUSE</span></span>                       | <span data-ttu-id="d0f26-270">15 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-270">15+</span></span>                   | <span data-ttu-id="d0f26-271">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-271">x64</span></span> |
| <span data-ttu-id="d0f26-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d0f26-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="d0f26-273">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-273">12 SP2+</span></span>               | <span data-ttu-id="d0f26-274">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-274">x64</span></span> |
| <span data-ttu-id="d0f26-275">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-275">Alpine Linux</span></span>                   | <span data-ttu-id="d0f26-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-276">3.8+</span></span>                  | <span data-ttu-id="d0f26-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="d0f26-277">x64, ARM64</span></span> |

<span data-ttu-id="d0f26-278">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="d0f26-279">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="d0f26-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="d0f26-280">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="d0f26-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="d0f26-281">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="d0f26-282">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="d0f26-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d0f26-283">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-284">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-285">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-285">OS</span></span>                             |  <span data-ttu-id="d0f26-286">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-286">Version</span></span>                |  <span data-ttu-id="d0f26-287">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="d0f26-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="d0f26-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="d0f26-289">6, 7</span></span>                   | <span data-ttu-id="d0f26-290">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-290">x64</span></span> |
| <span data-ttu-id="d0f26-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="d0f26-291">CentOS</span></span>                         |  <span data-ttu-id="d0f26-292">7</span><span class="sxs-lookup"><span data-stu-id="d0f26-292">7</span></span>                      | <span data-ttu-id="d0f26-293">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-293">x64</span></span> |
| <span data-ttu-id="d0f26-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-294">Oracle Linux</span></span>                   |  <span data-ttu-id="d0f26-295">7</span><span class="sxs-lookup"><span data-stu-id="d0f26-295">7</span></span>                      | <span data-ttu-id="d0f26-296">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-296">x64</span></span> |
| <span data-ttu-id="d0f26-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="d0f26-297">Fedora</span></span>                         |  <span data-ttu-id="d0f26-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="d0f26-298">29, 30</span></span>                 | <span data-ttu-id="d0f26-299">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-299">x64</span></span> |
| <span data-ttu-id="d0f26-300">Debian</span><span class="sxs-lookup"><span data-stu-id="d0f26-300">Debian</span></span>                         |  <span data-ttu-id="d0f26-301">9</span><span class="sxs-lookup"><span data-stu-id="d0f26-301">9</span></span>                      | <span data-ttu-id="d0f26-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-302">x64, ARM32</span></span> |
| <span data-ttu-id="d0f26-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d0f26-303">Ubuntu</span></span>                         |  <span data-ttu-id="d0f26-304">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="d0f26-304">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="d0f26-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-305">x64, ARM32</span></span> |
| <span data-ttu-id="d0f26-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="d0f26-306">Linux Mint</span></span>                     |  <span data-ttu-id="d0f26-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="d0f26-307">17, 18</span></span>                 | <span data-ttu-id="d0f26-308">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-308">x64</span></span> |
| <span data-ttu-id="d0f26-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d0f26-309">openSUSE</span></span>                       |  <span data-ttu-id="d0f26-310">15 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-310">15+</span></span>                    | <span data-ttu-id="d0f26-311">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-311">x64</span></span> |
| <span data-ttu-id="d0f26-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d0f26-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="d0f26-313">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-313">12 SP2+</span></span>                | <span data-ttu-id="d0f26-314">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-314">x64</span></span> |
| <span data-ttu-id="d0f26-315">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-315">Alpine Linux</span></span>                   |  <span data-ttu-id="d0f26-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-316">3.8+</span></span>                   | <span data-ttu-id="d0f26-317">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-317">x64</span></span> |

<span data-ttu-id="d0f26-318">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d0f26-319">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d0f26-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d0f26-320">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="d0f26-321">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="d0f26-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d0f26-322">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-323">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-324">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d0f26-324">OS</span></span>                             |  <span data-ttu-id="d0f26-325">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d0f26-325">Version</span></span>                |  <span data-ttu-id="d0f26-326">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="d0f26-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="d0f26-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d0f26-328">6, 7, 8</span></span>                | <span data-ttu-id="d0f26-329">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-329">x64</span></span> |
| <span data-ttu-id="d0f26-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="d0f26-330">CentOS</span></span>                         |  <span data-ttu-id="d0f26-331">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-331">7+</span></span>                     | <span data-ttu-id="d0f26-332">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-332">x64</span></span> |
| <span data-ttu-id="d0f26-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-333">Oracle Linux</span></span>                   |  <span data-ttu-id="d0f26-334">7 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-334">7+</span></span>                     | <span data-ttu-id="d0f26-335">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-335">x64</span></span> |
| <span data-ttu-id="d0f26-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="d0f26-336">Fedora</span></span>                         |  <span data-ttu-id="d0f26-337">29 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-337">29+</span></span>                    | <span data-ttu-id="d0f26-338">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-338">x64</span></span> |
| <span data-ttu-id="d0f26-339">Debian</span><span class="sxs-lookup"><span data-stu-id="d0f26-339">Debian</span></span>                         |  <span data-ttu-id="d0f26-340">9</span><span class="sxs-lookup"><span data-stu-id="d0f26-340">9</span></span>                      | <span data-ttu-id="d0f26-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-341">x64, ARM32</span></span> |
| <span data-ttu-id="d0f26-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d0f26-342">Ubuntu</span></span>                         |  <span data-ttu-id="d0f26-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="d0f26-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="d0f26-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d0f26-344">x64, ARM32</span></span> |
| <span data-ttu-id="d0f26-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="d0f26-345">Linux Mint</span></span>                     |  <span data-ttu-id="d0f26-346">17 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-346">17+</span></span>                    | <span data-ttu-id="d0f26-347">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-347">x64</span></span> |
| <span data-ttu-id="d0f26-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d0f26-348">openSUSE</span></span>                       |  <span data-ttu-id="d0f26-349">15 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-349">15+</span></span>                    | <span data-ttu-id="d0f26-350">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-350">x64</span></span> |
| <span data-ttu-id="d0f26-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d0f26-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="d0f26-352">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-352">12 SP2+</span></span>                | <span data-ttu-id="d0f26-353">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-353">x64</span></span> |
| <span data-ttu-id="d0f26-354">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="d0f26-354">Alpine Linux</span></span>                   |  <span data-ttu-id="d0f26-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d0f26-355">3.8+</span></span>                   | <span data-ttu-id="d0f26-356">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-356">x64</span></span> |

<span data-ttu-id="d0f26-357">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="d0f26-358">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="d0f26-358">Linux distribution dependencies</span></span>

<span data-ttu-id="d0f26-359">Linux dağıtımına bağlı olarak ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0f26-360">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="d0f26-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d0f26-361">Ubuntu</span></span>

<span data-ttu-id="d0f26-362">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="d0f26-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="d0f26-363">liblttng-ust0</span></span>
- <span data-ttu-id="d0f26-364">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="d0f26-365">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="d0f26-366">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d0f26-366">libssl1.0.0</span></span>
- <span data-ttu-id="d0f26-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="d0f26-367">libkrb5-3</span></span>
- <span data-ttu-id="d0f26-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d0f26-368">zlib1g</span></span>
- <span data-ttu-id="d0f26-369">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="d0f26-370">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="d0f26-371">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="d0f26-372">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="d0f26-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="d0f26-373">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="d0f26-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="d0f26-374">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="d0f26-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="d0f26-375">Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="d0f26-376">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f26-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="d0f26-377">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="d0f26-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="d0f26-378">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="d0f26-378">CentOS and Fedora</span></span>

<span data-ttu-id="d0f26-379">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="d0f26-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="d0f26-380">lttng-ust</span></span>
- <span data-ttu-id="d0f26-381">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="d0f26-381">libcurl</span></span>
- <span data-ttu-id="d0f26-382">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="d0f26-382">openssl-libs</span></span>
- <span data-ttu-id="d0f26-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="d0f26-383">krb5-libs</span></span>
- <span data-ttu-id="d0f26-384">libıu</span><span class="sxs-lookup"><span data-stu-id="d0f26-384">libicu</span></span>
- <span data-ttu-id="d0f26-385">zlib</span><span class="sxs-lookup"><span data-stu-id="d0f26-385">zlib</span></span>

<span data-ttu-id="d0f26-386">Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="d0f26-387">.NET Core 2,0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="d0f26-388">librüzgar</span><span class="sxs-lookup"><span data-stu-id="d0f26-388">libunwind</span></span>
- <span data-ttu-id="d0f26-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="d0f26-389">libuuid</span></span>

<span data-ttu-id="d0f26-390">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d0f26-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="d0f26-391">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d0f26-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="d0f26-392">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="d0f26-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="d0f26-393">CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="d0f26-394">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f26-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="d0f26-395">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="d0f26-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="d0f26-396">.NET Core aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0f26-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="d0f26-397">`+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0f26-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d0f26-398">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="d0f26-398">.NET Core Version</span></span> | <span data-ttu-id="d0f26-399">macOS</span><span class="sxs-lookup"><span data-stu-id="d0f26-399">macOS</span></span>                 | <span data-ttu-id="d0f26-400">Mimariler</span><span class="sxs-lookup"><span data-stu-id="d0f26-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="d0f26-401">3.1</span><span class="sxs-lookup"><span data-stu-id="d0f26-401">3.1</span></span>               | <span data-ttu-id="d0f26-402">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="d0f26-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d0f26-403">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-403">x64</span></span> | [<span data-ttu-id="d0f26-404">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d0f26-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="d0f26-405">3.0</span><span class="sxs-lookup"><span data-stu-id="d0f26-405">3.0</span></span>               | <span data-ttu-id="d0f26-406">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="d0f26-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d0f26-407">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-407">x64</span></span> | [<span data-ttu-id="d0f26-408">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d0f26-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="d0f26-409">2.2</span><span class="sxs-lookup"><span data-stu-id="d0f26-409">2.2</span></span>               | <span data-ttu-id="d0f26-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="d0f26-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="d0f26-411">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-411">x64</span></span> | [<span data-ttu-id="d0f26-412">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d0f26-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="d0f26-413">2.1</span><span class="sxs-lookup"><span data-stu-id="d0f26-413">2.1</span></span>               | <span data-ttu-id="d0f26-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="d0f26-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="d0f26-415">X64</span><span class="sxs-lookup"><span data-stu-id="d0f26-415">x64</span></span> | [<span data-ttu-id="d0f26-416">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d0f26-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="d0f26-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="d0f26-417">libgdiplus</span></span>

<span data-ttu-id="d0f26-418">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0f26-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="d0f26-419">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d0f26-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="d0f26-420">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="d0f26-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="d0f26-421">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d0f26-421">Next steps</span></span>

- <span data-ttu-id="d0f26-422">Uygulama geliştirmek ve çalıştırmak için, [.NET Core SDK](sdk.md) (çalışma zamanını içerir).</span><span class="sxs-lookup"><span data-stu-id="d0f26-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="d0f26-423">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma zamanı](runtime.md)'nı yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f26-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
