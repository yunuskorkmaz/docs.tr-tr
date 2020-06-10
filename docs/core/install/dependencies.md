---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları-.NET Core
description: Windows, Linux ve macOS 'ta .NET Core SDK ve çalışma zamanı yüklemek için işletim sistemi ve CPU mimarisi ön koşullarını ayrıntılı olarak izleyin.
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590766"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="3351e-103">.NET Core bağımlılıkları ve gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="3351e-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="3351e-104">Bu makalede .NET Core tarafından desteklenen işletim sistemleri ve CPU mimarisinin ayrıntıları verilir.</span><span class="sxs-lookup"><span data-stu-id="3351e-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="3351e-105">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="3351e-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="3351e-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3351e-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="3351e-107">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-108">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-109">OS</span></span>                            | <span data-ttu-id="3351e-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-110">Version</span></span>                        | <span data-ttu-id="3351e-111">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3351e-112">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-112">Windows Client</span></span>                | <span data-ttu-id="3351e-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3351e-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3351e-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-114">x64, x86</span></span>        |
| <span data-ttu-id="3351e-115">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-115">Windows 10 Client</span></span>             | <span data-ttu-id="3351e-116">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3351e-116">Version 1607+</span></span>                  | <span data-ttu-id="3351e-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-117">x64, x86</span></span>        |
| <span data-ttu-id="3351e-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3351e-118">Windows Server</span></span>                | <span data-ttu-id="3351e-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-119">2012 R2+</span></span>                       | <span data-ttu-id="3351e-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-120">x64, x86</span></span>        |
| <span data-ttu-id="3351e-121">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3351e-121">Nano Server</span></span>                   | <span data-ttu-id="3351e-122">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3351e-122">Version 1803+</span></span>                  | <span data-ttu-id="3351e-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-123">x64, ARM32</span></span>      |

<span data-ttu-id="3351e-124">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="3351e-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3351e-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="3351e-126">*.NET Core 3,0 şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3351e-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3351e-127">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-128">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-129">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-129">OS</span></span>                            | <span data-ttu-id="3351e-130">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-130">Version</span></span>                        | <span data-ttu-id="3351e-131">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3351e-132">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-132">Windows Client</span></span>                | <span data-ttu-id="3351e-133">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3351e-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3351e-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-134">x64, x86</span></span>        |
| <span data-ttu-id="3351e-135">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-135">Windows 10 Client</span></span>             | <span data-ttu-id="3351e-136">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3351e-136">Version 1607+</span></span>                  | <span data-ttu-id="3351e-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-137">x64, x86</span></span>        |
| <span data-ttu-id="3351e-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3351e-138">Windows Server</span></span>                | <span data-ttu-id="3351e-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-139">2012 R2+</span></span>                       | <span data-ttu-id="3351e-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-140">x64, x86</span></span>        |
| <span data-ttu-id="3351e-141">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3351e-141">Nano Server</span></span>                   | <span data-ttu-id="3351e-142">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3351e-142">Version 1803+</span></span>                  | <span data-ttu-id="3351e-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-143">x64, ARM32</span></span>      |

<span data-ttu-id="3351e-144">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="3351e-145">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="3351e-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="3351e-146">*.NET Core 2,2 Şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3351e-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3351e-147">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-148">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-149">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-149">OS</span></span>                            | <span data-ttu-id="3351e-150">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-150">Version</span></span>                        | <span data-ttu-id="3351e-151">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3351e-152">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-152">Windows Client</span></span>                | <span data-ttu-id="3351e-153">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3351e-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3351e-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-154">x64, x86</span></span>        |
| <span data-ttu-id="3351e-155">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-155">Windows 10 Client</span></span>             | <span data-ttu-id="3351e-156">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3351e-156">Version 1607+</span></span>                  | <span data-ttu-id="3351e-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-157">x64, x86</span></span>        |
| <span data-ttu-id="3351e-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3351e-158">Windows Server</span></span>                | <span data-ttu-id="3351e-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="3351e-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="3351e-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-160">x64, x86</span></span>        |
| <span data-ttu-id="3351e-161">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3351e-161">Nano Server</span></span>                   | <span data-ttu-id="3351e-162">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3351e-162">Version 1803+</span></span>                   | <span data-ttu-id="3351e-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-163">x64, ARM32</span></span>      |

<span data-ttu-id="3351e-164">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3351e-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3351e-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3351e-166">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-167">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-168">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-168">OS</span></span>                            | <span data-ttu-id="3351e-169">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-169">Version</span></span>                        | <span data-ttu-id="3351e-170">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3351e-171">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-171">Windows Client</span></span>                | <span data-ttu-id="3351e-172">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3351e-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3351e-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-173">x64, x86</span></span>        |
| <span data-ttu-id="3351e-174">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3351e-174">Windows 10 Client</span></span>             | <span data-ttu-id="3351e-175">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3351e-175">Version 1607+</span></span>                  | <span data-ttu-id="3351e-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-176">x64, x86</span></span>        |
| <span data-ttu-id="3351e-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3351e-177">Windows Server</span></span>                | <span data-ttu-id="3351e-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="3351e-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="3351e-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3351e-179">x64, x86</span></span>        |
| <span data-ttu-id="3351e-180">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3351e-180">Nano Server</span></span>                   | <span data-ttu-id="3351e-181">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3351e-181">Version 1803+</span></span>                  | <span data-ttu-id="3351e-182">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-182">x64,</span></span>            |

<span data-ttu-id="3351e-183">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="3351e-184">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3351e-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="3351e-185">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3351e-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="3351e-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3351e-186">Windows 7 SP1</span></span>
- <span data-ttu-id="3351e-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="3351e-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="3351e-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3351e-188">Windows 8.1</span></span>
- <span data-ttu-id="3351e-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3351e-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="3351e-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3351e-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="3351e-191">Aşağıdakileri yükleyerek:</span><span class="sxs-lookup"><span data-stu-id="3351e-191">Install the following:</span></span>

- <span data-ttu-id="3351e-192">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="3351e-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="3351e-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="3351e-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="3351e-194">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3351e-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="3351e-195">*API-MS-Win-CRT-Runtime-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3351e-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="3351e-196">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3351e-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="3351e-197">\-veya</span><span class="sxs-lookup"><span data-stu-id="3351e-197">\- or -</span></span>
>
> <span data-ttu-id="3351e-198">*API-MS-Win-Cor-TimeZone-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3351e-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="3351e-199">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3351e-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="3351e-200">\-veya</span><span class="sxs-lookup"><span data-stu-id="3351e-200">\- or -</span></span>
>
> <span data-ttu-id="3351e-201">*Hostfxr. dll* kitaplığı bulundu, ancak *C: \\ \<path_to_app> \\ hostfxr. dll* dosyasından yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="3351e-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="3351e-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3351e-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="3351e-203">.NET Core 3,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="3351e-204">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="3351e-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="3351e-205">.NET Core 3,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-206">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-207">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-207">OS</span></span>                             | <span data-ttu-id="3351e-208">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-208">Version</span></span>               | <span data-ttu-id="3351e-209">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="3351e-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="3351e-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="3351e-211">6, 7, 8</span></span>               | <span data-ttu-id="3351e-212">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-212">x64</span></span> |
| <span data-ttu-id="3351e-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="3351e-213">CentOS</span></span>                         | <span data-ttu-id="3351e-214">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-214">7+</span></span>                    | <span data-ttu-id="3351e-215">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-215">x64</span></span> |
| <span data-ttu-id="3351e-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-216">Oracle Linux</span></span>                   | <span data-ttu-id="3351e-217">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-217">7+</span></span>                    | <span data-ttu-id="3351e-218">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-218">x64</span></span> |
| <span data-ttu-id="3351e-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="3351e-219">Fedora</span></span>                         | <span data-ttu-id="3351e-220">30 +</span><span class="sxs-lookup"><span data-stu-id="3351e-220">30+</span></span>                   | <span data-ttu-id="3351e-221">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-221">x64</span></span> |
| <span data-ttu-id="3351e-222">Debian</span><span class="sxs-lookup"><span data-stu-id="3351e-222">Debian</span></span>                         | <span data-ttu-id="3351e-223">9 +</span><span class="sxs-lookup"><span data-stu-id="3351e-223">9+</span></span>                    | <span data-ttu-id="3351e-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="3351e-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3351e-225">Ubuntu</span></span>                         | <span data-ttu-id="3351e-226">16.04 +</span><span class="sxs-lookup"><span data-stu-id="3351e-226">16.04+</span></span>                | <span data-ttu-id="3351e-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="3351e-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="3351e-228">Linux Mint</span></span>                     | <span data-ttu-id="3351e-229">18 +</span><span class="sxs-lookup"><span data-stu-id="3351e-229">18+</span></span>                   | <span data-ttu-id="3351e-230">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-230">x64</span></span> |
| <span data-ttu-id="3351e-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3351e-231">openSUSE</span></span>                       | <span data-ttu-id="3351e-232">15 +</span><span class="sxs-lookup"><span data-stu-id="3351e-232">15+</span></span>                   | <span data-ttu-id="3351e-233">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-233">x64</span></span> |
| <span data-ttu-id="3351e-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="3351e-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="3351e-235">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-235">12 SP2+</span></span>               | <span data-ttu-id="3351e-236">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-236">x64</span></span> |
| <span data-ttu-id="3351e-237">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-237">Alpine Linux</span></span>                   | <span data-ttu-id="3351e-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="3351e-238">3.10+</span></span>                 | <span data-ttu-id="3351e-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-239">x64, ARM64</span></span> |

<span data-ttu-id="3351e-240">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="3351e-241">.NET Core 3,1 ' i ARM64 üzerinde yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="3351e-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3351e-242">ARM64 desteği Linux Kernel 4,14 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="3351e-243">Bazı Linux dağıtımları, diğerleri bu gereksinimi karşılar.</span><span class="sxs-lookup"><span data-stu-id="3351e-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="3351e-244">Örneğin, Ubuntu 18,04 desteklenir, ancak Ubuntu 16,04 değildir.</span><span class="sxs-lookup"><span data-stu-id="3351e-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="3351e-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3351e-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="3351e-246">*.NET Core 3,0 şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3351e-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3351e-247">.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="3351e-248">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="3351e-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="3351e-249">.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-250">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-251">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-251">OS</span></span>                             | <span data-ttu-id="3351e-252">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-252">Version</span></span>               | <span data-ttu-id="3351e-253">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="3351e-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="3351e-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="3351e-255">6, 7, 8</span></span>               | <span data-ttu-id="3351e-256">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-256">x64</span></span> |
| <span data-ttu-id="3351e-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="3351e-257">CentOS</span></span>                         | <span data-ttu-id="3351e-258">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-258">7+</span></span>                    | <span data-ttu-id="3351e-259">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-259">x64</span></span> |
| <span data-ttu-id="3351e-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-260">Oracle Linux</span></span>                   | <span data-ttu-id="3351e-261">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-261">7+</span></span>                    | <span data-ttu-id="3351e-262">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-262">x64</span></span> |
| <span data-ttu-id="3351e-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="3351e-263">Fedora</span></span>                         | <span data-ttu-id="3351e-264">29 +</span><span class="sxs-lookup"><span data-stu-id="3351e-264">29+</span></span>                   | <span data-ttu-id="3351e-265">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-265">x64</span></span> |
| <span data-ttu-id="3351e-266">Debian</span><span class="sxs-lookup"><span data-stu-id="3351e-266">Debian</span></span>                         | <span data-ttu-id="3351e-267">9 +</span><span class="sxs-lookup"><span data-stu-id="3351e-267">9+</span></span>                    | <span data-ttu-id="3351e-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="3351e-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3351e-269">Ubuntu</span></span>                         | <span data-ttu-id="3351e-270">16.04 +</span><span class="sxs-lookup"><span data-stu-id="3351e-270">16.04+</span></span>                | <span data-ttu-id="3351e-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="3351e-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="3351e-272">Linux Mint</span></span>                     | <span data-ttu-id="3351e-273">18 +</span><span class="sxs-lookup"><span data-stu-id="3351e-273">18+</span></span>                   | <span data-ttu-id="3351e-274">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-274">x64</span></span> |
| <span data-ttu-id="3351e-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3351e-275">openSUSE</span></span>                       | <span data-ttu-id="3351e-276">15 +</span><span class="sxs-lookup"><span data-stu-id="3351e-276">15+</span></span>                   | <span data-ttu-id="3351e-277">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-277">x64</span></span> |
| <span data-ttu-id="3351e-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="3351e-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="3351e-279">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-279">12 SP2+</span></span>               | <span data-ttu-id="3351e-280">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-280">x64</span></span> |
| <span data-ttu-id="3351e-281">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-281">Alpine Linux</span></span>                   | <span data-ttu-id="3351e-282">3.8 +</span><span class="sxs-lookup"><span data-stu-id="3351e-282">3.8+</span></span>                  | <span data-ttu-id="3351e-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="3351e-283">x64, ARM64</span></span> |

<span data-ttu-id="3351e-284">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="3351e-285">ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="3351e-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="3351e-286">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="3351e-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="3351e-287">*.NET Core 2,2 Şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3351e-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3351e-288">.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="3351e-289">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="3351e-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="3351e-290">.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-291">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-292">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-292">OS</span></span>                             |  <span data-ttu-id="3351e-293">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-293">Version</span></span>                |  <span data-ttu-id="3351e-294">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="3351e-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="3351e-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="3351e-296">6, 7</span></span>                   | <span data-ttu-id="3351e-297">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-297">x64</span></span> |
| <span data-ttu-id="3351e-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="3351e-298">CentOS</span></span>                         |  <span data-ttu-id="3351e-299">7</span><span class="sxs-lookup"><span data-stu-id="3351e-299">7</span></span>                      | <span data-ttu-id="3351e-300">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-300">x64</span></span> |
| <span data-ttu-id="3351e-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-301">Oracle Linux</span></span>                   |  <span data-ttu-id="3351e-302">7</span><span class="sxs-lookup"><span data-stu-id="3351e-302">7</span></span>                      | <span data-ttu-id="3351e-303">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-303">x64</span></span> |
| <span data-ttu-id="3351e-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="3351e-304">Fedora</span></span>                         |  <span data-ttu-id="3351e-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="3351e-305">29, 30</span></span>                 | <span data-ttu-id="3351e-306">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-306">x64</span></span> |
| <span data-ttu-id="3351e-307">Debian</span><span class="sxs-lookup"><span data-stu-id="3351e-307">Debian</span></span>                         |  <span data-ttu-id="3351e-308">9</span><span class="sxs-lookup"><span data-stu-id="3351e-308">9</span></span>                      | <span data-ttu-id="3351e-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-309">x64, ARM32</span></span> |
| <span data-ttu-id="3351e-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3351e-310">Ubuntu</span></span>                         |  <span data-ttu-id="3351e-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="3351e-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="3351e-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-312">x64, ARM32</span></span> |
| <span data-ttu-id="3351e-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="3351e-313">Linux Mint</span></span>                     |  <span data-ttu-id="3351e-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="3351e-314">17, 18</span></span>                 | <span data-ttu-id="3351e-315">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-315">x64</span></span> |
| <span data-ttu-id="3351e-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3351e-316">openSUSE</span></span>                       |  <span data-ttu-id="3351e-317">15 +</span><span class="sxs-lookup"><span data-stu-id="3351e-317">15+</span></span>                    | <span data-ttu-id="3351e-318">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-318">x64</span></span> |
| <span data-ttu-id="3351e-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="3351e-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="3351e-320">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-320">12 SP2+</span></span>                | <span data-ttu-id="3351e-321">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-321">x64</span></span> |
| <span data-ttu-id="3351e-322">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-322">Alpine Linux</span></span>                   |  <span data-ttu-id="3351e-323">3.8 +</span><span class="sxs-lookup"><span data-stu-id="3351e-323">3.8+</span></span>                   | <span data-ttu-id="3351e-324">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-324">x64</span></span> |

<span data-ttu-id="3351e-325">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3351e-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3351e-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3351e-327">.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="3351e-328">Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="3351e-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="3351e-329">.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-330">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-331">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3351e-331">OS</span></span>                             |  <span data-ttu-id="3351e-332">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3351e-332">Version</span></span>                |  <span data-ttu-id="3351e-333">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="3351e-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="3351e-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="3351e-335">6, 7, 8</span></span>                | <span data-ttu-id="3351e-336">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-336">x64</span></span> |
| <span data-ttu-id="3351e-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="3351e-337">CentOS</span></span>                         |  <span data-ttu-id="3351e-338">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-338">7+</span></span>                     | <span data-ttu-id="3351e-339">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-339">x64</span></span> |
| <span data-ttu-id="3351e-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-340">Oracle Linux</span></span>                   |  <span data-ttu-id="3351e-341">7 +</span><span class="sxs-lookup"><span data-stu-id="3351e-341">7+</span></span>                     | <span data-ttu-id="3351e-342">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-342">x64</span></span> |
| <span data-ttu-id="3351e-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="3351e-343">Fedora</span></span>                         |  <span data-ttu-id="3351e-344">30 +</span><span class="sxs-lookup"><span data-stu-id="3351e-344">30+</span></span>                    | <span data-ttu-id="3351e-345">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-345">x64</span></span> |
| <span data-ttu-id="3351e-346">Debian</span><span class="sxs-lookup"><span data-stu-id="3351e-346">Debian</span></span>                         |  <span data-ttu-id="3351e-347">9</span><span class="sxs-lookup"><span data-stu-id="3351e-347">9</span></span>                      | <span data-ttu-id="3351e-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-348">x64, ARM32</span></span> |
| <span data-ttu-id="3351e-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3351e-349">Ubuntu</span></span>                         |  <span data-ttu-id="3351e-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="3351e-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="3351e-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3351e-351">x64, ARM32</span></span> |
| <span data-ttu-id="3351e-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="3351e-352">Linux Mint</span></span>                     |  <span data-ttu-id="3351e-353">17 +</span><span class="sxs-lookup"><span data-stu-id="3351e-353">17+</span></span>                    | <span data-ttu-id="3351e-354">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-354">x64</span></span> |
| <span data-ttu-id="3351e-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3351e-355">openSUSE</span></span>                       |  <span data-ttu-id="3351e-356">15 +</span><span class="sxs-lookup"><span data-stu-id="3351e-356">15+</span></span>                    | <span data-ttu-id="3351e-357">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-357">x64</span></span> |
| <span data-ttu-id="3351e-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="3351e-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="3351e-359">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="3351e-359">12 SP2+</span></span>                | <span data-ttu-id="3351e-360">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-360">x64</span></span> |
| <span data-ttu-id="3351e-361">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="3351e-361">Alpine Linux</span></span>                   |  <span data-ttu-id="3351e-362">3.8 +</span><span class="sxs-lookup"><span data-stu-id="3351e-362">3.8+</span></span>                   | <span data-ttu-id="3351e-363">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-363">x64</span></span> |

<span data-ttu-id="3351e-364">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="3351e-365">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="3351e-365">Linux distribution dependencies</span></span>

<span data-ttu-id="3351e-366">Linux dağıtımına bağlı olarak ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3351e-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3351e-367">Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3351e-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="3351e-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3351e-368">Ubuntu</span></span>

<span data-ttu-id="3351e-369">Ubuntu dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3351e-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="3351e-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="3351e-370">liblttng-ust0</span></span>
- <span data-ttu-id="3351e-371">libcurl3 (14. x ve 16. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="3351e-372">libcurl4 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="3351e-373">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="3351e-373">libssl1.0.0</span></span>
- <span data-ttu-id="3351e-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="3351e-374">libkrb5-3</span></span>
- <span data-ttu-id="3351e-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="3351e-375">zlib1g</span></span>
- <span data-ttu-id="3351e-376">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="3351e-377">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="3351e-378">libicu57 (17. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="3351e-379">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="3351e-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="3351e-380">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="3351e-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="3351e-381">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="3351e-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="3351e-382">Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3351e-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="3351e-383">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3351e-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="3351e-384">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="3351e-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="3351e-385">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="3351e-385">CentOS and Fedora</span></span>

<span data-ttu-id="3351e-386">CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="3351e-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="3351e-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="3351e-387">lttng-ust</span></span>
- <span data-ttu-id="3351e-388">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="3351e-388">libcurl</span></span>
- <span data-ttu-id="3351e-389">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="3351e-389">openssl-libs</span></span>
- <span data-ttu-id="3351e-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="3351e-390">krb5-libs</span></span>
- <span data-ttu-id="3351e-391">libıu</span><span class="sxs-lookup"><span data-stu-id="3351e-391">libicu</span></span>
- <span data-ttu-id="3351e-392">zlib</span><span class="sxs-lookup"><span data-stu-id="3351e-392">zlib</span></span>

<span data-ttu-id="3351e-393">Fedora kullanıcıları: OpenSSL sürümünüz >= 1,1 Ise, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3351e-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="3351e-394">.NET Core 2,0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3351e-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="3351e-395">librüzgar</span><span class="sxs-lookup"><span data-stu-id="3351e-395">libunwind</span></span>
- <span data-ttu-id="3351e-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="3351e-396">libuuid</span></span>

<span data-ttu-id="3351e-397">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="3351e-398">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="3351e-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="3351e-399">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="3351e-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="3351e-400">CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3351e-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="3351e-401">En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3351e-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="3351e-402">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="3351e-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="3351e-403">Alpine</span><span class="sxs-lookup"><span data-stu-id="3351e-403">Alpine</span></span>

<span data-ttu-id="3351e-404">Alp dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3351e-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="3351e-405">ICU-libs (Genelleştirme devre dışıysa bu gerekli değildir)</span><span class="sxs-lookup"><span data-stu-id="3351e-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="3351e-406">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="3351e-406">krb5-libs</span></span>
- <span data-ttu-id="3351e-407">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="3351e-407">libcurl</span></span>
- <span data-ttu-id="3351e-408">libintl</span><span class="sxs-lookup"><span data-stu-id="3351e-408">libintl</span></span>
- <span data-ttu-id="3351e-409">libssl 1.1 (alp 3,9 veya üzeri için) veya libssl 1.0 (eski sürümler için)</span><span class="sxs-lookup"><span data-stu-id="3351e-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="3351e-410">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="3351e-410">libstdc++</span></span>
- <span data-ttu-id="3351e-411">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="3351e-411">lttng-ust</span></span>
- <span data-ttu-id="3351e-412">numactl (isteğe bağlı, yalnızca NUMA 'nın etkinleştirildiği cihazlarda yararlıdır)</span><span class="sxs-lookup"><span data-stu-id="3351e-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="3351e-413">zlib</span><span class="sxs-lookup"><span data-stu-id="3351e-413">zlib</span></span>

<span data-ttu-id="3351e-414">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="3351e-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="3351e-415">libgdiplus (yalnızca Edge/test deposunda kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="3351e-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="3351e-416">.NET Core aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3351e-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="3351e-417">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3351e-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3351e-418">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="3351e-418">.NET Core Version</span></span> | <span data-ttu-id="3351e-419">Mac OS</span><span class="sxs-lookup"><span data-stu-id="3351e-419">macOS</span></span>                 | <span data-ttu-id="3351e-420">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3351e-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="3351e-421">3,1</span><span class="sxs-lookup"><span data-stu-id="3351e-421">3.1</span></span>               | <span data-ttu-id="3351e-422">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="3351e-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="3351e-423">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-423">x64</span></span> | [<span data-ttu-id="3351e-424">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="3351e-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="3351e-425">3.0</span><span class="sxs-lookup"><span data-stu-id="3351e-425">3.0</span></span>               | <span data-ttu-id="3351e-426">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="3351e-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="3351e-427">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-427">x64</span></span> | [<span data-ttu-id="3351e-428">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="3351e-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="3351e-429">2,2</span><span class="sxs-lookup"><span data-stu-id="3351e-429">2.2</span></span>               | <span data-ttu-id="3351e-430">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="3351e-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="3351e-431">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-431">x64</span></span> | [<span data-ttu-id="3351e-432">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="3351e-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="3351e-433">2.1</span><span class="sxs-lookup"><span data-stu-id="3351e-433">2.1</span></span>               | <span data-ttu-id="3351e-434">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="3351e-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="3351e-435">x64</span><span class="sxs-lookup"><span data-stu-id="3351e-435">x64</span></span> | [<span data-ttu-id="3351e-436">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="3351e-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="3351e-437">MacOS Catalina (sürüm 10,15) ile başlayarak, geliştirici KIMLIĞIYLE dağıtılan 1 Haziran 2019 ' den sonra oluşturulan tüm yazılımlar, dikkat edilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3351e-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="3351e-438">Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3351e-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="3351e-439">.NET Core (çalışma zamanı ve SDK) yükleyicileri 3,1, 3,0 ve 2,1 sürümleri, 18 Şubat 2020 tarihinden itibaren giderilmiş.</span><span class="sxs-lookup"><span data-stu-id="3351e-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="3351e-440">Önceki yayınlanmış sürümler yok.</span><span class="sxs-lookup"><span data-stu-id="3351e-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="3351e-441">Desteklenmeyen bir uygulama çalıştırırsanız aşağıdaki görüntüye benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="3351e-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarleştirme uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="3351e-443">Zorunlu kılınma 'nın .NET Core 'u (ve .NET Core uygulamalarınızı) nasıl etkilediği hakkında daha fazla bilgi için bkz. [macOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="3351e-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="3351e-444">libgdiplus</span></span>

<span data-ttu-id="3351e-445">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3351e-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="3351e-446">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3351e-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="3351e-447">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="3351e-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="3351e-448">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3351e-448">Next steps</span></span>

- <span data-ttu-id="3351e-449">Uygulama geliştirmek ve çalıştırmak için, [.NET Core SDK](sdk.md) (çalışma zamanını içerir).</span><span class="sxs-lookup"><span data-stu-id="3351e-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="3351e-450">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma zamanı](runtime.md)'nı yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="3351e-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
