---
title: ".NET Core Windows için Önkoşullar"
description: "Windows üzerinde gereken bağımlılıkları geliştirmek ve .NET Core uygulamaları çalıştırmak için makine öğrenin."
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: fdbba188cf939ce3eb969a1f780e086fcf17da13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="10213-103">.NET Core Windows için Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="10213-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="10213-104">Bu makalede Windows .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10213-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="10213-105">Desteklenen işletim sistemi sürümleri ve izleyin bağımlılıkları Windows .NET Core uygulamaları geliştirme üç yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="10213-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="10213-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="10213-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="10213-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10213-107">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* [<span data-ttu-id="10213-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10213-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="10213-109">.NET core desteklenen Windows sürümleri</span><span class="sxs-lookup"><span data-stu-id="10213-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="10213-110">.NET core üzerinde aşağıdaki sürümleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="10213-110">.NET Core is supported on the following versions of :</span></span>

* <span data-ttu-id="10213-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="10213-111">Windows 7 SP1</span></span>
* <span data-ttu-id="10213-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="10213-112">Windows 8.1</span></span>
* <span data-ttu-id="10213-113">Windows 10, Windows 10 Anniversary güncelleştirme (sürüm 1607) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="10213-113">Windows 10, Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="10213-114">Windows Server 2008 R2 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="10213-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="10213-115">Windows Server 2012 SP1 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="10213-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="10213-116">Windows Server 2012 R2 (tam sunucu veya Sunucu Çekirdeği)</span><span class="sxs-lookup"><span data-stu-id="10213-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="10213-117">Windows Server 2016 (tam sunucu, Sunucu Çekirdeği veya Nano Server)</span><span class="sxs-lookup"><span data-stu-id="10213-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="10213-118">Bkz: [.NET Core 2.x - desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için desteklenen işletim sistemleri 2.x.</span><span class="sxs-lookup"><span data-stu-id="10213-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="10213-119">Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="10213-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="10213-120">.NET core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="10213-120">.NET Core dependencies</span></span>

<span data-ttu-id="10213-121">.NET core 1.1 ve daha önceki Visual C++ yeniden dağıtılabilir Windows 10 ve Windows Server 2016'den önceki Windows sürümlerinde çalışan gerektirir.</span><span class="sxs-lookup"><span data-stu-id="10213-121">.NET Core 1.1 and earlier requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="10213-122">Bu bağımlılık .NET Core yükleyici tarafından otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="10213-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="10213-123">[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) zaman el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="10213-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

   * <span data-ttu-id="10213-124">.NET Core ile yükleme [yükleyicisi betiği](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="10213-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
   * <span data-ttu-id="10213-125">Bağımsız bir .NET Core uygulamasını dağıtma.</span><span class="sxs-lookup"><span data-stu-id="10213-125">Deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="10213-126"><em>Yalnızca Windows 7 ve Windows Server 2008 makineler için:</em></span><span class="sxs-lookup"><span data-stu-id="10213-126"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="10213-127">Windows yüklemenizi güncel olduğundan ve düzeltmeyi içerir emin olun [KB2533623](https://support.microsoft.com/help/2533623) Windows Update aracılığıyla yüklü.</span><span class="sxs-lookup"><span data-stu-id="10213-127">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="10213-128">Visual Studio 2017 önkoşulları</span><span class="sxs-lookup"><span data-stu-id="10213-128">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="10213-129">.NET Core SDK'sını kullanarak .NET Core uygulamaları geliştirmek için herhangi bir Düzenleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10213-129">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span>  <span data-ttu-id="10213-130">[Visual Studio 2017](#visual-studio-2017) Windows .NET Core uygulamaları için bir tümleşik geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="10213-130">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="10213-131">Daha fazla bilgiyi Visual Studio 2017'deki değişiklikler hakkında [sürüm notları](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="10213-131">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="10213-132">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="10213-132">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="10213-133">Visual Studio 2017 .NET Core 2.x uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="10213-133">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="10213-134">[Visual Studio 2017 15.3.0 sürümünü karşıdan yükleyip ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **.NET Core platformlar arası geliştirme** iş yükü (içinde **diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="10213-134">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="10213-135">![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="10213-135">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span></span>

<span data-ttu-id="10213-136">Sonra **.NET Core platformlar arası geliştirme** araç takımı yüklendiğinde, Visual Studio 2017 kullanan .NET Core 1.x varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="10213-136">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="10213-137">.NET Core yükleme 2.x SDK Visual Studio 2017 .NET Core 2.x destek alma.</span><span class="sxs-lookup"><span data-stu-id="10213-137">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="10213-138">Yükleme [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="10213-138">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="10213-139">.NET Core mevcut veya yeni .NET Core 1.x projelerine yeniden hedefleyin 2.x aşağıdaki yönergeleri kullanarak:</span><span class="sxs-lookup"><span data-stu-id="10213-139">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="10213-140">Üzerinde **proje** menüsünde Seç **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="10213-140">On the **Project** menu, Choose **Properties**.</span></span> 
    * <span data-ttu-id="10213-141">İçinde **hedef framework** seçim menüsünü kümesine değeri **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="10213-141">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Ekran görüntüsü, Visual Studio 2017 uygulama projesi özelliğiyle öğesinin seçili ".NET Core 2.0" hedef framework menüsü](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="10213-143">Bir kez .NET Core 2.x SDK yüklü Visual Studio 2017 kullanan .NET Core SDK 2.x varsayılan ve aşağıdaki eylemleri destekler:</span><span class="sxs-lookup"><span data-stu-id="10213-143">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

  * <span data-ttu-id="10213-144">Açın, yapı ve mevcut .NET Core 1.x projeleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10213-144">Open, build, and run existing .NET Core 1.x projects.</span></span>
  * <span data-ttu-id="10213-145">.NET Core 1.x projeleri .NET Core 2.x, derleme ve çalıştırma yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="10213-145">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
  * <span data-ttu-id="10213-146">Yeni .NET Core 2.x projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10213-146">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="10213-147">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="10213-147">.NET Core 1.x</span></span>](#tab/netcore1x)
<span data-ttu-id="10213-148">Visual Studio'da .NET Core 1.x uygulamaları geliştirmek için [yükleyip Visual Studio 2017 RTM (sürüm 15.0.26228.4) ya da daha yüksek](/visualstudio/install/install-visual-studio) ile **".NET Core platformlar arası geliştirme"** iş yükündeki (  **Diğer Toolsets** bölüm) seçili.</span><span class="sxs-lookup"><span data-stu-id="10213-148">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="10213-149">![Seçili ".NET Core platformlar arası geliştirme" iş yükü ile Visual Studio 2017 ekran yükleme](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="10213-149">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="10213-150">.NET Core 1.x geliştirme için Visual Studio 2015 kullanmak da mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:</span><span class="sxs-lookup"><span data-stu-id="10213-150">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="10213-151">.NET Core araç desteklenmeyen bir önizleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="10213-151">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="10213-152">Projeleri project.json tabanlı, kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="10213-152">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="10213-153">Proje biçimi değişiklikler hakkında daha fazla bilgi için bkz: [değişiklikleri üst düzey genel bakış](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="10213-153">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

>[!TIP]
  > <span data-ttu-id="10213-154">Visual Studio 2017 sürümünüzü doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="10213-154">To verify your Visual Studio 2017 version:</span></span>
>
     > * <span data-ttu-id="10213-155">Üzerinde **yardımcı** menüsünde seçin **Microsoft Visual Studio hakkında**.</span><span class="sxs-lookup"><span data-stu-id="10213-155">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
     > * <span data-ttu-id="10213-156">İçinde **Microsoft Visual Studio hakkında** iletişim kutusunda, sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="10213-156">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>     * <span data-ttu-id="10213-157">.NET Core 2.x uygulamaları, Visual Studio 2017 sürüm 15.3 (26730.01) ya da daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="10213-157">For .NET Core 2.x apps, Visual Studio 2017 version 15.3 (26730.01) or higher.</span></span>
>     * <span data-ttu-id="10213-158">.NET Core 1.x uygulamaları, Visual Studio 2017 sürüm 15.0 (26228.04) ya da daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="10213-158">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 (26228.04) or higher.</span></span>
