---
title: 'Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma'
description: Bkz. Windows hizmetlerini yükleme ve kaldırma. .NET ile bir Windows hizmeti geliştirmekte çalışıyorsanız InstallUtil.exe veya PowerShell kullanabilirsiniz.
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
ms.openlocfilehash: 6b7cfd8b241df4fe01c9c2a08888c88a1c749d13
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609687"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="91166-104">Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="91166-104">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="91166-105">.NET Framework ile bir Windows hizmeti geliştiriyorsanız, [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell](/powershell/scripting/overview)'i kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91166-105">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="91166-106">Kullanıcıların yükleyebileceği ve kaldırabildiği bir Windows hizmetini yayınlamak isteyen geliştiriciler, ücretsiz [Wix araç takımını](https://wixtoolset.org/) veya [Gelişmiş Yükleyici](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html)veya diğerleri gibi ticari araçları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="91166-106">Developers who want to release a Windows service that users can install and uninstall can use the free [WiX Toolset](https://wixtoolset.org/) or commercial tools like [Advanced Installer](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html), or others.</span></span> <span data-ttu-id="91166-107">Daha fazla bilgi için bkz. [Yükleyici paketi oluşturma (Windows Masaüstü)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="91166-107">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="91166-108">Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="91166-108">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="91166-109">Bunun yerine, hizmeti hangi programın veya yazılım paketinin yüklendiğini öğrenin ve ardından bu programı kaldırmak için ayarlar ' da **uygulamalar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="91166-109">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="91166-110">Birçok hizmetin Windows 'un ayrılmaz parçaları olduğunu unutmayın; Bunları kaldırırsanız, sistem kararsızlığına neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91166-110">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="91166-111">Bu makaledeki adımları kullanmak için, önce Windows hizmetinize bir hizmet Yükleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="91166-111">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="91166-112">Daha fazla bilgi için bkz. [Izlenecek yol: Windows hizmet uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="91166-112">For more information, see [Walkthrough: Creating a Windows service app](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="91166-113">F5 'e basarak Windows hizmeti projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="91166-113">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="91166-114">Projeyi çalıştırmadan önce, hizmeti projeye yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="91166-114">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="91166-115">Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Sunucu Gezgini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91166-115">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="91166-116">Daha fazla bilgi için bkz. [Visual Studio 'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="91166-116">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="91166-117">InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="91166-117">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="91166-118">**Başlat** menüsünde \*\*Visual Studio \<*version*> \*\* dizinini seçin ve ardından \*\* \<*version*> vs için geliştirici komut istemi \*\*seçin.</span><span class="sxs-lookup"><span data-stu-id="91166-118">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="91166-119">Visual Studio için Geliştirici Komut İstemi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91166-119">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="91166-120">Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="91166-120">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="91166-121">Komut isteminden proje yürütülebiliri olarak parametre olarak *InstallUtil.exe* çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="91166-121">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="91166-122">Visual Studio için Geliştirici Komut İstemi kullanıyorsanız, *InstallUtil.exe* sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91166-122">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="91166-123">Aksi takdirde, yolu yola ekleyebilir veya tam yolu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91166-123">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="91166-124">Bu araç, \*%windir%\Microsoft.NET\Framework [64] \\<framework_version \> \*.NET Framework ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="91166-124">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="91166-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="91166-125">For example:</span></span>
     - <span data-ttu-id="91166-126">.NET Framework 4 veya 4,5 ' nin 32 bit sürümü ve sonrasında, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="91166-126">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="91166-127">.NET Framework 4 veya 4,5 ve sonraki sürümlerin 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="91166-127">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="91166-128">InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile kaldırın</span><span class="sxs-lookup"><span data-stu-id="91166-128">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="91166-129">**Başlat** menüsünde \*\*Visual Studio \<*version*> \*\* dizinini seçin ve ardından \*\* \<*version*> vs için geliştirici komut istemi \*\*seçin.</span><span class="sxs-lookup"><span data-stu-id="91166-129">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="91166-130">Visual Studio için Geliştirici Komut İstemi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91166-130">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="91166-131">Komut isteminden *InstallUtil.exe* bir parametre olarak projenizin çıkışıyla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="91166-131">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="91166-132">Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="91166-132">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="91166-133">Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="91166-133">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="91166-134">PowerShell kullanarak hizmetinizi el ile yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="91166-134">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="91166-135">**Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="91166-135">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="91166-136">Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="91166-136">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="91166-137">[**Yeni-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet 'ini, projenizin çıkışıyla ve bir hizmet adıyla birlikte parametre olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="91166-137">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="91166-138">PowerShell kullanarak hizmetinizi el ile kaldırma</span><span class="sxs-lookup"><span data-stu-id="91166-138">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="91166-139">**Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="91166-139">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="91166-140">[**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet 'ini, hizmetinizin adı parametresiyle çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="91166-140">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="91166-141">Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="91166-141">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="91166-142">Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="91166-142">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="91166-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91166-143">See also</span></span>

- [<span data-ttu-id="91166-144">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="91166-144">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="91166-145">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="91166-145">How to: Create Windows services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="91166-146">Nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="91166-146">How to: Add installers to your service application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="91166-147">Installutil.exe (Yükleme aracı)</span><span class="sxs-lookup"><span data-stu-id="91166-147">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
