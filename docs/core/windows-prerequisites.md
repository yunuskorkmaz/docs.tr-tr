---
title: .NET Core Windows için Önkoşullar
description: Windows üzerinde gereken bağımlılıkları geliştirmek ve .NET Core uygulamaları çalıştırmak için makine öğrenin.
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.openlocfilehash: 7c6f39f004ebc39ca714ce419a38d842fcf8f0cb
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="2db9a-103">.NET Core Windows için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2db9a-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="2db9a-104">Bu makalede Windows .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2db9a-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="2db9a-105">Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Windows .NET Core uygulamaları geliştirme üç yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="2db9a-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="2db9a-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="2db9a-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="2db9a-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2db9a-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="2db9a-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2db9a-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="2db9a-109">.NET core desteklenen Windows sürümleri</span><span class="sxs-lookup"><span data-stu-id="2db9a-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="2db9a-110">.NET core üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2db9a-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="2db9a-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="2db9a-111">Windows 7 SP1</span></span>
* <span data-ttu-id="2db9a-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="2db9a-112">Windows 8.1</span></span>
* <span data-ttu-id="2db9a-113">Windows 10 Anniversary güncelleştirme (sürüm 1607) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2db9a-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="2db9a-114">Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="2db9a-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="2db9a-115">Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="2db9a-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="2db9a-116">Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="2db9a-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="2db9a-117">Windows Server 2016 (tam sunucu, Sunucu Çekirdeği veya Nano Server)</span><span class="sxs-lookup"><span data-stu-id="2db9a-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="2db9a-118">Bkz: [.NET Core 2.x - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için desteklenen işletim sistemleri 2.x.</span><span class="sxs-lookup"><span data-stu-id="2db9a-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="2db9a-119">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="2db9a-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="2db9a-120">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="2db9a-120">.NET Core dependencies</span></span>

<span data-ttu-id="2db9a-121">.NET core 1.1 ve önceki sürümlerinde Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'den önceki Windows sürümlerinde çalışan gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2db9a-121">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="2db9a-122">Bu bağımlılık .NET Core yükleyici tarafından otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2db9a-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="2db9a-123">[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="2db9a-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="2db9a-124">.NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="2db9a-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="2db9a-125">Bağımsız bir .NET Core uygulamasını dağıtma.</span><span class="sxs-lookup"><span data-stu-id="2db9a-125">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="2db9a-126">Kaynak Ürün oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2db9a-126">Building the product from source.</span></span>
* <span data-ttu-id="2db9a-127">.NET Core yoluyla yükleme bir *.zip* dosyası.</span><span class="sxs-lookup"><span data-stu-id="2db9a-127">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="2db9a-128">Bu yapı/CI/CD sunucuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2db9a-128">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="2db9a-129">*Windows 8.1 ve önceki sürümleri veya Windows Server 2012 R2 ve önceki sürümleri için:* Windows yüklemenizi güncel olduğundan ve içerir emin olun [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) yüklenebileceği Windows Update aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="2db9a-129">*For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:* Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) which can be installed through Windows Update.</span></span> <span data-ttu-id="2db9a-130">Bu güncelleştirmenin yüklü yoksa, aşağıdaki gibi bir .NET Core uygulamasını başlatma sırasında bir hata görürsünüz: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="2db9a-130">If you don't have this update installed, you'll see an error when you launch a .NET Core application like the following: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="2db9a-131">Visual Studio 2017 önkoşulları</span><span class="sxs-lookup"><span data-stu-id="2db9a-131">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="2db9a-132">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2db9a-132">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="2db9a-133">[Visual Studio 2017](#visual-studio-2017) Windows .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2db9a-133">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="2db9a-134">Daha fazla bilgiyi Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="2db9a-134">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2db9a-135">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="2db9a-135">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="2db9a-136">Visual Studio 2017 .NET Core 2.x uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="2db9a-136">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="2db9a-137">[Visual Studio 2017 15.3.0 sürümünü karşıdan yükleyip ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **.NET Core platformlar arası geliştirme** iş yükü (içinde **diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="2db9a-137">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="2db9a-139">Sonra **.NET Core platformlar arası geliştirme** araç takımı yüklendiğinde, Visual Studio 2017 kullanan .NET Core 1.x varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="2db9a-139">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="2db9a-140">.NET Core yükleme 2.x SDK Visual Studio 2017 .NET Core 2.x destek alma.</span><span class="sxs-lookup"><span data-stu-id="2db9a-140">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="2db9a-141">Yükleme [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="2db9a-141">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="2db9a-142">.NET Core mevcut veya yeni .NET Core 1.x projelerine yeniden hedefleyin 2.x aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="2db9a-142">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="2db9a-143">Üzerinde **proje** menüsünde Seç **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2db9a-143">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="2db9a-144">İçinde **hedef framework** seçim menüsünü kümesine değeri **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="2db9a-144">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle öğesinin seçili ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="2db9a-146">Bir kez .NET Core 2.x SDK yüklü Visual Studio 2017 kullanan .NET Core SDK 2.x varsayılan ve aşağıdaki eylemleri destekler:</span><span class="sxs-lookup"><span data-stu-id="2db9a-146">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="2db9a-147">Açın, yapı ve mevcut .NET Core 1.x projeleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2db9a-147">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="2db9a-148">.NET Core 1.x projeleri .NET Core 2.x, derleme ve çalıştırma yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="2db9a-148">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="2db9a-149">Yeni .NET Core 2.x projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2db9a-149">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2db9a-150">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="2db9a-150">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2db9a-151">Visual Studio'da .NET Core 1.x uygulamaları geliştirmek için [yükleyip Visual Studio 2017 RTM (sürüm 15.0.26228.4) ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **".NET Core platformlar arası geliştirme"** iş yükündeki (  **Diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="2db9a-151">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="2db9a-153">.NET Core 1.x geliştirme için Visual Studio 2015 kullanmak da mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:</span><span class="sxs-lookup"><span data-stu-id="2db9a-153">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="2db9a-154">.NET Core araç desteklenmeyen bir önizleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2db9a-154">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="2db9a-155">Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2db9a-155">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="2db9a-156">Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz: [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="2db9a-156">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="2db9a-157">Visual Studio 2017 sürümünüzü doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="2db9a-157">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="2db9a-158">Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.</span><span class="sxs-lookup"><span data-stu-id="2db9a-158">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="2db9a-159">İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2db9a-159">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="2db9a-160">.NET Core 2.1 Preview 1 uygulamalar, Visual Studio 2017 sürüm 15,6 için Önizleme 6 veya üstünü.</span><span class="sxs-lookup"><span data-stu-id="2db9a-160">For .NET Core 2.1 Preview 1 apps, Visual Studio 2017 version 15.6 Preview 6 or higher.</span></span>
>   * <span data-ttu-id="2db9a-161">.NET Core 2.0 uygulamalar için Visual Studio 2017 15.3 veya daha yüksek bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="2db9a-161">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="2db9a-162">.NET Core 1.x uygulamalar için Visual Studio 2017 15.0 veya daha yüksek bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="2db9a-162">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
