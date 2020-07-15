---
title: Windows 'a .NET Core 'u yükler
description: .NET Core 'u hangi Windows sürümleriyle yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 97f67d00b3eb4dafc55256aea51f4295bb0ef06a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308955"
---
# <a name="install-net-core-on-windows"></a><span data-ttu-id="57555-103">Windows 'a .NET Core 'u yükler</span><span class="sxs-lookup"><span data-stu-id="57555-103">Install .NET Core on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="57555-107">Bu makalede, Windows 'a .NET Core yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="57555-107">In this article, you'll learn how to install .NET Core on Windows.</span></span> <span data-ttu-id="57555-108">.NET Core çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="57555-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="57555-109">Çalışma zamanı .NET Core uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="57555-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="57555-110">SDK, .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57555-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="57555-111">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="57555-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="57555-112">.NET Core 'un en son sürümü 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="57555-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="57555-113">.NET Core indirin</span><span class="sxs-lookup"><span data-stu-id="57555-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="57555-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="57555-114">Supported releases</span></span>

<span data-ttu-id="57555-115">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57555-115">The following table is a list of currently supported .NET Core releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="57555-116">Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşana](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows sürümü yaşam sonuna ulaşana](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="57555-116">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="57555-117">Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü.</span><span class="sxs-lookup"><span data-stu-id="57555-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="57555-118">Aşağıdaki tabloda yalnızca **Home**, **Pro**, **Pro eğitim**ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur.</span><span class="sxs-lookup"><span data-stu-id="57555-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="57555-119">Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="57555-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="57555-120">✔️, Windows veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="57555-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="57555-121">Bir ❌ Windows veya .NET Core sürümünün bu Windows sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57555-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="57555-122">Hem bir Windows sürümü hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="57555-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="57555-123">Operating System</span><span class="sxs-lookup"><span data-stu-id="57555-123">Operating System</span></span>                      | <span data-ttu-id="57555-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="57555-124">.NET Core 2.1</span></span> | <span data-ttu-id="57555-125">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-125">.NET Core 3.1</span></span> | <span data-ttu-id="57555-126">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="57555-126">.NET 5 Preview</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="57555-127">✔️ Windows 10, sürüm 2004</span><span class="sxs-lookup"><span data-stu-id="57555-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="57555-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="57555-128">✔️ 2.1</span></span>        | <span data-ttu-id="57555-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-129">✔️ 3.1</span></span>        | <span data-ttu-id="57555-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="57555-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-131">✔️ Windows 10, sürüm 1909</span><span class="sxs-lookup"><span data-stu-id="57555-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="57555-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="57555-132">✔️ 2.1</span></span>        | <span data-ttu-id="57555-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-133">✔️ 3.1</span></span>        | <span data-ttu-id="57555-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="57555-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-135">✔️ Windows 10, sürüm 1903</span><span class="sxs-lookup"><span data-stu-id="57555-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="57555-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="57555-136">✔️ 2.1</span></span>        | <span data-ttu-id="57555-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-137">✔️ 3.1</span></span>        | <span data-ttu-id="57555-138">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="57555-138">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-139">✔️ Windows 10, sürüm 1809</span><span class="sxs-lookup"><span data-stu-id="57555-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="57555-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="57555-140">✔️ 2.1</span></span>        | <span data-ttu-id="57555-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-141">✔️ 3.1</span></span>        | <span data-ttu-id="57555-142">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="57555-142">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-143">❌Windows 10, sürüm 1803</span><span class="sxs-lookup"><span data-stu-id="57555-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="57555-144">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="57555-144">✔️ 2.1</span></span>        | <span data-ttu-id="57555-145">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-145">❌ 3.1</span></span>        | <span data-ttu-id="57555-146">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-146">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-147">❌Windows 10, sürüm 1709</span><span class="sxs-lookup"><span data-stu-id="57555-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="57555-148">❌2,1</span><span class="sxs-lookup"><span data-stu-id="57555-148">❌ 2.1</span></span>        | <span data-ttu-id="57555-149">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-149">❌ 3.1</span></span>        | <span data-ttu-id="57555-150">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-150">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-151">❌Windows 10, sürüm 1703</span><span class="sxs-lookup"><span data-stu-id="57555-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="57555-152">❌2,1</span><span class="sxs-lookup"><span data-stu-id="57555-152">❌ 2.1</span></span>        | <span data-ttu-id="57555-153">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-153">❌ 3.1</span></span>        | <span data-ttu-id="57555-154">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-154">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-155">❌Windows 10, sürüm 1607</span><span class="sxs-lookup"><span data-stu-id="57555-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="57555-156">❌2,1</span><span class="sxs-lookup"><span data-stu-id="57555-156">❌ 2.1</span></span>        | <span data-ttu-id="57555-157">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-157">❌ 3.1</span></span>        | <span data-ttu-id="57555-158">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-158">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-159">❌Windows 10, sürüm 1511</span><span class="sxs-lookup"><span data-stu-id="57555-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="57555-160">❌2,1</span><span class="sxs-lookup"><span data-stu-id="57555-160">❌ 2.1</span></span>        | <span data-ttu-id="57555-161">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-161">❌ 3.1</span></span>        | <span data-ttu-id="57555-162">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-162">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="57555-163">❌Windows 10, sürüm 1507</span><span class="sxs-lookup"><span data-stu-id="57555-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="57555-164">❌2,1</span><span class="sxs-lookup"><span data-stu-id="57555-164">❌ 2.1</span></span>        | <span data-ttu-id="57555-165">❌3,1</span><span class="sxs-lookup"><span data-stu-id="57555-165">❌ 3.1</span></span>        | <span data-ttu-id="57555-166">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="57555-166">❌ 5.0 Preview</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="57555-167">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="57555-167">Unsupported releases</span></span>

<span data-ttu-id="57555-168">Aşağıdaki .NET Core sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="57555-168">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="57555-169">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="57555-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="57555-170">3,0</span><span class="sxs-lookup"><span data-stu-id="57555-170">3.0</span></span>
- <span data-ttu-id="57555-171">2,2</span><span class="sxs-lookup"><span data-stu-id="57555-171">2.2</span></span>
- <span data-ttu-id="57555-172">2,0</span><span class="sxs-lookup"><span data-stu-id="57555-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="57555-173">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="57555-173">Runtime information</span></span>

<span data-ttu-id="57555-174">Çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57555-174">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="57555-175">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="57555-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="57555-176">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="57555-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="57555-177">Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="57555-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="57555-178">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="57555-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="57555-179">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="57555-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="57555-180">.NET Core çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="57555-180">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="57555-181">*Masaüstü çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="57555-181">*Desktop runtime*</span></span>\
<span data-ttu-id="57555-182">Windows için masaüstü uygulamaları Windows Forms .NET Core WPF ve .NET Core çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="57555-182">Runs .NET Core WPF and .NET Core Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="57555-183">.NET Core çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="57555-183">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="57555-184">*.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="57555-184">*.NET Core runtime*</span></span>\
<span data-ttu-id="57555-185">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="57555-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="57555-186">.NET Core uygulamalarıyla en iyi uyumluluk için *ASP.NET Core çalışma zamanı* ve *Masaüstü çalışma zamanı* yüklemenizi kesinlikle öneririz.</span><span class="sxs-lookup"><span data-stu-id="57555-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="57555-187">.NET Core çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="57555-187">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="57555-188">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="57555-188">SDK information</span></span>

<span data-ttu-id="57555-189">SDK, .NET Core Uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57555-189">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="57555-190">SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="57555-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="57555-191">.NET Core SDK indir</span><span class="sxs-lookup"><span data-stu-id="57555-191">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="57555-192">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="57555-192">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="57555-193">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="57555-193">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="57555-194">Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="57555-194">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="57555-195">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57555-195">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="57555-196">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="57555-196">OS</span></span>                            | <span data-ttu-id="57555-197">Sürüm</span><span class="sxs-lookup"><span data-stu-id="57555-197">Version</span></span>                        | <span data-ttu-id="57555-198">Mimariler</span><span class="sxs-lookup"><span data-stu-id="57555-198">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="57555-199">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-199">Windows Client</span></span>                | <span data-ttu-id="57555-200">8.1</span><span class="sxs-lookup"><span data-stu-id="57555-200">8.1</span></span>                            | <span data-ttu-id="57555-201">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-201">x64, x86</span></span>        |
| <span data-ttu-id="57555-202">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-202">Windows 10 Client</span></span>             | <span data-ttu-id="57555-203">Sürüm 1609 +</span><span class="sxs-lookup"><span data-stu-id="57555-203">Version 1609+</span></span>                  | <span data-ttu-id="57555-204">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-204">x64, x86</span></span>        |
| <span data-ttu-id="57555-205">Windows Server</span><span class="sxs-lookup"><span data-stu-id="57555-205">Windows Server</span></span>                | <span data-ttu-id="57555-206">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="57555-206">2012 R2+</span></span>                       | <span data-ttu-id="57555-207">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-207">x64, x86</span></span>        |
| <span data-ttu-id="57555-208">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="57555-208">Nano Server</span></span>                   | <span data-ttu-id="57555-209">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="57555-209">Version 1803+</span></span>                  | <span data-ttu-id="57555-210">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="57555-210">x64, ARM32</span></span>      |

<span data-ttu-id="57555-211">.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="57555-211">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="57555-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="57555-212">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="57555-213">*.NET Core 3,0 şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="57555-213">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="57555-214">Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="57555-214">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="57555-215">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57555-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="57555-216">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="57555-216">OS</span></span>                            | <span data-ttu-id="57555-217">Sürüm</span><span class="sxs-lookup"><span data-stu-id="57555-217">Version</span></span>                        | <span data-ttu-id="57555-218">Mimariler</span><span class="sxs-lookup"><span data-stu-id="57555-218">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="57555-219">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-219">Windows Client</span></span>                | <span data-ttu-id="57555-220">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="57555-220">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="57555-221">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-221">x64, x86</span></span>        |
| <span data-ttu-id="57555-222">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-222">Windows 10 Client</span></span>             | <span data-ttu-id="57555-223">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="57555-223">Version 1607+</span></span>                  | <span data-ttu-id="57555-224">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-224">x64, x86</span></span>        |
| <span data-ttu-id="57555-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="57555-225">Windows Server</span></span>                | <span data-ttu-id="57555-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="57555-226">2012 R2+</span></span>                       | <span data-ttu-id="57555-227">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-227">x64, x86</span></span>        |
| <span data-ttu-id="57555-228">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="57555-228">Nano Server</span></span>                   | <span data-ttu-id="57555-229">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="57555-229">Version 1803+</span></span>                  | <span data-ttu-id="57555-230">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="57555-230">x64, ARM32</span></span>      |

<span data-ttu-id="57555-231">.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="57555-231">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="57555-232">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="57555-232">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="57555-233">*.NET Core 2,2 Şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="57555-233">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="57555-234">Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="57555-234">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="57555-235">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57555-235">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="57555-236">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="57555-236">OS</span></span>                            | <span data-ttu-id="57555-237">Sürüm</span><span class="sxs-lookup"><span data-stu-id="57555-237">Version</span></span>                        | <span data-ttu-id="57555-238">Mimariler</span><span class="sxs-lookup"><span data-stu-id="57555-238">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="57555-239">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-239">Windows Client</span></span>                | <span data-ttu-id="57555-240">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="57555-240">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="57555-241">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-241">x64, x86</span></span>        |
| <span data-ttu-id="57555-242">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-242">Windows 10 Client</span></span>             | <span data-ttu-id="57555-243">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="57555-243">Version 1607+</span></span>                  | <span data-ttu-id="57555-244">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-244">x64, x86</span></span>        |
| <span data-ttu-id="57555-245">Windows Server</span><span class="sxs-lookup"><span data-stu-id="57555-245">Windows Server</span></span>                | <span data-ttu-id="57555-246">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="57555-246">2008 R2 SP1+</span></span>                   | <span data-ttu-id="57555-247">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-247">x64, x86</span></span>        |
| <span data-ttu-id="57555-248">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="57555-248">Nano Server</span></span>                   | <span data-ttu-id="57555-249">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="57555-249">Version 1803+</span></span>                   | <span data-ttu-id="57555-250">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="57555-250">x64, ARM32</span></span>      |

<span data-ttu-id="57555-251">.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="57555-251">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="57555-252">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="57555-252">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="57555-253">Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:</span><span class="sxs-lookup"><span data-stu-id="57555-253">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="57555-254">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57555-254">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="57555-255">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="57555-255">OS</span></span>                            | <span data-ttu-id="57555-256">Sürüm</span><span class="sxs-lookup"><span data-stu-id="57555-256">Version</span></span>                        | <span data-ttu-id="57555-257">Mimariler</span><span class="sxs-lookup"><span data-stu-id="57555-257">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="57555-258">Windows İstemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-258">Windows Client</span></span>                | <span data-ttu-id="57555-259">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="57555-259">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="57555-260">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-260">x64, x86</span></span>        |
| <span data-ttu-id="57555-261">Windows 10 Istemcisi</span><span class="sxs-lookup"><span data-stu-id="57555-261">Windows 10 Client</span></span>             | <span data-ttu-id="57555-262">Sürüm 1607 +</span><span class="sxs-lookup"><span data-stu-id="57555-262">Version 1607+</span></span>                  | <span data-ttu-id="57555-263">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-263">x64, x86</span></span>        |
| <span data-ttu-id="57555-264">Windows Server</span><span class="sxs-lookup"><span data-stu-id="57555-264">Windows Server</span></span>                | <span data-ttu-id="57555-265">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="57555-265">2008 R2 SP1+</span></span>                   | <span data-ttu-id="57555-266">x64, x86</span><span class="sxs-lookup"><span data-stu-id="57555-266">x64, x86</span></span>        |
| <span data-ttu-id="57555-267">Nano Sunucu</span><span class="sxs-lookup"><span data-stu-id="57555-267">Nano Server</span></span>                   | <span data-ttu-id="57555-268">Sürüm 1803 +</span><span class="sxs-lookup"><span data-stu-id="57555-268">Version 1803+</span></span>                  | <span data-ttu-id="57555-269">x64</span><span class="sxs-lookup"><span data-stu-id="57555-269">x64,</span></span>            |

<span data-ttu-id="57555-270">.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="57555-270">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="57555-271">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="57555-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="57555-272">Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="57555-272">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="57555-273">❌Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="57555-273">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="57555-274">❌Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="57555-274">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="57555-275">✔️ Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="57555-275">✔️ Windows 8.1</span></span>
- <span data-ttu-id="57555-276">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="57555-276">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="57555-277">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="57555-277">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="57555-278">Aşağıdakileri yükleyerek:</span><span class="sxs-lookup"><span data-stu-id="57555-278">Install the following:</span></span>

- <span data-ttu-id="57555-279">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="57555-279">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="57555-280">KB2533623</span><span class="sxs-lookup"><span data-stu-id="57555-280">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="57555-281">Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:</span><span class="sxs-lookup"><span data-stu-id="57555-281">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="57555-282">Bilgisayarınızda *api-ms-win-crt-runtime-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="57555-282">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="57555-283">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="57555-283">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="57555-284">\-veya</span><span class="sxs-lookup"><span data-stu-id="57555-284">\- or -</span></span>
>
> <span data-ttu-id="57555-285">Bilgisayarınızda *api-ms-win-cor-timezone-l1-1-0.dll* olmadığından program başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="57555-285">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="57555-286">Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="57555-286">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="57555-287">\-veya</span><span class="sxs-lookup"><span data-stu-id="57555-287">\- or -</span></span>
>
> <span data-ttu-id="57555-288">Kitaplık *hostfxr.dll* bulundu, ancak *C: \\ \<path_to_app> \\hostfxr.dll* öğesinden yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="57555-288">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="57555-289">PowerShell otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="57555-289">Install with PowerShell automation</span></span>

<span data-ttu-id="57555-290">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57555-290">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="57555-291">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57555-291">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="57555-292">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="57555-292">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="57555-293">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` .</span><span class="sxs-lookup"><span data-stu-id="57555-293">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="57555-294">`Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="57555-294">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="57555-295">Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="57555-295">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

<span data-ttu-id="57555-296">Anahtarı atlayarak SDK 'Yı yükler `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="57555-296">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="57555-297">`-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="57555-297">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="57555-298">Visual Studio ile Install</span><span class="sxs-lookup"><span data-stu-id="57555-298">Install with Visual Studio</span></span>

<span data-ttu-id="57555-299">.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57555-299">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="57555-300">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="57555-300">.NET Core SDK version</span></span> | <span data-ttu-id="57555-301">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="57555-301">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="57555-302">3,1</span><span class="sxs-lookup"><span data-stu-id="57555-302">3.1</span></span>                   | <span data-ttu-id="57555-303">Visual Studio 2019 sürüm 16,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="57555-303">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="57555-304">3,0</span><span class="sxs-lookup"><span data-stu-id="57555-304">3.0</span></span>                   | <span data-ttu-id="57555-305">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="57555-305">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="57555-306">2,2</span><span class="sxs-lookup"><span data-stu-id="57555-306">2.2</span></span>                   | <span data-ttu-id="57555-307">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="57555-307">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="57555-308">2.1</span><span class="sxs-lookup"><span data-stu-id="57555-308">2.1</span></span>                   | <span data-ttu-id="57555-309">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="57555-309">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="57555-310">Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57555-310">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="57555-311">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="57555-311">Open Visual Studio.</span></span>
01. <span data-ttu-id="57555-312">**Help**  >  **Microsoft Visual Studio hakkında**yardım seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="57555-312">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="57555-313">**Hakkında** iletişim kutusunda sürüm numarasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="57555-313">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="57555-314">Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="57555-314">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="57555-315">[Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="57555-315">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="57555-316">İş yükü seçin</span><span class="sxs-lookup"><span data-stu-id="57555-316">Select a workload</span></span>

<span data-ttu-id="57555-317">Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:</span><span class="sxs-lookup"><span data-stu-id="57555-317">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="57555-318">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="57555-318">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="57555-319">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="57555-319">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="57555-320">**Web & bulut** bölümündeki **Azure geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="57555-320">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="57555-321">**Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="57555-321">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="57555-322">[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="57555-322">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="57555-323">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="57555-323">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="57555-324">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="57555-324">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="57555-325">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57555-325">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="57555-326">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="57555-326">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="57555-327">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="57555-327">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="57555-328">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="57555-328">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="57555-329">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="57555-329">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="57555-330">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="57555-330">Download and manually install</span></span>

<span data-ttu-id="57555-331">.NET Core için Windows yükleyicilerine alternatif olarak, SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57555-331">As an alternative to the Windows installers for .NET Core, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="57555-332">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="57555-332">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="57555-333">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="57555-333">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="57555-334">Hem .NET Core SDK hem de .NET Core çalışma zamanı, indirildikten sonra el ile yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="57555-334">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="57555-335">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="57555-335">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="57555-336">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="57555-336">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="57555-337">✔️ [.net 5,0 Preview İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="57555-337">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="57555-338">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="57555-338">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="57555-339">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="57555-339">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="57555-340">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="57555-340">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="57555-341">Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="57555-341">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="57555-342">Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="57555-342">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="57555-343">Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz ve açıkça kullanmayı tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57555-343">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="57555-344">Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="57555-344">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="57555-345">Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57555-345">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="57555-346">`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .NET Core, genel olarak yüklenen tüm .NET Core sürümlerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="57555-346">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET Core ignores any globally installed .NET Core version.</span></span> <span data-ttu-id="57555-347">Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken, .NET Core 'un varsayılan genel yüklemesi konumunu dikkate almasına izin vermek için bu ortam ayarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="57555-347">Remove that environment setting to let .NET Core consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="57555-348">Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .NET Core 'u yüklebildiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="57555-348">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET Core.</span></span>

## <a name="docker"></a><span data-ttu-id="57555-349">Docker</span><span class="sxs-lookup"><span data-stu-id="57555-349">Docker</span></span>

<span data-ttu-id="57555-350">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="57555-350">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="57555-351">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="57555-351">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="57555-352">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="57555-352">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="57555-353">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="57555-353">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="57555-354">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="57555-354">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="57555-355">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="57555-355">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="57555-356">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="57555-356">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="57555-357">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="57555-357">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="57555-358">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="57555-358">Next steps</span></span>

- <span data-ttu-id="57555-359">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="57555-359">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="57555-360">[Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="57555-360">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="57555-361">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="57555-361">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="57555-362">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="57555-362">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
