---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 786814549724948fa69b18a05cee966e0940aaf4
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549351"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="f5ad7-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="f5ad7-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="f5ad7-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="f5ad7-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="f5ad7-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="f5ad7-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="f5ad7-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="f5ad7-113">.NET İndir</span><span class="sxs-lookup"><span data-stu-id="f5ad7-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="f5ad7-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="f5ad7-114">Supported releases</span></span>

<span data-ttu-id="f5ad7-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="f5ad7-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="f5ad7-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="f5ad7-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="f5ad7-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="f5ad7-120">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-121">Operating System</span><span class="sxs-lookup"><span data-stu-id="f5ad7-121">Operating System</span></span>            | <span data-ttu-id="f5ad7-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-122">.NET Core 2.1</span></span> | <span data-ttu-id="f5ad7-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-123">.NET Core 3.1</span></span> | <span data-ttu-id="f5ad7-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="f5ad7-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="f5ad7-125">Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="f5ad7-125">Windows 10, Version 2004</span></span>    | <span data-ttu-id="f5ad7-126">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-126">✔️</span></span>           | <span data-ttu-id="f5ad7-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-127">✔️</span></span>            | <span data-ttu-id="f5ad7-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-128">✔️</span></span>    |
| <span data-ttu-id="f5ad7-129">Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="f5ad7-129">Windows 10, Version 1909</span></span>    | <span data-ttu-id="f5ad7-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-130">✔️</span></span>           | <span data-ttu-id="f5ad7-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-131">✔️</span></span>            | <span data-ttu-id="f5ad7-132">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-132">✔️</span></span>    |
| <span data-ttu-id="f5ad7-133">Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="f5ad7-133">Windows 10, Version 1903</span></span>    | <span data-ttu-id="f5ad7-134">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-134">✔️</span></span>           | <span data-ttu-id="f5ad7-135">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-135">✔️</span></span>            | <span data-ttu-id="f5ad7-136">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-136">✔️</span></span>    |
| <span data-ttu-id="f5ad7-137">Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="f5ad7-137">Windows 10, Version 1809</span></span>    | <span data-ttu-id="f5ad7-138">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-138">✔️</span></span>           | <span data-ttu-id="f5ad7-139">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-139">✔️</span></span>            | <span data-ttu-id="f5ad7-140">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-140">✔️</span></span>    |
| <span data-ttu-id="f5ad7-141">Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="f5ad7-141">Windows 10, Version 1803</span></span>    | <span data-ttu-id="f5ad7-142">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-142">✔️</span></span>           | <span data-ttu-id="f5ad7-143">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-143">✔️</span></span>            | <span data-ttu-id="f5ad7-144">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-144">✔️</span></span>    |
| <span data-ttu-id="f5ad7-145">Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="f5ad7-145">Windows 10, Version 1709</span></span>    | <span data-ttu-id="f5ad7-146">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-146">✔️</span></span>           | <span data-ttu-id="f5ad7-147">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-147">✔️</span></span>            | <span data-ttu-id="f5ad7-148">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-148">✔️</span></span>    |
| <span data-ttu-id="f5ad7-149">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="f5ad7-149">Windows 10, Version 1607</span></span>    | <span data-ttu-id="f5ad7-150">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-150">✔️</span></span>           | <span data-ttu-id="f5ad7-151">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-151">✔️</span></span>            | <span data-ttu-id="f5ad7-152">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-152">✔️</span></span>    |
| <span data-ttu-id="f5ad7-153">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-153">Windows 8.1</span></span>                 | <span data-ttu-id="f5ad7-154">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-154">✔️</span></span>           | <span data-ttu-id="f5ad7-155">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-155">✔️</span></span>            | <span data-ttu-id="f5ad7-156">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-156">✔️</span></span>    |
| <span data-ttu-id="f5ad7-157">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="f5ad7-157">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="f5ad7-158">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-158">✔️</span></span>           | <span data-ttu-id="f5ad7-159">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-159">✔️</span></span>            | <span data-ttu-id="f5ad7-160">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-160">✔️</span></span>    |
| <span data-ttu-id="f5ad7-161">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="f5ad7-161">Windows 10, Version 1607</span></span>    | <span data-ttu-id="f5ad7-162">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-162">✔️</span></span>           | <span data-ttu-id="f5ad7-163">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-163">✔️</span></span>            | <span data-ttu-id="f5ad7-164">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-164">✔️</span></span>    |
| <span data-ttu-id="f5ad7-165">Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="f5ad7-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="f5ad7-166">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-166">✔️</span></span>           | <span data-ttu-id="f5ad7-167">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-167">✔️</span></span>            | <span data-ttu-id="f5ad7-168">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-168">✔️</span></span>    |
| <span data-ttu-id="f5ad7-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-169">Windows Server 2012 R2</span></span>      | <span data-ttu-id="f5ad7-170">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-170">✔️</span></span>           | <span data-ttu-id="f5ad7-171">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-171">✔️</span></span>            | <span data-ttu-id="f5ad7-172">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-172">✔️</span></span>    |
| <span data-ttu-id="f5ad7-173">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-173">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="f5ad7-174">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-174">✔️</span></span>           | <span data-ttu-id="f5ad7-175">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-175">✔️</span></span>            | <span data-ttu-id="f5ad7-176">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-176">✔️</span></span>    |
| <span data-ttu-id="f5ad7-177">Nano sunucu, sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-177">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="f5ad7-178">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-178">✔️</span></span>           | <span data-ttu-id="f5ad7-179">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-179">✔️</span></span>            | <span data-ttu-id="f5ad7-180">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-180">✔️</span></span>    |
| <span data-ttu-id="f5ad7-181">Nano sunucu, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="f5ad7-181">Nano Server, Version 1803</span></span>   | <span data-ttu-id="f5ad7-182">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-182">✔️</span></span>           | <span data-ttu-id="f5ad7-183">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ad7-183">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="f5ad7-184">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="f5ad7-184">Unsupported releases</span></span>

<span data-ttu-id="f5ad7-185">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-185">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="f5ad7-186">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-186">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f5ad7-187">3,0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-187">3.0</span></span>
- <span data-ttu-id="f5ad7-188">2.2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-188">2.2</span></span>
- <span data-ttu-id="f5ad7-189">2,0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-189">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="f5ad7-190">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-190">Runtime information</span></span>

<span data-ttu-id="f5ad7-191">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-191">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="f5ad7-192">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-192">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="f5ad7-193">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-193">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="f5ad7-194">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-194">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="f5ad7-195">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="f5ad7-195">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="f5ad7-196">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-196">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="f5ad7-197">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-197">Includes the .NET runtime.</span></span>

<span data-ttu-id="f5ad7-198">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="f5ad7-198">*Desktop runtime*</span></span>\
<span data-ttu-id="f5ad7-199">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-199">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="f5ad7-200">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-200">Includes the .NET runtime.</span></span>

<span data-ttu-id="f5ad7-201">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="f5ad7-201">*.NET runtime*</span></span>\
<span data-ttu-id="f5ad7-202">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-202">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="f5ad7-203">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-203">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="f5ad7-204">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="f5ad7-204">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="f5ad7-205">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-205">SDK information</span></span>

<span data-ttu-id="f5ad7-206">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-206">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="f5ad7-207">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-207">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="f5ad7-208">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="f5ad7-208">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="f5ad7-209">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-209">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="f5ad7-210">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-210">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="f5ad7-211">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-211">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-212">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-212">OS</span></span>                  | <span data-ttu-id="f5ad7-213">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-213">Version</span></span>       | <span data-ttu-id="f5ad7-214">Mimariler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-214">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="f5ad7-215">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-215">Windows 10 Client</span></span>   | <span data-ttu-id="f5ad7-216">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-216">Version 1607+</span></span> | <span data-ttu-id="f5ad7-217">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="f5ad7-217">x64, x86, ARM64</span></span> |
| <span data-ttu-id="f5ad7-218">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-218">Windows Client</span></span>      | <span data-ttu-id="f5ad7-219">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-219">7 SP1+, 8.1</span></span>   | <span data-ttu-id="f5ad7-220">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-220">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-221">Windows Server</span><span class="sxs-lookup"><span data-stu-id="f5ad7-221">Windows Server</span></span>      | <span data-ttu-id="f5ad7-222">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-222">2012 R2+</span></span>      | <span data-ttu-id="f5ad7-223">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-223">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-224">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="f5ad7-224">Windows Server Core</span></span> | <span data-ttu-id="f5ad7-225">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-225">2012 R2+</span></span>      | <span data-ttu-id="f5ad7-226">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-226">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-227">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="f5ad7-227">Nano Server</span></span>         | <span data-ttu-id="f5ad7-228">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-228">Version 1809+</span></span> | <span data-ttu-id="f5ad7-229">x64</span><span class="sxs-lookup"><span data-stu-id="f5ad7-229">x64</span></span>             |

<span data-ttu-id="f5ad7-230">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-230">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="f5ad7-231">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-231">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="f5ad7-232">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-232">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="f5ad7-233">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-233">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-234">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-234">OS</span></span>                            | <span data-ttu-id="f5ad7-235">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-235">Version</span></span>                        | <span data-ttu-id="f5ad7-236">Mimariler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-236">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="f5ad7-237">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-237">Windows Client</span></span>                | <span data-ttu-id="f5ad7-238">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-238">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="f5ad7-239">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-239">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-240">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-240">Windows 10 Client</span></span>             | <span data-ttu-id="f5ad7-241">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-241">Version 1607+</span></span>                  | <span data-ttu-id="f5ad7-242">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-242">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-243">Windows Server</span><span class="sxs-lookup"><span data-stu-id="f5ad7-243">Windows Server</span></span>                | <span data-ttu-id="f5ad7-244">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-244">2012 R2+</span></span>                       | <span data-ttu-id="f5ad7-245">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-245">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-246">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="f5ad7-246">Nano Server</span></span>                   | <span data-ttu-id="f5ad7-247">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-247">Version 1803+</span></span>                  | <span data-ttu-id="f5ad7-248">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="f5ad7-248">x64, ARM32</span></span>      |

<span data-ttu-id="f5ad7-249">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-249">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="f5ad7-250">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-250">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="f5ad7-251">*.NET Core 3,0 şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="f5ad7-251">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="f5ad7-252">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-252">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="f5ad7-253">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-253">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-254">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-254">OS</span></span>                            | <span data-ttu-id="f5ad7-255">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-255">Version</span></span>                        | <span data-ttu-id="f5ad7-256">Mimariler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-256">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="f5ad7-257">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-257">Windows Client</span></span>                | <span data-ttu-id="f5ad7-258">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-258">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="f5ad7-259">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-259">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-260">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-260">Windows 10 Client</span></span>             | <span data-ttu-id="f5ad7-261">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-261">Version 1607+</span></span>                  | <span data-ttu-id="f5ad7-262">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-262">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-263">Windows Server</span><span class="sxs-lookup"><span data-stu-id="f5ad7-263">Windows Server</span></span>                | <span data-ttu-id="f5ad7-264">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-264">2012 R2+</span></span>                       | <span data-ttu-id="f5ad7-265">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-265">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-266">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="f5ad7-266">Nano Server</span></span>                   | <span data-ttu-id="f5ad7-267">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-267">Version 1803+</span></span>                  | <span data-ttu-id="f5ad7-268">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="f5ad7-268">x64, ARM32</span></span>      |

<span data-ttu-id="f5ad7-269">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-269">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="f5ad7-270">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-270">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="f5ad7-271">*.NET Core 2,2 Şu anda ❌ destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="f5ad7-271">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="f5ad7-272">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-272">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="f5ad7-273">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-273">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-274">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-274">OS</span></span>                            | <span data-ttu-id="f5ad7-275">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-275">Version</span></span>                        | <span data-ttu-id="f5ad7-276">Mimariler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-276">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="f5ad7-277">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-277">Windows Client</span></span>                | <span data-ttu-id="f5ad7-278">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-278">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="f5ad7-279">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-279">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-280">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-280">Windows 10 Client</span></span>             | <span data-ttu-id="f5ad7-281">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-281">Version 1607+</span></span>                  | <span data-ttu-id="f5ad7-282">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-282">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-283">Windows Server</span><span class="sxs-lookup"><span data-stu-id="f5ad7-283">Windows Server</span></span>                | <span data-ttu-id="f5ad7-284">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-284">2008 R2 SP1+</span></span>                   | <span data-ttu-id="f5ad7-285">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-285">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-286">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="f5ad7-286">Nano Server</span></span>                   | <span data-ttu-id="f5ad7-287">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-287">Version 1803+</span></span>                   | <span data-ttu-id="f5ad7-288">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="f5ad7-288">x64, ARM32</span></span>      |

<span data-ttu-id="f5ad7-289">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-289">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="f5ad7-290">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-290">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="f5ad7-291">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-291">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="f5ad7-292">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-292">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="f5ad7-293">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-293">OS</span></span>                            | <span data-ttu-id="f5ad7-294">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-294">Version</span></span>                        | <span data-ttu-id="f5ad7-295">Mimariler</span><span class="sxs-lookup"><span data-stu-id="f5ad7-295">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="f5ad7-296">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-296">Windows Client</span></span>                | <span data-ttu-id="f5ad7-297">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-297">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="f5ad7-298">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-298">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-299">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-299">Windows 10 Client</span></span>             | <span data-ttu-id="f5ad7-300">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-300">Version 1607+</span></span>                  | <span data-ttu-id="f5ad7-301">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-301">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-302">Windows Server</span><span class="sxs-lookup"><span data-stu-id="f5ad7-302">Windows Server</span></span>                | <span data-ttu-id="f5ad7-303">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-303">2008 R2 SP1+</span></span>                   | <span data-ttu-id="f5ad7-304">x64, x86</span><span class="sxs-lookup"><span data-stu-id="f5ad7-304">x64, x86</span></span>        |
| <span data-ttu-id="f5ad7-305">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="f5ad7-305">Nano Server</span></span>                   | <span data-ttu-id="f5ad7-306">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="f5ad7-306">Version 1803+</span></span>                  | <span data-ttu-id="f5ad7-307">x64</span><span class="sxs-lookup"><span data-stu-id="f5ad7-307">x64,</span></span>            |

<span data-ttu-id="f5ad7-308">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-308">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="f5ad7-309">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-309">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="f5ad7-310">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-310">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="f5ad7-311">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="f5ad7-311">Windows 7 SP1 [ESU][esu]</span></span>
- <span data-ttu-id="f5ad7-312">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-312">Windows Vista SP 2</span></span>
- <span data-ttu-id="f5ad7-313">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-313">Windows 8.1</span></span>
- <span data-ttu-id="f5ad7-314">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-314">Windows Server 2008 R2</span></span>
- <span data-ttu-id="f5ad7-315">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-315">Windows Server 2012 R2</span></span>

<span data-ttu-id="f5ad7-316">Aşağıdakileri yükleyerek:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-316">Install the following:</span></span>

- <span data-ttu-id="f5ad7-317">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-317">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="f5ad7-318">KB2533623</span><span class="sxs-lookup"><span data-stu-id="f5ad7-318">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="f5ad7-319">Aşağıdaki hatalardan birini alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-319">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="f5ad7-320">Bilgisayarınızda *api-ms-win-crt-runtime-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-320">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="f5ad7-321">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-321">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="f5ad7-322">\- veya</span><span class="sxs-lookup"><span data-stu-id="f5ad7-322">\- or -</span></span>
>
> <span data-ttu-id="f5ad7-323">Bilgisayarınızda *api-ms-win-cor-timezone-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-323">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="f5ad7-324">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-324">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="f5ad7-325">\- veya</span><span class="sxs-lookup"><span data-stu-id="f5ad7-325">\- or -</span></span>
>
> <span data-ttu-id="f5ad7-326">Kitaplık *hostfxr.dll* bulundu, ancak *C: \\ \<path_to_app> \\hostfxr.dll* öğesinden yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-326">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f5ad7-327">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="f5ad7-327">Install with PowerShell automation</span></span>

<span data-ttu-id="f5ad7-328">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-328">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f5ad7-329">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-329">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f5ad7-330">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-330">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f5ad7-331">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="f5ad7-331">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="f5ad7-332">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-332">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="f5ad7-333">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-333">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="f5ad7-334">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="f5ad7-334">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="f5ad7-335">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-335">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="f5ad7-336">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="f5ad7-336">Install with Visual Studio</span></span>

<span data-ttu-id="f5ad7-337">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-337">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="f5ad7-338">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="f5ad7-338">.NET SDK version</span></span>      | <span data-ttu-id="f5ad7-339">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="f5ad7-339">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="f5ad7-340">5.0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-340">5.0</span></span>                   | <span data-ttu-id="f5ad7-341">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-341">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="f5ad7-342">3,1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-342">3.1</span></span>                   | <span data-ttu-id="f5ad7-343">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-343">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="f5ad7-344">3,0</span><span class="sxs-lookup"><span data-stu-id="f5ad7-344">3.0</span></span>                   | <span data-ttu-id="f5ad7-345">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-345">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="f5ad7-346">2.2</span><span class="sxs-lookup"><span data-stu-id="f5ad7-346">2.2</span></span>                   | <span data-ttu-id="f5ad7-347">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-347">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="f5ad7-348">2.1</span><span class="sxs-lookup"><span data-stu-id="f5ad7-348">2.1</span></span>                   | <span data-ttu-id="f5ad7-349">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-349">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="f5ad7-350">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-350">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="f5ad7-351">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-351">Open Visual Studio.</span></span>
01. <span data-ttu-id="f5ad7-352">**Help**  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-352">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="f5ad7-353">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-353">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="f5ad7-354">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-354">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="f5ad7-355">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-355">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="f5ad7-356">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="f5ad7-356">Select a workload</span></span>

<span data-ttu-id="f5ad7-357">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-357">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="f5ad7-358">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-358">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="f5ad7-359">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-359">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f5ad7-360">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-360">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f5ad7-361">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-361">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="f5ad7-362">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f5ad7-362">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="f5ad7-363">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="f5ad7-363">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="f5ad7-364">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-364">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="f5ad7-365">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-365">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="f5ad7-366">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-366">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="f5ad7-367">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-367">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="f5ad7-368">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-368">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="f5ad7-369">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-369">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="f5ad7-370">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="f5ad7-370">Windows Installer</span></span>

<span data-ttu-id="f5ad7-371">.NET için [karşıdan yükleme sayfası](https://dotnet.microsoft.com/download/dotnet-core) Windows ınstaller yürütülebilir dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-371">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="f5ad7-372">.NET< yüklemek için MSI dosyalarını kullandığınızda, ve parametrelerini ayarlayarak yükleme yolunu özelleştirebilirsiniz `DOTNETHOME_X64` `DOTNETHOME_X86` :</span><span class="sxs-lookup"><span data-stu-id="f5ad7-372">When you use the MSI files to install .NET< you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a><span data-ttu-id="f5ad7-373">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="f5ad7-373">Download and manually install</span></span>

<span data-ttu-id="f5ad7-374">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-374">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="f5ad7-375">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-375">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="f5ad7-376">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-376">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="f5ad7-377">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-377">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="f5ad7-378">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-378">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="f5ad7-379">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-379">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="f5ad7-380">.NET 5,0 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-380">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="f5ad7-381">.NET Core 3,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-381">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f5ad7-382">.NET Core 2,1 İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-382">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="f5ad7-383">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="f5ad7-383">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="f5ad7-384">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="f5ad7-384">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="f5ad7-385">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-385">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="f5ad7-386">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-386">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="f5ad7-387">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f5ad7-387">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="f5ad7-388">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-388">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="f5ad7-389">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-389">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="f5ad7-390">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-390">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="f5ad7-391">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-391">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="f5ad7-392">Docker</span><span class="sxs-lookup"><span data-stu-id="f5ad7-392">Docker</span></span>

<span data-ttu-id="f5ad7-393">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-393">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f5ad7-394">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-394">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f5ad7-395">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-395">.NET can run in a Docker container.</span></span> <span data-ttu-id="f5ad7-396">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-396">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="f5ad7-397">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-397">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f5ad7-398">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-398">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f5ad7-399">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-399">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f5ad7-400">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-400">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f5ad7-401">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f5ad7-401">Next steps</span></span>

- <span data-ttu-id="f5ad7-402">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-402">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="f5ad7-403">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-403">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="f5ad7-404">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f5ad7-404">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f5ad7-405">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="f5ad7-405">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
