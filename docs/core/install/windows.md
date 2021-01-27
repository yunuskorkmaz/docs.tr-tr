---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 33492cc6fa6c64ec3a1d745a4fa0c6cc418f87bd
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898794"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="c6606-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="c6606-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="c6606-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c6606-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="c6606-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6606-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="c6606-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="c6606-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="c6606-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c6606-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="c6606-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6606-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c6606-113">.NET İndir</span><span class="sxs-lookup"><span data-stu-id="c6606-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="c6606-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="c6606-114">Supported releases</span></span>

<span data-ttu-id="c6606-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6606-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="c6606-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="c6606-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="c6606-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="c6606-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="c6606-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="c6606-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="c6606-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="c6606-120">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-121">Operating System</span><span class="sxs-lookup"><span data-stu-id="c6606-121">Operating System</span></span>            | <span data-ttu-id="c6606-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c6606-122">.NET Core 2.1</span></span> | <span data-ttu-id="c6606-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c6606-123">.NET Core 3.1</span></span> | <span data-ttu-id="c6606-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="c6606-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="c6606-125">Windows 10, sürüm 20H2</span><span class="sxs-lookup"><span data-stu-id="c6606-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="c6606-126">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-126">✔️</span></span>           | <span data-ttu-id="c6606-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-127">✔️</span></span>            | <span data-ttu-id="c6606-128">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-128">✔️</span></span>    |
| <span data-ttu-id="c6606-129">Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="c6606-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="c6606-130">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-130">✔️</span></span>           | <span data-ttu-id="c6606-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-131">✔️</span></span>            | <span data-ttu-id="c6606-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-132">✔️</span></span>    |
| <span data-ttu-id="c6606-133">Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="c6606-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="c6606-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-134">✔️</span></span>           | <span data-ttu-id="c6606-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-135">✔️</span></span>            | <span data-ttu-id="c6606-136">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-136">✔️</span></span>    |
| <span data-ttu-id="c6606-137">Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="c6606-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="c6606-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-138">✔️</span></span>           | <span data-ttu-id="c6606-139">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-139">✔️</span></span>            | <span data-ttu-id="c6606-140">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-140">✔️</span></span>    |
| <span data-ttu-id="c6606-141">Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="c6606-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="c6606-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-142">✔️</span></span>           | <span data-ttu-id="c6606-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-143">✔️</span></span>            | <span data-ttu-id="c6606-144">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-144">✔️</span></span>    |
| <span data-ttu-id="c6606-145">Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="c6606-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="c6606-146">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-146">✔️</span></span>           | <span data-ttu-id="c6606-147">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-147">✔️</span></span>            | <span data-ttu-id="c6606-148">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-148">✔️</span></span>    |
| <span data-ttu-id="c6606-149">Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="c6606-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="c6606-150">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-150">✔️</span></span>           | <span data-ttu-id="c6606-151">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-151">✔️</span></span>            | <span data-ttu-id="c6606-152">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-152">✔️</span></span>    |
| <span data-ttu-id="c6606-153">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="c6606-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="c6606-154">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-154">✔️</span></span>           | <span data-ttu-id="c6606-155">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-155">✔️</span></span>            | <span data-ttu-id="c6606-156">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-156">✔️</span></span>    |
| <span data-ttu-id="c6606-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c6606-157">Windows 8.1</span></span>                 | <span data-ttu-id="c6606-158">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-158">✔️</span></span>           | <span data-ttu-id="c6606-159">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-159">✔️</span></span>            | <span data-ttu-id="c6606-160">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-160">✔️</span></span>    |
| <span data-ttu-id="c6606-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="c6606-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="c6606-162">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-162">✔️</span></span>           | <span data-ttu-id="c6606-163">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-163">✔️</span></span>            | <span data-ttu-id="c6606-164">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-164">✔️</span></span>    |
| <span data-ttu-id="c6606-165">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="c6606-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="c6606-166">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-166">✔️</span></span>           | <span data-ttu-id="c6606-167">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-167">✔️</span></span>            | <span data-ttu-id="c6606-168">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-168">✔️</span></span>    |
| <span data-ttu-id="c6606-169">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="c6606-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="c6606-170">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-170">✔️</span></span>           | <span data-ttu-id="c6606-171">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-171">✔️</span></span>            | <span data-ttu-id="c6606-172">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-172">✔️</span></span>    |
| <span data-ttu-id="c6606-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c6606-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="c6606-174">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-174">✔️</span></span>           | <span data-ttu-id="c6606-175">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-175">✔️</span></span>            | <span data-ttu-id="c6606-176">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-176">✔️</span></span>    |
| <span data-ttu-id="c6606-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c6606-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="c6606-178">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-178">✔️</span></span>           | <span data-ttu-id="c6606-179">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-179">✔️</span></span>            | <span data-ttu-id="c6606-180">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-180">✔️</span></span>    |
| <span data-ttu-id="c6606-181">Nano sunucu, sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="c6606-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="c6606-182">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-182">✔️</span></span>           | <span data-ttu-id="c6606-183">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-183">✔️</span></span>            | <span data-ttu-id="c6606-184">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-184">✔️</span></span>    |
| <span data-ttu-id="c6606-185">Nano sunucu, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="c6606-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="c6606-186">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-186">✔️</span></span>           | <span data-ttu-id="c6606-187">✔️</span><span class="sxs-lookup"><span data-stu-id="c6606-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="c6606-188">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="c6606-188">Unsupported releases</span></span>

<span data-ttu-id="c6606-189">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="c6606-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="c6606-190">Bu sürümlere yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="c6606-190">The downloads for these versions still remain published:</span></span>

- <span data-ttu-id="c6606-191">3.0</span><span class="sxs-lookup"><span data-stu-id="c6606-191">3.0</span></span>
- <span data-ttu-id="c6606-192">2,2</span><span class="sxs-lookup"><span data-stu-id="c6606-192">2.2</span></span>
- <span data-ttu-id="c6606-193">2.0</span><span class="sxs-lookup"><span data-stu-id="c6606-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="c6606-194">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="c6606-194">Runtime information</span></span>

<span data-ttu-id="c6606-195">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="c6606-196">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="c6606-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="c6606-197">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="c6606-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="c6606-198">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="c6606-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="c6606-199">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="c6606-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="c6606-200">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c6606-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="c6606-201">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="c6606-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="c6606-202">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="c6606-202">*Desktop runtime*</span></span>\
<span data-ttu-id="c6606-203">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c6606-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="c6606-204">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="c6606-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="c6606-205">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="c6606-205">*.NET runtime*</span></span>\
<span data-ttu-id="c6606-206">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="c6606-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="c6606-207">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="c6606-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c6606-208">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="c6606-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="c6606-209">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="c6606-209">SDK information</span></span>

<span data-ttu-id="c6606-210">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="c6606-211">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="c6606-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="c6606-212">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="c6606-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="c6606-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c6606-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="c6606-214">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c6606-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="c6606-215">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-216">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="c6606-216">OS</span></span>                  | <span data-ttu-id="c6606-217">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-217">Version</span></span>       | <span data-ttu-id="c6606-218">Mimariler</span><span class="sxs-lookup"><span data-stu-id="c6606-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="c6606-219">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-219">Windows 10 Client</span></span>   | <span data-ttu-id="c6606-220">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="c6606-220">Version 1607+</span></span> | <span data-ttu-id="c6606-221">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="c6606-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="c6606-222">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-222">Windows Client</span></span>      | <span data-ttu-id="c6606-223">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c6606-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="c6606-224">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-224">x64, x86</span></span>        |
| <span data-ttu-id="c6606-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c6606-225">Windows Server</span></span>      | <span data-ttu-id="c6606-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c6606-226">2012 R2+</span></span>      | <span data-ttu-id="c6606-227">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-227">x64, x86</span></span>        |
| <span data-ttu-id="c6606-228">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c6606-228">Windows Server Core</span></span> | <span data-ttu-id="c6606-229">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c6606-229">2012 R2+</span></span>      | <span data-ttu-id="c6606-230">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-230">x64, x86</span></span>        |
| <span data-ttu-id="c6606-231">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="c6606-231">Nano Server</span></span>         | <span data-ttu-id="c6606-232">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="c6606-232">Version 1809+</span></span> | <span data-ttu-id="c6606-233">x64</span><span class="sxs-lookup"><span data-stu-id="c6606-233">x64</span></span>             |

<span data-ttu-id="c6606-234">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="c6606-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c6606-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="c6606-236">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c6606-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="c6606-237">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-238">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="c6606-238">OS</span></span>                            | <span data-ttu-id="c6606-239">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-239">Version</span></span>                        | <span data-ttu-id="c6606-240">Mimariler</span><span class="sxs-lookup"><span data-stu-id="c6606-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c6606-241">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-241">Windows Client</span></span>                | <span data-ttu-id="c6606-242">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c6606-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c6606-243">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-243">x64, x86</span></span>        |
| <span data-ttu-id="c6606-244">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-244">Windows 10 Client</span></span>             | <span data-ttu-id="c6606-245">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="c6606-245">Version 1607+</span></span>                  | <span data-ttu-id="c6606-246">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-246">x64, x86</span></span>        |
| <span data-ttu-id="c6606-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c6606-247">Windows Server</span></span>                | <span data-ttu-id="c6606-248">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c6606-248">2012 R2+</span></span>                       | <span data-ttu-id="c6606-249">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-249">x64, x86</span></span>        |
| <span data-ttu-id="c6606-250">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="c6606-250">Nano Server</span></span>                   | <span data-ttu-id="c6606-251">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="c6606-251">Version 1803+</span></span>                  | <span data-ttu-id="c6606-252">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c6606-252">x64, ARM32</span></span>      |

<span data-ttu-id="c6606-253">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="c6606-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c6606-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="c6606-255">*.NET Core 3,0 şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="c6606-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="c6606-256">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c6606-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="c6606-257">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-258">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="c6606-258">OS</span></span>                            | <span data-ttu-id="c6606-259">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-259">Version</span></span>                        | <span data-ttu-id="c6606-260">Mimariler</span><span class="sxs-lookup"><span data-stu-id="c6606-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c6606-261">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-261">Windows Client</span></span>                | <span data-ttu-id="c6606-262">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c6606-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c6606-263">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-263">x64, x86</span></span>        |
| <span data-ttu-id="c6606-264">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-264">Windows 10 Client</span></span>             | <span data-ttu-id="c6606-265">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="c6606-265">Version 1607+</span></span>                  | <span data-ttu-id="c6606-266">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-266">x64, x86</span></span>        |
| <span data-ttu-id="c6606-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c6606-267">Windows Server</span></span>                | <span data-ttu-id="c6606-268">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c6606-268">2012 R2+</span></span>                       | <span data-ttu-id="c6606-269">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-269">x64, x86</span></span>        |
| <span data-ttu-id="c6606-270">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="c6606-270">Nano Server</span></span>                   | <span data-ttu-id="c6606-271">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="c6606-271">Version 1803+</span></span>                  | <span data-ttu-id="c6606-272">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c6606-272">x64, ARM32</span></span>      |

<span data-ttu-id="c6606-273">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="c6606-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c6606-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c6606-275">*.NET Core 2,2 Şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="c6606-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="c6606-276">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c6606-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="c6606-277">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-278">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="c6606-278">OS</span></span>                            | <span data-ttu-id="c6606-279">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-279">Version</span></span>                        | <span data-ttu-id="c6606-280">Mimariler</span><span class="sxs-lookup"><span data-stu-id="c6606-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c6606-281">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-281">Windows Client</span></span>                | <span data-ttu-id="c6606-282">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c6606-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c6606-283">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-283">x64, x86</span></span>        |
| <span data-ttu-id="c6606-284">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-284">Windows 10 Client</span></span>             | <span data-ttu-id="c6606-285">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="c6606-285">Version 1607+</span></span>                  | <span data-ttu-id="c6606-286">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-286">x64, x86</span></span>        |
| <span data-ttu-id="c6606-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c6606-287">Windows Server</span></span>                | <span data-ttu-id="c6606-288">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="c6606-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="c6606-289">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-289">x64, x86</span></span>        |
| <span data-ttu-id="c6606-290">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="c6606-290">Nano Server</span></span>                   | <span data-ttu-id="c6606-291">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="c6606-291">Version 1803+</span></span>                   | <span data-ttu-id="c6606-292">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c6606-292">x64, ARM32</span></span>      |

<span data-ttu-id="c6606-293">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="c6606-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c6606-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c6606-295">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c6606-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="c6606-296">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6606-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c6606-297">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="c6606-297">OS</span></span>                            | <span data-ttu-id="c6606-298">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-298">Version</span></span>                        | <span data-ttu-id="c6606-299">Mimariler</span><span class="sxs-lookup"><span data-stu-id="c6606-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c6606-300">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-300">Windows Client</span></span>                | <span data-ttu-id="c6606-301">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c6606-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c6606-302">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-302">x64, x86</span></span>        |
| <span data-ttu-id="c6606-303">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="c6606-303">Windows 10 Client</span></span>             | <span data-ttu-id="c6606-304">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="c6606-304">Version 1607+</span></span>                  | <span data-ttu-id="c6606-305">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-305">x64, x86</span></span>        |
| <span data-ttu-id="c6606-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c6606-306">Windows Server</span></span>                | <span data-ttu-id="c6606-307">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="c6606-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="c6606-308">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c6606-308">x64, x86</span></span>        |
| <span data-ttu-id="c6606-309">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="c6606-309">Nano Server</span></span>                   | <span data-ttu-id="c6606-310">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="c6606-310">Version 1803+</span></span>                  | <span data-ttu-id="c6606-311">x64</span><span class="sxs-lookup"><span data-stu-id="c6606-311">x64,</span></span>            |

<span data-ttu-id="c6606-312">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

### <a name="offline-install-for-windows-7"></a><span data-ttu-id="c6606-313">Windows 7 için çevrimdışı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c6606-313">Offline install for Windows 7</span></span>

<span data-ttu-id="c6606-314">Windows 7 ' de .NET Core 2,1 için çevrimdışı yükleme yaparken öncelikle en son [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) ' nin hedef makinede yüklü olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6606-314">When doing an offline install for .NET Core 2.1 on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="c6606-315">_certmgr.exe_ aracı bir sertifikayı yüklemeyi otomatikleştirebilir ve Visual Studio 'dan veya Windows SDK elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-315">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="c6606-316">Aşağıdaki komut, .NET Core 2,1 yükleyicisini çalıştırmadan önce sertifikayı yüklemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="c6606-316">The following command is used to install the certificate before running the .NET Core 2.1 installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

<span data-ttu-id="c6606-317">[Aşağıdaki Windows 7](#additional-deps)için gereken bağımlılıkları gözden geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6606-317">Be sure to review the dependencies required for [Windows 7 below](#additional-deps).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="c6606-318">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c6606-318">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="c6606-319">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız daha fazla bağımlılık gerekir:</span><span class="sxs-lookup"><span data-stu-id="c6606-319">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="c6606-320">Operating System</span><span class="sxs-lookup"><span data-stu-id="c6606-320">Operating System</span></span>         | <span data-ttu-id="c6606-321">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c6606-321">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="c6606-322">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="c6606-322">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="c6606-323">-Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="c6606-323">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="c6606-324">-KB3063858 [64-bit][kb64]  /  [32-bit][kb32]</span><span class="sxs-lookup"><span data-stu-id="c6606-324">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="c6606-325">- [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (yalnızca .net Core 2,1 çevrimdışı Yükleyici)</span><span class="sxs-lookup"><span data-stu-id="c6606-325">- [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 offline installer only)</span></span> |
| <span data-ttu-id="c6606-326">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="c6606-326">Windows Vista SP 2</span></span>       | <span data-ttu-id="c6606-327">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="c6606-327">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="c6606-328">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c6606-328">Windows 8.1</span></span>              | <span data-ttu-id="c6606-329">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="c6606-329">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="c6606-330">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c6606-330">Windows Server 2008 R2</span></span>   | <span data-ttu-id="c6606-331">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="c6606-331">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="c6606-332">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c6606-332">Windows Server 2012 R2</span></span>   | <span data-ttu-id="c6606-333">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="c6606-333">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="c6606-334">Aşağıdaki dll 'lerden biriyle ilgili bir hata alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="c6606-334">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="c6606-335">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="c6606-335">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="c6606-336">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="c6606-336">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="c6606-337">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="c6606-337">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="c6606-338">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="c6606-338">Install with PowerShell automation</span></span>

<span data-ttu-id="c6606-339">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-339">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c6606-340">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6606-340">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c6606-341">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="c6606-341">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="c6606-342">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="c6606-342">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="c6606-343">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6606-343">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="c6606-344">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="c6606-344">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="c6606-345">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="c6606-345">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="c6606-346">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c6606-346">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="c6606-347">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="c6606-347">Install with Visual Studio</span></span>

<span data-ttu-id="c6606-348">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6606-348">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="c6606-349">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="c6606-349">.NET SDK version</span></span>      | <span data-ttu-id="c6606-350">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="c6606-350">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c6606-351">5.0</span><span class="sxs-lookup"><span data-stu-id="c6606-351">5.0</span></span>                   | <span data-ttu-id="c6606-352">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6606-352">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="c6606-353">3,1</span><span class="sxs-lookup"><span data-stu-id="c6606-353">3.1</span></span>                   | <span data-ttu-id="c6606-354">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6606-354">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="c6606-355">3.0</span><span class="sxs-lookup"><span data-stu-id="c6606-355">3.0</span></span>                   | <span data-ttu-id="c6606-356">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6606-356">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="c6606-357">2,2</span><span class="sxs-lookup"><span data-stu-id="c6606-357">2.2</span></span>                   | <span data-ttu-id="c6606-358">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6606-358">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="c6606-359">2.1</span><span class="sxs-lookup"><span data-stu-id="c6606-359">2.1</span></span>                   | <span data-ttu-id="c6606-360">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6606-360">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="c6606-361">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6606-361">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="c6606-362">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="c6606-362">Open Visual Studio.</span></span>
01. <span data-ttu-id="c6606-363">  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c6606-363">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="c6606-364">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="c6606-364">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="c6606-365">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-365">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="c6606-366">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="c6606-366">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="c6606-367">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="c6606-367">Select a workload</span></span>

<span data-ttu-id="c6606-368">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="c6606-368">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="c6606-369">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6606-369">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="c6606-370">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6606-370">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c6606-371">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6606-371">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c6606-372">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6606-372">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="c6606-373">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="c6606-373">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="c6606-374">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="c6606-374">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="c6606-375">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="c6606-375">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="c6606-376">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-376">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="c6606-377">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="c6606-377">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="c6606-378">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="c6606-378">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="c6606-379">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c6606-379">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="c6606-380">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="c6606-380">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="c6606-381">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="c6606-381">Windows Installer</span></span>

<span data-ttu-id="c6606-382">.NET için [karşıdan yükleme sayfası](https://dotnet.microsoft.com/download/dotnet-core) Windows ınstaller yürütülebilir dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6606-382">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="c6606-383">.NET yüklemek için Windows yükleyicilerini kullandığınızda, ve parametrelerini ayarlayarak yükleme yolunu özelleştirebilirsiniz `DOTNETHOME_X64` `DOTNETHOME_X86` :</span><span class="sxs-lookup"><span data-stu-id="c6606-383">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="c6606-384">.NET 'i bir üretim ortamında veya sürekli tümleştirmeyi destekleyecek şekilde sessizce yüklemek istiyorsanız aşağıdaki anahtarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="c6606-384">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="c6606-385">.NET 'i yükleme.</span><span class="sxs-lookup"><span data-stu-id="c6606-385">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="c6606-386">Tüm UI ve istemlerin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="c6606-386">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="c6606-387">Yeniden başlatma girişimlerini engeller.</span><span class="sxs-lookup"><span data-stu-id="c6606-387">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="c6606-388">Daha fazla bilgi için bkz. [Standart yükleyici Command-Line seçenekleri](/windows/win32/msi/standard-installer-command-line-options).</span><span class="sxs-lookup"><span data-stu-id="c6606-388">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="c6606-389">Yükleyici, başarılı için 0 çıkış kodu ve bir yeniden başlatmanın gerekli olduğunu göstermek için 3010 çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6606-389">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="c6606-390">Diğer herhangi bir değer genellikle bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="c6606-390">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="c6606-391">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="c6606-391">Download and manually install</span></span>

<span data-ttu-id="c6606-392">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6606-392">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="c6606-393">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="c6606-393">Manual install is usually done as part of continuous integration testing.</span></span> <span data-ttu-id="c6606-394">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="c6606-394">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="c6606-395">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-395">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="c6606-396">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c6606-396">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="c6606-397">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="c6606-397">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="c6606-398">.NET 5,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="c6606-398">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="c6606-399">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="c6606-399">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="c6606-400">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="c6606-400">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="c6606-401">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="c6606-401">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="c6606-402">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="c6606-402">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="c6606-403">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6606-403">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="c6606-404">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6606-404">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="c6606-405">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c6606-405">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="c6606-406">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6606-406">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="c6606-407">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="c6606-407">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="c6606-408">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c6606-408">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="c6606-409">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="c6606-409">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="c6606-410">Docker</span><span class="sxs-lookup"><span data-stu-id="c6606-410">Docker</span></span>

<span data-ttu-id="c6606-411">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6606-411">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c6606-412">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6606-412">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c6606-413">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-413">.NET can run in a Docker container.</span></span> <span data-ttu-id="c6606-414">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c6606-414">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="c6606-415">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c6606-415">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c6606-416">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6606-416">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c6606-417">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6606-417">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c6606-418">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="c6606-418">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6606-419">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c6606-419">Next steps</span></span>

- <span data-ttu-id="c6606-420">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c6606-420">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="c6606-421">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-421">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="c6606-422">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="c6606-422">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="c6606-423">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="c6606-423">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
