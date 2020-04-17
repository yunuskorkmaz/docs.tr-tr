---
title: 'Nasıl yapilir: Windows hizmetlerini yükleme ve kaldırma'
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
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607925"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="07048-102">Nasıl yapilir: Windows hizmetlerini yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="07048-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="07048-103">.NET Framework yüklü bir Windows hizmeti geliştiriyorsanız, [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell'i](/powershell/scripting/overview)kullanarak servis uygulamanızı hızlı bir şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07048-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="07048-104">Kullanıcıların yükleyip kaldırabileceği bir Windows hizmeti yayımlamak isteyen geliştiriciler InstallShield'i kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07048-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="07048-105">Daha fazla bilgi için [bkz.](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)</span><span class="sxs-lookup"><span data-stu-id="07048-105">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="07048-106">Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin.</span><span class="sxs-lookup"><span data-stu-id="07048-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="07048-107">Bunun yerine, hizmeti hangi program veya yazılım paketinin yüklediğini öğrenin ve ardından bu programı kaldırmak için Ayarlar'daki **Uygulamaları** seçin.</span><span class="sxs-lookup"><span data-stu-id="07048-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="07048-108">Birçok hizmetin Windows'un ayrılmaz parçaları olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="07048-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="07048-109">Bu makaledeki adımları kullanmak için öncelikle Windows hizmetinize bir hizmet yükleyici eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07048-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="07048-110">Daha fazla bilgi için [Walkthrough: Windows hizmeti uygulaması oluşturma '](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)na bakın.</span><span class="sxs-lookup"><span data-stu-id="07048-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="07048-111">F5 tuşuna basarak Windows hizmet projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="07048-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="07048-112">Projeyi çalıştıramadan önce hizmeti projeye yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07048-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="07048-113">Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Server Explorer'ı** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07048-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="07048-114">Daha fazla bilgi için [Visual Studio'da Sunucu Gezgini nasıl kullanılır.](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="07048-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="07048-115">InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="07048-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="07048-116">**Başlat** menüsünden Visual \*\* \<Studio *sürüm* > \*\* dizinini seçin ve ardından **VS \< *sürümü*>için Geliştirici Komut Komut Ustem'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="07048-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="07048-117">Visual Studio için Geliştirici Komut Komut Ustem görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="07048-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="07048-118">Projenizin derlenebilir yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="07048-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="07048-119">*InstallUtil.exe* komut isteminden projenizin yürütülebilir bir parametre olarak çalıştırılabilir çalıştırışlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="07048-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="07048-120">Visual Studio için Geliştirici Komut Komut Komut Ui komut istemikullanıyorsanız, *InstallUtil.exe* sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07048-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="07048-121">Aksi takdirde, onu yola ekleyebilir veya çağırmak için tam nitelikli yolu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07048-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="07048-122">Bu araç *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.NET Framework ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="07048-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="07048-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="07048-123">For example:</span></span>
     - <span data-ttu-id="07048-124">.NET Framework 4 veya 4.5 ve sonraki 32 bit sürümü için, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*' dir.</span><span class="sxs-lookup"><span data-stu-id="07048-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="07048-125">.NET Framework 4 veya 4.5 ve sonraki 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe'* dir.</span><span class="sxs-lookup"><span data-stu-id="07048-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="07048-126">InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile kaldırın</span><span class="sxs-lookup"><span data-stu-id="07048-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="07048-127">**Başlat** menüsünden Visual \*\* \<Studio *sürüm* > \*\* dizinini seçin ve ardından **VS \< *sürümü*>için Geliştirici Komut Komut Ustem'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="07048-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="07048-128">Visual Studio için Geliştirici Komut Komut Ustem görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="07048-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="07048-129">*InstallUtil.exe* komut isteminden projenizin çıktısını parametre olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="07048-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="07048-130">Bir hizmetin yürütülebilirliği silindikten sonra, hizmet kayıt defterinde hala bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="07048-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="07048-131">Bu durumda, hizmetgirişini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="07048-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="07048-132">PowerShell'i kullanarak hizmetinizi el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="07048-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="07048-133">**Başlat** menüsünden Windows **PowerShell** dizinini seçin ve ardından **Windows PowerShell'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="07048-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="07048-134">Projenizin derlenebilir yürütülebilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="07048-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="07048-135">Yeni [**Servis**](/powershell/module/microsoft.powershell.management/new-service) cmdletini projenizin çıktısı ve bir hizmet adı ile parametreler olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="07048-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="07048-136">PowerShell'i kullanarak hizmetinizi el ile kaldırın</span><span class="sxs-lookup"><span data-stu-id="07048-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="07048-137">**Başlat** menüsünden Windows **PowerShell** dizinini seçin ve ardından **Windows PowerShell'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="07048-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="07048-138">[**Hizmetin**](/powershell/module/microsoft.powershell.management/remove-service) adı ile Hizmet Kaldır cmdletini parametre olarak çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="07048-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="07048-139">Bir hizmetin yürütülebilirliği silindikten sonra, hizmet kayıt defterinde hala bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="07048-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="07048-140">Bu durumda, hizmetgirişini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="07048-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="07048-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07048-141">See also</span></span>

- [<span data-ttu-id="07048-142">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="07048-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="07048-143">Nasıl yapilir: Windows hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="07048-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="07048-144">Nasıl yapilir: Servis uygulamanıza yükleyici ekleme</span><span class="sxs-lookup"><span data-stu-id="07048-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="07048-145">Installutil.exe (Yükleme aracı)</span><span class="sxs-lookup"><span data-stu-id="07048-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
