---
title: MacOS 'ta .NET 'i yükler
description: .NET yükleyebileceğiniz macOS sürümleri hakkında bilgi edinin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f926479227f11def5c8bb8c6bf29ad30a04e6ed2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715140"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="4c82c-103">MacOS 'ta .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="4c82c-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

<span data-ttu-id="4c82c-107">Bu makalede, macOS 'ta .NET yüklemeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4c82c-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="4c82c-108">.NET çalışma zamanı ve SDK 'dan oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c82c-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="4c82c-109">Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="4c82c-110">SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="4c82c-111">.NET çalışma zamanı her zaman SDK ile birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="4c82c-112">En son .NET sürümü 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4c82c-113">.NET Core indirin</span><span class="sxs-lookup"><span data-stu-id="4c82c-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="4c82c-114">Desteklenen yayınlar</span><span class="sxs-lookup"><span data-stu-id="4c82c-114">Supported releases</span></span>

<span data-ttu-id="4c82c-115">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen macOS sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="4c82c-116">Bu sürümler, [.NET sürümünün destek sonuna ulaşmasını](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)ve bu sürümlerin desteklenmemesini destekler.</span><span class="sxs-lookup"><span data-stu-id="4c82c-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="4c82c-117">✔️, .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="4c82c-118">Bir ❌ , .NET Core sürümünün desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="4c82c-119">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="4c82c-119">Operating System</span></span>          | <span data-ttu-id="4c82c-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4c82c-120">.NET Core 2.1</span></span> | <span data-ttu-id="4c82c-121">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="4c82c-121">.NET Core 3.1</span></span> | <span data-ttu-id="4c82c-122">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4c82c-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4c82c-123">macOS 10,15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="4c82c-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="4c82c-124">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c82c-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c82c-125">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c82c-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c82c-126">✔️ 5,0 ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c82c-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c82c-127">macOS 10,14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="4c82c-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="4c82c-128">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c82c-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c82c-129">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c82c-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c82c-130">✔️ 5,0 ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c82c-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c82c-131">macOS 10,13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="4c82c-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="4c82c-132">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c82c-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c82c-133">✔️ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c82c-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c82c-134">✔️ 5,0 ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c82c-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c82c-135">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="4c82c-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="4c82c-136">✔️ 2,1 ([sürüm notları][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c82c-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c82c-137">❌ 3,1 ([sürüm notları][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c82c-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c82c-138">❌ 5,0 ([sürüm notları][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c82c-138">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="4c82c-139">Desteklenmeyen yayınlar</span><span class="sxs-lookup"><span data-stu-id="4c82c-139">Unsupported releases</span></span>

<span data-ttu-id="4c82c-140">Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-140">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="4c82c-141">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="4c82c-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4c82c-142">3,0 ([sürüm notları][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="4c82c-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="4c82c-143">2,2 ([sürüm notları][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="4c82c-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="4c82c-144">2,0 ([sürüm notları][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="4c82c-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="4c82c-145">Çalışma zamanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="4c82c-145">Runtime information</span></span>

<span data-ttu-id="4c82c-146">Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-146">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="4c82c-147">Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler.</span><span class="sxs-lookup"><span data-stu-id="4c82c-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="4c82c-148">Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.</span><span class="sxs-lookup"><span data-stu-id="4c82c-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="4c82c-149">MacOS 'ta yükleyebileceğiniz üç farklı çalışma zamanı vardır:</span><span class="sxs-lookup"><span data-stu-id="4c82c-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="4c82c-150">*ASP.NET Core çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="4c82c-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="4c82c-151">ASP.NET Core uygulamalar çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="4c82c-152">.NET çalışma zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-152">Includes the .NET runtime.</span></span>

<span data-ttu-id="4c82c-153">*.NET çalışma zamanı*</span><span class="sxs-lookup"><span data-stu-id="4c82c-153">*.NET runtime*</span></span>\
<span data-ttu-id="4c82c-154">Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez.</span><span class="sxs-lookup"><span data-stu-id="4c82c-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="4c82c-155">.NET uygulamalarıyla en iyi uyumluluk için *ASP.NET Core çalışma zamanı* yüklemenizi kesinlikle öneririz.</span><span class="sxs-lookup"><span data-stu-id="4c82c-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4c82c-156">.NET çalışma zamanını indirin</span><span class="sxs-lookup"><span data-stu-id="4c82c-156">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="4c82c-157">SDK bilgileri</span><span class="sxs-lookup"><span data-stu-id="4c82c-157">SDK information</span></span>

<span data-ttu-id="4c82c-158">SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-158">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="4c82c-159">SDK 'nın [yüklenmesi her iki](#runtime-information)çalışma zamanını da içerir: ASP.NET Core ve .net.</span><span class="sxs-lookup"><span data-stu-id="4c82c-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="4c82c-160">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="4c82c-160">Dependencies</span></span>

<span data-ttu-id="4c82c-161">.NET aşağıdaki macOS sürümleriyle desteklenir:</span><span class="sxs-lookup"><span data-stu-id="4c82c-161">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="4c82c-162">Bir `+` sembol en düşük sürümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c82c-162">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4c82c-163">.NET Core sürümü</span><span class="sxs-lookup"><span data-stu-id="4c82c-163">.NET Core Version</span></span> | <span data-ttu-id="4c82c-164">Mac OS</span><span class="sxs-lookup"><span data-stu-id="4c82c-164">macOS</span></span>                 | <span data-ttu-id="4c82c-165">Mimariler</span><span class="sxs-lookup"><span data-stu-id="4c82c-165">Architectures</span></span> | <span data-ttu-id="4c82c-166">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-166">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="4c82c-167">5.0</span><span class="sxs-lookup"><span data-stu-id="4c82c-167">5.0</span></span>               | <span data-ttu-id="4c82c-168">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="4c82c-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4c82c-169">x64</span><span class="sxs-lookup"><span data-stu-id="4c82c-169">x64</span></span> | [<span data-ttu-id="4c82c-170">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="4c82c-171">3,1</span><span class="sxs-lookup"><span data-stu-id="4c82c-171">3.1</span></span>               | <span data-ttu-id="4c82c-172">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="4c82c-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4c82c-173">x64</span><span class="sxs-lookup"><span data-stu-id="4c82c-173">x64</span></span> | [<span data-ttu-id="4c82c-174">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="4c82c-175">3,0</span><span class="sxs-lookup"><span data-stu-id="4c82c-175">3.0</span></span>               | <span data-ttu-id="4c82c-176">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="4c82c-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4c82c-177">x64</span><span class="sxs-lookup"><span data-stu-id="4c82c-177">x64</span></span> | [<span data-ttu-id="4c82c-178">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="4c82c-179">2.2</span><span class="sxs-lookup"><span data-stu-id="4c82c-179">2.2</span></span>               | <span data-ttu-id="4c82c-180">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="4c82c-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="4c82c-181">x64</span><span class="sxs-lookup"><span data-stu-id="4c82c-181">x64</span></span> | [<span data-ttu-id="4c82c-182">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="4c82c-183">2.1</span><span class="sxs-lookup"><span data-stu-id="4c82c-183">2.1</span></span>               | <span data-ttu-id="4c82c-184">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="4c82c-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="4c82c-185">x64</span><span class="sxs-lookup"><span data-stu-id="4c82c-185">x64</span></span> | [<span data-ttu-id="4c82c-186">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4c82c-186">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="4c82c-187">MacOS Catalina (sürüm 10,15) ile başlayarak, geliştirici KIMLIĞIYLE dağıtılan 1 Haziran 2019 ' den sonra oluşturulan tüm yazılımlar, dikkat edilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-187">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="4c82c-188">Bu gereksinim .NET çalışma zamanı, .NET SDK ve .NET ile oluşturulan yazılımlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-188">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="4c82c-189">.NET 5,0 ve .NET Core 3,1, 3,0 ve 2,1 için çalışma zamanı ve SDK yükleyicileri, 18 Şubat 2020 ' den itibaren giderilmiş.</span><span class="sxs-lookup"><span data-stu-id="4c82c-189">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="4c82c-190">Önceki yayınlanmış sürümler yok.</span><span class="sxs-lookup"><span data-stu-id="4c82c-190">Prior released versions aren't notarized.</span></span> <span data-ttu-id="4c82c-191">Desteklenmeyen bir uygulama çalıştırırsanız aşağıdaki görüntüye benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="4c82c-191">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notarleştirme uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="4c82c-193">Zorlanan uygulamanın .NET 'i (ve .NET uygulamalarınızı) nasıl etkilediği hakkında daha fazla bilgi için bkz. [macOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="4c82c-193">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="4c82c-194">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="4c82c-194">libgdiplus</span></span>

<span data-ttu-id="4c82c-195">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-195">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="4c82c-196">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-196">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="4c82c-197">*Brew* yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="4c82c-197">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="4c82c-198">Bir yükleyici ile yükleme</span><span class="sxs-lookup"><span data-stu-id="4c82c-198">Install with an installer</span></span>

<span data-ttu-id="4c82c-199">macOS, .NET 5,0 SDK 'Yı yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4c82c-199">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="4c82c-200">x64 (64-bit) CPU 'Lar</span><span class="sxs-lookup"><span data-stu-id="4c82c-200">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="4c82c-201">İndirme ve el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="4c82c-201">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="4c82c-202">.NET için macOS yükleyicilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c82c-202">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="4c82c-203">El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-203">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="4c82c-204">Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-204">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="4c82c-205">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4c82c-205">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="4c82c-206">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="4c82c-206">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="4c82c-207">✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="4c82c-207">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="4c82c-208">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="4c82c-208">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="4c82c-209">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="4c82c-209">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="4c82c-210">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="4c82c-210">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="4c82c-211">Ardından, indirilen dosyayı ayıklayın ve `export` .NET tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .net 'ın yol içinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c82c-211">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="4c82c-212">Çalışma zamanını ayıklamak ve .NET CLı komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET ikili sürümü indirin.</span><span class="sxs-lookup"><span data-stu-id="4c82c-212">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="4c82c-213">Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c82c-213">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="4c82c-214">Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-214">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="4c82c-215">**Çalışma zamanını ayıklamak için aşağıdaki komutu kullanın**:</span><span class="sxs-lookup"><span data-stu-id="4c82c-215">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="4c82c-216">**SDK 'yı ayıklamak için aşağıdaki komutu kullanın**:</span><span class="sxs-lookup"><span data-stu-id="4c82c-216">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="4c82c-217">Yukarıdaki `export` Komutlar yalnızca .net CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-217">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="4c82c-218">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c82c-218">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="4c82c-219">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-219">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="4c82c-220">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4c82c-220">For example:</span></span>
>
> - <span data-ttu-id="4c82c-221">**Bash kabuğu**: *~/.bash_profile*, *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="4c82c-221">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="4c82c-222">**Korn kabuğu**: *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="4c82c-222">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="4c82c-223">**Z kabuğu**: *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="4c82c-223">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="4c82c-224">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` .</span><span class="sxs-lookup"><span data-stu-id="4c82c-224">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="4c82c-225">Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="4c82c-225">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="4c82c-226">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c82c-226">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="4c82c-227">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-227">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="4c82c-228">Mac için Visual Studio ile yüklensin</span><span class="sxs-lookup"><span data-stu-id="4c82c-228">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="4c82c-229">**.Net** iş yükü seçiliyken Mac için Visual Studio .NET SDK 'sını yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="4c82c-229">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="4c82c-230">MacOS 'ta .NET geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="4c82c-230">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="4c82c-231">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="4c82c-231">.NET SDK version</span></span>      | <span data-ttu-id="4c82c-232">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="4c82c-232">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="4c82c-233">5.0</span><span class="sxs-lookup"><span data-stu-id="4c82c-233">5.0</span></span>                   | <span data-ttu-id="4c82c-234">Mac için Visual Studio 2019 sürüm 8,8 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="4c82c-234">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="4c82c-235">3,1</span><span class="sxs-lookup"><span data-stu-id="4c82c-235">3.1</span></span>                   | <span data-ttu-id="4c82c-236">Mac için Visual Studio 2019 sürüm 8,4 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="4c82c-236">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="4c82c-237">2.1</span><span class="sxs-lookup"><span data-stu-id="4c82c-237">2.1</span></span>                   | <span data-ttu-id="4c82c-238">Mac için Visual Studio 2019 sürüm 8,0 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="4c82c-238">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="4c82c-239">[![.NET iş yükü özelliği ile Mac için macOS Visual Studio 2019](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="4c82c-239">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="4c82c-240">Visual Studio Code birlikte yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="4c82c-240">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="4c82c-241">Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-241">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="4c82c-242">Visual Studio Code Windows, macOS ve Linux için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-242">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="4c82c-243">Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET yükleyicisi ile birlikte gelmediğinden, .NET desteği ekleme basittir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-243">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="4c82c-244">[Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="4c82c-244">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="4c82c-245">[.NET SDK 'Sını indirip yükleyin](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4c82c-245">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="4c82c-246">[Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="4c82c-246">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="4c82c-247">Bash otomasyonu ile Install</span><span class="sxs-lookup"><span data-stu-id="4c82c-247">Install with bash automation</span></span>

<span data-ttu-id="4c82c-248">[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-248">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="4c82c-249">Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c82c-249">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="4c82c-250">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-250">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="4c82c-251">Anahtarı belirterek belirli bir sürümü seçebilirsiniz `current` .</span><span class="sxs-lookup"><span data-stu-id="4c82c-251">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="4c82c-252">`runtime`Çalışma zamanı yüklemek için anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c82c-252">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="4c82c-253">Aksi halde, komut dosyası [SDK 'yı](./windows.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="4c82c-253">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="4c82c-254">Önceki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse.</span><span class="sxs-lookup"><span data-stu-id="4c82c-254">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="4c82c-255">ASP.NET Core çalışma zamanı standart .NET çalışma zamanını da içerir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-255">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="4c82c-256">Docker</span><span class="sxs-lookup"><span data-stu-id="4c82c-256">Docker</span></span>

<span data-ttu-id="4c82c-257">Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c82c-257">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="4c82c-258">Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c82c-258">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="4c82c-259">.NET, bir Docker kapsayıcısında çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-259">.NET can run in a Docker container.</span></span> <span data-ttu-id="4c82c-260">Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet/)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-260">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="4c82c-261">Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4c82c-261">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="4c82c-262">Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c82c-262">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="4c82c-263">Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c82c-263">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="4c82c-264">Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.</span><span class="sxs-lookup"><span data-stu-id="4c82c-264">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c82c-265">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4c82c-265">Next steps</span></span>

- <span data-ttu-id="4c82c-266">[.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="4c82c-266">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="4c82c-267">[MacOS Catalina Ile çalışma](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="4c82c-267">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="4c82c-268">[Öğretici: macOS 'u kullanmaya](../tutorials/with-visual-studio-mac.md)başlayın.</span><span class="sxs-lookup"><span data-stu-id="4c82c-268">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="4c82c-269">[Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="4c82c-269">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="4c82c-270">[Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.</span><span class="sxs-lookup"><span data-stu-id="4c82c-270">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
