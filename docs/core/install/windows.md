---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 57cebc562949627be70aabe24e75ad4567d072fd
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536131"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="fb4fc-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="fb4fc-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="fb4fc-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="fb4fc-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="fb4fc-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="fb4fc-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="fb4fc-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="fb4fc-113">.NET İndir</span><span class="sxs-lookup"><span data-stu-id="fb4fc-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="fb4fc-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="fb4fc-114">Supported releases</span></span>

<span data-ttu-id="fb4fc-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="fb4fc-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="fb4fc-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="fb4fc-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="fb4fc-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="fb4fc-120">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-121">Operating System</span><span class="sxs-lookup"><span data-stu-id="fb4fc-121">Operating System</span></span>            | <span data-ttu-id="fb4fc-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-122">.NET Core 2.1</span></span> | <span data-ttu-id="fb4fc-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-123">.NET Core 3.1</span></span> | <span data-ttu-id="fb4fc-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="fb4fc-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="fb4fc-125">Windows 10, sürüm 20H2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="fb4fc-126">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-126">✔️</span></span>           | <span data-ttu-id="fb4fc-127">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-127">✔️</span></span>            | <span data-ttu-id="fb4fc-128">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-128">✔️</span></span>    |
| <span data-ttu-id="fb4fc-129">Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="fb4fc-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="fb4fc-130">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-130">✔️</span></span>           | <span data-ttu-id="fb4fc-131">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-131">✔️</span></span>            | <span data-ttu-id="fb4fc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-132">✔️</span></span>    |
| <span data-ttu-id="fb4fc-133">Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="fb4fc-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="fb4fc-134">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-134">✔️</span></span>           | <span data-ttu-id="fb4fc-135">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-135">✔️</span></span>            | <span data-ttu-id="fb4fc-136">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-136">✔️</span></span>    |
| <span data-ttu-id="fb4fc-137">Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="fb4fc-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="fb4fc-138">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-138">✔️</span></span>           | <span data-ttu-id="fb4fc-139">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-139">✔️</span></span>            | <span data-ttu-id="fb4fc-140">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-140">✔️</span></span>    |
| <span data-ttu-id="fb4fc-141">Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="fb4fc-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="fb4fc-142">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-142">✔️</span></span>           | <span data-ttu-id="fb4fc-143">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-143">✔️</span></span>            | <span data-ttu-id="fb4fc-144">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-144">✔️</span></span>    |
| <span data-ttu-id="fb4fc-145">Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="fb4fc-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="fb4fc-146">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-146">✔️</span></span>           | <span data-ttu-id="fb4fc-147">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-147">✔️</span></span>            | <span data-ttu-id="fb4fc-148">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-148">✔️</span></span>    |
| <span data-ttu-id="fb4fc-149">Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="fb4fc-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="fb4fc-150">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-150">✔️</span></span>           | <span data-ttu-id="fb4fc-151">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-151">✔️</span></span>            | <span data-ttu-id="fb4fc-152">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-152">✔️</span></span>    |
| <span data-ttu-id="fb4fc-153">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="fb4fc-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="fb4fc-154">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-154">✔️</span></span>           | <span data-ttu-id="fb4fc-155">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-155">✔️</span></span>            | <span data-ttu-id="fb4fc-156">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-156">✔️</span></span>    |
| <span data-ttu-id="fb4fc-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-157">Windows 8.1</span></span>                 | <span data-ttu-id="fb4fc-158">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-158">✔️</span></span>           | <span data-ttu-id="fb4fc-159">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-159">✔️</span></span>            | <span data-ttu-id="fb4fc-160">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-160">✔️</span></span>    |
| <span data-ttu-id="fb4fc-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="fb4fc-162">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-162">✔️</span></span>           | <span data-ttu-id="fb4fc-163">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-163">✔️</span></span>            | <span data-ttu-id="fb4fc-164">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-164">✔️</span></span>    |
| <span data-ttu-id="fb4fc-165">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="fb4fc-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="fb4fc-166">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-166">✔️</span></span>           | <span data-ttu-id="fb4fc-167">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-167">✔️</span></span>            | <span data-ttu-id="fb4fc-168">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-168">✔️</span></span>    |
| <span data-ttu-id="fb4fc-169">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="fb4fc-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="fb4fc-170">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-170">✔️</span></span>           | <span data-ttu-id="fb4fc-171">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-171">✔️</span></span>            | <span data-ttu-id="fb4fc-172">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-172">✔️</span></span>    |
| <span data-ttu-id="fb4fc-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="fb4fc-174">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-174">✔️</span></span>           | <span data-ttu-id="fb4fc-175">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-175">✔️</span></span>            | <span data-ttu-id="fb4fc-176">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-176">✔️</span></span>    |
| <span data-ttu-id="fb4fc-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="fb4fc-178">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-178">✔️</span></span>           | <span data-ttu-id="fb4fc-179">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-179">✔️</span></span>            | <span data-ttu-id="fb4fc-180">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-180">✔️</span></span>    |
| <span data-ttu-id="fb4fc-181">Nano sunucu, sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="fb4fc-182">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-182">✔️</span></span>           | <span data-ttu-id="fb4fc-183">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-183">✔️</span></span>            | <span data-ttu-id="fb4fc-184">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-184">✔️</span></span>    |
| <span data-ttu-id="fb4fc-185">Nano sunucu, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="fb4fc-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="fb4fc-186">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-186">✔️</span></span>           | <span data-ttu-id="fb4fc-187">✔️</span><span class="sxs-lookup"><span data-stu-id="fb4fc-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="fb4fc-188">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="fb4fc-188">Unsupported releases</span></span>

<span data-ttu-id="fb4fc-189">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="fb4fc-190">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-190">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fb4fc-191">3,0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-191">3.0</span></span>
- <span data-ttu-id="fb4fc-192">2.2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-192">2.2</span></span>
- <span data-ttu-id="fb4fc-193">2.0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="fb4fc-194">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-194">Runtime information</span></span>

<span data-ttu-id="fb4fc-195">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="fb4fc-196">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="fb4fc-197">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="fb4fc-198">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="fb4fc-199">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="fb4fc-200">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="fb4fc-201">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="fb4fc-202">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-202">*Desktop runtime*</span></span>\
<span data-ttu-id="fb4fc-203">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="fb4fc-204">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="fb4fc-205">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-205">*.NET runtime*</span></span>\
<span data-ttu-id="fb4fc-206">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="fb4fc-207">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="fb4fc-208">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="fb4fc-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="fb4fc-209">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-209">SDK information</span></span>

<span data-ttu-id="fb4fc-210">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="fb4fc-211">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="fb4fc-212">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="fb4fc-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="fb4fc-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="fb4fc-214">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="fb4fc-215">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-216">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-216">OS</span></span>                  | <span data-ttu-id="fb4fc-217">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-217">Version</span></span>       | <span data-ttu-id="fb4fc-218">Mimariler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="fb4fc-219">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-219">Windows 10 Client</span></span>   | <span data-ttu-id="fb4fc-220">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-220">Version 1607+</span></span> | <span data-ttu-id="fb4fc-221">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="fb4fc-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="fb4fc-222">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-222">Windows Client</span></span>      | <span data-ttu-id="fb4fc-223">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="fb4fc-224">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-224">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fb4fc-225">Windows Server</span></span>      | <span data-ttu-id="fb4fc-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-226">2012 R2+</span></span>      | <span data-ttu-id="fb4fc-227">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-227">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-228">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="fb4fc-228">Windows Server Core</span></span> | <span data-ttu-id="fb4fc-229">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-229">2012 R2+</span></span>      | <span data-ttu-id="fb4fc-230">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-230">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-231">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="fb4fc-231">Nano Server</span></span>         | <span data-ttu-id="fb4fc-232">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-232">Version 1809+</span></span> | <span data-ttu-id="fb4fc-233">x64</span><span class="sxs-lookup"><span data-stu-id="fb4fc-233">x64</span></span>             |

<span data-ttu-id="fb4fc-234">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="fb4fc-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="fb4fc-236">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fb4fc-237">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-238">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-238">OS</span></span>                            | <span data-ttu-id="fb4fc-239">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-239">Version</span></span>                        | <span data-ttu-id="fb4fc-240">Mimariler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fb4fc-241">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-241">Windows Client</span></span>                | <span data-ttu-id="fb4fc-242">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fb4fc-243">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-243">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-244">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-244">Windows 10 Client</span></span>             | <span data-ttu-id="fb4fc-245">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-245">Version 1607+</span></span>                  | <span data-ttu-id="fb4fc-246">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-246">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fb4fc-247">Windows Server</span></span>                | <span data-ttu-id="fb4fc-248">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-248">2012 R2+</span></span>                       | <span data-ttu-id="fb4fc-249">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-249">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-250">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="fb4fc-250">Nano Server</span></span>                   | <span data-ttu-id="fb4fc-251">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-251">Version 1803+</span></span>                  | <span data-ttu-id="fb4fc-252">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fb4fc-252">x64, ARM32</span></span>      |

<span data-ttu-id="fb4fc-253">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="fb4fc-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fb4fc-255">*.NET Core 3,0 şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="fb4fc-256">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="fb4fc-257">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-258">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-258">OS</span></span>                            | <span data-ttu-id="fb4fc-259">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-259">Version</span></span>                        | <span data-ttu-id="fb4fc-260">Mimariler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fb4fc-261">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-261">Windows Client</span></span>                | <span data-ttu-id="fb4fc-262">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fb4fc-263">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-263">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-264">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-264">Windows 10 Client</span></span>             | <span data-ttu-id="fb4fc-265">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-265">Version 1607+</span></span>                  | <span data-ttu-id="fb4fc-266">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-266">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fb4fc-267">Windows Server</span></span>                | <span data-ttu-id="fb4fc-268">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-268">2012 R2+</span></span>                       | <span data-ttu-id="fb4fc-269">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-269">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-270">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="fb4fc-270">Nano Server</span></span>                   | <span data-ttu-id="fb4fc-271">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-271">Version 1803+</span></span>                  | <span data-ttu-id="fb4fc-272">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fb4fc-272">x64, ARM32</span></span>      |

<span data-ttu-id="fb4fc-273">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="fb4fc-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fb4fc-275">*.NET Core 2,2 Şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="fb4fc-276">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="fb4fc-277">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-278">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-278">OS</span></span>                            | <span data-ttu-id="fb4fc-279">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-279">Version</span></span>                        | <span data-ttu-id="fb4fc-280">Mimariler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fb4fc-281">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-281">Windows Client</span></span>                | <span data-ttu-id="fb4fc-282">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fb4fc-283">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-283">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-284">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-284">Windows 10 Client</span></span>             | <span data-ttu-id="fb4fc-285">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-285">Version 1607+</span></span>                  | <span data-ttu-id="fb4fc-286">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-286">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fb4fc-287">Windows Server</span></span>                | <span data-ttu-id="fb4fc-288">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fb4fc-289">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-289">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-290">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="fb4fc-290">Nano Server</span></span>                   | <span data-ttu-id="fb4fc-291">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-291">Version 1803+</span></span>                   | <span data-ttu-id="fb4fc-292">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fb4fc-292">x64, ARM32</span></span>      |

<span data-ttu-id="fb4fc-293">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="fb4fc-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fb4fc-295">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fb4fc-296">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fb4fc-297">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-297">OS</span></span>                            | <span data-ttu-id="fb4fc-298">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-298">Version</span></span>                        | <span data-ttu-id="fb4fc-299">Mimariler</span><span class="sxs-lookup"><span data-stu-id="fb4fc-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fb4fc-300">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-300">Windows Client</span></span>                | <span data-ttu-id="fb4fc-301">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fb4fc-302">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-302">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-303">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-303">Windows 10 Client</span></span>             | <span data-ttu-id="fb4fc-304">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-304">Version 1607+</span></span>                  | <span data-ttu-id="fb4fc-305">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-305">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="fb4fc-306">Windows Server</span></span>                | <span data-ttu-id="fb4fc-307">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fb4fc-308">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fb4fc-308">x64, x86</span></span>        |
| <span data-ttu-id="fb4fc-309">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="fb4fc-309">Nano Server</span></span>                   | <span data-ttu-id="fb4fc-310">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="fb4fc-310">Version 1803+</span></span>                  | <span data-ttu-id="fb4fc-311">x64</span><span class="sxs-lookup"><span data-stu-id="fb4fc-311">x64,</span></span>            |

<span data-ttu-id="fb4fc-312">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="fb4fc-313">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="fb4fc-314">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız daha fazla bağımlılık gerekir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-314">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="fb4fc-315">Operating System</span><span class="sxs-lookup"><span data-stu-id="fb4fc-315">Operating System</span></span>         | <span data-ttu-id="fb4fc-316">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="fb4fc-316">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="fb4fc-317">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-317">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="fb4fc-318">-Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-318">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="fb4fc-319">-KB3063858 [64-bit][kb64]  /  [32-bit][kb32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-319">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="fb4fc-320">- [MicrosoftRootCertificateAuthority2011. cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) (yalnızca .net Core 2,1)</span><span class="sxs-lookup"><span data-stu-id="fb4fc-320">- [MicrosoftRootCertificateAuthority2011.cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) (.NET Core 2.1 only)</span></span> |
| <span data-ttu-id="fb4fc-321">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-321">Windows Vista SP 2</span></span>       | <span data-ttu-id="fb4fc-322">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="fb4fc-323">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-323">Windows 8.1</span></span>              | <span data-ttu-id="fb4fc-324">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="fb4fc-325">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-325">Windows Server 2008 R2</span></span>   | <span data-ttu-id="fb4fc-326">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="fb4fc-327">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-327">Windows Server 2012 R2</span></span>   | <span data-ttu-id="fb4fc-328">Microsoft Visual C++ 2015-2019 yeniden dağıtılabilir [64-bit][vcc64]  /  [32-bit][vcc32]</span><span class="sxs-lookup"><span data-stu-id="fb4fc-328">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="fb4fc-329">Aşağıdaki dll 'lerden biriyle ilgili bir hata alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-329">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="fb4fc-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="fb4fc-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="fb4fc-332">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="fb4fc-332">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="fb4fc-333">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="fb4fc-333">Install with PowerShell automation</span></span>

<span data-ttu-id="fb4fc-334">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-334">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="fb4fc-335">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-335">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="fb4fc-336">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-336">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="fb4fc-337">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="fb4fc-337">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="fb4fc-338">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-338">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="fb4fc-339">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-339">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="fb4fc-340">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="fb4fc-340">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="fb4fc-341">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-341">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="fb4fc-342">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="fb4fc-342">Install with Visual Studio</span></span>

<span data-ttu-id="fb4fc-343">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-343">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="fb4fc-344">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="fb4fc-344">.NET SDK version</span></span>      | <span data-ttu-id="fb4fc-345">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="fb4fc-345">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="fb4fc-346">5.0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-346">5.0</span></span>                   | <span data-ttu-id="fb4fc-347">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-347">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="fb4fc-348">3,1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-348">3.1</span></span>                   | <span data-ttu-id="fb4fc-349">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-349">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="fb4fc-350">3,0</span><span class="sxs-lookup"><span data-stu-id="fb4fc-350">3.0</span></span>                   | <span data-ttu-id="fb4fc-351">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-351">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="fb4fc-352">2.2</span><span class="sxs-lookup"><span data-stu-id="fb4fc-352">2.2</span></span>                   | <span data-ttu-id="fb4fc-353">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-353">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="fb4fc-354">2.1</span><span class="sxs-lookup"><span data-stu-id="fb4fc-354">2.1</span></span>                   | <span data-ttu-id="fb4fc-355">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-355">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="fb4fc-356">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-356">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="fb4fc-357">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-357">Open Visual Studio.</span></span>
01. <span data-ttu-id="fb4fc-358">  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-358">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="fb4fc-359">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-359">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="fb4fc-360">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-360">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="fb4fc-361">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-361">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="fb4fc-362">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="fb4fc-362">Select a workload</span></span>

<span data-ttu-id="fb4fc-363">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-363">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="fb4fc-364">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-364">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="fb4fc-365">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-365">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="fb4fc-366">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-366">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="fb4fc-367">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-367">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="fb4fc-368">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="fb4fc-368">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="fb4fc-369">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="fb4fc-369">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="fb4fc-370">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-370">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="fb4fc-371">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-371">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="fb4fc-372">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-372">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="fb4fc-373">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-373">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="fb4fc-374">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-374">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="fb4fc-375">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-375">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="fb4fc-376">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="fb4fc-376">Windows Installer</span></span>

<span data-ttu-id="fb4fc-377">.NET için [karşıdan yükleme sayfası](https://dotnet.microsoft.com/download/dotnet-core) Windows ınstaller yürütülebilir dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-377">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="fb4fc-378">.NET yüklemek için Windows yükleyicilerini kullandığınızda, ve parametrelerini ayarlayarak yükleme yolunu özelleştirebilirsiniz `DOTNETHOME_X64` `DOTNETHOME_X86` :</span><span class="sxs-lookup"><span data-stu-id="fb4fc-378">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="fb4fc-379">.NET 'i bir üretim ortamında veya sürekli tümleştirmeyi destekleyecek şekilde sessizce yüklemek istiyorsanız aşağıdaki anahtarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-379">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="fb4fc-380">.NET 'i yükleme.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-380">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="fb4fc-381">Tüm UI ve istemlerin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-381">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="fb4fc-382">Yeniden başlatma girişimlerini engeller.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-382">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="fb4fc-383">Daha fazla bilgi için bkz. [Standart yükleyici Command-Line seçenekleri](/windows/win32/msi/standard-installer-command-line-options).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-383">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="fb4fc-384">Yükleyici, başarılı için 0 çıkış kodu ve bir yeniden başlatmanın gerekli olduğunu göstermek için 3010 çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-384">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="fb4fc-385">Diğer herhangi bir değer genellikle bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-385">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="fb4fc-386">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="fb4fc-386">Download and manually install</span></span>

<span data-ttu-id="fb4fc-387">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-387">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="fb4fc-388">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-388">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="fb4fc-389">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-389">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="fb4fc-390">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-390">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="fb4fc-391">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-391">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="fb4fc-392">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-392">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="fb4fc-393">.NET 5,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-393">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="fb4fc-394">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-394">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="fb4fc-395">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-395">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="fb4fc-396">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="fb4fc-396">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="fb4fc-397">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="fb4fc-397">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="fb4fc-398">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-398">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="fb4fc-399">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-399">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="fb4fc-400">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fb4fc-400">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="fb4fc-401">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-401">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="fb4fc-402">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-402">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="fb4fc-403">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-403">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="fb4fc-404">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-404">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="fb4fc-405">Docker</span><span class="sxs-lookup"><span data-stu-id="fb4fc-405">Docker</span></span>

<span data-ttu-id="fb4fc-406">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-406">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="fb4fc-407">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-407">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="fb4fc-408">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-408">.NET can run in a Docker container.</span></span> <span data-ttu-id="fb4fc-409">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-409">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="fb4fc-410">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-410">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="fb4fc-411">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-411">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="fb4fc-412">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-412">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="fb4fc-413">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-413">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb4fc-414">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fb4fc-414">Next steps</span></span>

- <span data-ttu-id="fb4fc-415">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-415">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="fb4fc-416">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-416">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="fb4fc-417">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fb4fc-417">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="fb4fc-418">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="fb4fc-418">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/en-us/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/en-us/download/details.aspx?id=47409
