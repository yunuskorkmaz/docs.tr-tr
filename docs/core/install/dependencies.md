---
title: .NET Core SDK and runtime dependencies - .NET Core
description: Details the operating system and CPU architecture prerequisites to install the .NET Core SDK and runtime on Windows, Linux, and macOS.
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
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="12edf-103">.NET Core dependencies and requirements</span><span class="sxs-lookup"><span data-stu-id="12edf-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="12edf-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12edf-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="12edf-105">Supported operating systems</span><span class="sxs-lookup"><span data-stu-id="12edf-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="12edf-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12edf-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="12edf-107">The following Windows versions are supported with .NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="12edf-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-108">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-109">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-109">OS</span></span>                            | <span data-ttu-id="12edf-110">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-110">Version</span></span>                        | <span data-ttu-id="12edf-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="12edf-112">Windows Client</span><span class="sxs-lookup"><span data-stu-id="12edf-112">Windows Client</span></span>                | <span data-ttu-id="12edf-113">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="12edf-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="12edf-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-114">x64, x86</span></span>        |
| <span data-ttu-id="12edf-115">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="12edf-115">Windows 10 Client</span></span>             | <span data-ttu-id="12edf-116">Version 1607+</span><span class="sxs-lookup"><span data-stu-id="12edf-116">Version 1607+</span></span>                  | <span data-ttu-id="12edf-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-117">x64, x86</span></span>        |
| <span data-ttu-id="12edf-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="12edf-118">Windows Server</span></span>                | <span data-ttu-id="12edf-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="12edf-119">2012 R2+</span></span>                       | <span data-ttu-id="12edf-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-120">x64, x86</span></span>        |
| <span data-ttu-id="12edf-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="12edf-121">Nano Server</span></span>                   | <span data-ttu-id="12edf-122">Version 1803+</span><span class="sxs-lookup"><span data-stu-id="12edf-122">Version 1803+</span></span>                  | <span data-ttu-id="12edf-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-123">x64, ARM32</span></span>      |

<span data-ttu-id="12edf-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="12edf-125">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="12edf-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="12edf-126">The following Windows versions are supported with .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="12edf-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-127">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-128">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-128">OS</span></span>                            | <span data-ttu-id="12edf-129">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-129">Version</span></span>                        | <span data-ttu-id="12edf-130">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="12edf-131">Windows Client</span><span class="sxs-lookup"><span data-stu-id="12edf-131">Windows Client</span></span>                | <span data-ttu-id="12edf-132">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="12edf-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="12edf-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-133">x64, x86</span></span>        |
| <span data-ttu-id="12edf-134">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="12edf-134">Windows 10 Client</span></span>             | <span data-ttu-id="12edf-135">Version 1607+</span><span class="sxs-lookup"><span data-stu-id="12edf-135">Version 1607+</span></span>                  | <span data-ttu-id="12edf-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-136">x64, x86</span></span>        |
| <span data-ttu-id="12edf-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="12edf-137">Windows Server</span></span>                | <span data-ttu-id="12edf-138">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="12edf-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="12edf-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-139">x64, x86</span></span>        |
| <span data-ttu-id="12edf-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="12edf-140">Nano Server</span></span>                   | <span data-ttu-id="12edf-141">Version 1803+</span><span class="sxs-lookup"><span data-stu-id="12edf-141">Version 1803+</span></span>                   | <span data-ttu-id="12edf-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-142">x64, ARM32</span></span>      |

<span data-ttu-id="12edf-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="12edf-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="12edf-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="12edf-145">The following Windows versions are supported with .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="12edf-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-146">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-147">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-147">OS</span></span>                            | <span data-ttu-id="12edf-148">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-148">Version</span></span>                        | <span data-ttu-id="12edf-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="12edf-150">Windows Client</span><span class="sxs-lookup"><span data-stu-id="12edf-150">Windows Client</span></span>                | <span data-ttu-id="12edf-151">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="12edf-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="12edf-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-152">x64, x86</span></span>        |
| <span data-ttu-id="12edf-153">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="12edf-153">Windows 10 Client</span></span>             | <span data-ttu-id="12edf-154">Version 1607+</span><span class="sxs-lookup"><span data-stu-id="12edf-154">Version 1607+</span></span>                  | <span data-ttu-id="12edf-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-155">x64, x86</span></span>        |
| <span data-ttu-id="12edf-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="12edf-156">Windows Server</span></span>                | <span data-ttu-id="12edf-157">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="12edf-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="12edf-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="12edf-158">x64, x86</span></span>        |
| <span data-ttu-id="12edf-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="12edf-159">Nano Server</span></span>                   | <span data-ttu-id="12edf-160">Version 1803+</span><span class="sxs-lookup"><span data-stu-id="12edf-160">Version 1803+</span></span>                  | <span data-ttu-id="12edf-161">x64,</span><span class="sxs-lookup"><span data-stu-id="12edf-161">x64,</span></span>            |

<span data-ttu-id="12edf-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="12edf-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="12edf-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="12edf-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span><span class="sxs-lookup"><span data-stu-id="12edf-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="12edf-165">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="12edf-165">Windows 7 SP1</span></span>
- <span data-ttu-id="12edf-166">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="12edf-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="12edf-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="12edf-167">Windows 8.1</span></span>
- <span data-ttu-id="12edf-168">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="12edf-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="12edf-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="12edf-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="12edf-170">Install the following:</span><span class="sxs-lookup"><span data-stu-id="12edf-170">Install the following:</span></span>

- <span data-ttu-id="12edf-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="12edf-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="12edf-172">KB2533623</span><span class="sxs-lookup"><span data-stu-id="12edf-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="12edf-173">The requirements above are also required if you come across one of the following errors:</span><span class="sxs-lookup"><span data-stu-id="12edf-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="12edf-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span><span class="sxs-lookup"><span data-stu-id="12edf-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="12edf-175">Try reinstalling the program to fix this problem.</span><span class="sxs-lookup"><span data-stu-id="12edf-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="12edf-176">\- or -</span><span class="sxs-lookup"><span data-stu-id="12edf-176">\- or -</span></span>
>
> <span data-ttu-id="12edf-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span><span class="sxs-lookup"><span data-stu-id="12edf-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="12edf-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12edf-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="12edf-179">.NET Core 3.0 treats Linux as a single operating system.</span><span class="sxs-lookup"><span data-stu-id="12edf-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="12edf-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span><span class="sxs-lookup"><span data-stu-id="12edf-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="12edf-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span><span class="sxs-lookup"><span data-stu-id="12edf-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-182">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-183">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-183">OS</span></span>                             | <span data-ttu-id="12edf-184">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-184">Version</span></span>               | <span data-ttu-id="12edf-185">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="12edf-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="12edf-187">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="12edf-187">6, 7, 8</span></span>               | <span data-ttu-id="12edf-188">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-188">x64</span></span> |
| <span data-ttu-id="12edf-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="12edf-189">CentOS</span></span>                         | <span data-ttu-id="12edf-190">7+</span><span class="sxs-lookup"><span data-stu-id="12edf-190">7+</span></span>                    | <span data-ttu-id="12edf-191">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-191">x64</span></span> |
| <span data-ttu-id="12edf-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-192">Oracle Linux</span></span>                   | <span data-ttu-id="12edf-193">7+</span><span class="sxs-lookup"><span data-stu-id="12edf-193">7+</span></span>                    | <span data-ttu-id="12edf-194">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-194">x64</span></span> |
| <span data-ttu-id="12edf-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="12edf-195">Fedora</span></span>                         | <span data-ttu-id="12edf-196">29+</span><span class="sxs-lookup"><span data-stu-id="12edf-196">29+</span></span>                   | <span data-ttu-id="12edf-197">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-197">x64</span></span> |
| <span data-ttu-id="12edf-198">Debian</span><span class="sxs-lookup"><span data-stu-id="12edf-198">Debian</span></span>                         | <span data-ttu-id="12edf-199">9+</span><span class="sxs-lookup"><span data-stu-id="12edf-199">9+</span></span>                    | <span data-ttu-id="12edf-200">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="12edf-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="12edf-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12edf-201">Ubuntu</span></span>                         | <span data-ttu-id="12edf-202">16.04+</span><span class="sxs-lookup"><span data-stu-id="12edf-202">16.04+</span></span>                | <span data-ttu-id="12edf-203">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="12edf-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="12edf-204">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="12edf-204">Linux Mint</span></span>                     | <span data-ttu-id="12edf-205">18+</span><span class="sxs-lookup"><span data-stu-id="12edf-205">18+</span></span>                   | <span data-ttu-id="12edf-206">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-206">x64</span></span> |
| <span data-ttu-id="12edf-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="12edf-207">openSUSE</span></span>                       | <span data-ttu-id="12edf-208">15+</span><span class="sxs-lookup"><span data-stu-id="12edf-208">15+</span></span>                   | <span data-ttu-id="12edf-209">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-209">x64</span></span> |
| <span data-ttu-id="12edf-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="12edf-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="12edf-211">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="12edf-211">12 SP2+</span></span>               | <span data-ttu-id="12edf-212">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-212">x64</span></span> |
| <span data-ttu-id="12edf-213">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-213">Alpine Linux</span></span>                   | <span data-ttu-id="12edf-214">3.8+</span><span class="sxs-lookup"><span data-stu-id="12edf-214">3.8+</span></span>                  | <span data-ttu-id="12edf-215">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="12edf-215">x64, ARM64</span></span> |

<span data-ttu-id="12edf-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="12edf-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="12edf-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="12edf-218">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="12edf-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="12edf-219">.NET Core 2.2 treats Linux as a single operating system.</span><span class="sxs-lookup"><span data-stu-id="12edf-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="12edf-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span><span class="sxs-lookup"><span data-stu-id="12edf-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="12edf-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span><span class="sxs-lookup"><span data-stu-id="12edf-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-222">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-223">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-223">OS</span></span>                             |  <span data-ttu-id="12edf-224">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-224">Version</span></span>                |  <span data-ttu-id="12edf-225">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="12edf-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="12edf-227">6, 7</span><span class="sxs-lookup"><span data-stu-id="12edf-227">6, 7</span></span>                   | <span data-ttu-id="12edf-228">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-228">x64</span></span> |
| <span data-ttu-id="12edf-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="12edf-229">CentOS</span></span>                         |  <span data-ttu-id="12edf-230">7</span><span class="sxs-lookup"><span data-stu-id="12edf-230">7</span></span>                      | <span data-ttu-id="12edf-231">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-231">x64</span></span> |
| <span data-ttu-id="12edf-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-232">Oracle Linux</span></span>                   |  <span data-ttu-id="12edf-233">7</span><span class="sxs-lookup"><span data-stu-id="12edf-233">7</span></span>                      | <span data-ttu-id="12edf-234">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-234">x64</span></span> |
| <span data-ttu-id="12edf-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="12edf-235">Fedora</span></span>                         |  <span data-ttu-id="12edf-236">29, 30</span><span class="sxs-lookup"><span data-stu-id="12edf-236">29, 30</span></span>                 | <span data-ttu-id="12edf-237">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-237">x64</span></span> |
| <span data-ttu-id="12edf-238">Debian</span><span class="sxs-lookup"><span data-stu-id="12edf-238">Debian</span></span>                         |  <span data-ttu-id="12edf-239">9</span><span class="sxs-lookup"><span data-stu-id="12edf-239">9</span></span>                      | <span data-ttu-id="12edf-240">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-240">x64, ARM32</span></span> |
| <span data-ttu-id="12edf-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12edf-241">Ubuntu</span></span>                         |  <span data-ttu-id="12edf-242">16.04, 18.04, 18.10, 19.04</span><span class="sxs-lookup"><span data-stu-id="12edf-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="12edf-243">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-243">x64, ARM32</span></span> |
| <span data-ttu-id="12edf-244">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="12edf-244">Linux Mint</span></span>                     |  <span data-ttu-id="12edf-245">17, 18</span><span class="sxs-lookup"><span data-stu-id="12edf-245">17, 18</span></span>                 | <span data-ttu-id="12edf-246">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-246">x64</span></span> |
| <span data-ttu-id="12edf-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="12edf-247">openSUSE</span></span>                       |  <span data-ttu-id="12edf-248">15+</span><span class="sxs-lookup"><span data-stu-id="12edf-248">15+</span></span>                    | <span data-ttu-id="12edf-249">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-249">x64</span></span> |
| <span data-ttu-id="12edf-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="12edf-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="12edf-251">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="12edf-251">12 SP2+</span></span>                | <span data-ttu-id="12edf-252">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-252">x64</span></span> |
| <span data-ttu-id="12edf-253">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-253">Alpine Linux</span></span>                   |  <span data-ttu-id="12edf-254">3.8+</span><span class="sxs-lookup"><span data-stu-id="12edf-254">3.8+</span></span>                   | <span data-ttu-id="12edf-255">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-255">x64</span></span> |

<span data-ttu-id="12edf-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="12edf-257">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="12edf-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="12edf-258">.NET Core 2.1 treats Linux as a single operating system.</span><span class="sxs-lookup"><span data-stu-id="12edf-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="12edf-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span><span class="sxs-lookup"><span data-stu-id="12edf-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="12edf-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span><span class="sxs-lookup"><span data-stu-id="12edf-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-261">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-262">OS</span><span class="sxs-lookup"><span data-stu-id="12edf-262">OS</span></span>                             |  <span data-ttu-id="12edf-263">Version</span><span class="sxs-lookup"><span data-stu-id="12edf-263">Version</span></span>                |  <span data-ttu-id="12edf-264">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="12edf-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="12edf-266">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="12edf-266">6, 7, 8</span></span>                | <span data-ttu-id="12edf-267">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-267">x64</span></span> |
| <span data-ttu-id="12edf-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="12edf-268">CentOS</span></span>                         |  <span data-ttu-id="12edf-269">7+</span><span class="sxs-lookup"><span data-stu-id="12edf-269">7+</span></span>                     | <span data-ttu-id="12edf-270">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-270">x64</span></span> |
| <span data-ttu-id="12edf-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-271">Oracle Linux</span></span>                   |  <span data-ttu-id="12edf-272">7+</span><span class="sxs-lookup"><span data-stu-id="12edf-272">7+</span></span>                     | <span data-ttu-id="12edf-273">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-273">x64</span></span> |
| <span data-ttu-id="12edf-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="12edf-274">Fedora</span></span>                         |  <span data-ttu-id="12edf-275">29+</span><span class="sxs-lookup"><span data-stu-id="12edf-275">29+</span></span>                    | <span data-ttu-id="12edf-276">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-276">x64</span></span> |
| <span data-ttu-id="12edf-277">Debian</span><span class="sxs-lookup"><span data-stu-id="12edf-277">Debian</span></span>                         |  <span data-ttu-id="12edf-278">9</span><span class="sxs-lookup"><span data-stu-id="12edf-278">9</span></span>                      | <span data-ttu-id="12edf-279">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-279">x64, ARM32</span></span> |
| <span data-ttu-id="12edf-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12edf-280">Ubuntu</span></span>                         |  <span data-ttu-id="12edf-281">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="12edf-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="12edf-282">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="12edf-282">x64, ARM32</span></span> |
| <span data-ttu-id="12edf-283">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="12edf-283">Linux Mint</span></span>                     |  <span data-ttu-id="12edf-284">17+</span><span class="sxs-lookup"><span data-stu-id="12edf-284">17+</span></span>                    | <span data-ttu-id="12edf-285">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-285">x64</span></span> |
| <span data-ttu-id="12edf-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="12edf-286">openSUSE</span></span>                       |  <span data-ttu-id="12edf-287">15+</span><span class="sxs-lookup"><span data-stu-id="12edf-287">15+</span></span>                    | <span data-ttu-id="12edf-288">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-288">x64</span></span> |
| <span data-ttu-id="12edf-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="12edf-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="12edf-290">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="12edf-290">12 SP2+</span></span>                | <span data-ttu-id="12edf-291">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-291">x64</span></span> |
| <span data-ttu-id="12edf-292">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="12edf-292">Alpine Linux</span></span>                   |  <span data-ttu-id="12edf-293">3.8+</span><span class="sxs-lookup"><span data-stu-id="12edf-293">3.8+</span></span>                   | <span data-ttu-id="12edf-294">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-294">x64</span></span> |

<span data-ttu-id="12edf-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="12edf-296">Linux distribution dependencies</span><span class="sxs-lookup"><span data-stu-id="12edf-296">Linux distribution dependencies</span></span>

<span data-ttu-id="12edf-297">Based on your linux distribution, you may need to install additional dependencies.</span><span class="sxs-lookup"><span data-stu-id="12edf-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12edf-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span><span class="sxs-lookup"><span data-stu-id="12edf-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="12edf-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12edf-299">Ubuntu</span></span>

<span data-ttu-id="12edf-300">Ubuntu distributions require the following libraries to be installed:</span><span class="sxs-lookup"><span data-stu-id="12edf-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="12edf-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="12edf-301">liblttng-ust0</span></span>
- <span data-ttu-id="12edf-302">libcurl3 (for 14.x and 16.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="12edf-303">libcurl4 (for 18.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="12edf-304">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="12edf-304">libssl1.0.0</span></span>
- <span data-ttu-id="12edf-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="12edf-305">libkrb5-3</span></span>
- <span data-ttu-id="12edf-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="12edf-306">zlib1g</span></span>
- <span data-ttu-id="12edf-307">libicu52 (for 14.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="12edf-308">libicu55 (for 16.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="12edf-309">libicu57 (for 17.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="12edf-310">libicu60 (for 18.x)</span><span class="sxs-lookup"><span data-stu-id="12edf-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="12edf-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span><span class="sxs-lookup"><span data-stu-id="12edf-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="12edf-312">libgdiplus (version 6.0.1 or later)</span><span class="sxs-lookup"><span data-stu-id="12edf-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="12edf-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="12edf-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="12edf-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span><span class="sxs-lookup"><span data-stu-id="12edf-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="12edf-315">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="12edf-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="12edf-316">CentOS and Fedora</span><span class="sxs-lookup"><span data-stu-id="12edf-316">CentOS and Fedora</span></span>

<span data-ttu-id="12edf-317">CentOS distributions require the following libraries installed:</span><span class="sxs-lookup"><span data-stu-id="12edf-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="12edf-318">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="12edf-318">lttng-ust</span></span>
- <span data-ttu-id="12edf-319">libcurl</span><span class="sxs-lookup"><span data-stu-id="12edf-319">libcurl</span></span>
- <span data-ttu-id="12edf-320">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="12edf-320">openssl-libs</span></span>
- <span data-ttu-id="12edf-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="12edf-321">krb5-libs</span></span>
- <span data-ttu-id="12edf-322">libicu</span><span class="sxs-lookup"><span data-stu-id="12edf-322">libicu</span></span>
- <span data-ttu-id="12edf-323">zlib</span><span class="sxs-lookup"><span data-stu-id="12edf-323">zlib</span></span>

<span data-ttu-id="12edf-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="12edf-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="12edf-325">For .NET Core 2.0, the following dependencies are also required:</span><span class="sxs-lookup"><span data-stu-id="12edf-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="12edf-326">libunwind</span><span class="sxs-lookup"><span data-stu-id="12edf-326">libunwind</span></span>
- <span data-ttu-id="12edf-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="12edf-327">libuuid</span></span>

<span data-ttu-id="12edf-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="12edf-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span><span class="sxs-lookup"><span data-stu-id="12edf-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="12edf-330">libgdiplus (version 6.0.1 or later)</span><span class="sxs-lookup"><span data-stu-id="12edf-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="12edf-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="12edf-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="12edf-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span><span class="sxs-lookup"><span data-stu-id="12edf-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="12edf-333">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="12edf-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="12edf-334">.NET Core is supported on the following macOS releases:</span><span class="sxs-lookup"><span data-stu-id="12edf-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="12edf-335">A `+` symbol represents the minimum version.</span><span class="sxs-lookup"><span data-stu-id="12edf-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="12edf-336">.NET Core Version</span><span class="sxs-lookup"><span data-stu-id="12edf-336">.NET Core Version</span></span> | <span data-ttu-id="12edf-337">macOS</span><span class="sxs-lookup"><span data-stu-id="12edf-337">macOS</span></span>                 | <span data-ttu-id="12edf-338">Architectures</span><span class="sxs-lookup"><span data-stu-id="12edf-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="12edf-339">3.0</span><span class="sxs-lookup"><span data-stu-id="12edf-339">3.0</span></span>               | <span data-ttu-id="12edf-340">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="12edf-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="12edf-341">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-341">x64</span></span> | [<span data-ttu-id="12edf-342">More information</span><span class="sxs-lookup"><span data-stu-id="12edf-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="12edf-343">2.2</span><span class="sxs-lookup"><span data-stu-id="12edf-343">2.2</span></span>               | <span data-ttu-id="12edf-344">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="12edf-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="12edf-345">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-345">x64</span></span> | [<span data-ttu-id="12edf-346">More information</span><span class="sxs-lookup"><span data-stu-id="12edf-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="12edf-347">2.1</span><span class="sxs-lookup"><span data-stu-id="12edf-347">2.1</span></span>               | <span data-ttu-id="12edf-348">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="12edf-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="12edf-349">X64</span><span class="sxs-lookup"><span data-stu-id="12edf-349">x64</span></span> | [<span data-ttu-id="12edf-350">More information</span><span class="sxs-lookup"><span data-stu-id="12edf-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="12edf-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="12edf-351">libgdiplus</span></span>

<span data-ttu-id="12edf-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span><span class="sxs-lookup"><span data-stu-id="12edf-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="12edf-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span><span class="sxs-lookup"><span data-stu-id="12edf-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="12edf-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span><span class="sxs-lookup"><span data-stu-id="12edf-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="12edf-355">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="12edf-355">Next steps</span></span>

- <span data-ttu-id="12edf-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span><span class="sxs-lookup"><span data-stu-id="12edf-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="12edf-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="12edf-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
