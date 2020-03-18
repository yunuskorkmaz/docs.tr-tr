---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları - .NET Core
description: .NET Core SDK'yı ve Windows, Linux ve macOS'ta çalışma süresini yüklemek için işletim sistemi ve CPU mimarisi ön koşulları ayrıntılarıyla anlatılmaktadır.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157822"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="a1f0f-103">.NET Temel bağımlılıklar ve gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1f0f-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="a1f0f-104">Bu makalede, işletim sistemleri ve CPU mimarisi .NET Core tarafından desteklenen ayrıntılar.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a1f0f-105">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="a1f0f-106">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="a1f0f-107">Aşağıdaki Windows sürümleri .NET Core 3.1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-108">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-109">OS</span></span>                            | <span data-ttu-id="a1f0f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-110">Version</span></span>                        | <span data-ttu-id="a1f0f-111">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a1f0f-112">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-112">Windows Client</span></span>                | <span data-ttu-id="a1f0f-113">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a1f0f-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-114">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-115">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="a1f0f-115">Windows 10 Client</span></span>             | <span data-ttu-id="a1f0f-116">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-116">Version 1607+</span></span>                  | <span data-ttu-id="a1f0f-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-117">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a1f0f-118">Windows Server</span></span>                | <span data-ttu-id="a1f0f-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-119">2012 R2+</span></span>                       | <span data-ttu-id="a1f0f-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-120">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-121">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-121">Nano Server</span></span>                   | <span data-ttu-id="a1f0f-122">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-122">Version 1803+</span></span>                  | <span data-ttu-id="a1f0f-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-123">x64, ARM32</span></span>      |

<span data-ttu-id="a1f0f-124">.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="a1f0f-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a1f0f-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="a1f0f-126">Aşağıdaki Windows sürümleri .NET Core 3.0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-127">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-128">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-128">OS</span></span>                            | <span data-ttu-id="a1f0f-129">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-129">Version</span></span>                        | <span data-ttu-id="a1f0f-130">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a1f0f-131">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-131">Windows Client</span></span>                | <span data-ttu-id="a1f0f-132">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a1f0f-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-133">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-134">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="a1f0f-134">Windows 10 Client</span></span>             | <span data-ttu-id="a1f0f-135">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-135">Version 1607+</span></span>                  | <span data-ttu-id="a1f0f-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-136">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a1f0f-137">Windows Server</span></span>                | <span data-ttu-id="a1f0f-138">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-138">2012 R2+</span></span>                       | <span data-ttu-id="a1f0f-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-139">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-140">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-140">Nano Server</span></span>                   | <span data-ttu-id="a1f0f-141">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-141">Version 1803+</span></span>                  | <span data-ttu-id="a1f0f-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-142">x64, ARM32</span></span>      |

<span data-ttu-id="a1f0f-143">.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="a1f0f-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="a1f0f-145">Aşağıdaki Windows sürümleri .NET Core 2.2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-146">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-147">OS</span></span>                            | <span data-ttu-id="a1f0f-148">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-148">Version</span></span>                        | <span data-ttu-id="a1f0f-149">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a1f0f-150">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-150">Windows Client</span></span>                | <span data-ttu-id="a1f0f-151">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a1f0f-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-152">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-153">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="a1f0f-153">Windows 10 Client</span></span>             | <span data-ttu-id="a1f0f-154">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-154">Version 1607+</span></span>                  | <span data-ttu-id="a1f0f-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-155">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a1f0f-156">Windows Server</span></span>                | <span data-ttu-id="a1f0f-157">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="a1f0f-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-158">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-159">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-159">Nano Server</span></span>                   | <span data-ttu-id="a1f0f-160">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-160">Version 1803+</span></span>                   | <span data-ttu-id="a1f0f-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-161">x64, ARM32</span></span>      |

<span data-ttu-id="a1f0f-162">.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a1f0f-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a1f0f-164">Aşağıdaki Windows sürümleri .NET Core 2.1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-165">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-166">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-166">OS</span></span>                            | <span data-ttu-id="a1f0f-167">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-167">Version</span></span>                        | <span data-ttu-id="a1f0f-168">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="a1f0f-169">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-169">Windows Client</span></span>                | <span data-ttu-id="a1f0f-170">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="a1f0f-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-171">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-172">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="a1f0f-172">Windows 10 Client</span></span>             | <span data-ttu-id="a1f0f-173">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-173">Version 1607+</span></span>                  | <span data-ttu-id="a1f0f-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-174">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="a1f0f-175">Windows Server</span></span>                | <span data-ttu-id="a1f0f-176">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="a1f0f-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="a1f0f-177">x64, x86</span></span>        |
| <span data-ttu-id="a1f0f-178">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-178">Nano Server</span></span>                   | <span data-ttu-id="a1f0f-179">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-179">Version 1803+</span></span>                  | <span data-ttu-id="a1f0f-180">x64,</span><span class="sxs-lookup"><span data-stu-id="a1f0f-180">x64,</span></span>            |

<span data-ttu-id="a1f0f-181">.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="a1f0f-182">Windows 7 / Vista / 8.1 / Sunucu 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="a1f0f-183">.NET SDK'yı veya çalışma süresini aşağıdaki Windows sürümlerine yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="a1f0f-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-184">Windows 7 SP1</span></span>
- <span data-ttu-id="a1f0f-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="a1f0f-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-186">Windows 8.1</span></span>
- <span data-ttu-id="a1f0f-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="a1f0f-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="a1f0f-189">Aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-189">Install the following:</span></span>

- <span data-ttu-id="a1f0f-190">[Microsoft Visual C++ 2015 Yeniden Dağıtılabilir Güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="a1f0f-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="a1f0f-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="a1f0f-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="a1f0f-192">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="a1f0f-193">*Api-ms-win-crt-runtime-l1-1-0.dll* bilgisayarınızdan eksik olduğu için program başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="a1f0f-194">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="a1f0f-195">\-veya -</span><span class="sxs-lookup"><span data-stu-id="a1f0f-195">\- or -</span></span>
>
> <span data-ttu-id="a1f0f-196">Kütüphane *hostfxr.dll* bulundu, ancak *C\\\<yükleme: \\path_to_app>hostfxr.dll* başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="a1f0f-197">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="a1f0f-198">.NET Core 3.1, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="a1f0f-199">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a1f0f-200">.NET Core 3.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-201">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-202">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-202">OS</span></span>                             | <span data-ttu-id="a1f0f-203">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-203">Version</span></span>               | <span data-ttu-id="a1f0f-204">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="a1f0f-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="a1f0f-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a1f0f-206">6, 7, 8</span></span>               | <span data-ttu-id="a1f0f-207">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-207">x64</span></span> |
| <span data-ttu-id="a1f0f-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="a1f0f-208">CentOS</span></span>                         | <span data-ttu-id="a1f0f-209">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-209">7+</span></span>                    | <span data-ttu-id="a1f0f-210">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-210">x64</span></span> |
| <span data-ttu-id="a1f0f-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-211">Oracle Linux</span></span>                   | <span data-ttu-id="a1f0f-212">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-212">7+</span></span>                    | <span data-ttu-id="a1f0f-213">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-213">x64</span></span> |
| <span data-ttu-id="a1f0f-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="a1f0f-214">Fedora</span></span>                         | <span data-ttu-id="a1f0f-215">29+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-215">29+</span></span>                   | <span data-ttu-id="a1f0f-216">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-216">x64</span></span> |
| <span data-ttu-id="a1f0f-217">Debian</span><span class="sxs-lookup"><span data-stu-id="a1f0f-217">Debian</span></span>                         | <span data-ttu-id="a1f0f-218">9+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-218">9+</span></span>                    | <span data-ttu-id="a1f0f-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a1f0f-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-220">Ubuntu</span></span>                         | <span data-ttu-id="a1f0f-221">16,04+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-221">16.04+</span></span>                | <span data-ttu-id="a1f0f-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a1f0f-223">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="a1f0f-223">Linux Mint</span></span>                     | <span data-ttu-id="a1f0f-224">18+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-224">18+</span></span>                   | <span data-ttu-id="a1f0f-225">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-225">x64</span></span> |
| <span data-ttu-id="a1f0f-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a1f0f-226">openSUSE</span></span>                       | <span data-ttu-id="a1f0f-227">15+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-227">15+</span></span>                   | <span data-ttu-id="a1f0f-228">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-228">x64</span></span> |
| <span data-ttu-id="a1f0f-229">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="a1f0f-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-230">12 SP2+</span></span>               | <span data-ttu-id="a1f0f-231">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-231">x64</span></span> |
| <span data-ttu-id="a1f0f-232">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-232">Alpine Linux</span></span>                   | <span data-ttu-id="a1f0f-233">3.10+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-233">3.10+</span></span>                 | <span data-ttu-id="a1f0f-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-234">x64, ARM64</span></span> |

<span data-ttu-id="a1f0f-235">.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="a1f0f-236">ARM64'e .NET Core 3.1'in nasıl yüklenir (çekirdek 4.14+) nasıl yüklenirhakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1f0f-237">ARM64 desteği Linux çekirdeği 4.14 veya daha yüksek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="a1f0f-238">Bazı linux dağıtımları bu gereksinimi karşılarken, diğerleri bunu karşılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="a1f0f-239">Örneğin, Ubuntu 18.04 desteklenir, ancak Ubuntu 16.04 desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="a1f0f-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a1f0f-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="a1f0f-241">.NET Core 3.0, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="a1f0f-242">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a1f0f-243">.NET Core 3.0 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-244">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-245">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-245">OS</span></span>                             | <span data-ttu-id="a1f0f-246">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-246">Version</span></span>               | <span data-ttu-id="a1f0f-247">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="a1f0f-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="a1f0f-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a1f0f-249">6, 7, 8</span></span>               | <span data-ttu-id="a1f0f-250">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-250">x64</span></span> |
| <span data-ttu-id="a1f0f-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="a1f0f-251">CentOS</span></span>                         | <span data-ttu-id="a1f0f-252">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-252">7+</span></span>                    | <span data-ttu-id="a1f0f-253">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-253">x64</span></span> |
| <span data-ttu-id="a1f0f-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-254">Oracle Linux</span></span>                   | <span data-ttu-id="a1f0f-255">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-255">7+</span></span>                    | <span data-ttu-id="a1f0f-256">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-256">x64</span></span> |
| <span data-ttu-id="a1f0f-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="a1f0f-257">Fedora</span></span>                         | <span data-ttu-id="a1f0f-258">29+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-258">29+</span></span>                   | <span data-ttu-id="a1f0f-259">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-259">x64</span></span> |
| <span data-ttu-id="a1f0f-260">Debian</span><span class="sxs-lookup"><span data-stu-id="a1f0f-260">Debian</span></span>                         | <span data-ttu-id="a1f0f-261">9+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-261">9+</span></span>                    | <span data-ttu-id="a1f0f-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a1f0f-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-263">Ubuntu</span></span>                         | <span data-ttu-id="a1f0f-264">16,04+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-264">16.04+</span></span>                | <span data-ttu-id="a1f0f-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="a1f0f-266">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="a1f0f-266">Linux Mint</span></span>                     | <span data-ttu-id="a1f0f-267">18+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-267">18+</span></span>                   | <span data-ttu-id="a1f0f-268">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-268">x64</span></span> |
| <span data-ttu-id="a1f0f-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a1f0f-269">openSUSE</span></span>                       | <span data-ttu-id="a1f0f-270">15+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-270">15+</span></span>                   | <span data-ttu-id="a1f0f-271">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-271">x64</span></span> |
| <span data-ttu-id="a1f0f-272">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="a1f0f-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-273">12 SP2+</span></span>               | <span data-ttu-id="a1f0f-274">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-274">x64</span></span> |
| <span data-ttu-id="a1f0f-275">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-275">Alpine Linux</span></span>                   | <span data-ttu-id="a1f0f-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-276">3.8+</span></span>                  | <span data-ttu-id="a1f0f-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-277">x64, ARM64</span></span> |

<span data-ttu-id="a1f0f-278">.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="a1f0f-279">ARM64'e .NET Core 3.0 nasıl yüklenir hakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="a1f0f-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="a1f0f-281">.NET Core 2.2, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="a1f0f-282">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a1f0f-283">.NET Core 2.2 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-284">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-285">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-285">OS</span></span>                             |  <span data-ttu-id="a1f0f-286">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-286">Version</span></span>                |  <span data-ttu-id="a1f0f-287">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="a1f0f-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="a1f0f-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="a1f0f-289">6, 7</span></span>                   | <span data-ttu-id="a1f0f-290">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-290">x64</span></span> |
| <span data-ttu-id="a1f0f-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="a1f0f-291">CentOS</span></span>                         |  <span data-ttu-id="a1f0f-292">7</span><span class="sxs-lookup"><span data-stu-id="a1f0f-292">7</span></span>                      | <span data-ttu-id="a1f0f-293">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-293">x64</span></span> |
| <span data-ttu-id="a1f0f-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-294">Oracle Linux</span></span>                   |  <span data-ttu-id="a1f0f-295">7</span><span class="sxs-lookup"><span data-stu-id="a1f0f-295">7</span></span>                      | <span data-ttu-id="a1f0f-296">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-296">x64</span></span> |
| <span data-ttu-id="a1f0f-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="a1f0f-297">Fedora</span></span>                         |  <span data-ttu-id="a1f0f-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="a1f0f-298">29, 30</span></span>                 | <span data-ttu-id="a1f0f-299">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-299">x64</span></span> |
| <span data-ttu-id="a1f0f-300">Debian</span><span class="sxs-lookup"><span data-stu-id="a1f0f-300">Debian</span></span>                         |  <span data-ttu-id="a1f0f-301">9</span><span class="sxs-lookup"><span data-stu-id="a1f0f-301">9</span></span>                      | <span data-ttu-id="a1f0f-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-302">x64, ARM32</span></span> |
| <span data-ttu-id="a1f0f-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-303">Ubuntu</span></span>                         |  <span data-ttu-id="a1f0f-304">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="a1f0f-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="a1f0f-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-305">x64, ARM32</span></span> |
| <span data-ttu-id="a1f0f-306">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="a1f0f-306">Linux Mint</span></span>                     |  <span data-ttu-id="a1f0f-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="a1f0f-307">17, 18</span></span>                 | <span data-ttu-id="a1f0f-308">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-308">x64</span></span> |
| <span data-ttu-id="a1f0f-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a1f0f-309">openSUSE</span></span>                       |  <span data-ttu-id="a1f0f-310">15+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-310">15+</span></span>                    | <span data-ttu-id="a1f0f-311">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-311">x64</span></span> |
| <span data-ttu-id="a1f0f-312">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="a1f0f-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-313">12 SP2+</span></span>                | <span data-ttu-id="a1f0f-314">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-314">x64</span></span> |
| <span data-ttu-id="a1f0f-315">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-315">Alpine Linux</span></span>                   |  <span data-ttu-id="a1f0f-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-316">3.8+</span></span>                   | <span data-ttu-id="a1f0f-317">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-317">x64</span></span> |

<span data-ttu-id="a1f0f-318">.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="a1f0f-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a1f0f-320">.NET Core 2.1, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="a1f0f-321">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="a1f0f-322">.NET Core 2.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-323">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-324">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-324">OS</span></span>                             |  <span data-ttu-id="a1f0f-325">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a1f0f-325">Version</span></span>                |  <span data-ttu-id="a1f0f-326">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="a1f0f-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="a1f0f-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="a1f0f-328">6, 7, 8</span></span>                | <span data-ttu-id="a1f0f-329">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-329">x64</span></span> |
| <span data-ttu-id="a1f0f-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="a1f0f-330">CentOS</span></span>                         |  <span data-ttu-id="a1f0f-331">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-331">7+</span></span>                     | <span data-ttu-id="a1f0f-332">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-332">x64</span></span> |
| <span data-ttu-id="a1f0f-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-333">Oracle Linux</span></span>                   |  <span data-ttu-id="a1f0f-334">7+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-334">7+</span></span>                     | <span data-ttu-id="a1f0f-335">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-335">x64</span></span> |
| <span data-ttu-id="a1f0f-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="a1f0f-336">Fedora</span></span>                         |  <span data-ttu-id="a1f0f-337">29+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-337">29+</span></span>                    | <span data-ttu-id="a1f0f-338">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-338">x64</span></span> |
| <span data-ttu-id="a1f0f-339">Debian</span><span class="sxs-lookup"><span data-stu-id="a1f0f-339">Debian</span></span>                         |  <span data-ttu-id="a1f0f-340">9</span><span class="sxs-lookup"><span data-stu-id="a1f0f-340">9</span></span>                      | <span data-ttu-id="a1f0f-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-341">x64, ARM32</span></span> |
| <span data-ttu-id="a1f0f-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-342">Ubuntu</span></span>                         |  <span data-ttu-id="a1f0f-343">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="a1f0f-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="a1f0f-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="a1f0f-344">x64, ARM32</span></span> |
| <span data-ttu-id="a1f0f-345">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="a1f0f-345">Linux Mint</span></span>                     |  <span data-ttu-id="a1f0f-346">17+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-346">17+</span></span>                    | <span data-ttu-id="a1f0f-347">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-347">x64</span></span> |
| <span data-ttu-id="a1f0f-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="a1f0f-348">openSUSE</span></span>                       |  <span data-ttu-id="a1f0f-349">15+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-349">15+</span></span>                    | <span data-ttu-id="a1f0f-350">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-350">x64</span></span> |
| <span data-ttu-id="a1f0f-351">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="a1f0f-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-352">12 SP2+</span></span>                | <span data-ttu-id="a1f0f-353">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-353">x64</span></span> |
| <span data-ttu-id="a1f0f-354">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="a1f0f-354">Alpine Linux</span></span>                   |  <span data-ttu-id="a1f0f-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="a1f0f-355">3.8+</span></span>                   | <span data-ttu-id="a1f0f-356">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-356">x64</span></span> |

<span data-ttu-id="a1f0f-357">.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="a1f0f-358">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="a1f0f-358">Linux distribution dependencies</span></span>

<span data-ttu-id="a1f0f-359">Linux dağıtımınıza bağlı olarak, ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1f0f-360">Tam sürümleri ve adları tercih Linux dağıtımı biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="a1f0f-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-361">Ubuntu</span></span>

<span data-ttu-id="a1f0f-362">Ubuntu dağılımları, aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="a1f0f-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="a1f0f-363">liblttng-ust0</span></span>
- <span data-ttu-id="a1f0f-364">libcurl3 (14.x ve 16.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="a1f0f-365">libcurl4 (18.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="a1f0f-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="a1f0f-366">libssl1.0.0</span></span>
- <span data-ttu-id="a1f0f-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="a1f0f-367">libkrb5-3</span></span>
- <span data-ttu-id="a1f0f-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="a1f0f-368">zlib1g</span></span>
- <span data-ttu-id="a1f0f-369">libicu52 (14.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="a1f0f-370">libicu55 (16.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="a1f0f-371">libicu57 (17.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="a1f0f-372">libicu60 (18.x için)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="a1f0f-373">*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="a1f0f-374">libgdiplus (sürüm 6.0.1 veya sonrası)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="a1f0f-375">Ubuntu çoğu sürümleri libgdiplus önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="a1f0f-376">Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="a1f0f-377">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="a1f0f-378">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="a1f0f-378">CentOS and Fedora</span></span>

<span data-ttu-id="a1f0f-379">CentOS dağıtımları için aşağıdaki kitaplıklar yüklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="a1f0f-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="a1f0f-380">lttng-ust</span></span>
- <span data-ttu-id="a1f0f-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="a1f0f-381">libcurl</span></span>
- <span data-ttu-id="a1f0f-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="a1f0f-382">openssl-libs</span></span>
- <span data-ttu-id="a1f0f-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="a1f0f-383">krb5-libs</span></span>
- <span data-ttu-id="a1f0f-384">libicu</span><span class="sxs-lookup"><span data-stu-id="a1f0f-384">libicu</span></span>
- <span data-ttu-id="a1f0f-385">Zlib</span><span class="sxs-lookup"><span data-stu-id="a1f0f-385">zlib</span></span>

<span data-ttu-id="a1f0f-386">Fedora kullanıcıları: OpenSSL sürümünüz = 1.1'i >**ise, compat-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="a1f0f-387">.NET Core 2.0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="a1f0f-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="a1f0f-388">libunwind</span></span>
- <span data-ttu-id="a1f0f-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="a1f0f-389">libuuid</span></span>

<span data-ttu-id="a1f0f-390">Bağımlılıklar hakkında daha fazla bilgi için, [bağımsız Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="a1f0f-391">*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="a1f0f-392">libgdiplus (sürüm 6.0.1 veya sonrası)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="a1f0f-393">CentOS ve Fedora'nın çoğu sürümü nde libgdiplus'ın önceki bir sürümü yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="a1f0f-394">Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="a1f0f-395">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="a1f0f-396">.NET Core aşağıdaki macOS sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="a1f0f-397">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="a1f0f-398">.NET Çekirdek Sürümü</span><span class="sxs-lookup"><span data-stu-id="a1f0f-398">.NET Core Version</span></span> | <span data-ttu-id="a1f0f-399">macOS</span><span class="sxs-lookup"><span data-stu-id="a1f0f-399">macOS</span></span>                 | <span data-ttu-id="a1f0f-400">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="a1f0f-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="a1f0f-401">3.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-401">3.1</span></span>               | <span data-ttu-id="a1f0f-402">Yüksek Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="a1f0f-403">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-403">x64</span></span> | [<span data-ttu-id="a1f0f-404">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="a1f0f-405">3,0</span><span class="sxs-lookup"><span data-stu-id="a1f0f-405">3.0</span></span>               | <span data-ttu-id="a1f0f-406">Yüksek Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="a1f0f-407">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-407">x64</span></span> | [<span data-ttu-id="a1f0f-408">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="a1f0f-409">2,2</span><span class="sxs-lookup"><span data-stu-id="a1f0f-409">2.2</span></span>               | <span data-ttu-id="a1f0f-410">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="a1f0f-411">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-411">x64</span></span> | [<span data-ttu-id="a1f0f-412">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="a1f0f-413">2.1</span><span class="sxs-lookup"><span data-stu-id="a1f0f-413">2.1</span></span>               | <span data-ttu-id="a1f0f-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="a1f0f-415">x64</span><span class="sxs-lookup"><span data-stu-id="a1f0f-415">x64</span></span> | [<span data-ttu-id="a1f0f-416">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a1f0f-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="a1f0f-417">MacOS Catalina (sürüm 10.15) ile başlayarak, Geliştirici Kimliği ile dağıtılan 1 Haziran 2019 tarihinden sonra üretilen tüm yazılımların noter tasdikli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="a1f0f-418">Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="a1f0f-419">.NET Core (hem çalışma süresi hem de SDK) 3.1, 3.0 ve 2.1 sürümlerinin yükleyicileri 18 Şubat 2020'den beri noter olarak noterolarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="a1f0f-420">Önceki sürümler noter onaylı değildir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="a1f0f-421">Noter onaylı olmayan bir uygulama çalıştırıyorsanız, aşağıdaki resme benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina noterizasyon uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="a1f0f-423">Zorunlu noterizasyonun .NET Core 'u (ve .NET Core uygulamalarını) nasıl etkilediği hakkında daha fazla bilgi için [bkz.](macos-notarization-issues.md)</span><span class="sxs-lookup"><span data-stu-id="a1f0f-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="a1f0f-424">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="a1f0f-424">libgdiplus</span></span>

<span data-ttu-id="a1f0f-425">*.System.Drawing.Common* assembly kullanan NET Core uygulamaları libgdiplus'ın yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="a1f0f-426">Libgdiplus elde etmek için kolay bir yolu macOS için [Homebrew ("brew")](https://brew.sh/) paket yöneticisi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="a1f0f-427">*Brew*yükledikten sonra, terminal (komut) komut u komutu aşağıdaki komutları çalıştırarak libgdiplus yükleyin:</span><span class="sxs-lookup"><span data-stu-id="a1f0f-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="a1f0f-428">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a1f0f-428">Next steps</span></span>

- <span data-ttu-id="a1f0f-429">Uygulamaları geliştirmek ve çalıştırmak için [.NET Core SDK'yı](sdk.md) (çalışma süresini içerir) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="a1f0f-430">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma süresini](runtime.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a1f0f-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
