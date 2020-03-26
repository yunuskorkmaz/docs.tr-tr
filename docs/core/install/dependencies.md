---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları - .NET Core
description: .NET Core SDK'yı ve Windows, Linux ve macOS'ta çalışma süresini yüklemek için işletim sistemi ve CPU mimarisi ön koşulları ayrıntılarıyla anlatılmaktadır.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546568"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="dfb05-103">.NET Temel bağımlılıklar ve gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfb05-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="dfb05-104">Bu makalede, işletim sistemleri ve CPU mimarisi .NET Core tarafından desteklenen ayrıntılar.</span><span class="sxs-lookup"><span data-stu-id="dfb05-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="dfb05-105">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="dfb05-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="dfb05-106">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="dfb05-107">Aşağıdaki Windows sürümleri .NET Core 3.1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-108">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-109">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-109">OS</span></span>                            | <span data-ttu-id="dfb05-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-110">Version</span></span>                        | <span data-ttu-id="dfb05-111">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfb05-112">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="dfb05-112">Windows Client</span></span>                | <span data-ttu-id="dfb05-113">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfb05-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-114">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-115">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="dfb05-115">Windows 10 Client</span></span>             | <span data-ttu-id="dfb05-116">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="dfb05-116">Version 1607+</span></span>                  | <span data-ttu-id="dfb05-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-117">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfb05-118">Windows Server</span></span>                | <span data-ttu-id="dfb05-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-119">2012 R2+</span></span>                       | <span data-ttu-id="dfb05-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-120">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-121">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="dfb05-121">Nano Server</span></span>                   | <span data-ttu-id="dfb05-122">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="dfb05-122">Version 1803+</span></span>                  | <span data-ttu-id="dfb05-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-123">x64, ARM32</span></span>      |

<span data-ttu-id="dfb05-124">.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="dfb05-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dfb05-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="dfb05-126">*.NET Core 3.0 şu anda destek değil. Daha fazla bilgi için [.NET Çekirdek Destek Politikası'na](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.*</span><span class="sxs-lookup"><span data-stu-id="dfb05-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfb05-127">Aşağıdaki Windows sürümleri .NET Core 3.0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-128">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-129">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-129">OS</span></span>                            | <span data-ttu-id="dfb05-130">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-130">Version</span></span>                        | <span data-ttu-id="dfb05-131">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfb05-132">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="dfb05-132">Windows Client</span></span>                | <span data-ttu-id="dfb05-133">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfb05-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-134">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-135">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="dfb05-135">Windows 10 Client</span></span>             | <span data-ttu-id="dfb05-136">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="dfb05-136">Version 1607+</span></span>                  | <span data-ttu-id="dfb05-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-137">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfb05-138">Windows Server</span></span>                | <span data-ttu-id="dfb05-139">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-139">2012 R2+</span></span>                       | <span data-ttu-id="dfb05-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-140">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-141">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="dfb05-141">Nano Server</span></span>                   | <span data-ttu-id="dfb05-142">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="dfb05-142">Version 1803+</span></span>                  | <span data-ttu-id="dfb05-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-143">x64, ARM32</span></span>      |

<span data-ttu-id="dfb05-144">.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="dfb05-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="dfb05-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dfb05-146">*.NET Core 2.2 şu anda destek değil. Daha fazla bilgi için [.NET Çekirdek Destek Politikası'na](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.*</span><span class="sxs-lookup"><span data-stu-id="dfb05-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfb05-147">Aşağıdaki Windows sürümleri .NET Core 2.2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-148">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-149">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-149">OS</span></span>                            | <span data-ttu-id="dfb05-150">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-150">Version</span></span>                        | <span data-ttu-id="dfb05-151">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfb05-152">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="dfb05-152">Windows Client</span></span>                | <span data-ttu-id="dfb05-153">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfb05-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-154">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-155">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="dfb05-155">Windows 10 Client</span></span>             | <span data-ttu-id="dfb05-156">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="dfb05-156">Version 1607+</span></span>                  | <span data-ttu-id="dfb05-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-157">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfb05-158">Windows Server</span></span>                | <span data-ttu-id="dfb05-159">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="dfb05-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="dfb05-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-160">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-161">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="dfb05-161">Nano Server</span></span>                   | <span data-ttu-id="dfb05-162">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="dfb05-162">Version 1803+</span></span>                   | <span data-ttu-id="dfb05-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-163">x64, ARM32</span></span>      |

<span data-ttu-id="dfb05-164">.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="dfb05-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dfb05-166">Aşağıdaki Windows sürümleri .NET Core 2.1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-167">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-168">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-168">OS</span></span>                            | <span data-ttu-id="dfb05-169">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-169">Version</span></span>                        | <span data-ttu-id="dfb05-170">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfb05-171">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="dfb05-171">Windows Client</span></span>                | <span data-ttu-id="dfb05-172">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfb05-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-173">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-174">Windows 10 İstemci</span><span class="sxs-lookup"><span data-stu-id="dfb05-174">Windows 10 Client</span></span>             | <span data-ttu-id="dfb05-175">Sürüm 1607+</span><span class="sxs-lookup"><span data-stu-id="dfb05-175">Version 1607+</span></span>                  | <span data-ttu-id="dfb05-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-176">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfb05-177">Windows Server</span></span>                | <span data-ttu-id="dfb05-178">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="dfb05-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="dfb05-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfb05-179">x64, x86</span></span>        |
| <span data-ttu-id="dfb05-180">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="dfb05-180">Nano Server</span></span>                   | <span data-ttu-id="dfb05-181">Sürüm 1803+</span><span class="sxs-lookup"><span data-stu-id="dfb05-181">Version 1803+</span></span>                  | <span data-ttu-id="dfb05-182">x64,</span><span class="sxs-lookup"><span data-stu-id="dfb05-182">x64,</span></span>            |

<span data-ttu-id="dfb05-183">.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="dfb05-184">Windows 7 / Vista / 8.1 / Sunucu 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dfb05-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="dfb05-185">.NET SDK'yı veya çalışma süresini aşağıdaki Windows sürümlerine yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="dfb05-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="dfb05-186">Windows 7 SP1</span></span>
- <span data-ttu-id="dfb05-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="dfb05-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="dfb05-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-188">Windows 8.1</span></span>
- <span data-ttu-id="dfb05-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dfb05-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="dfb05-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dfb05-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="dfb05-191">Aşağıdakileri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="dfb05-191">Install the following:</span></span>

- <span data-ttu-id="dfb05-192">[Microsoft Visual C++ 2015 Yeniden Dağıtılabilir Güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="dfb05-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="dfb05-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="dfb05-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="dfb05-194">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="dfb05-195">*Api-ms-win-crt-runtime-l1-1-0.dll* bilgisayarınızdan eksik olduğu için program başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="dfb05-196">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="dfb05-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="dfb05-197">\-veya -</span><span class="sxs-lookup"><span data-stu-id="dfb05-197">\- or -</span></span>
>
> <span data-ttu-id="dfb05-198">Kütüphane *hostfxr.dll* bulundu, ancak *C\\\<yükleme: \\path_to_app>hostfxr.dll* başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="dfb05-198">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="dfb05-199">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-199">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="dfb05-200">.NET Core 3.1, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="dfb05-200">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfb05-201">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="dfb05-201">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfb05-202">.NET Core 3.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-202">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-203">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-203">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-204">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-204">OS</span></span>                             | <span data-ttu-id="dfb05-205">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-205">Version</span></span>               | <span data-ttu-id="dfb05-206">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-206">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="dfb05-207">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-207">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="dfb05-208">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfb05-208">6, 7, 8</span></span>               | <span data-ttu-id="dfb05-209">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-209">x64</span></span> |
| <span data-ttu-id="dfb05-210">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfb05-210">CentOS</span></span>                         | <span data-ttu-id="dfb05-211">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-211">7+</span></span>                    | <span data-ttu-id="dfb05-212">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-212">x64</span></span> |
| <span data-ttu-id="dfb05-213">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-213">Oracle Linux</span></span>                   | <span data-ttu-id="dfb05-214">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-214">7+</span></span>                    | <span data-ttu-id="dfb05-215">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-215">x64</span></span> |
| <span data-ttu-id="dfb05-216">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfb05-216">Fedora</span></span>                         | <span data-ttu-id="dfb05-217">30+</span><span class="sxs-lookup"><span data-stu-id="dfb05-217">30+</span></span>                   | <span data-ttu-id="dfb05-218">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-218">x64</span></span> |
| <span data-ttu-id="dfb05-219">Debian</span><span class="sxs-lookup"><span data-stu-id="dfb05-219">Debian</span></span>                         | <span data-ttu-id="dfb05-220">9+</span><span class="sxs-lookup"><span data-stu-id="dfb05-220">9+</span></span>                    | <span data-ttu-id="dfb05-221">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-221">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfb05-222">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb05-222">Ubuntu</span></span>                         | <span data-ttu-id="dfb05-223">16,04+</span><span class="sxs-lookup"><span data-stu-id="dfb05-223">16.04+</span></span>                | <span data-ttu-id="dfb05-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfb05-225">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="dfb05-225">Linux Mint</span></span>                     | <span data-ttu-id="dfb05-226">18+</span><span class="sxs-lookup"><span data-stu-id="dfb05-226">18+</span></span>                   | <span data-ttu-id="dfb05-227">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-227">x64</span></span> |
| <span data-ttu-id="dfb05-228">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfb05-228">openSUSE</span></span>                       | <span data-ttu-id="dfb05-229">15+</span><span class="sxs-lookup"><span data-stu-id="dfb05-229">15+</span></span>                   | <span data-ttu-id="dfb05-230">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-230">x64</span></span> |
| <span data-ttu-id="dfb05-231">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfb05-231">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="dfb05-232">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-232">12 SP2+</span></span>               | <span data-ttu-id="dfb05-233">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-233">x64</span></span> |
| <span data-ttu-id="dfb05-234">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-234">Alpine Linux</span></span>                   | <span data-ttu-id="dfb05-235">3.10+</span><span class="sxs-lookup"><span data-stu-id="dfb05-235">3.10+</span></span>                 | <span data-ttu-id="dfb05-236">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-236">x64, ARM64</span></span> |

<span data-ttu-id="dfb05-237">.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-237">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="dfb05-238">ARM64'e .NET Core 3.1'in nasıl yüklenir (çekirdek 4.14+) nasıl yüklenirhakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="dfb05-238">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfb05-239">ARM64 desteği Linux çekirdeği 4.14 veya daha yüksek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-239">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="dfb05-240">Bazı linux dağıtımları bu gereksinimi karşılarken, diğerleri bunu karşılamaz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-240">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="dfb05-241">Örneğin, Ubuntu 18.04 desteklenir, ancak Ubuntu 16.04 desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dfb05-241">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="dfb05-242">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dfb05-242">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="dfb05-243">*.NET Core 3.0 şu anda destek değil. Daha fazla bilgi için [.NET Çekirdek Destek Politikası'na](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.*</span><span class="sxs-lookup"><span data-stu-id="dfb05-243">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfb05-244">.NET Core 3.0, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="dfb05-244">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfb05-245">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="dfb05-245">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfb05-246">.NET Core 3.0 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-246">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-247">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-247">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-248">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-248">OS</span></span>                             | <span data-ttu-id="dfb05-249">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-249">Version</span></span>               | <span data-ttu-id="dfb05-250">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-250">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="dfb05-251">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-251">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="dfb05-252">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfb05-252">6, 7, 8</span></span>               | <span data-ttu-id="dfb05-253">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-253">x64</span></span> |
| <span data-ttu-id="dfb05-254">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfb05-254">CentOS</span></span>                         | <span data-ttu-id="dfb05-255">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-255">7+</span></span>                    | <span data-ttu-id="dfb05-256">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-256">x64</span></span> |
| <span data-ttu-id="dfb05-257">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-257">Oracle Linux</span></span>                   | <span data-ttu-id="dfb05-258">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-258">7+</span></span>                    | <span data-ttu-id="dfb05-259">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-259">x64</span></span> |
| <span data-ttu-id="dfb05-260">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfb05-260">Fedora</span></span>                         | <span data-ttu-id="dfb05-261">29+</span><span class="sxs-lookup"><span data-stu-id="dfb05-261">29+</span></span>                   | <span data-ttu-id="dfb05-262">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-262">x64</span></span> |
| <span data-ttu-id="dfb05-263">Debian</span><span class="sxs-lookup"><span data-stu-id="dfb05-263">Debian</span></span>                         | <span data-ttu-id="dfb05-264">9+</span><span class="sxs-lookup"><span data-stu-id="dfb05-264">9+</span></span>                    | <span data-ttu-id="dfb05-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfb05-266">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb05-266">Ubuntu</span></span>                         | <span data-ttu-id="dfb05-267">16,04+</span><span class="sxs-lookup"><span data-stu-id="dfb05-267">16.04+</span></span>                | <span data-ttu-id="dfb05-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfb05-269">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="dfb05-269">Linux Mint</span></span>                     | <span data-ttu-id="dfb05-270">18+</span><span class="sxs-lookup"><span data-stu-id="dfb05-270">18+</span></span>                   | <span data-ttu-id="dfb05-271">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-271">x64</span></span> |
| <span data-ttu-id="dfb05-272">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfb05-272">openSUSE</span></span>                       | <span data-ttu-id="dfb05-273">15+</span><span class="sxs-lookup"><span data-stu-id="dfb05-273">15+</span></span>                   | <span data-ttu-id="dfb05-274">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-274">x64</span></span> |
| <span data-ttu-id="dfb05-275">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfb05-275">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="dfb05-276">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-276">12 SP2+</span></span>               | <span data-ttu-id="dfb05-277">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-277">x64</span></span> |
| <span data-ttu-id="dfb05-278">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-278">Alpine Linux</span></span>                   | <span data-ttu-id="dfb05-279">3.8+</span><span class="sxs-lookup"><span data-stu-id="dfb05-279">3.8+</span></span>                  | <span data-ttu-id="dfb05-280">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfb05-280">x64, ARM64</span></span> |

<span data-ttu-id="dfb05-281">.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-281">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="dfb05-282">ARM64'e .NET Core 3.0 nasıl yüklenir hakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="dfb05-282">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="dfb05-283">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="dfb05-283">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dfb05-284">*.NET Core 2.2 şu anda destek değil. Daha fazla bilgi için [.NET Çekirdek Destek Politikası'na](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.*</span><span class="sxs-lookup"><span data-stu-id="dfb05-284">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfb05-285">.NET Core 2.2, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="dfb05-285">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfb05-286">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="dfb05-286">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfb05-287">.NET Core 2.2 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-287">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-288">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-288">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-289">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-289">OS</span></span>                             |  <span data-ttu-id="dfb05-290">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-290">Version</span></span>                |  <span data-ttu-id="dfb05-291">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-291">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="dfb05-292">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-292">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="dfb05-293">6, 7</span><span class="sxs-lookup"><span data-stu-id="dfb05-293">6, 7</span></span>                   | <span data-ttu-id="dfb05-294">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-294">x64</span></span> |
| <span data-ttu-id="dfb05-295">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfb05-295">CentOS</span></span>                         |  <span data-ttu-id="dfb05-296">7</span><span class="sxs-lookup"><span data-stu-id="dfb05-296">7</span></span>                      | <span data-ttu-id="dfb05-297">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-297">x64</span></span> |
| <span data-ttu-id="dfb05-298">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-298">Oracle Linux</span></span>                   |  <span data-ttu-id="dfb05-299">7</span><span class="sxs-lookup"><span data-stu-id="dfb05-299">7</span></span>                      | <span data-ttu-id="dfb05-300">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-300">x64</span></span> |
| <span data-ttu-id="dfb05-301">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfb05-301">Fedora</span></span>                         |  <span data-ttu-id="dfb05-302">29, 30</span><span class="sxs-lookup"><span data-stu-id="dfb05-302">29, 30</span></span>                 | <span data-ttu-id="dfb05-303">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-303">x64</span></span> |
| <span data-ttu-id="dfb05-304">Debian</span><span class="sxs-lookup"><span data-stu-id="dfb05-304">Debian</span></span>                         |  <span data-ttu-id="dfb05-305">9</span><span class="sxs-lookup"><span data-stu-id="dfb05-305">9</span></span>                      | <span data-ttu-id="dfb05-306">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-306">x64, ARM32</span></span> |
| <span data-ttu-id="dfb05-307">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb05-307">Ubuntu</span></span>                         |  <span data-ttu-id="dfb05-308">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="dfb05-308">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="dfb05-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-309">x64, ARM32</span></span> |
| <span data-ttu-id="dfb05-310">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="dfb05-310">Linux Mint</span></span>                     |  <span data-ttu-id="dfb05-311">17, 18</span><span class="sxs-lookup"><span data-stu-id="dfb05-311">17, 18</span></span>                 | <span data-ttu-id="dfb05-312">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-312">x64</span></span> |
| <span data-ttu-id="dfb05-313">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfb05-313">openSUSE</span></span>                       |  <span data-ttu-id="dfb05-314">15+</span><span class="sxs-lookup"><span data-stu-id="dfb05-314">15+</span></span>                    | <span data-ttu-id="dfb05-315">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-315">x64</span></span> |
| <span data-ttu-id="dfb05-316">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfb05-316">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="dfb05-317">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-317">12 SP2+</span></span>                | <span data-ttu-id="dfb05-318">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-318">x64</span></span> |
| <span data-ttu-id="dfb05-319">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-319">Alpine Linux</span></span>                   |  <span data-ttu-id="dfb05-320">3.8+</span><span class="sxs-lookup"><span data-stu-id="dfb05-320">3.8+</span></span>                   | <span data-ttu-id="dfb05-321">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-321">x64</span></span> |

<span data-ttu-id="dfb05-322">.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-322">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="dfb05-323">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-323">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dfb05-324">.NET Core 2.1, Linux'u tek bir işletim sistemi olarak ele alıyor.</span><span class="sxs-lookup"><span data-stu-id="dfb05-324">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfb05-325">Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.</span><span class="sxs-lookup"><span data-stu-id="dfb05-325">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfb05-326">.NET Core 2.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-326">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-327">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-327">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-328">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="dfb05-328">OS</span></span>                             |  <span data-ttu-id="dfb05-329">Sürüm</span><span class="sxs-lookup"><span data-stu-id="dfb05-329">Version</span></span>                |  <span data-ttu-id="dfb05-330">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-330">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="dfb05-331">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-331">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="dfb05-332">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfb05-332">6, 7, 8</span></span>                | <span data-ttu-id="dfb05-333">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-333">x64</span></span> |
| <span data-ttu-id="dfb05-334">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfb05-334">CentOS</span></span>                         |  <span data-ttu-id="dfb05-335">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-335">7+</span></span>                     | <span data-ttu-id="dfb05-336">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-336">x64</span></span> |
| <span data-ttu-id="dfb05-337">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-337">Oracle Linux</span></span>                   |  <span data-ttu-id="dfb05-338">7+</span><span class="sxs-lookup"><span data-stu-id="dfb05-338">7+</span></span>                     | <span data-ttu-id="dfb05-339">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-339">x64</span></span> |
| <span data-ttu-id="dfb05-340">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfb05-340">Fedora</span></span>                         |  <span data-ttu-id="dfb05-341">30+</span><span class="sxs-lookup"><span data-stu-id="dfb05-341">30+</span></span>                    | <span data-ttu-id="dfb05-342">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-342">x64</span></span> |
| <span data-ttu-id="dfb05-343">Debian</span><span class="sxs-lookup"><span data-stu-id="dfb05-343">Debian</span></span>                         |  <span data-ttu-id="dfb05-344">9</span><span class="sxs-lookup"><span data-stu-id="dfb05-344">9</span></span>                      | <span data-ttu-id="dfb05-345">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-345">x64, ARM32</span></span> |
| <span data-ttu-id="dfb05-346">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb05-346">Ubuntu</span></span>                         |  <span data-ttu-id="dfb05-347">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="dfb05-347">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="dfb05-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfb05-348">x64, ARM32</span></span> |
| <span data-ttu-id="dfb05-349">Linux Darphane</span><span class="sxs-lookup"><span data-stu-id="dfb05-349">Linux Mint</span></span>                     |  <span data-ttu-id="dfb05-350">17+</span><span class="sxs-lookup"><span data-stu-id="dfb05-350">17+</span></span>                    | <span data-ttu-id="dfb05-351">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-351">x64</span></span> |
| <span data-ttu-id="dfb05-352">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfb05-352">openSUSE</span></span>                       |  <span data-ttu-id="dfb05-353">15+</span><span class="sxs-lookup"><span data-stu-id="dfb05-353">15+</span></span>                    | <span data-ttu-id="dfb05-354">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-354">x64</span></span> |
| <span data-ttu-id="dfb05-355">SUSE Kurumsal Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfb05-355">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="dfb05-356">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="dfb05-356">12 SP2+</span></span>                | <span data-ttu-id="dfb05-357">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-357">x64</span></span> |
| <span data-ttu-id="dfb05-358">Alp Linux</span><span class="sxs-lookup"><span data-stu-id="dfb05-358">Alpine Linux</span></span>                   |  <span data-ttu-id="dfb05-359">3.8+</span><span class="sxs-lookup"><span data-stu-id="dfb05-359">3.8+</span></span>                   | <span data-ttu-id="dfb05-360">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-360">x64</span></span> |

<span data-ttu-id="dfb05-361">.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-361">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="dfb05-362">Linux dağıtım bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="dfb05-362">Linux distribution dependencies</span></span>

<span data-ttu-id="dfb05-363">Linux dağıtımınıza bağlı olarak, ek bağımlılıklar yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-363">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfb05-364">Tam sürümleri ve adları tercih Linux dağıtımı biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-364">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="dfb05-365">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb05-365">Ubuntu</span></span>

<span data-ttu-id="dfb05-366">Ubuntu dağılımları, aşağıdaki kitaplıkların yüklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-366">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="dfb05-367">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="dfb05-367">liblttng-ust0</span></span>
- <span data-ttu-id="dfb05-368">libcurl3 (14.x ve 16.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-368">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="dfb05-369">libcurl4 (18.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-369">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="dfb05-370">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="dfb05-370">libssl1.0.0</span></span>
- <span data-ttu-id="dfb05-371">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="dfb05-371">libkrb5-3</span></span>
- <span data-ttu-id="dfb05-372">zlib1g</span><span class="sxs-lookup"><span data-stu-id="dfb05-372">zlib1g</span></span>
- <span data-ttu-id="dfb05-373">libicu52 (14.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-373">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="dfb05-374">libicu55 (16.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-374">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="dfb05-375">libicu57 (17.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-375">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="dfb05-376">libicu60 (18.x için)</span><span class="sxs-lookup"><span data-stu-id="dfb05-376">libicu60 (for 18.x)</span></span>

<span data-ttu-id="dfb05-377">*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-377">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="dfb05-378">libgdiplus (sürüm 6.0.1 veya sonrası)</span><span class="sxs-lookup"><span data-stu-id="dfb05-378">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="dfb05-379">Ubuntu çoğu sürümleri libgdiplus önceki bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-379">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="dfb05-380">Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-380">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="dfb05-381">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="dfb05-381">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="dfb05-382">CentOS ve Fedora</span><span class="sxs-lookup"><span data-stu-id="dfb05-382">CentOS and Fedora</span></span>

<span data-ttu-id="dfb05-383">CentOS dağıtımları için aşağıdaki kitaplıklar yüklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-383">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="dfb05-384">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="dfb05-384">lttng-ust</span></span>
- <span data-ttu-id="dfb05-385">libcurl</span><span class="sxs-lookup"><span data-stu-id="dfb05-385">libcurl</span></span>
- <span data-ttu-id="dfb05-386">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="dfb05-386">openssl-libs</span></span>
- <span data-ttu-id="dfb05-387">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="dfb05-387">krb5-libs</span></span>
- <span data-ttu-id="dfb05-388">libicu</span><span class="sxs-lookup"><span data-stu-id="dfb05-388">libicu</span></span>
- <span data-ttu-id="dfb05-389">Zlib</span><span class="sxs-lookup"><span data-stu-id="dfb05-389">zlib</span></span>

<span data-ttu-id="dfb05-390">Fedora kullanıcıları: OpenSSL sürümünüz = 1.1'i >**ise, compat-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-390">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="dfb05-391">.NET Core 2.0 için aşağıdaki bağımlılıklar da gereklidir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-391">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="dfb05-392">libunwind</span><span class="sxs-lookup"><span data-stu-id="dfb05-392">libunwind</span></span>
- <span data-ttu-id="dfb05-393">libuuid</span><span class="sxs-lookup"><span data-stu-id="dfb05-393">libuuid</span></span>

<span data-ttu-id="dfb05-394">Bağımlılıklar hakkında daha fazla bilgi için, [bağımsız Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dfb05-394">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="dfb05-395">*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-395">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="dfb05-396">libgdiplus (sürüm 6.0.1 veya sonrası)</span><span class="sxs-lookup"><span data-stu-id="dfb05-396">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="dfb05-397">CentOS ve Fedora'nın çoğu sürümü nde libgdiplus'ın önceki bir sürümü yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="dfb05-397">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="dfb05-398">Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfb05-398">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="dfb05-399">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="dfb05-399">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="dfb05-400">.NET Core aşağıdaki macOS sürümlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="dfb05-400">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="dfb05-401">Bir `+` sembol minimum sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dfb05-401">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfb05-402">.NET Çekirdek Sürümü</span><span class="sxs-lookup"><span data-stu-id="dfb05-402">.NET Core Version</span></span> | <span data-ttu-id="dfb05-403">macOS</span><span class="sxs-lookup"><span data-stu-id="dfb05-403">macOS</span></span>                 | <span data-ttu-id="dfb05-404">Mimarileri</span><span class="sxs-lookup"><span data-stu-id="dfb05-404">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="dfb05-405">3.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-405">3.1</span></span>               | <span data-ttu-id="dfb05-406">Yüksek Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="dfb05-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="dfb05-407">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-407">x64</span></span> | [<span data-ttu-id="dfb05-408">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="dfb05-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="dfb05-409">3,0</span><span class="sxs-lookup"><span data-stu-id="dfb05-409">3.0</span></span>               | <span data-ttu-id="dfb05-410">Yüksek Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="dfb05-410">High Sierra (10.13+)</span></span>  | <span data-ttu-id="dfb05-411">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-411">x64</span></span> | [<span data-ttu-id="dfb05-412">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="dfb05-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="dfb05-413">2,2</span><span class="sxs-lookup"><span data-stu-id="dfb05-413">2.2</span></span>               | <span data-ttu-id="dfb05-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="dfb05-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="dfb05-415">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-415">x64</span></span> | [<span data-ttu-id="dfb05-416">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="dfb05-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="dfb05-417">2.1</span><span class="sxs-lookup"><span data-stu-id="dfb05-417">2.1</span></span>               | <span data-ttu-id="dfb05-418">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="dfb05-418">Sierra (10.12+)</span></span>       | <span data-ttu-id="dfb05-419">x64</span><span class="sxs-lookup"><span data-stu-id="dfb05-419">x64</span></span> | [<span data-ttu-id="dfb05-420">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="dfb05-420">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="dfb05-421">MacOS Catalina (sürüm 10.15) ile başlayarak, Geliştirici Kimliği ile dağıtılan 1 Haziran 2019 tarihinden sonra üretilen tüm yazılımların noter tasdikli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-421">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="dfb05-422">Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-422">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="dfb05-423">.NET Core (hem çalışma süresi hem de SDK) 3.1, 3.0 ve 2.1 sürümlerinin yükleyicileri 18 Şubat 2020'den beri noter olarak noterolarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-423">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="dfb05-424">Önceki sürümler noter onaylı değildir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-424">Prior released versions aren't notarized.</span></span> <span data-ttu-id="dfb05-425">Noter onaylı olmayan bir uygulama çalıştırıyorsanız, aşağıdaki resme benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="dfb05-425">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina noterizasyon uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="dfb05-427">Zorunlu noterizasyonun .NET Core 'u (ve .NET Core uygulamalarını) nasıl etkilediği hakkında daha fazla bilgi için [bkz.](macos-notarization-issues.md)</span><span class="sxs-lookup"><span data-stu-id="dfb05-427">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="dfb05-428">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="dfb05-428">libgdiplus</span></span>

<span data-ttu-id="dfb05-429">*.System.Drawing.Common* assembly kullanan NET Core uygulamaları libgdiplus'ın yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dfb05-429">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="dfb05-430">Libgdiplus elde etmek için kolay bir yolu macOS için [Homebrew ("brew")](https://brew.sh/) paket yöneticisi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dfb05-430">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="dfb05-431">*Brew*yükledikten sonra, terminal (komut) komut u komutu aşağıdaki komutları çalıştırarak libgdiplus yükleyin:</span><span class="sxs-lookup"><span data-stu-id="dfb05-431">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="dfb05-432">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dfb05-432">Next steps</span></span>

- <span data-ttu-id="dfb05-433">Uygulamaları geliştirmek ve çalıştırmak için [.NET Core SDK'yı](sdk.md) (çalışma süresini içerir) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dfb05-433">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="dfb05-434">Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma süresini](runtime.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dfb05-434">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
