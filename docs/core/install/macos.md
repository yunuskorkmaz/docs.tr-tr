---
title: MacOS 'ta .NET Core 'u yükler
description: .NET Core 'u hangi macOS sürümlerinin yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: f946759a57bf2eedd296ecbd55fd3a5a7560638d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538372"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="6edef-103">MacOS 'ta .NET Core 'u yükler</span><span class="sxs-lookup"><span data-stu-id="6edef-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="6edef-107">Bu makalede, macOS 'ta .NET Core 'u yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6edef-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="6edef-108">.NET Core çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6edef-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="6edef-109">Çalışma zamanı .NET Core uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="6edef-110">SDK, .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6edef-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="6edef-111">.NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6edef-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="6edef-112">.NET Core 'un en son sürümü 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6edef-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="6edef-113">.NET Core indirin</span><span class="sxs-lookup"><span data-stu-id="6edef-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="6edef-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="6edef-114">Supported releases</span></span>

<span data-ttu-id="6edef-115">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve üzerinde desteklendikleri macOS sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6edef-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="6edef-116">Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaştığında](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="6edef-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="6edef-117">✔️, .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6edef-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="6edef-118">Bir ❌ , .NET Core sürümünün desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6edef-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="6edef-119">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="6edef-119">Operating System</span></span>          | <span data-ttu-id="6edef-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6edef-120">.NET Core 2.1</span></span> | <span data-ttu-id="6edef-121">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6edef-121">.NET Core 3.1</span></span> | <span data-ttu-id="6edef-122">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="6edef-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6edef-123">macOS 10,15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="6edef-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="6edef-124">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="6edef-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="6edef-125">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="6edef-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="6edef-126">✔️ 5,0 Preview ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="6edef-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="6edef-127">macOS 10,14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="6edef-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="6edef-128">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="6edef-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="6edef-129">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="6edef-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="6edef-130">✔️ 5,0 Preview ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="6edef-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="6edef-131">macOS 10,13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="6edef-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="6edef-132">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="6edef-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="6edef-133">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="6edef-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="6edef-134">✔️ 5,0 Preview ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="6edef-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="6edef-135">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="6edef-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="6edef-136">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="6edef-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="6edef-137">❌ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="6edef-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="6edef-138">❌ 5,0 Önizleme ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="6edef-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="6edef-139">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="6edef-139">Unsupported releases</span></span>

<span data-ttu-id="6edef-140">Aşağıdaki .NET Core sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="6edef-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="6edef-141">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="6edef-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6edef-142">3,0 ([sürüm notları][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="6edef-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="6edef-143">2,2 ([sürüm notları][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="6edef-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="6edef-144">2,0 ([sürüm notları][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="6edef-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="6edef-145">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="6edef-145">Runtime information</span></span>

<span data-ttu-id="6edef-146">Çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6edef-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="6edef-147">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="6edef-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="6edef-148">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="6edef-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="6edef-149">MacOS 'ta yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="6edef-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="6edef-150">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="6edef-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="6edef-151">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6edef-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="6edef-152">.NET Core çalışma zamanını içerir.</span><span class="sxs-lookup"><span data-stu-id="6edef-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="6edef-153">*.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="6edef-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="6edef-154">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="6edef-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="6edef-155">.NET Core uygulamalarıyla en iyi uyumluluk için *ASP.NET Core çalışma zamanı* yüklemenizi kesinlikle öneririz.</span><span class="sxs-lookup"><span data-stu-id="6edef-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="6edef-156">.NET Core çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="6edef-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="6edef-157">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="6edef-157">SDK information</span></span>

<span data-ttu-id="6edef-158">SDK, .NET Core Uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6edef-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="6edef-159">SDK 'Yı [yüklemek her iki](#runtime-information)çalışma zamanını içerir: ASP.NET Core ve .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6edef-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="6edef-160">.NET Core SDK indir</span><span class="sxs-lookup"><span data-stu-id="6edef-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="6edef-161">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="6edef-161">Dependencies</span></span>

<span data-ttu-id="6edef-162">.NET Core aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="6edef-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="6edef-163">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6edef-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6edef-164">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="6edef-164">.NET Core Version</span></span> | <span data-ttu-id="6edef-165">macOS</span><span class="sxs-lookup"><span data-stu-id="6edef-165">macOS</span></span>                 | <span data-ttu-id="6edef-166">Mimariler</span><span class="sxs-lookup"><span data-stu-id="6edef-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="6edef-167">3,1</span><span class="sxs-lookup"><span data-stu-id="6edef-167">3.1</span></span>               | <span data-ttu-id="6edef-168">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="6edef-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6edef-169">x64</span><span class="sxs-lookup"><span data-stu-id="6edef-169">x64</span></span> | [<span data-ttu-id="6edef-170">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6edef-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="6edef-171">3.0</span><span class="sxs-lookup"><span data-stu-id="6edef-171">3.0</span></span>               | <span data-ttu-id="6edef-172">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="6edef-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6edef-173">x64</span><span class="sxs-lookup"><span data-stu-id="6edef-173">x64</span></span> | [<span data-ttu-id="6edef-174">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6edef-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="6edef-175">2.2</span><span class="sxs-lookup"><span data-stu-id="6edef-175">2.2</span></span>               | <span data-ttu-id="6edef-176">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="6edef-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="6edef-177">x64</span><span class="sxs-lookup"><span data-stu-id="6edef-177">x64</span></span> | [<span data-ttu-id="6edef-178">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6edef-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="6edef-179">2.1</span><span class="sxs-lookup"><span data-stu-id="6edef-179">2.1</span></span>               | <span data-ttu-id="6edef-180">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="6edef-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="6edef-181">x64</span><span class="sxs-lookup"><span data-stu-id="6edef-181">x64</span></span> | [<span data-ttu-id="6edef-182">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="6edef-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="6edef-183">MacOS Catalina (sürüm 10,15) ile başlayarak, geliştirici KIMLIĞIYLE dağıtılan 1 Haziran 2019 ' den sonra oluşturulan tüm yazılımlar, dikkat edilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6edef-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="6edef-184">Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6edef-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="6edef-185">.NET Core (çalışma zamanı ve SDK) yükleyicileri 3,1, 3,0 ve 2,1 sürümleri, 18 Şubat 2020 tarihinden itibaren giderilmiş.</span><span class="sxs-lookup"><span data-stu-id="6edef-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="6edef-186">Önceki yayınlanmış sürümler yok.</span><span class="sxs-lookup"><span data-stu-id="6edef-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="6edef-187">Desteklenmeyen bir uygulama çalıştırırsanız aşağıdaki görüntüye benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="6edef-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarleştirme uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="6edef-189">Zorunlu kılınma 'nın .NET Core 'u (ve .NET Core uygulamalarınızı) nasıl etkilediği hakkında daha fazla bilgi için bkz. [macOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6edef-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="6edef-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="6edef-190">libgdiplus</span></span>

<span data-ttu-id="6edef-191">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6edef-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="6edef-192">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6edef-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="6edef-193">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="6edef-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="6edef-194">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6edef-194">Install with an installer</span></span>

<span data-ttu-id="6edef-195">macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6edef-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="6edef-196">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="6edef-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="6edef-197">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="6edef-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="6edef-198">.NET Core için macOS yükleyicilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6edef-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="6edef-199">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="6edef-200">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="6edef-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="6edef-201">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6edef-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="6edef-202">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="6edef-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="6edef-203">✔️ [.net 5,0 Preview İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="6edef-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="6edef-204">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="6edef-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="6edef-205">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="6edef-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="6edef-206">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="6edef-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="6edef-207">Ardından, indirilen dosyayı ayıklayın ve `export` .NET Core tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .NET Core 'un yolunda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6edef-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="6edef-208">Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü indirin.</span><span class="sxs-lookup"><span data-stu-id="6edef-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="6edef-209">Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6edef-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="6edef-210">Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="6edef-211">**Çalışma zamanını ayıklamak için aşağıdaki komutu kullanın**:</span><span class="sxs-lookup"><span data-stu-id="6edef-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="6edef-212">**SDK 'yı ayıklamak için aşağıdaki komutu kullanın**:</span><span class="sxs-lookup"><span data-stu-id="6edef-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="6edef-213">Yukarıdaki `export` Komutlar yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6edef-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="6edef-214">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6edef-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="6edef-215">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="6edef-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="6edef-216">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6edef-216">For example:</span></span>
>
> - <span data-ttu-id="6edef-217">**Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="6edef-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="6edef-218">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="6edef-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="6edef-219">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="6edef-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="6edef-220">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` .</span><span class="sxs-lookup"><span data-stu-id="6edef-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="6edef-221">Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="6edef-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="6edef-222">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6edef-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="6edef-223">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6edef-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="6edef-224">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="6edef-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="6edef-225">**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6edef-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="6edef-226">MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="6edef-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="6edef-227">En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 ' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6edef-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="6edef-228">[![.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6edef-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="6edef-229">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="6edef-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="6edef-230">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="6edef-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="6edef-231">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="6edef-232">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="6edef-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="6edef-233">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="6edef-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="6edef-234">[.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6edef-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="6edef-235">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="6edef-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="6edef-236">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="6edef-236">Install with bash automation</span></span>

<span data-ttu-id="6edef-237">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6edef-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="6edef-238">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6edef-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6edef-239">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6edef-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="6edef-240">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `current` .</span><span class="sxs-lookup"><span data-stu-id="6edef-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="6edef-241">`runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6edef-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="6edef-242">Aksi halde, komut dosyası [SDK 'yı](./windows.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="6edef-242">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="6edef-243">Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="6edef-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="6edef-244">ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="6edef-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="6edef-245">Docker</span><span class="sxs-lookup"><span data-stu-id="6edef-245">Docker</span></span>

<span data-ttu-id="6edef-246">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edef-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="6edef-247">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6edef-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="6edef-248">.NET Core, Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="6edef-249">Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6edef-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="6edef-250">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6edef-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="6edef-251">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edef-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="6edef-252">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edef-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="6edef-253">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="6edef-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6edef-254">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6edef-254">Next steps</span></span>

- <span data-ttu-id="6edef-255">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="6edef-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="6edef-256">[MacOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6edef-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="6edef-257">[Öğretici: macOS 'u kullanmaya](../tutorials/with-visual-studio-mac.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="6edef-257">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="6edef-258">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="6edef-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="6edef-259">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="6edef-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
