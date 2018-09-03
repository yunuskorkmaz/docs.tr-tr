---
title: Windows üzerinde .NET Core önkoşulları
description: Windows üzerinde gereken bağımlılıklar geliştirin ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: bbf54c8d215783656830f0fa035708be82a7c39c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482616"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="cd530-103">Windows üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="cd530-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="cd530-104">Bu makalede, Windows üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd530-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="cd530-105">Windows üzerinde .NET Core uygulamaları geliştirme kullandığı üç yöntem desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıkları geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="cd530-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="cd530-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="cd530-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="cd530-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="cd530-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="cd530-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cd530-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="cd530-109">.NET core desteklenen Windows sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd530-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="cd530-110">.NET core üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="cd530-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="cd530-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="cd530-111">Windows 7 SP1</span></span>
* <span data-ttu-id="cd530-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cd530-112">Windows 8.1</span></span>
* <span data-ttu-id="cd530-113">Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="cd530-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="cd530-114">Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="cd530-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="cd530-115">Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="cd530-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="cd530-116">Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="cd530-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="cd530-117">Windows Server 2016 veya sonraki sürümleri (tam sunucu, Sunucu Çekirdeği veya Nano Server)</span><span class="sxs-lookup"><span data-stu-id="cd530-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="cd530-118">Aşağıdaki makaleler sürüm başına .NET Core desteklenen işletim sistemlerinin tam bir listesi vardır:</span><span class="sxs-lookup"><span data-stu-id="cd530-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="cd530-119">.NET core 2.1 - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd530-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="cd530-120">.NET core 2.0 - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd530-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="cd530-121">.NET core 1.x - desteklenen işletim sistemi sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd530-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="cd530-122">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="cd530-122">.NET Core dependencies</span></span>

<span data-ttu-id="cd530-123">.NET core 1.1 ve önceki sürümlerinde Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'dan önceki Windows sürümlerinde çalışan gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cd530-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="cd530-124">Bu bağımlılık, .NET Core yükleyici tarafından otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cd530-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="cd530-125">[Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="cd530-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="cd530-126">.NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="cd530-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="cd530-127">Kendi başına bir .NET Core uygulaması dağıtma.</span><span class="sxs-lookup"><span data-stu-id="cd530-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="cd530-128">Kaynak Ürün oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cd530-128">Building the product from source.</span></span>
* <span data-ttu-id="cd530-129">.NET Core ile yükleme bir *.zip* dosya.</span><span class="sxs-lookup"><span data-stu-id="cd530-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="cd530-130">Bu derleme/CI/CD sunucuları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd530-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="cd530-131">**Windows 8.1 ve önceki sürümleri veya Windows Server 2012 R2 ve önceki sürümleri için:**</span><span class="sxs-lookup"><span data-stu-id="cd530-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="cd530-132">Windows yüklemenizin güncel olduğundan ve içerir emin [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), Windows güncelleştirmesi yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd530-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="cd530-133">Bu yazılımın yüklü yoksa, .NET Core uygulamasını başlattığında aşağıdaki gibi bir hata görürsünüz: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="cd530-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="cd530-134">**Windows 7 veya Windows Server 2008 R2 için:**</span><span class="sxs-lookup"><span data-stu-id="cd530-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="cd530-135">KB2999226 yanı sıra, ayrıca olduğundan emin olun [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) yüklü.</span><span class="sxs-lookup"><span data-stu-id="cd530-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="cd530-136">Bu yazılımın yüklü yoksa, .NET Core uygulamasını başlattığında aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="cd530-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="cd530-137">Visual Studio 2017 ile önkoşulları</span><span class="sxs-lookup"><span data-stu-id="cd530-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="cd530-138">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd530-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="cd530-139">[Visual Studio 2017](#visual-studio-2017) Windows üzerinde .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd530-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="cd530-140">Daha fazla Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="cd530-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd530-141">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd530-141">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="cd530-142">Visual Studio 2017'de .NET Core 2.1 uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="cd530-142">To develop .NET Core 2.1 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="cd530-143">[Visual Studio 2017 sürüm 15.7.0 yükleyip veya üzeri](/visualstudio/install/install-visual-studio) ile **.NET Core çoklu platform geliştirme** iş yükü (içinde **diğer araç takımları** bölümü) seçili.</span><span class="sxs-lookup"><span data-stu-id="cd530-143">[Download and install Visual Studio 2017 version 15.7.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-15-8-workloads.jpg)

<span data-ttu-id="cd530-145">Sonra **.NET Core çoklu platform geliştirme** araç takımı, varsayılan olarak yüklenir, Visual Studio 2017 15.7 kullanan .NET Core 2.0 SDK'sını ve Visual Studio 2017 15,8 2.1 SDK'sını kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd530-145">After the **.NET Core cross-platform development** toolset is installed, by default, Visual Studio 2017 15.7 uses .NET Core 2.0 SDK and Visual Studio 2017 15.8 uses 2.1 SDK.</span></span>

 2. <span data-ttu-id="cd530-146">Visual Studio 2017 15.7 kullanıyorsanız yükleyin [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) veya Visual Studio 2017 15,8 yükseltin.</span><span class="sxs-lookup"><span data-stu-id="cd530-146">If you're using Visual Studio 2017 15.7, install the [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) or upgrade to Visual Studio 2017 15.8.</span></span>

 3. <span data-ttu-id="cd530-147">Aşağıdaki yönergeleri kullanarak .NET Core 2.1 için mevcut veya yeni .NET Core projeleri yeniden hedefle:</span><span class="sxs-lookup"><span data-stu-id="cd530-147">Retarget existing or new .NET Core projects to .NET Core 2.1 using the following instructions:</span></span>
    * <span data-ttu-id="cd530-148">Üzerinde **proje** menüsünde Seç **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cd530-148">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="cd530-149">İçinde **hedef Framework'ü** seçim menüsünde ayarlayın değeri **.NET Core 2.1**.</span><span class="sxs-lookup"><span data-stu-id="cd530-149">In the **Target framework** selection menu, set the value to **.NET Core 2.1**.</span></span>

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle seçili öğe ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="cd530-151">Visual Studio ile .NET Core 2.1 SDK yapılandırılmış oluşturduktan sonra aşağıdaki işlemleri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd530-151">Once you have Visual Studio configured with .NET Core 2.1 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="cd530-152">Açın, derleme ve mevcut .NET Core 1.x ve 2.x'i projeleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cd530-152">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="cd530-153">.NET Core yeniden hedefle 1.x ve .NET Core 2.1 2.0 projeleri derlemek ve çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="cd530-153">Retarget .NET Core 1.x and 2.0 projects to .NET Core 2.1, build, and run.</span></span>
* <span data-ttu-id="cd530-154">Yeni .NET Core 2.1 projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd530-154">Create new .NET Core 2.1 projects.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd530-155">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd530-155">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="cd530-156">Visual Studio 2017'de .NET Core 2.0 uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="cd530-156">To develop .NET Core 2.0 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="cd530-157">[Visual Studio 2017 sürüm 15.3.0 yükleyip veya üzeri](/visualstudio/install/install-visual-studio) ile **.NET Core çoklu platform geliştirme** iş yükü (içinde **diğer araç takımları** bölümü) seçili.</span><span class="sxs-lookup"><span data-stu-id="cd530-157">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="cd530-159">Sonra **.NET Core çoklu platform geliştirme** araç yüklendiğinde, Visual Studio 2017, .NET Core kullanan 1.x varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="cd530-159">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="cd530-160">Visual Studio 2017'de .NET Core 2.0 desteği almak için .NET Core 2.0 SDK'sını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cd530-160">Install the .NET Core 2.0 SDK to get .NET Core 2.0 support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="cd530-161">Yükleme [.NET Core 2.0 SDK'sı](https://www.microsoft.com/net/download/dotnet-core/2.0).</span><span class="sxs-lookup"><span data-stu-id="cd530-161">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span></span>
 3. <span data-ttu-id="cd530-162">Aşağıdaki yönergeleri kullanarak .NET Core 2.0 için mevcut veya yeni .NET Core 1.x projeleri yeniden hedefle:</span><span class="sxs-lookup"><span data-stu-id="cd530-162">Retarget existing or new .NET Core 1.x projects to .NET Core 2.0 using the following instructions:</span></span>
    * <span data-ttu-id="cd530-163">Üzerinde **proje** menüsünde Seç **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cd530-163">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="cd530-164">İçinde **hedef Framework'ü** seçim menüsünde ayarlayın değeri **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="cd530-164">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle seçili öğe ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="cd530-166">.NET Core 2.0 SDK'yı yükledikten sonra Visual Studio 2017, .NET Core SDK 2.0 varsayılan olarak kullanır ve aşağıdaki eylemleri destekler:</span><span class="sxs-lookup"><span data-stu-id="cd530-166">Once the .NET Core 2.0 SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.0 by default, and supports the following actions:</span></span>

* <span data-ttu-id="cd530-167">Açık, derleme ve mevcut .NET Core 1.x projelerini çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="cd530-167">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="cd530-168">.NET Core 2.0, derleme, .NET Core 1.x projeleri yeniden hedefle ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cd530-168">Retarget .NET Core 1.x projects to .NET Core 2.0, build, and run.</span></span>
* <span data-ttu-id="cd530-169">Yeni .NET Core 2.0 projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd530-169">Create new .NET Core 2.0 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd530-170">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd530-170">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cd530-171">Visual Studio'da .NET Core 1.x uygulamalar geliştirmek için [Visual Studio 2017'yi indirip](/visualstudio/install/install-visual-studio) ile **".NET Core çoklu platform geliştirme"** iş yükü (içinde **diğer araç takımları**bölümü) seçili.</span><span class="sxs-lookup"><span data-stu-id="cd530-171">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core çoklu platform geliştirme" iş yüküyle Visual Studio 2017 ekran görüntüsü yükleme](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="cd530-173">Visual Studio 2015 için .NET Core 1.x geliştirme kullanmak da mümkündür, ancak aşağıdaki nedenlerle önerilmez:</span><span class="sxs-lookup"><span data-stu-id="cd530-173">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="cd530-174">.NET Core araçları, desteklenmeyen bir önizleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="cd530-174">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="cd530-175">Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd530-175">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="cd530-176">Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz. [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="cd530-176">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="cd530-177">Visual Studio 2017 sürüm doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="cd530-177">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="cd530-178">Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.</span><span class="sxs-lookup"><span data-stu-id="cd530-178">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="cd530-179">İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="cd530-179">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="cd530-180">.NET Core 2.2 Önizleme 1 uygulamalar için Visual Studio 2017 sürüm 15.9 (şu anda önizlemede) veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cd530-180">For .NET Core 2.2 Preview 1 apps, Visual Studio 2017 version 15.9 (currently in Preview) or higher.</span></span>
>   * <span data-ttu-id="cd530-181">.NET Core 2.1 uygulamaları için Visual Studio 2017 sürüm 15.7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cd530-181">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="cd530-182">.NET Core 2.0 uygulamaları için Visual Studio 2017 sürüm 15.3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cd530-182">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="cd530-183">.NET Core 1.x uygulamaları için Visual Studio 2017 sürüm 15.0 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="cd530-183">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
