---
title: Windows üzerinde .NET Core önkoşulları
description: .NET Core uygulamaları geliştirmek ve çalıştırmak için Windows makinenizde hangi bağımlılıklara ihtiyacınız olduğunu öğrenin.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591665"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="c6b0b-103">Windows üzerinde .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="c6b0b-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="c6b0b-104">Bu makalede, Windows 'da .NET Core uygulamalarını çalıştırmak için desteklenen işletim sistemi sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="c6b0b-105">Desteklenen işletim sistemi sürümleri ve aşağıdaki bağımlılıklar, Windows 'ta .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="c6b0b-106">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="c6b0b-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="c6b0b-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6b0b-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="c6b0b-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c6b0b-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="c6b0b-109">Ayrıca, Visual Studio 'Yu kullanarak Windows üzerinde geliştirirseniz, [Visual Studio ile .NET Core uygulamaları geliştirmeye yönelik önkoşullar](#prerequisites-to-develop-net-core-apps-with-visual-studio) , .NET Core geliştirmesi için desteklenen en düşük sürümler hakkında daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="c6b0b-110">.NET Core tarafından desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="c6b0b-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="c6b0b-111">Aşağıdaki makalelerde sürüm başına .NET Core tarafından desteklenen işletim sistemlerinin kapsamlı bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="c6b0b-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c6b0b-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="c6b0b-113">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c6b0b-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="c6b0b-114">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c6b0b-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

<span data-ttu-id="c6b0b-115">İndirme bağlantıları ve daha fazla bilgi için bkz. eski sürümler için en son sürümü veya [.net İndirmeleri arşivini](https://dotnet.microsoft.com/download/archives#dotnet-core) indirmek üzere [.net İndirmeleri](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="c6b0b-115">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="c6b0b-116">.NET Core bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="c6b0b-116">.NET Core dependencies</span></span>

<span data-ttu-id="c6b0b-117">[Microsoft Visual C++ 2015 Redistributable güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685) , şu durumlarda el ile yüklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-117">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="c6b0b-118">.NET Core, [Yükleyici betiği](./tools/dotnet-install-script.md)ile yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-118">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="c6b0b-119">Kendi kendine içerilen bir .NET Core uygulaması dağıtma.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-119">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="c6b0b-120">Ürünün kaynaktan oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-120">Building the product from source.</span></span>
* <span data-ttu-id="c6b0b-121">.NET Core 'u bir *. zip* dosyası aracılığıyla yükleme.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-121">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="c6b0b-122">Bu, derleme/CI/CD sunucuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-122">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b0b-123">**Windows 8.1 ve önceki sürümler veya Windows Server 2012 R2 ve önceki sürümleri için:**</span><span class="sxs-lookup"><span data-stu-id="c6b0b-123">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="c6b0b-124">Windows yüklemenizin güncel olduğundan ve Windows Update aracılığıyla yüklenebilen [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows)içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-124">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="c6b0b-125">Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="c6b0b-125">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="c6b0b-126">**Windows 7 veya Windows Server 2008 R2 için:**</span><span class="sxs-lookup"><span data-stu-id="c6b0b-126">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="c6b0b-127">KB2999226 ' ye ek olarak, [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) ' ın de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-127">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="c6b0b-128">Bu güncelleştirme yüklü değilse, bir .NET Core uygulaması başlattığınızda aşağıdakine benzer bir hata görürsünüz: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-128">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="c6b0b-129">Visual Studio ile .NET Core uygulamaları geliştirmeye yönelik önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c6b0b-129">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="c6b0b-130">.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz, ancak Visual Studio 2017 ve üzeri sürümleri, Windows üzerinde .NET Core uygulamaları için tümleşik bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-130">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="c6b0b-131">Her .NET Core sürümünde en düşük Visual Studio sürümü gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-131">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="c6b0b-132">Visual Studio sürümünüzü doğrulamak için:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-132">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="c6b0b-133">**Yardım** menüsünde **Microsoft Visual Studio hakkında**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-133">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="c6b0b-134">**Microsoft Visual Studio hakkında** iletişim kutusunda sürüm numarasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-134">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="c6b0b-135">Aşağıdaki tabloda her SDK için en düşük sürüm listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-135">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="c6b0b-136">.NET Core SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="c6b0b-136">.NET Core SDK version</span></span> | <span data-ttu-id="c6b0b-137">Visual Studio sürümü</span><span class="sxs-lookup"><span data-stu-id="c6b0b-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c6b0b-138">3,0</span><span class="sxs-lookup"><span data-stu-id="c6b0b-138">3.0</span></span>                   | <span data-ttu-id="c6b0b-139">Visual Studio 2019 sürüm 16,3 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-139">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="c6b0b-140">2.2</span><span class="sxs-lookup"><span data-stu-id="c6b0b-140">2.2</span></span>                   | <span data-ttu-id="c6b0b-141">Visual Studio 2017 sürüm 15,9 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-141">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="c6b0b-142">2.1</span><span class="sxs-lookup"><span data-stu-id="c6b0b-142">2.1</span></span>                   | <span data-ttu-id="c6b0b-143">Visual Studio 2017 sürüm 15,7 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-143">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="c6b0b-144">'in</span><span class="sxs-lookup"><span data-stu-id="c6b0b-144">1.x</span></span>                   | <span data-ttu-id="c6b0b-145">Visual Studio 2017 sürüm 15,0 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-145">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="c6b0b-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c6b0b-146">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="c6b0b-147">.NET Core 3,0 SDK kullanarak Visual Studio 2019 ' de .NET Core uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-147">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="c6b0b-148">[Visual Studio 2019 sürüm 16,3 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) ve oluşturmakta olduğunuz uygulamanın türüne bağlı olarak .NET Core SDK içeren aşağıdaki iş yüklerinden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-148">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="c6b0b-149">**Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-149">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="c6b0b-150">**Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-150">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="c6b0b-151">**Windows** bölümündeki **net masaüstü geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-151">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="c6b0b-152">Aşağıdaki görüntüde, Visual Studio Kullanıcı arabiriminde seçilen **.NET Core platformlar arası geliştirme** iş yükü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-152">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2019 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="c6b0b-154">Visual Studio 2019 16,3, bu iş yüklerinden herhangi biri yüklendikten sonra varsayılan olarak .NET Core 3,0 SDK kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-154">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="c6b0b-155">Mevcut projelerinizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak var olan tüm .NET Core projelerini .NET Core 3,0 ' e yeniden hedefleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-155">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="c6b0b-156">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-156">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="c6b0b-157">**Hedef çerçeve** seçim menüsünde, değeri **.NET Core 3,0**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-157">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Visual Studio 2019 uygulama projesi özelliğinin ".NET Core 3,0" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="c6b0b-159">Visual Studio 'Yu .NET Core 3,0 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-159">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="c6b0b-160">Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-160">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="c6b0b-161">.NET Core 1. x ve 2. x projelerini .NET Core 3,0, derlemek ve çalıştırmak için yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-161">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="c6b0b-162">Yeni .NET Core 3,0 projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-162">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6b0b-163">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="c6b0b-163">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c6b0b-164">.NET Core 2,2 SDK kullanarak Visual Studio 2017 ' de .NET Core uygulamaları geliştirmek için:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-164">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="c6b0b-165">**.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2019 sürüm 16,3 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="c6b0b-165">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
* <span data-ttu-id="c6b0b-166">**.NET Core platformlar arası geliştirme** iş yükü ( **diğer araç kümeleri** bölümünde) seçiliyken [Visual Studio 2017 sürüm 15.9.0 veya üstünü indirip yükleyin](/visualstudio/install/install-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="c6b0b-166">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core platformlar arası geliştirme" iş yükü seçiliyken Visual Studio 2017 yüklemesinin ekran görüntüsü](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="c6b0b-168">**.NET Core platformlar arası geliştirme** araç takımı yüklendikten sonra, Visual Studio genellikle .NET Core SDK önceki bir sürümünü yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-168">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="c6b0b-169">Örneğin, Visual Studio 2017 15,9, iş yükü yüklendikten sonra varsayılan olarak .NET Core 2,1 SDK kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-169">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="c6b0b-170">Visual Studio 'Yu .NET Core 2,2 SDK kullanacak şekilde güncelleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-170">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="c6b0b-171">[.NET Core 2,2 SDK 'sını](https://dotnet.microsoft.com/download)yükler.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-171">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="c6b0b-172">Projenizin en son .NET Core çalışma zamanını kullanmasını istiyorsanız, aşağıdaki yönergeleri kullanarak, mevcut veya yeni .NET Core projelerini .NET Core 2,2 'e yeniden hedefleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-172">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="c6b0b-173">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-173">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="c6b0b-174">**Hedef çerçeve** seçim menüsünde, değeri **.NET Core 2,2**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-174">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Visual Studio 2017 uygulama projesi özelliğinin ".NET Core 2,2" hedef Framework menü öğesi seçiliyken ekran görüntüsü](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="c6b0b-176">Visual Studio 'Yu .NET Core 2,2 SDK ile yapılandırdıktan sonra, aşağıdaki işlemleri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6b0b-176">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="c6b0b-177">Mevcut .NET Core 1. x ve 2. x projelerini açın, derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-177">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="c6b0b-178">.NET Core 1. x ve 2. x projelerini .NET Core 2,2, derlemek ve çalıştırmak için yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-178">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="c6b0b-179">Yeni .NET Core 2,2 projeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6b0b-179">Create new .NET Core 2.2 projects.</span></span>

---
