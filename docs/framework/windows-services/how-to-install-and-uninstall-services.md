---
title: 'Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma'
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
author: ghogen
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003127"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="59186-102">Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="59186-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="59186-103">.NET Framework ile bir Windows hizmeti geliştiriyorsanız, [*InstallUtil. exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell](/powershell/scripting/overview)'i kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59186-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="59186-104">Kullanıcıların yükleyebileceği ve kaldırabildiği bir Windows hizmetini yayınlamak isteyen geliştiriciler InstallShield kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59186-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="59186-105">Daha fazla bilgi için bkz. [Yükleyici paketi oluşturma (Windows istemcisi)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="59186-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

> [!WARNING]
> <span data-ttu-id="59186-106">Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="59186-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="59186-107">Bunun yerine, hizmeti hangi programın veya yazılım paketinin yüklendiğini öğrenin ve ardından bu programı kaldırmak için ayarlar ' da **uygulamalar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="59186-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="59186-108">Birçok hizmetin Windows 'un ayrılmaz parçaları olduğunu unutmayın; Bunları kaldırırsanız, sistem kararsızlığına neden olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59186-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="59186-109">Bu makaledeki adımları kullanmak için, önce Windows hizmetinize bir hizmet Yükleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59186-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="59186-110">Daha fazla bilgi için bkz. [Izlenecek yol: Windows hizmet uygulaması oluşturma](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="59186-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="59186-111">F5 'e basarak Windows hizmeti projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="59186-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="59186-112">Projeyi çalıştırmadan önce, hizmeti projeye yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="59186-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="59186-113">Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Sunucu Gezgini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59186-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="59186-114">Daha fazla bilgi için bkz. [Visual Studio 'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="59186-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="59186-115">InstallUtil. exe yardımcı programını kullanarak hizmetinizi el ile yükleme</span><span class="sxs-lookup"><span data-stu-id="59186-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="59186-116">**Başlat** menüsünde, **Visual Studio \<*Sürüm*>** dizinini seçin ve sonra **vs \<*Sürüm*>için geliştirici komut istemi** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="59186-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="59186-117">Visual Studio için Geliştirici Komut İstemi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59186-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="59186-118">Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="59186-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="59186-119">Komut isteminden *InstallUtil. exe* ' yi bir parametre olarak projenizin yürütülebilir dosyası ile çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59186-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="59186-120">Visual Studio için Geliştirici Komut İstemi kullanıyorsanız, *InstallUtil. exe* dosyası sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59186-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="59186-121">Aksi takdirde, yolu yola ekleyebilir veya tam yolu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59186-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="59186-122">Bu araç, *%windir%\Microsoft.NET\Framework [64]\\< framework_version\>* .NET Framework ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="59186-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="59186-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="59186-123">For example:</span></span>
     - <span data-ttu-id="59186-124">.NET Framework 4 veya 4,5 ' nin 32 bit sürümü ve sonrasında, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*' dir.</span><span class="sxs-lookup"><span data-stu-id="59186-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="59186-125">.NET Framework 4 veya 4,5 ve sonraki sürümlerin 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*' dir.</span><span class="sxs-lookup"><span data-stu-id="59186-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="59186-126">InstallUtil. exe yardımcı programını kullanarak hizmetinizi el ile kaldırın</span><span class="sxs-lookup"><span data-stu-id="59186-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="59186-127">**Başlat** menüsünde, **Visual Studio \<*Sürüm*>** dizinini seçin ve sonra **vs \<*Sürüm*>için geliştirici komut istemi** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="59186-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="59186-128">Visual Studio için Geliştirici Komut İstemi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59186-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="59186-129">Komut isteminden *InstallUtil. exe* ' yi bir parametre olarak projenizin çıkışıyla çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59186-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="59186-130">Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="59186-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="59186-131">Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="59186-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="59186-132">PowerShell kullanarak hizmetinizi el ile yükleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="59186-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="59186-133">**Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="59186-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="59186-134">Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="59186-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="59186-135">[**Yeni-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet 'ini, projenizin çıkışıyla ve bir hizmet adıyla birlikte parametre olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59186-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="59186-136">PowerShell kullanarak hizmetinizi el ile kaldırma</span><span class="sxs-lookup"><span data-stu-id="59186-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="59186-137">**Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="59186-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="59186-138">[**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet 'ini, hizmetinizin adı parametresiyle çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59186-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="59186-139">Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="59186-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="59186-140">Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="59186-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="59186-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59186-141">See also</span></span>

- [<span data-ttu-id="59186-142">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="59186-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="59186-143">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="59186-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="59186-144">Nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="59186-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="59186-145">InstallUtil. exe (yükleyici aracı)</span><span class="sxs-lookup"><span data-stu-id="59186-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
