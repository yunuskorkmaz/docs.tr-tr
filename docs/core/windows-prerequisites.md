---
title: Windows üzerinde .NET Core önkoşulları
description: .NET Core uygulamaları geliştirmek ve çalıştırmak için Windows makinenizde hangi bağımlılıklara ihtiyacınız olduğunu öğrenin.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 1921ef565c2d04624009f7684e439ddba1cdf57e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331067"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="40531-103">Windows üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="40531-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="40531-104">Bu makalede, Windows 'da .NET Core uygulamalarını çalıştırmak için desteklenen işletim sistemi sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40531-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="40531-105">Desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıklar, Windows 'ta .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="40531-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="40531-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="40531-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="40531-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="40531-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="40531-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="40531-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="40531-109">Ayrıca, Visual Studio 2017 kullanarak Windows üzerinde geliştirme yapıyorsanız, [Visual studio 2017 Ile Önkoşullar](#prerequisites-with-visual-studio-2017) bölümü, .NET Core geliştirmesi için desteklenen en düşük sürümler hakkında daha ayrıntılı bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="40531-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="40531-110">.NET Core tarafından desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="40531-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="40531-111">Aşağıdaki makalelerde sürüm başına .NET Core tarafından desteklenen işletim sistemlerinin kapsamlı bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40531-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="40531-112">.NET Core 3,0 (Önizleme)</span><span class="sxs-lookup"><span data-stu-id="40531-112">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="40531-113">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="40531-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="40531-114">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="40531-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="40531-115">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="40531-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="40531-116">İndirme bağlantıları ve daha fazla bilgi için bkz. eski sürümler için en son sürümü veya [.net İndirmeleri arşivini](https://dotnet.microsoft.com/download/archives#dotnet-core) indirmek üzere [.net İndirmeleri](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="40531-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="40531-117">.NET Core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="40531-117">.NET Core dependencies</span></span>

<span data-ttu-id="40531-118">.NET Core 1,1 ve önceki sürümleri, Windows 10 C++ ve windows Server 2016 ' den önceki Windows sürümlerinde çalışırken görsel yeniden dağıtılabilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40531-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="40531-119">Bu bağımlılık, .NET Core yükleyicisi tarafından otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="40531-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="40531-120">[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) , şu durumlarda el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="40531-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="40531-121">.NET Core, [Yükleyici betiği](./tools/dotnet-install-script.md)ile yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="40531-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="40531-122">Kendi kendine içerilen bir .NET Core uygulaması dağıtma.</span><span class="sxs-lookup"><span data-stu-id="40531-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="40531-123">Ürünün kaynaktan oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="40531-123">Building the product from source.</span></span>
* <span data-ttu-id="40531-124">.NET Core 'u bir *. zip* dosyası aracılığıyla yükleme.</span><span class="sxs-lookup"><span data-stu-id="40531-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="40531-125">Bu, derleme/CI/CD sunucuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="40531-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="40531-126">**Windows 8.1 ve önceki sürümler veya Windows Server 2012 R2 ve önceki sürümleri için:**</span><span class="sxs-lookup"><span data-stu-id="40531-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="40531-127">Windows yüklemenizin güncel olduğundan ve Windows Update aracılığıyla yüklenebilen [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows)içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="40531-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="40531-128">Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="40531-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="40531-129">**Windows 7 veya Windows Server 2008 R2 için:**</span><span class="sxs-lookup"><span data-stu-id="40531-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="40531-130">KB2999226 ' ye ek olarak, [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) ' ın de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="40531-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="40531-131">Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="40531-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="40531-132">.NET Core 3,0 Preview 3 önkoşulları</span><span class="sxs-lookup"><span data-stu-id="40531-132">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="40531-133">.NET Core 3,0 Preview 3, diğer .NET Core sürümleriyle aynı önkoşullara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="40531-133">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="40531-134">Ancak, .NET Core 3,0 projeleri oluşturmak için Visual Studio 'Yu kullanmak istiyorsanız, [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40531-134">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="40531-135">Visual Studio 2019, çakışma olmadan Visual Studio 'nun diğer sürümleriyle yan yana yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="40531-135">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="40531-136">Visual Studio 2017 ile Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="40531-136">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="40531-137">.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40531-137">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="40531-138">Visual Studio 2017, Windows üzerinde .NET Core uygulamaları için tümleşik bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="40531-138">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="40531-139">Visual Studio 2017 ' deki değişiklikler hakkında daha fazla bilgi için bkz. [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="40531-139">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="40531-140">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="40531-140">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="40531-141">.NET Core 2,2 SDK kullanarak Visual Studio 2017 ' de .NET Core uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="40531-141">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="40531-142">**.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2017 sürüm 15.9.0 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="40531-142">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="40531-144">**.NET Core platformlar arası geliştirme** araç takımı yüklendikten sonra, Visual Studio genellikle .NET Core SDK önceki bir sürümünü yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="40531-144">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="40531-145">Örneğin, Visual Studio 2017 15,9, iş yükü yüklendikten sonra varsayılan olarak .NET Core 2,1 SDK kullanır.</span><span class="sxs-lookup"><span data-stu-id="40531-145">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="40531-146">Visual Studio 'Yu .NET Core 2,2 SDK kullanacak şekilde güncelleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="40531-146">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="40531-147">[.NET Core 2,2 SDK 'sını](https://dotnet.microsoft.com/download)yükler.</span><span class="sxs-lookup"><span data-stu-id="40531-147">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="40531-148">Projenizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak var olan veya yeni .NET Core projelerini .NET Core 2,2 'e yeniden hedefleyin:</span><span class="sxs-lookup"><span data-stu-id="40531-148">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="40531-149">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="40531-149">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="40531-150">**Hedef çerçeve** seçim menüsünde, değeri **.NET Core 2,2**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40531-150">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Visual Studio 2017 uygulama projesi özelliğinin ".NET Core 2,2" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="40531-152">Visual Studio 'Yu .NET Core 2,2 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40531-152">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="40531-153">Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="40531-153">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="40531-154">.NET Core 1. x ve 2. x projelerini .NET Core 2,2, derlemek ve çalıştırmak için yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="40531-154">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="40531-155">Yeni .NET Core 2,2 projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="40531-155">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="40531-156">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="40531-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="40531-157">Visual Studio 'da .NET Core 1. x uygulamaları geliştirmek için, [Visual studio 2017](/visualstudio/install/install-visual-studio) ' i **".NET Core platformlar arası geliştirme"** Iş yükü ( **diğer araç kümeleri** bölümünde) seçili olacak şekilde indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="40531-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="40531-159">.NET Core 1. x geliştirme için Visual Studio 2015 kullanmak mümkündür, ancak aşağıdaki nedenlerden dolayı önerilmez:</span><span class="sxs-lookup"><span data-stu-id="40531-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="40531-160">.NET Core araçları, desteklenmeyen bir önizleme sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="40531-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="40531-161">Projeler, kullanım dışı olan Project. JSON tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="40531-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="40531-162">Proje biçimi değişiklikleri hakkında daha fazla bilgi için bkz. [değişikliklere Ilişkin üst düzey genel bakış](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="40531-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="40531-163">Visual Studio sürümünüzü doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="40531-163">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="40531-164">**Yardım** menüsünde **Microsoft Visual Studio hakkında**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="40531-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="40531-165">**Microsoft Visual Studio hakkında** iletişim kutusunda sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="40531-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="40531-166">.NET Core 3,0 Preview 3 uygulamaları, Visual Studio 2019 sürüm 16,0 veya üzeri için.</span><span class="sxs-lookup"><span data-stu-id="40531-166">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="40531-167">.NET Core 2,2 uygulamaları için Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="40531-167">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="40531-168">.NET Core 2,1 uygulamaları için Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="40531-168">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="40531-169">.NET Core 1. x uygulamaları, Visual Studio 2017 sürüm 15,0 veya üzeri için.</span><span class="sxs-lookup"><span data-stu-id="40531-169">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
