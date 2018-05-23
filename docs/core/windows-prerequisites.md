---
title: .NET Core Windows için Önkoşullar
description: Windows üzerinde gereken bağımlılıkları geliştirmek ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="c1ac3-103">.NET Core Windows için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c1ac3-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="c1ac3-104">Bu makalede Windows .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="c1ac3-105">Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Windows .NET Core uygulamaları geliştirme üç yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="c1ac3-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="c1ac3-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="c1ac3-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c1ac3-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="c1ac3-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c1ac3-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="c1ac3-109">.NET core desteklenen Windows sürümleri</span><span class="sxs-lookup"><span data-stu-id="c1ac3-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="c1ac3-110">.NET core üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="c1ac3-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="c1ac3-111">Windows 7 SP1</span></span>
* <span data-ttu-id="c1ac3-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c1ac3-112">Windows 8.1</span></span>
* <span data-ttu-id="c1ac3-113">Windows 10 Anniversary güncelleştirme (sürüm 1607) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="c1ac3-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="c1ac3-114">Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="c1ac3-115">Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="c1ac3-116">Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="c1ac3-117">Windows Server 2016 veya sonraki sürümleri (tam sunucu, Sunucu Çekirdeği veya Nano Server)</span><span class="sxs-lookup"><span data-stu-id="c1ac3-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="c1ac3-118">Aşağıdaki makalelerde her sürümü .NET Core desteklenen işletim sistemlerinin tam bir listesi vardır:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="c1ac3-119">.NET core 2.1 - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="c1ac3-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="c1ac3-120">.NET core 2.0 - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="c1ac3-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="c1ac3-121">.NET core 1.x - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="c1ac3-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="c1ac3-122">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="c1ac3-122">.NET Core dependencies</span></span>

<span data-ttu-id="c1ac3-123">.NET core 1.1 ve önceki sürümlerinde Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'den önceki Windows sürümlerinde çalışan gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="c1ac3-124">Bu bağımlılık .NET Core yükleyici tarafından otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="c1ac3-125">[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="c1ac3-126">.NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c1ac3-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="c1ac3-127">Bağımsız bir .NET Core uygulamasını dağıtma.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="c1ac3-128">Kaynak Ürün oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-128">Building the product from source.</span></span>
* <span data-ttu-id="c1ac3-129">.NET Core yoluyla yükleme bir *.zip* dosyası.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="c1ac3-130">Bu yapı/CI/CD sunucuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="c1ac3-131">**Windows 8.1 ve önceki sürümleri veya Windows Server 2012 R2 ve önceki sürümleri için:**</span><span class="sxs-lookup"><span data-stu-id="c1ac3-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="c1ac3-132">Windows yüklemenizi güncel olduğundan ve içerir emin olun [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), yüklenebileceği Windows Update aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="c1ac3-133">Bu güncelleştirmenin yüklü yoksa, .NET Core uygulama başlattığında aşağıdaki gibi bir hata görürsünüz: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="c1ac3-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="c1ac3-134">**Windows 7 veya Windows Server 2008 R2 için:**</span><span class="sxs-lookup"><span data-stu-id="c1ac3-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="c1ac3-135">KB2999226 ek olarak, aynı zamanda sahip olduğunuzdan emin olun [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) yüklü.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="c1ac3-136">Bu güncelleştirmenin yüklü yoksa, bir .NET Core uygulamasını başlattığında aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="c1ac3-137">Visual Studio 2017 önkoşulları</span><span class="sxs-lookup"><span data-stu-id="c1ac3-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="c1ac3-138">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="c1ac3-139">[Visual Studio 2017](#visual-studio-2017) Windows .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="c1ac3-140">Daha fazla bilgiyi Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="c1ac3-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c1ac3-141">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c1ac3-141">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c1ac3-142">Visual Studio 2017 .NET Core 2.x uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-142">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="c1ac3-143">[Visual Studio 2017 15.3.0 sürümünü karşıdan yükleyip ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **.NET Core platformlar arası geliştirme** iş yükü (içinde **diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-143">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="c1ac3-145">Sonra **.NET Core platformlar arası geliştirme** araç takımı yüklendiğinde, Visual Studio 2017 kullanan .NET Core 1.x varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-145">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="c1ac3-146">.NET Core yükleme 2.x SDK Visual Studio 2017 .NET Core 2.x destek alma.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-146">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="c1ac3-147">Yükleme [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="c1ac3-147">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="c1ac3-148">.NET Core mevcut veya yeni .NET Core 1.x projelerine yeniden hedefleyin 2.x aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-148">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="c1ac3-149">Üzerinde **proje** menüsünde Seç **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-149">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="c1ac3-150">İçinde **hedef framework** seçim menüsünü kümesine değeri **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-150">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle öğesinin seçili ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="c1ac3-152">Bir kez .NET Core 2.x SDK yüklü Visual Studio 2017 kullanan .NET Core SDK 2.x varsayılan ve aşağıdaki eylemleri destekler:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-152">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="c1ac3-153">Açın, yapı ve mevcut .NET Core 1.x projeleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-153">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="c1ac3-154">.NET Core 1.x projeleri .NET Core 2.x, derleme ve çalıştırma yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-154">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="c1ac3-155">Yeni .NET Core 2.x projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-155">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c1ac3-156">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c1ac3-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c1ac3-157">Visual Studio'da .NET Core 1.x uygulamaları geliştirmek için [yükleyip Visual Studio 2017 RTM (sürüm 15.0.26228.4) ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **".NET Core platformlar arası geliştirme"** iş yükündeki (  **Diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="c1ac3-159">.NET Core 1.x geliştirme için Visual Studio 2015 kullanmak da mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="c1ac3-160">.NET Core araç desteklenmeyen bir önizleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="c1ac3-161">Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="c1ac3-162">Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz: [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="c1ac3-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="c1ac3-163">Visual Studio 2017 sürümünüzü doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="c1ac3-163">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="c1ac3-164">Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="c1ac3-165">İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="c1ac3-166">.NET Core 2.1 RC uygulamalar için Visual Studio 2017 15.7 veya daha yüksek bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-166">For .NET Core 2.1 RC apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="c1ac3-167">.NET Core 2.0 uygulamalar için Visual Studio 2017 15.3 veya daha yüksek bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-167">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="c1ac3-168">.NET Core 1.x uygulamalar için Visual Studio 2017 15.0 veya daha yüksek bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="c1ac3-168">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
