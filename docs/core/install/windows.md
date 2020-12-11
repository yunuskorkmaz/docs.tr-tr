---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b5c0949bbd591906536094a33d8583a265d8a4c8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110240"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="5507a-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="5507a-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="5507a-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5507a-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="5507a-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="5507a-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="5507a-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="5507a-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5507a-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="5507a-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5507a-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="5507a-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5507a-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="5507a-113">.NET İndir</span><span class="sxs-lookup"><span data-stu-id="5507a-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="5507a-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="5507a-114">Supported releases</span></span>

<span data-ttu-id="5507a-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5507a-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="5507a-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="5507a-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="5507a-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="5507a-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="5507a-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="5507a-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="5507a-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="5507a-120">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-121">Operating System</span><span class="sxs-lookup"><span data-stu-id="5507a-121">Operating System</span></span>            | <span data-ttu-id="5507a-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5507a-122">.NET Core 2.1</span></span> | <span data-ttu-id="5507a-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5507a-123">.NET Core 3.1</span></span> | <span data-ttu-id="5507a-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="5507a-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="5507a-125">Windows 10, sürüm 20H2</span><span class="sxs-lookup"><span data-stu-id="5507a-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="5507a-126">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-126">✔️</span></span>           | <span data-ttu-id="5507a-127">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-127">✔️</span></span>            | <span data-ttu-id="5507a-128">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-128">✔️</span></span>    |
| <span data-ttu-id="5507a-129">Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="5507a-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="5507a-130">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-130">✔️</span></span>           | <span data-ttu-id="5507a-131">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-131">✔️</span></span>            | <span data-ttu-id="5507a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-132">✔️</span></span>    |
| <span data-ttu-id="5507a-133">Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="5507a-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="5507a-134">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-134">✔️</span></span>           | <span data-ttu-id="5507a-135">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-135">✔️</span></span>            | <span data-ttu-id="5507a-136">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-136">✔️</span></span>    |
| <span data-ttu-id="5507a-137">Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="5507a-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="5507a-138">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-138">✔️</span></span>           | <span data-ttu-id="5507a-139">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-139">✔️</span></span>            | <span data-ttu-id="5507a-140">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-140">✔️</span></span>    |
| <span data-ttu-id="5507a-141">Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="5507a-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="5507a-142">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-142">✔️</span></span>           | <span data-ttu-id="5507a-143">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-143">✔️</span></span>            | <span data-ttu-id="5507a-144">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-144">✔️</span></span>    |
| <span data-ttu-id="5507a-145">Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="5507a-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="5507a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-146">✔️</span></span>           | <span data-ttu-id="5507a-147">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-147">✔️</span></span>            | <span data-ttu-id="5507a-148">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-148">✔️</span></span>    |
| <span data-ttu-id="5507a-149">Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="5507a-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="5507a-150">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-150">✔️</span></span>           | <span data-ttu-id="5507a-151">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-151">✔️</span></span>            | <span data-ttu-id="5507a-152">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-152">✔️</span></span>    |
| <span data-ttu-id="5507a-153">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="5507a-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="5507a-154">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-154">✔️</span></span>           | <span data-ttu-id="5507a-155">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-155">✔️</span></span>            | <span data-ttu-id="5507a-156">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-156">✔️</span></span>    |
| <span data-ttu-id="5507a-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5507a-157">Windows 8.1</span></span>                 | <span data-ttu-id="5507a-158">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-158">✔️</span></span>           | <span data-ttu-id="5507a-159">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-159">✔️</span></span>            | <span data-ttu-id="5507a-160">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-160">✔️</span></span>    |
| <span data-ttu-id="5507a-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="5507a-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="5507a-162">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-162">✔️</span></span>           | <span data-ttu-id="5507a-163">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-163">✔️</span></span>            | <span data-ttu-id="5507a-164">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-164">✔️</span></span>    |
| <span data-ttu-id="5507a-165">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="5507a-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="5507a-166">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-166">✔️</span></span>           | <span data-ttu-id="5507a-167">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-167">✔️</span></span>            | <span data-ttu-id="5507a-168">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-168">✔️</span></span>    |
| <span data-ttu-id="5507a-169">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="5507a-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="5507a-170">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-170">✔️</span></span>           | <span data-ttu-id="5507a-171">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-171">✔️</span></span>            | <span data-ttu-id="5507a-172">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-172">✔️</span></span>    |
| <span data-ttu-id="5507a-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5507a-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="5507a-174">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-174">✔️</span></span>           | <span data-ttu-id="5507a-175">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-175">✔️</span></span>            | <span data-ttu-id="5507a-176">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-176">✔️</span></span>    |
| <span data-ttu-id="5507a-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5507a-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="5507a-178">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-178">✔️</span></span>           | <span data-ttu-id="5507a-179">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-179">✔️</span></span>            | <span data-ttu-id="5507a-180">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-180">✔️</span></span>    |
| <span data-ttu-id="5507a-181">Nano sunucu, sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="5507a-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="5507a-182">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-182">✔️</span></span>           | <span data-ttu-id="5507a-183">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-183">✔️</span></span>            | <span data-ttu-id="5507a-184">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-184">✔️</span></span>    |
| <span data-ttu-id="5507a-185">Nano sunucu, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="5507a-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="5507a-186">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-186">✔️</span></span>           | <span data-ttu-id="5507a-187">✔️</span><span class="sxs-lookup"><span data-stu-id="5507a-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="5507a-188">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="5507a-188">Unsupported releases</span></span>

<span data-ttu-id="5507a-189">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="5507a-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="5507a-190">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="5507a-190">The downloads for these still remain published:</span></span>

- <span data-ttu-id="5507a-191">3,0</span><span class="sxs-lookup"><span data-stu-id="5507a-191">3.0</span></span>
- <span data-ttu-id="5507a-192">2.2</span><span class="sxs-lookup"><span data-stu-id="5507a-192">2.2</span></span>
- <span data-ttu-id="5507a-193">2,0</span><span class="sxs-lookup"><span data-stu-id="5507a-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="5507a-194">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="5507a-194">Runtime information</span></span>

<span data-ttu-id="5507a-195">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5507a-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="5507a-196">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="5507a-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="5507a-197">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="5507a-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="5507a-198">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="5507a-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="5507a-199">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="5507a-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="5507a-200">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5507a-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="5507a-201">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="5507a-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="5507a-202">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="5507a-202">*Desktop runtime*</span></span>\
<span data-ttu-id="5507a-203">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5507a-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="5507a-204">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="5507a-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="5507a-205">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="5507a-205">*.NET runtime*</span></span>\
<span data-ttu-id="5507a-206">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="5507a-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="5507a-207">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="5507a-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="5507a-208">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="5507a-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="5507a-209">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="5507a-209">SDK information</span></span>

<span data-ttu-id="5507a-210">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5507a-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="5507a-211">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="5507a-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="5507a-212">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="5507a-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="5507a-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="5507a-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="5507a-214">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5507a-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="5507a-215">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-216">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="5507a-216">OS</span></span>                  | <span data-ttu-id="5507a-217">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-217">Version</span></span>       | <span data-ttu-id="5507a-218">Mimariler</span><span class="sxs-lookup"><span data-stu-id="5507a-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="5507a-219">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-219">Windows 10 Client</span></span>   | <span data-ttu-id="5507a-220">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="5507a-220">Version 1607+</span></span> | <span data-ttu-id="5507a-221">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="5507a-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="5507a-222">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-222">Windows Client</span></span>      | <span data-ttu-id="5507a-223">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5507a-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="5507a-224">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-224">x64, x86</span></span>        |
| <span data-ttu-id="5507a-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5507a-225">Windows Server</span></span>      | <span data-ttu-id="5507a-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="5507a-226">2012 R2+</span></span>      | <span data-ttu-id="5507a-227">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-227">x64, x86</span></span>        |
| <span data-ttu-id="5507a-228">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="5507a-228">Windows Server Core</span></span> | <span data-ttu-id="5507a-229">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="5507a-229">2012 R2+</span></span>      | <span data-ttu-id="5507a-230">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-230">x64, x86</span></span>        |
| <span data-ttu-id="5507a-231">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="5507a-231">Nano Server</span></span>         | <span data-ttu-id="5507a-232">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="5507a-232">Version 1809+</span></span> | <span data-ttu-id="5507a-233">x64</span><span class="sxs-lookup"><span data-stu-id="5507a-233">x64</span></span>             |

<span data-ttu-id="5507a-234">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="5507a-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5507a-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="5507a-236">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5507a-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5507a-237">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-238">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="5507a-238">OS</span></span>                            | <span data-ttu-id="5507a-239">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-239">Version</span></span>                        | <span data-ttu-id="5507a-240">Mimariler</span><span class="sxs-lookup"><span data-stu-id="5507a-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5507a-241">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-241">Windows Client</span></span>                | <span data-ttu-id="5507a-242">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5507a-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5507a-243">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-243">x64, x86</span></span>        |
| <span data-ttu-id="5507a-244">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-244">Windows 10 Client</span></span>             | <span data-ttu-id="5507a-245">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="5507a-245">Version 1607+</span></span>                  | <span data-ttu-id="5507a-246">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-246">x64, x86</span></span>        |
| <span data-ttu-id="5507a-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5507a-247">Windows Server</span></span>                | <span data-ttu-id="5507a-248">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="5507a-248">2012 R2+</span></span>                       | <span data-ttu-id="5507a-249">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-249">x64, x86</span></span>        |
| <span data-ttu-id="5507a-250">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="5507a-250">Nano Server</span></span>                   | <span data-ttu-id="5507a-251">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="5507a-251">Version 1803+</span></span>                  | <span data-ttu-id="5507a-252">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5507a-252">x64, ARM32</span></span>      |

<span data-ttu-id="5507a-253">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="5507a-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5507a-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5507a-255">*.NET Core 3,0 şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5507a-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5507a-256">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5507a-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="5507a-257">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-258">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="5507a-258">OS</span></span>                            | <span data-ttu-id="5507a-259">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-259">Version</span></span>                        | <span data-ttu-id="5507a-260">Mimariler</span><span class="sxs-lookup"><span data-stu-id="5507a-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5507a-261">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-261">Windows Client</span></span>                | <span data-ttu-id="5507a-262">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5507a-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5507a-263">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-263">x64, x86</span></span>        |
| <span data-ttu-id="5507a-264">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-264">Windows 10 Client</span></span>             | <span data-ttu-id="5507a-265">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="5507a-265">Version 1607+</span></span>                  | <span data-ttu-id="5507a-266">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-266">x64, x86</span></span>        |
| <span data-ttu-id="5507a-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5507a-267">Windows Server</span></span>                | <span data-ttu-id="5507a-268">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="5507a-268">2012 R2+</span></span>                       | <span data-ttu-id="5507a-269">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-269">x64, x86</span></span>        |
| <span data-ttu-id="5507a-270">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="5507a-270">Nano Server</span></span>                   | <span data-ttu-id="5507a-271">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="5507a-271">Version 1803+</span></span>                  | <span data-ttu-id="5507a-272">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5507a-272">x64, ARM32</span></span>      |

<span data-ttu-id="5507a-273">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="5507a-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5507a-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5507a-275">*.NET Core 2,2 Şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5507a-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5507a-276">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5507a-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="5507a-277">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-278">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="5507a-278">OS</span></span>                            | <span data-ttu-id="5507a-279">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-279">Version</span></span>                        | <span data-ttu-id="5507a-280">Mimariler</span><span class="sxs-lookup"><span data-stu-id="5507a-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5507a-281">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-281">Windows Client</span></span>                | <span data-ttu-id="5507a-282">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5507a-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5507a-283">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-283">x64, x86</span></span>        |
| <span data-ttu-id="5507a-284">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-284">Windows 10 Client</span></span>             | <span data-ttu-id="5507a-285">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="5507a-285">Version 1607+</span></span>                  | <span data-ttu-id="5507a-286">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-286">x64, x86</span></span>        |
| <span data-ttu-id="5507a-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5507a-287">Windows Server</span></span>                | <span data-ttu-id="5507a-288">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="5507a-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5507a-289">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-289">x64, x86</span></span>        |
| <span data-ttu-id="5507a-290">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="5507a-290">Nano Server</span></span>                   | <span data-ttu-id="5507a-291">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="5507a-291">Version 1803+</span></span>                   | <span data-ttu-id="5507a-292">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5507a-292">x64, ARM32</span></span>      |

<span data-ttu-id="5507a-293">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="5507a-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5507a-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5507a-295">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="5507a-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5507a-296">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5507a-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5507a-297">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="5507a-297">OS</span></span>                            | <span data-ttu-id="5507a-298">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-298">Version</span></span>                        | <span data-ttu-id="5507a-299">Mimariler</span><span class="sxs-lookup"><span data-stu-id="5507a-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5507a-300">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-300">Windows Client</span></span>                | <span data-ttu-id="5507a-301">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5507a-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5507a-302">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-302">x64, x86</span></span>        |
| <span data-ttu-id="5507a-303">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="5507a-303">Windows 10 Client</span></span>             | <span data-ttu-id="5507a-304">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="5507a-304">Version 1607+</span></span>                  | <span data-ttu-id="5507a-305">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-305">x64, x86</span></span>        |
| <span data-ttu-id="5507a-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5507a-306">Windows Server</span></span>                | <span data-ttu-id="5507a-307">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="5507a-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5507a-308">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5507a-308">x64, x86</span></span>        |
| <span data-ttu-id="5507a-309">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="5507a-309">Nano Server</span></span>                   | <span data-ttu-id="5507a-310">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="5507a-310">Version 1803+</span></span>                  | <span data-ttu-id="5507a-311">x64</span><span class="sxs-lookup"><span data-stu-id="5507a-311">x64,</span></span>            |

<span data-ttu-id="5507a-312">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="5507a-313">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5507a-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="5507a-314">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5507a-314">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="5507a-315">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="5507a-315">Windows 7 SP1 [ESU][esu]</span></span>
- <span data-ttu-id="5507a-316">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="5507a-316">Windows Vista SP 2</span></span>
- <span data-ttu-id="5507a-317">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5507a-317">Windows 8.1</span></span>
- <span data-ttu-id="5507a-318">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5507a-318">Windows Server 2008 R2</span></span>
- <span data-ttu-id="5507a-319">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5507a-319">Windows Server 2012 R2</span></span>

<span data-ttu-id="5507a-320">Aşağıdakileri yükleyerek:</span><span class="sxs-lookup"><span data-stu-id="5507a-320">Install the following:</span></span>

- <span data-ttu-id="5507a-321">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="5507a-321">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="5507a-322">KB2533623</span><span class="sxs-lookup"><span data-stu-id="5507a-322">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="5507a-323">Aşağıdaki hatalardan birini alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5507a-323">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="5507a-324">Bilgisayarınızda *api-ms-win-crt-runtime-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5507a-324">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="5507a-325">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="5507a-325">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="5507a-326">\- veya</span><span class="sxs-lookup"><span data-stu-id="5507a-326">\- or -</span></span>
>
> <span data-ttu-id="5507a-327">Bilgisayarınızda *api-ms-win-cor-timezone-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5507a-327">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="5507a-328">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="5507a-328">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="5507a-329">\- veya</span><span class="sxs-lookup"><span data-stu-id="5507a-329">\- or -</span></span>
>
> <span data-ttu-id="5507a-330">Kitaplık *hostfxr.dll* bulundu, ancak *C: \\ \<path_to_app> \\hostfxr.dll* öğesinden yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="5507a-330">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="5507a-331">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="5507a-331">Install with PowerShell automation</span></span>

<span data-ttu-id="5507a-332">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5507a-332">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="5507a-333">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5507a-333">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="5507a-334">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="5507a-334">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="5507a-335">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="5507a-335">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="5507a-336">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5507a-336">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="5507a-337">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="5507a-337">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="5507a-338">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="5507a-338">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="5507a-339">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5507a-339">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="5507a-340">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="5507a-340">Install with Visual Studio</span></span>

<span data-ttu-id="5507a-341">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5507a-341">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="5507a-342">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="5507a-342">.NET SDK version</span></span>      | <span data-ttu-id="5507a-343">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="5507a-343">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="5507a-344">5.0</span><span class="sxs-lookup"><span data-stu-id="5507a-344">5.0</span></span>                   | <span data-ttu-id="5507a-345">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="5507a-345">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="5507a-346">3,1</span><span class="sxs-lookup"><span data-stu-id="5507a-346">3.1</span></span>                   | <span data-ttu-id="5507a-347">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="5507a-347">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="5507a-348">3,0</span><span class="sxs-lookup"><span data-stu-id="5507a-348">3.0</span></span>                   | <span data-ttu-id="5507a-349">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="5507a-349">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="5507a-350">2.2</span><span class="sxs-lookup"><span data-stu-id="5507a-350">2.2</span></span>                   | <span data-ttu-id="5507a-351">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="5507a-351">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="5507a-352">2.1</span><span class="sxs-lookup"><span data-stu-id="5507a-352">2.1</span></span>                   | <span data-ttu-id="5507a-353">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="5507a-353">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="5507a-354">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5507a-354">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="5507a-355">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="5507a-355">Open Visual Studio.</span></span>
01. <span data-ttu-id="5507a-356">  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="5507a-356">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="5507a-357">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="5507a-357">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="5507a-358">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-358">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="5507a-359">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="5507a-359">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="5507a-360">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="5507a-360">Select a workload</span></span>

<span data-ttu-id="5507a-361">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="5507a-361">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="5507a-362">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="5507a-362">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="5507a-363">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="5507a-363">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="5507a-364">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="5507a-364">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="5507a-365">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="5507a-365">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="5507a-366">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="5507a-366">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="5507a-367">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="5507a-367">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="5507a-368">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="5507a-368">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="5507a-369">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-369">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="5507a-370">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="5507a-370">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="5507a-371">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="5507a-371">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="5507a-372">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5507a-372">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="5507a-373">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="5507a-373">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="5507a-374">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="5507a-374">Windows Installer</span></span>

<span data-ttu-id="5507a-375">.NET için [karşıdan yükleme sayfası](https://dotnet.microsoft.com/download/dotnet-core) Windows ınstaller yürütülebilir dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5507a-375">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="5507a-376">.NET< yüklemek için MSI dosyalarını kullandığınızda, ve parametrelerini ayarlayarak yükleme yolunu özelleştirebilirsiniz `DOTNETHOME_X64` `DOTNETHOME_X86` :</span><span class="sxs-lookup"><span data-stu-id="5507a-376">When you use the MSI files to install .NET< you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a><span data-ttu-id="5507a-377">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="5507a-377">Download and manually install</span></span>

<span data-ttu-id="5507a-378">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5507a-378">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="5507a-379">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-379">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="5507a-380">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="5507a-380">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="5507a-381">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-381">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="5507a-382">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5507a-382">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="5507a-383">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="5507a-383">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="5507a-384">.NET 5,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="5507a-384">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="5507a-385">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="5507a-385">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="5507a-386">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="5507a-386">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="5507a-387">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="5507a-387">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="5507a-388">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="5507a-388">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="5507a-389">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="5507a-389">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="5507a-390">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5507a-390">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="5507a-391">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5507a-391">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="5507a-392">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5507a-392">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="5507a-393">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="5507a-393">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="5507a-394">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5507a-394">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="5507a-395">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="5507a-395">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="5507a-396">Docker</span><span class="sxs-lookup"><span data-stu-id="5507a-396">Docker</span></span>

<span data-ttu-id="5507a-397">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5507a-397">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="5507a-398">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5507a-398">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="5507a-399">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-399">.NET can run in a Docker container.</span></span> <span data-ttu-id="5507a-400">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5507a-400">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="5507a-401">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5507a-401">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="5507a-402">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5507a-402">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="5507a-403">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5507a-403">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="5507a-404">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="5507a-404">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5507a-405">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5507a-405">Next steps</span></span>

- <span data-ttu-id="5507a-406">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="5507a-406">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="5507a-407">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-407">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="5507a-408">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="5507a-408">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="5507a-409">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="5507a-409">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
