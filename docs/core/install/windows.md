---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9b0c5c2ea26546a142029b730dfd38923231bae4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873750"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="45b85-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="45b85-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="45b85-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="45b85-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="45b85-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="45b85-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="45b85-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="45b85-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b85-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="45b85-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="45b85-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="45b85-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="45b85-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="45b85-113">.NET’i indirme</span><span class="sxs-lookup"><span data-stu-id="45b85-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a><span data-ttu-id="45b85-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="45b85-114">Supported releases</span></span>

<span data-ttu-id="45b85-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="45b85-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="45b85-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="45b85-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="45b85-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="45b85-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="45b85-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="45b85-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="45b85-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="45b85-120">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-121">Operating System</span><span class="sxs-lookup"><span data-stu-id="45b85-121">Operating System</span></span>            | <span data-ttu-id="45b85-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="45b85-122">.NET Core 2.1</span></span> | <span data-ttu-id="45b85-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="45b85-123">.NET Core 3.1</span></span> | <span data-ttu-id="45b85-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="45b85-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="45b85-125">Windows 10/Windows Server, sürüm 20H2</span><span class="sxs-lookup"><span data-stu-id="45b85-125">Windows 10 / Windows Server, Version 20H2</span></span>    | <span data-ttu-id="45b85-126">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-126">✔️</span></span>           | <span data-ttu-id="45b85-127">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-127">✔️</span></span>            | <span data-ttu-id="45b85-128">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-128">✔️</span></span>    |
| <span data-ttu-id="45b85-129">Windows 10/Windows Server, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="45b85-129">Windows 10 / Windows Server, Version 2004</span></span>    | <span data-ttu-id="45b85-130">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-130">✔️</span></span>           | <span data-ttu-id="45b85-131">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-131">✔️</span></span>            | <span data-ttu-id="45b85-132">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-132">✔️</span></span>    |
| <span data-ttu-id="45b85-133">Windows 10/Windows Server, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="45b85-133">Windows 10 / Windows Server, Version 1909</span></span>    | <span data-ttu-id="45b85-134">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-134">✔️</span></span>           | <span data-ttu-id="45b85-135">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-135">✔️</span></span>            | <span data-ttu-id="45b85-136">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-136">✔️</span></span>    |
| <span data-ttu-id="45b85-137">Windows 10/Windows Server, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="45b85-137">Windows 10 / Windows Server, Version 1903</span></span>    | <span data-ttu-id="45b85-138">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-138">✔️</span></span>           | <span data-ttu-id="45b85-139">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-139">✔️</span></span>            | <span data-ttu-id="45b85-140">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-140">✔️</span></span>    |
| <span data-ttu-id="45b85-141">Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="45b85-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="45b85-142">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-142">✔️</span></span>           | <span data-ttu-id="45b85-143">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-143">✔️</span></span>            | <span data-ttu-id="45b85-144">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-144">✔️</span></span>    |
| <span data-ttu-id="45b85-145">Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="45b85-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="45b85-146">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-146">✔️</span></span>           | <span data-ttu-id="45b85-147">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-147">✔️</span></span>            | <span data-ttu-id="45b85-148">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-148">✔️</span></span>    |
| <span data-ttu-id="45b85-149">Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="45b85-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="45b85-150">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-150">✔️</span></span>           | <span data-ttu-id="45b85-151">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-151">✔️</span></span>            | <span data-ttu-id="45b85-152">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-152">✔️</span></span>    |
| <span data-ttu-id="45b85-153">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="45b85-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="45b85-154">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-154">✔️</span></span>           | <span data-ttu-id="45b85-155">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-155">✔️</span></span>            | <span data-ttu-id="45b85-156">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-156">✔️</span></span>    |
| <span data-ttu-id="45b85-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="45b85-157">Windows 8.1</span></span>                 | <span data-ttu-id="45b85-158">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-158">✔️</span></span>           | <span data-ttu-id="45b85-159">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-159">✔️</span></span>            | <span data-ttu-id="45b85-160">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-160">✔️</span></span>    |
| <span data-ttu-id="45b85-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="45b85-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="45b85-162">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-162">✔️</span></span>           | <span data-ttu-id="45b85-163">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-163">✔️</span></span>            | <span data-ttu-id="45b85-164">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-164">✔️</span></span>    |
| <span data-ttu-id="45b85-165">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="45b85-165">Windows Server 2019</span></span><br><span data-ttu-id="45b85-166">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="45b85-166">Windows Server 2016</span></span><br><span data-ttu-id="45b85-167">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="45b85-167">Windows Server 2012 R2</span></span><br>      | <span data-ttu-id="45b85-168">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-168">✔️</span></span>           | <span data-ttu-id="45b85-169">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-169">✔️</span></span>            | <span data-ttu-id="45b85-170">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-170">✔️</span></span>    |
| <span data-ttu-id="45b85-171">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="45b85-171">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="45b85-172">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-172">✔️</span></span>           | <span data-ttu-id="45b85-173">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-173">✔️</span></span>            | <span data-ttu-id="45b85-174">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-174">✔️</span></span>    |
| <span data-ttu-id="45b85-175">Nano sunucu, sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="45b85-175">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="45b85-176">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-176">✔️</span></span>           | <span data-ttu-id="45b85-177">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-177">✔️</span></span>            | <span data-ttu-id="45b85-178">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-178">✔️</span></span>    |
| <span data-ttu-id="45b85-179">Nano sunucu, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="45b85-179">Nano Server, Version 1803</span></span>   | <span data-ttu-id="45b85-180">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-180">✔️</span></span>           | <span data-ttu-id="45b85-181">✔️</span><span class="sxs-lookup"><span data-stu-id="45b85-181">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="45b85-182">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="45b85-182">Unsupported releases</span></span>

<span data-ttu-id="45b85-183">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir:</span><span class="sxs-lookup"><span data-stu-id="45b85-183">The following versions of .NET are ❌ no longer supported:</span></span>

- <span data-ttu-id="45b85-184">3.0</span><span class="sxs-lookup"><span data-stu-id="45b85-184">3.0</span></span>
- <span data-ttu-id="45b85-185">2,2</span><span class="sxs-lookup"><span data-stu-id="45b85-185">2.2</span></span>
- <span data-ttu-id="45b85-186">2.0</span><span class="sxs-lookup"><span data-stu-id="45b85-186">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="45b85-187">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="45b85-187">Runtime information</span></span>

<span data-ttu-id="45b85-188">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b85-188">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="45b85-189">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="45b85-189">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="45b85-190">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="45b85-190">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="45b85-191">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="45b85-191">There are three different runtimes you can install on Windows:</span></span>

- <span data-ttu-id="45b85-192">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="45b85-192">*ASP.NET Core runtime*</span></span>\
  <span data-ttu-id="45b85-193">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="45b85-193">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="45b85-194">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="45b85-194">Includes the .NET runtime.</span></span>

- <span data-ttu-id="45b85-195">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="45b85-195">*Desktop runtime*</span></span>\
  <span data-ttu-id="45b85-196">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="45b85-196">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="45b85-197">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="45b85-197">Includes the .NET runtime.</span></span>

- <span data-ttu-id="45b85-198">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="45b85-198">*.NET runtime*</span></span>\
  <span data-ttu-id="45b85-199">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="45b85-199">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="45b85-200">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="45b85-200">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="45b85-201">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="45b85-201">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a><span data-ttu-id="45b85-202">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="45b85-202">SDK information</span></span>

<span data-ttu-id="45b85-203">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b85-203">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="45b85-204">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="45b85-204">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="45b85-205">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="45b85-205">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="45b85-206">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="45b85-206">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="45b85-207">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="45b85-207">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="45b85-208">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-208">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-209">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="45b85-209">OS</span></span>                  | <span data-ttu-id="45b85-210">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-210">Version</span></span>       | <span data-ttu-id="45b85-211">Mimariler</span><span class="sxs-lookup"><span data-stu-id="45b85-211">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="45b85-212">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-212">Windows 10 Client</span></span>   | <span data-ttu-id="45b85-213">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="45b85-213">Version 1607+</span></span> | <span data-ttu-id="45b85-214">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="45b85-214">x64, x86, ARM64</span></span> |
| <span data-ttu-id="45b85-215">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-215">Windows Client</span></span>      | <span data-ttu-id="45b85-216">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="45b85-216">7 SP1+, 8.1</span></span>   | <span data-ttu-id="45b85-217">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-217">x64, x86</span></span>        |
| <span data-ttu-id="45b85-218">Windows Server</span><span class="sxs-lookup"><span data-stu-id="45b85-218">Windows Server</span></span>      | <span data-ttu-id="45b85-219">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="45b85-219">2012 R2+</span></span>      | <span data-ttu-id="45b85-220">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-220">x64, x86</span></span>        |
| <span data-ttu-id="45b85-221">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="45b85-221">Windows Server Core</span></span> | <span data-ttu-id="45b85-222">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="45b85-222">2012 R2+</span></span>      | <span data-ttu-id="45b85-223">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-223">x64, x86</span></span>        |
| <span data-ttu-id="45b85-224">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="45b85-224">Nano Server</span></span>         | <span data-ttu-id="45b85-225">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="45b85-225">Version 1809+</span></span> | <span data-ttu-id="45b85-226">x64</span><span class="sxs-lookup"><span data-stu-id="45b85-226">x64</span></span>             |

<span data-ttu-id="45b85-227">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-227">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="45b85-228">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="45b85-228">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="45b85-229">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="45b85-229">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="45b85-230">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-230">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-231">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="45b85-231">OS</span></span>                            | <span data-ttu-id="45b85-232">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-232">Version</span></span>                        | <span data-ttu-id="45b85-233">Mimariler</span><span class="sxs-lookup"><span data-stu-id="45b85-233">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="45b85-234">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-234">Windows Client</span></span>                | <span data-ttu-id="45b85-235">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="45b85-235">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="45b85-236">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-236">x64, x86</span></span>        |
| <span data-ttu-id="45b85-237">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-237">Windows 10 Client</span></span>             | <span data-ttu-id="45b85-238">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="45b85-238">Version 1607+</span></span>                  | <span data-ttu-id="45b85-239">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-239">x64, x86</span></span>        |
| <span data-ttu-id="45b85-240">Windows Server</span><span class="sxs-lookup"><span data-stu-id="45b85-240">Windows Server</span></span>                | <span data-ttu-id="45b85-241">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="45b85-241">2012 R2+</span></span>                       | <span data-ttu-id="45b85-242">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-242">x64, x86</span></span>        |
| <span data-ttu-id="45b85-243">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="45b85-243">Nano Server</span></span>                   | <span data-ttu-id="45b85-244">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="45b85-244">Version 1803+</span></span>                  | <span data-ttu-id="45b85-245">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="45b85-245">x64, ARM32</span></span>      |

<span data-ttu-id="45b85-246">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-246">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="45b85-247">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="45b85-247">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="45b85-248">*.NET Core 3,0 şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="45b85-248">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="45b85-249">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="45b85-249">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="45b85-250">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-251">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="45b85-251">OS</span></span>                            | <span data-ttu-id="45b85-252">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-252">Version</span></span>                        | <span data-ttu-id="45b85-253">Mimariler</span><span class="sxs-lookup"><span data-stu-id="45b85-253">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="45b85-254">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-254">Windows Client</span></span>                | <span data-ttu-id="45b85-255">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="45b85-255">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="45b85-256">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-256">x64, x86</span></span>        |
| <span data-ttu-id="45b85-257">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-257">Windows 10 Client</span></span>             | <span data-ttu-id="45b85-258">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="45b85-258">Version 1607+</span></span>                  | <span data-ttu-id="45b85-259">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-259">x64, x86</span></span>        |
| <span data-ttu-id="45b85-260">Windows Server</span><span class="sxs-lookup"><span data-stu-id="45b85-260">Windows Server</span></span>                | <span data-ttu-id="45b85-261">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="45b85-261">2012 R2+</span></span>                       | <span data-ttu-id="45b85-262">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-262">x64, x86</span></span>        |
| <span data-ttu-id="45b85-263">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="45b85-263">Nano Server</span></span>                   | <span data-ttu-id="45b85-264">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="45b85-264">Version 1803+</span></span>                  | <span data-ttu-id="45b85-265">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="45b85-265">x64, ARM32</span></span>      |

<span data-ttu-id="45b85-266">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-266">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="45b85-267">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="45b85-267">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="45b85-268">*.NET Core 2,2 Şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="45b85-268">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="45b85-269">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="45b85-269">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="45b85-270">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-270">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-271">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="45b85-271">OS</span></span>                            | <span data-ttu-id="45b85-272">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-272">Version</span></span>                        | <span data-ttu-id="45b85-273">Mimariler</span><span class="sxs-lookup"><span data-stu-id="45b85-273">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="45b85-274">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-274">Windows Client</span></span>                | <span data-ttu-id="45b85-275">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="45b85-275">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="45b85-276">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-276">x64, x86</span></span>        |
| <span data-ttu-id="45b85-277">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-277">Windows 10 Client</span></span>             | <span data-ttu-id="45b85-278">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="45b85-278">Version 1607+</span></span>                  | <span data-ttu-id="45b85-279">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-279">x64, x86</span></span>        |
| <span data-ttu-id="45b85-280">Windows Server</span><span class="sxs-lookup"><span data-stu-id="45b85-280">Windows Server</span></span>                | <span data-ttu-id="45b85-281">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="45b85-281">2008 R2 SP1+</span></span>                   | <span data-ttu-id="45b85-282">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-282">x64, x86</span></span>        |
| <span data-ttu-id="45b85-283">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="45b85-283">Nano Server</span></span>                   | <span data-ttu-id="45b85-284">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="45b85-284">Version 1803+</span></span>                   | <span data-ttu-id="45b85-285">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="45b85-285">x64, ARM32</span></span>      |

<span data-ttu-id="45b85-286">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-286">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="45b85-287">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="45b85-287">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="45b85-288">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="45b85-288">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="45b85-289">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45b85-289">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="45b85-290">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="45b85-290">OS</span></span>                            | <span data-ttu-id="45b85-291">Sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-291">Version</span></span>                        | <span data-ttu-id="45b85-292">Mimariler</span><span class="sxs-lookup"><span data-stu-id="45b85-292">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="45b85-293">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-293">Windows Client</span></span>                | <span data-ttu-id="45b85-294">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="45b85-294">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="45b85-295">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-295">x64, x86</span></span>        |
| <span data-ttu-id="45b85-296">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="45b85-296">Windows 10 Client</span></span>             | <span data-ttu-id="45b85-297">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="45b85-297">Version 1607+</span></span>                  | <span data-ttu-id="45b85-298">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-298">x64, x86</span></span>        |
| <span data-ttu-id="45b85-299">Windows Server</span><span class="sxs-lookup"><span data-stu-id="45b85-299">Windows Server</span></span>                | <span data-ttu-id="45b85-300">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="45b85-300">2008 R2 SP1+</span></span>                   | <span data-ttu-id="45b85-301">x64, x86</span><span class="sxs-lookup"><span data-stu-id="45b85-301">x64, x86</span></span>        |
| <span data-ttu-id="45b85-302">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="45b85-302">Nano Server</span></span>                   | <span data-ttu-id="45b85-303">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="45b85-303">Version 1803+</span></span>                  | <span data-ttu-id="45b85-304">x64</span><span class="sxs-lookup"><span data-stu-id="45b85-304">x64,</span></span>            |

<span data-ttu-id="45b85-305">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-305">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md).</span></span>

### <a name="offline-install-for-windows-7"></a><span data-ttu-id="45b85-306">Windows 7 için çevrimdışı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="45b85-306">Offline install for Windows 7</span></span>

<span data-ttu-id="45b85-307">Windows 7 ' de .NET Core 2,1 için çevrimdışı yükleme yaparken öncelikle en son [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) ' nin hedef makinede yüklü olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="45b85-307">When doing an offline install for .NET Core 2.1 on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="45b85-308">_certmgr.exe_ aracı bir sertifikayı yüklemeyi otomatikleştirebilir ve Visual Studio 'dan veya Windows SDK elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-308">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="45b85-309">Aşağıdaki komut, .NET Core 2,1 yükleyicisini çalıştırmadan önce sertifikayı yüklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="45b85-309">The following command is used to install the certificate before running the .NET Core 2.1 installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

<span data-ttu-id="45b85-310">[Aşağıdaki Windows 7](#additional-deps)için gereken bağımlılıkları gözden geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="45b85-310">Be sure to review the dependencies required for [Windows 7 below](#additional-deps).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="45b85-311">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="45b85-311">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="45b85-312">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız daha fazla bağımlılık gerekir:</span><span class="sxs-lookup"><span data-stu-id="45b85-312">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="45b85-313">Operating System</span><span class="sxs-lookup"><span data-stu-id="45b85-313">Operating System</span></span>         | <span data-ttu-id="45b85-314">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="45b85-314">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="45b85-315">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="45b85-315">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="45b85-316">-Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="45b85-316">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="45b85-317">-KB3063858 [64-bit][kb64]  /  [32-bit][kb32]</span><span class="sxs-lookup"><span data-stu-id="45b85-317">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="45b85-318">- [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (yalnızca .net Core 2,1 çevrimdışı Yükleyici)</span><span class="sxs-lookup"><span data-stu-id="45b85-318">- [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 offline installer only)</span></span> |
| <span data-ttu-id="45b85-319">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="45b85-319">Windows Vista SP 2</span></span>       | <span data-ttu-id="45b85-320">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="45b85-320">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="45b85-321">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="45b85-321">Windows 8.1</span></span>              | <span data-ttu-id="45b85-322">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="45b85-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="45b85-323">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="45b85-323">Windows Server 2008 R2</span></span>   | <span data-ttu-id="45b85-324">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="45b85-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="45b85-325">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="45b85-325">Windows Server 2012 R2</span></span>   | <span data-ttu-id="45b85-326">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="45b85-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="45b85-327">Aşağıdaki dll 'lerden biriyle ilgili bir hata alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="45b85-327">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="45b85-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="45b85-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="45b85-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="45b85-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="45b85-330">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="45b85-330">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="45b85-331">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="45b85-331">Install with PowerShell automation</span></span>

<span data-ttu-id="45b85-332">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b85-332">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="45b85-333">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b85-333">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="45b85-334">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="45b85-334">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="45b85-335">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="45b85-335">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="45b85-336">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45b85-336">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="45b85-337">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="45b85-337">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="45b85-338">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="45b85-338">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="45b85-339">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="45b85-339">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="45b85-340">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="45b85-340">Install with Visual Studio</span></span>

<span data-ttu-id="45b85-341">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45b85-341">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="45b85-342">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="45b85-342">.NET SDK version</span></span>      | <span data-ttu-id="45b85-343">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="45b85-343">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="45b85-344">5.0</span><span class="sxs-lookup"><span data-stu-id="45b85-344">5.0</span></span>                   | <span data-ttu-id="45b85-345">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="45b85-345">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="45b85-346">3,1</span><span class="sxs-lookup"><span data-stu-id="45b85-346">3.1</span></span>                   | <span data-ttu-id="45b85-347">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="45b85-347">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="45b85-348">3.0</span><span class="sxs-lookup"><span data-stu-id="45b85-348">3.0</span></span>                   | <span data-ttu-id="45b85-349">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="45b85-349">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="45b85-350">2,2</span><span class="sxs-lookup"><span data-stu-id="45b85-350">2.2</span></span>                   | <span data-ttu-id="45b85-351">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="45b85-351">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="45b85-352">2.1</span><span class="sxs-lookup"><span data-stu-id="45b85-352">2.1</span></span>                   | <span data-ttu-id="45b85-353">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="45b85-353">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="45b85-354">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b85-354">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="45b85-355">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="45b85-355">Open Visual Studio.</span></span>
01. <span data-ttu-id="45b85-356">  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="45b85-356">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="45b85-357">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="45b85-357">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="45b85-358">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-358">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="45b85-359">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="45b85-359">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="45b85-360">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="45b85-360">Select a workload</span></span>

<span data-ttu-id="45b85-361">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="45b85-361">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="45b85-362">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="45b85-362">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="45b85-363">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="45b85-363">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="45b85-364">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="45b85-364">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="45b85-365">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="45b85-365">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="45b85-366">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="45b85-366">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="45b85-367">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="45b85-367">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="45b85-368">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="45b85-368">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="45b85-369">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-369">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="45b85-370">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="45b85-370">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="45b85-371">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="45b85-371">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="45b85-372">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="45b85-372">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet).</span></span>
01. <span data-ttu-id="45b85-373">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="45b85-373">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="45b85-374">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="45b85-374">Windows Installer</span></span>

<span data-ttu-id="45b85-375">.NET için [karşıdan yükleme sayfası](https://dotnet.microsoft.com/download/dotnet) Windows ınstaller yürütülebilir dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="45b85-375">The [download page](https://dotnet.microsoft.com/download/dotnet) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="45b85-376">.NET yüklemek için Windows yükleyicilerini kullandığınızda, ve parametrelerini ayarlayarak yükleme yolunu özelleştirebilirsiniz `DOTNETHOME_X64` `DOTNETHOME_X86` :</span><span class="sxs-lookup"><span data-stu-id="45b85-376">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="45b85-377">.NET 'i bir üretim ortamında veya sürekli tümleştirmeyi destekleyecek şekilde sessizce yüklemek istiyorsanız aşağıdaki anahtarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="45b85-377">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="45b85-378">.NET 'i yükleme.</span><span class="sxs-lookup"><span data-stu-id="45b85-378">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="45b85-379">Tüm UI ve istemlerin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="45b85-379">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="45b85-380">Yeniden başlatma girişimlerini engeller.</span><span class="sxs-lookup"><span data-stu-id="45b85-380">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="45b85-381">Daha fazla bilgi için bkz. [Standart yükleyici Command-Line seçenekleri](/windows/win32/msi/standard-installer-command-line-options).</span><span class="sxs-lookup"><span data-stu-id="45b85-381">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="45b85-382">Yükleyici, başarılı için 0 çıkış kodu ve bir yeniden başlatmanın gerekli olduğunu göstermek için 3010 çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b85-382">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="45b85-383">Diğer herhangi bir değer genellikle bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="45b85-383">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="45b85-384">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="45b85-384">Download and manually install</span></span>

<span data-ttu-id="45b85-385">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b85-385">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="45b85-386">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="45b85-386">Manual install is usually done as part of continuous integration testing.</span></span> <span data-ttu-id="45b85-387">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="45b85-387">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet).</span></span>

<span data-ttu-id="45b85-388">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-388">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="45b85-389">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="45b85-389">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="45b85-390">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="45b85-390">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="45b85-391">.NET 5,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="45b85-391">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="45b85-392">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="45b85-392">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/3.1)
- [<span data-ttu-id="45b85-393">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="45b85-393">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/2.1)
- [<span data-ttu-id="45b85-394">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="45b85-394">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="45b85-395">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="45b85-395">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="45b85-396">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="45b85-396">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="45b85-397">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45b85-397">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="45b85-398">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="45b85-398">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="45b85-399">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45b85-399">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="45b85-400">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="45b85-400">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="45b85-401">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="45b85-401">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="45b85-402">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="45b85-402">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="45b85-403">Docker</span><span class="sxs-lookup"><span data-stu-id="45b85-403">Docker</span></span>

<span data-ttu-id="45b85-404">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="45b85-404">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="45b85-405">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="45b85-405">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="45b85-406">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-406">.NET can run in a Docker container.</span></span> <span data-ttu-id="45b85-407">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="45b85-407">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="45b85-408">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="45b85-408">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="45b85-409">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="45b85-409">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="45b85-410">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="45b85-410">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="45b85-411">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="45b85-411">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="45b85-412">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="45b85-412">Next steps</span></span>

- <span data-ttu-id="45b85-413">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="45b85-413">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="45b85-414">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-414">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="45b85-415">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="45b85-415">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="45b85-416">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="45b85-416">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
