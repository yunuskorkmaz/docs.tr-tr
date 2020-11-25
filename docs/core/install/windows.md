---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 4d3abde965d9a2ab0f86477feeb7c10f274a4b9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715127"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="3929e-103">Windows 'a .NET yükler</span><span class="sxs-lookup"><span data-stu-id="3929e-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="3929e-107">Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3929e-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="3929e-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="3929e-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="3929e-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="3929e-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3929e-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="3929e-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3929e-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="3929e-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3929e-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="3929e-113">.NET İndir</span><span class="sxs-lookup"><span data-stu-id="3929e-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="3929e-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="3929e-114">Supported releases</span></span>

<span data-ttu-id="3929e-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3929e-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="3929e-116">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="3929e-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="3929e-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="3929e-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="3929e-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="3929e-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="3929e-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="3929e-120">✔️, Windows veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3929e-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="3929e-121">Bir ❌ Windows veya .NET Core sürümünün bu Windows sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3929e-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="3929e-122">Hem bir Windows sürümü hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3929e-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3929e-123">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-123">Operating System</span></span>                      | <span data-ttu-id="3929e-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3929e-124">.NET Core 2.1</span></span> | <span data-ttu-id="3929e-125">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-125">.NET Core 3.1</span></span> | <span data-ttu-id="3929e-126">.NET 5</span><span class="sxs-lookup"><span data-stu-id="3929e-126">.NET 5</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3929e-127">✔️ Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="3929e-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="3929e-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-128">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-129">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-130">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-130">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-131">✔️ Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="3929e-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="3929e-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-132">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-133">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-134">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-134">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-135">✔️ Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="3929e-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="3929e-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-136">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-137">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-138">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-138">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-139">✔️ Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="3929e-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="3929e-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-140">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-141">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-142">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-142">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-143">❌ Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="3929e-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="3929e-144">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-144">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-145">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-145">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-146">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-146">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-147">❌ Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="3929e-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="3929e-148">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-148">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-149">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-149">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-150">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-150">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-151">❌ Windows 10, sürüm 1703</span><span class="sxs-lookup"><span data-stu-id="3929e-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="3929e-152">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-152">❌ 2.1</span></span>        | <span data-ttu-id="3929e-153">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-153">❌ 3.1</span></span>        | <span data-ttu-id="3929e-154">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-154">❌ 5.0</span></span> |
| <span data-ttu-id="3929e-155">❌ Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="3929e-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="3929e-156">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-156">✔️ 2.1</span></span>        | <span data-ttu-id="3929e-157">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-157">✔️ 3.1</span></span>        | <span data-ttu-id="3929e-158">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-158">✔️ 5.0</span></span> |
| <span data-ttu-id="3929e-159">❌ Windows 10, sürüm 1511</span><span class="sxs-lookup"><span data-stu-id="3929e-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="3929e-160">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-160">❌ 2.1</span></span>        | <span data-ttu-id="3929e-161">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-161">❌ 3.1</span></span>        | <span data-ttu-id="3929e-162">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-162">❌ 5.0</span></span> |
| <span data-ttu-id="3929e-163">❌ Windows 10, sürüm 1507</span><span class="sxs-lookup"><span data-stu-id="3929e-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="3929e-164">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="3929e-164">❌ 2.1</span></span>        | <span data-ttu-id="3929e-165">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-165">❌ 3.1</span></span>        | <span data-ttu-id="3929e-166">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-166">❌ 5.0</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="3929e-167">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="3929e-167">Unsupported releases</span></span>

<span data-ttu-id="3929e-168">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="3929e-168">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="3929e-169">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="3929e-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3929e-170">3,0</span><span class="sxs-lookup"><span data-stu-id="3929e-170">3.0</span></span>
- <span data-ttu-id="3929e-171">2.2</span><span class="sxs-lookup"><span data-stu-id="3929e-171">2.2</span></span>
- <span data-ttu-id="3929e-172">2,0</span><span class="sxs-lookup"><span data-stu-id="3929e-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="3929e-173">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="3929e-173">Runtime information</span></span>

<span data-ttu-id="3929e-174">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3929e-174">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="3929e-175">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="3929e-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="3929e-176">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="3929e-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="3929e-177">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="3929e-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="3929e-178">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="3929e-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="3929e-179">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3929e-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="3929e-180">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="3929e-180">Includes the .NET runtime.</span></span>

<span data-ttu-id="3929e-181">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="3929e-181">*Desktop runtime*</span></span>\
<span data-ttu-id="3929e-182">.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3929e-182">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="3929e-183">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="3929e-183">Includes the .NET runtime.</span></span>

<span data-ttu-id="3929e-184">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="3929e-184">*.NET runtime*</span></span>\
<span data-ttu-id="3929e-185">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="3929e-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="3929e-186">.NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="3929e-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="3929e-187">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="3929e-187">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="3929e-188">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="3929e-188">SDK information</span></span>

<span data-ttu-id="3929e-189">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3929e-189">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="3929e-190">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.</span><span class="sxs-lookup"><span data-stu-id="3929e-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="3929e-191">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="3929e-191">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="3929e-192">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3929e-192">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="3929e-193">Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3929e-193">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="3929e-194">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-194">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3929e-195">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-195">OS</span></span>                  | <span data-ttu-id="3929e-196">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-196">Version</span></span>       | <span data-ttu-id="3929e-197">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3929e-197">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="3929e-198">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-198">Windows 10 Client</span></span>   | <span data-ttu-id="3929e-199">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3929e-199">Version 1607+</span></span> | <span data-ttu-id="3929e-200">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="3929e-200">x64, x86, ARM64</span></span> |
| <span data-ttu-id="3929e-201">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-201">Windows Client</span></span>      | <span data-ttu-id="3929e-202">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3929e-202">7 SP1+, 8.1</span></span>   | <span data-ttu-id="3929e-203">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-203">x64, x86</span></span>        |
| <span data-ttu-id="3929e-204">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3929e-204">Windows Server</span></span>      | <span data-ttu-id="3929e-205">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3929e-205">2012 R2+</span></span>      | <span data-ttu-id="3929e-206">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-206">x64, x86</span></span>        |
| <span data-ttu-id="3929e-207">Windows Server çekirdeği</span><span class="sxs-lookup"><span data-stu-id="3929e-207">Windows Server Core</span></span> | <span data-ttu-id="3929e-208">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3929e-208">2012 R2+</span></span>      | <span data-ttu-id="3929e-209">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-209">x64, x86</span></span>        |
| <span data-ttu-id="3929e-210">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3929e-210">Nano Server</span></span>         | <span data-ttu-id="3929e-211">Sürüm 1809 +</span><span class="sxs-lookup"><span data-stu-id="3929e-211">Version 1809+</span></span> | <span data-ttu-id="3929e-212">x64</span><span class="sxs-lookup"><span data-stu-id="3929e-212">x64</span></span>             |

<span data-ttu-id="3929e-213">.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-213">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="3929e-214">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-214">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="3929e-215">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3929e-215">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="3929e-216">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-216">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3929e-217">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-217">OS</span></span>                            | <span data-ttu-id="3929e-218">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-218">Version</span></span>                        | <span data-ttu-id="3929e-219">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3929e-219">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3929e-220">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-220">Windows Client</span></span>                | <span data-ttu-id="3929e-221">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3929e-221">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3929e-222">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-222">x64, x86</span></span>        |
| <span data-ttu-id="3929e-223">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-223">Windows 10 Client</span></span>             | <span data-ttu-id="3929e-224">Sürüm 1609 +</span><span class="sxs-lookup"><span data-stu-id="3929e-224">Version 1609+</span></span>                  | <span data-ttu-id="3929e-225">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-225">x64, x86</span></span>        |
| <span data-ttu-id="3929e-226">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3929e-226">Windows Server</span></span>                | <span data-ttu-id="3929e-227">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3929e-227">2012 R2+</span></span>                       | <span data-ttu-id="3929e-228">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-228">x64, x86</span></span>        |
| <span data-ttu-id="3929e-229">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3929e-229">Nano Server</span></span>                   | <span data-ttu-id="3929e-230">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3929e-230">Version 1803+</span></span>                  | <span data-ttu-id="3929e-231">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3929e-231">x64, ARM32</span></span>      |

<span data-ttu-id="3929e-232">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-232">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="3929e-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3929e-233">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="3929e-234">*.NET Core 3,0 şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3929e-234">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3929e-235">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3929e-235">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="3929e-236">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-236">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3929e-237">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-237">OS</span></span>                            | <span data-ttu-id="3929e-238">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-238">Version</span></span>                        | <span data-ttu-id="3929e-239">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3929e-239">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3929e-240">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-240">Windows Client</span></span>                | <span data-ttu-id="3929e-241">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3929e-241">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3929e-242">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-242">x64, x86</span></span>        |
| <span data-ttu-id="3929e-243">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-243">Windows 10 Client</span></span>             | <span data-ttu-id="3929e-244">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3929e-244">Version 1607+</span></span>                  | <span data-ttu-id="3929e-245">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-245">x64, x86</span></span>        |
| <span data-ttu-id="3929e-246">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3929e-246">Windows Server</span></span>                | <span data-ttu-id="3929e-247">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="3929e-247">2012 R2+</span></span>                       | <span data-ttu-id="3929e-248">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-248">x64, x86</span></span>        |
| <span data-ttu-id="3929e-249">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3929e-249">Nano Server</span></span>                   | <span data-ttu-id="3929e-250">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3929e-250">Version 1803+</span></span>                  | <span data-ttu-id="3929e-251">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3929e-251">x64, ARM32</span></span>      |

<span data-ttu-id="3929e-252">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-252">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="3929e-253">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="3929e-253">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="3929e-254">*.NET Core 2,2 Şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="3929e-254">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="3929e-255">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3929e-255">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="3929e-256">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-256">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3929e-257">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-257">OS</span></span>                            | <span data-ttu-id="3929e-258">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-258">Version</span></span>                        | <span data-ttu-id="3929e-259">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3929e-259">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3929e-260">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-260">Windows Client</span></span>                | <span data-ttu-id="3929e-261">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3929e-261">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3929e-262">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-262">x64, x86</span></span>        |
| <span data-ttu-id="3929e-263">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-263">Windows 10 Client</span></span>             | <span data-ttu-id="3929e-264">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3929e-264">Version 1607+</span></span>                  | <span data-ttu-id="3929e-265">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-265">x64, x86</span></span>        |
| <span data-ttu-id="3929e-266">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3929e-266">Windows Server</span></span>                | <span data-ttu-id="3929e-267">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="3929e-267">2008 R2 SP1+</span></span>                   | <span data-ttu-id="3929e-268">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-268">x64, x86</span></span>        |
| <span data-ttu-id="3929e-269">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3929e-269">Nano Server</span></span>                   | <span data-ttu-id="3929e-270">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3929e-270">Version 1803+</span></span>                   | <span data-ttu-id="3929e-271">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="3929e-271">x64, ARM32</span></span>      |

<span data-ttu-id="3929e-272">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-272">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3929e-273">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3929e-273">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3929e-274">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3929e-274">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="3929e-275">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3929e-275">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="3929e-276">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="3929e-276">OS</span></span>                            | <span data-ttu-id="3929e-277">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-277">Version</span></span>                        | <span data-ttu-id="3929e-278">Mimariler</span><span class="sxs-lookup"><span data-stu-id="3929e-278">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="3929e-279">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-279">Windows Client</span></span>                | <span data-ttu-id="3929e-280">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="3929e-280">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="3929e-281">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-281">x64, x86</span></span>        |
| <span data-ttu-id="3929e-282">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="3929e-282">Windows 10 Client</span></span>             | <span data-ttu-id="3929e-283">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="3929e-283">Version 1607+</span></span>                  | <span data-ttu-id="3929e-284">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-284">x64, x86</span></span>        |
| <span data-ttu-id="3929e-285">Windows Server</span><span class="sxs-lookup"><span data-stu-id="3929e-285">Windows Server</span></span>                | <span data-ttu-id="3929e-286">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="3929e-286">2008 R2 SP1+</span></span>                   | <span data-ttu-id="3929e-287">x64, x86</span><span class="sxs-lookup"><span data-stu-id="3929e-287">x64, x86</span></span>        |
| <span data-ttu-id="3929e-288">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="3929e-288">Nano Server</span></span>                   | <span data-ttu-id="3929e-289">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="3929e-289">Version 1803+</span></span>                  | <span data-ttu-id="3929e-290">x64</span><span class="sxs-lookup"><span data-stu-id="3929e-290">x64,</span></span>            |

<span data-ttu-id="3929e-291">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-291">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="3929e-292">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3929e-292">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="3929e-293">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3929e-293">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="3929e-294">❌ Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3929e-294">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="3929e-295">❌ Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="3929e-295">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="3929e-296">✔️ Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3929e-296">✔️ Windows 8.1</span></span>
- <span data-ttu-id="3929e-297">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3929e-297">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="3929e-298">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3929e-298">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="3929e-299">Aşağıdakileri yükleyerek:</span><span class="sxs-lookup"><span data-stu-id="3929e-299">Install the following:</span></span>

- <span data-ttu-id="3929e-300">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="3929e-300">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="3929e-301">KB2533623</span><span class="sxs-lookup"><span data-stu-id="3929e-301">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="3929e-302">Aşağıdaki hatalardan birini alırsanız, önceki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3929e-302">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="3929e-303">Bilgisayarınızda *api-ms-win-crt-runtime-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3929e-303">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="3929e-304">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3929e-304">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="3929e-305">\- veya</span><span class="sxs-lookup"><span data-stu-id="3929e-305">\- or -</span></span>
>
> <span data-ttu-id="3929e-306">Bilgisayarınızda *api-ms-win-cor-timezone-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3929e-306">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="3929e-307">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3929e-307">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="3929e-308">\- veya</span><span class="sxs-lookup"><span data-stu-id="3929e-308">\- or -</span></span>
>
> <span data-ttu-id="3929e-309">Kitaplık *hostfxr.dll* bulundu, ancak *C: \\ \<path_to_app> \\hostfxr.dll* öğesinden yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="3929e-309">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="3929e-310">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="3929e-310">Install with PowerShell automation</span></span>

<span data-ttu-id="3929e-311">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3929e-311">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="3929e-312">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3929e-312">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="3929e-313">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3929e-313">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="3929e-314">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="3929e-314">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="3929e-315">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3929e-315">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="3929e-316">Aksi halde, komut dosyası SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="3929e-316">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="3929e-317">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="3929e-317">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="3929e-318">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3929e-318">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="3929e-319">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="3929e-319">Install with Visual Studio</span></span>

<span data-ttu-id="3929e-320">.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3929e-320">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="3929e-321">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="3929e-321">.NET SDK version</span></span>      | <span data-ttu-id="3929e-322">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="3929e-322">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="3929e-323">5.0</span><span class="sxs-lookup"><span data-stu-id="3929e-323">5.0</span></span>                   | <span data-ttu-id="3929e-324">Visual Studio 2019 sürüm 16,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3929e-324">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="3929e-325">3,1</span><span class="sxs-lookup"><span data-stu-id="3929e-325">3.1</span></span>                   | <span data-ttu-id="3929e-326">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3929e-326">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="3929e-327">3,0</span><span class="sxs-lookup"><span data-stu-id="3929e-327">3.0</span></span>                   | <span data-ttu-id="3929e-328">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3929e-328">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="3929e-329">2.2</span><span class="sxs-lookup"><span data-stu-id="3929e-329">2.2</span></span>                   | <span data-ttu-id="3929e-330">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3929e-330">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="3929e-331">2.1</span><span class="sxs-lookup"><span data-stu-id="3929e-331">2.1</span></span>                   | <span data-ttu-id="3929e-332">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="3929e-332">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="3929e-333">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3929e-333">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="3929e-334">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="3929e-334">Open Visual Studio.</span></span>
01. <span data-ttu-id="3929e-335">**Help**  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="3929e-335">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="3929e-336">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="3929e-336">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="3929e-337">Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-337">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="3929e-338">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="3929e-338">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="3929e-339">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="3929e-339">Select a workload</span></span>

<span data-ttu-id="3929e-340">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="3929e-340">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="3929e-341">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="3929e-341">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="3929e-342">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="3929e-342">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="3929e-343">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="3929e-343">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="3929e-344">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="3929e-344">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="3929e-345">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="3929e-345">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="3929e-346">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="3929e-346">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="3929e-347">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="3929e-347">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="3929e-348">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-348">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="3929e-349">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="3929e-349">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="3929e-350">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="3929e-350">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="3929e-351">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="3929e-351">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="3929e-352">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="3929e-352">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="3929e-353">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="3929e-353">Download and manually install</span></span>

<span data-ttu-id="3929e-354">.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3929e-354">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="3929e-355">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-355">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="3929e-356">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="3929e-356">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="3929e-357">Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-357">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="3929e-358">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3929e-358">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="3929e-359">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="3929e-359">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="3929e-360">✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="3929e-360">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="3929e-361">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="3929e-361">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="3929e-362">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="3929e-362">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="3929e-363">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="3929e-363">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="3929e-364">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="3929e-364">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="3929e-365">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="3929e-365">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="3929e-366">Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3929e-366">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="3929e-367">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3929e-367">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="3929e-368">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3929e-368">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="3929e-369">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="3929e-369">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="3929e-370">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3929e-370">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="3929e-371">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="3929e-371">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="3929e-372">Docker</span><span class="sxs-lookup"><span data-stu-id="3929e-372">Docker</span></span>

<span data-ttu-id="3929e-373">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3929e-373">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="3929e-374">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3929e-374">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="3929e-375">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-375">.NET can run in a Docker container.</span></span> <span data-ttu-id="3929e-376">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3929e-376">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="3929e-377">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3929e-377">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="3929e-378">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3929e-378">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="3929e-379">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3929e-379">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="3929e-380">Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="3929e-380">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3929e-381">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3929e-381">Next steps</span></span>

- <span data-ttu-id="3929e-382">[.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="3929e-382">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="3929e-383">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-383">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="3929e-384">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="3929e-384">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="3929e-385">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="3929e-385">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
