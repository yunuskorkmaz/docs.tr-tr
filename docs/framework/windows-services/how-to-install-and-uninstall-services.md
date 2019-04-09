---
title: 'Nasıl yapılır: Windows Hizmetleri Yükleme ve kaldırma'
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
ms.openlocfilehash: c4eb1e5fd0c0b06f332b1eba7d3445963699415c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100384"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="28d9e-102">Nasıl yapılır: Windows Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="28d9e-102">How to: Install and uninstall Windows services</span></span>
<span data-ttu-id="28d9e-103">.NET Framework ile Windows hizmet geliştiriyorsanız, hızlı bir şekilde hizmet uygulamanızı kullanarak yükleyebileceğiniz [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="28d9e-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility.</span></span> <span data-ttu-id="28d9e-104">Bir Windows hizmeti, kullanıcıların yüklemek ve kaldırmak yayımlamayı isteyen geliştiriciler InstallShield kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28d9e-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="28d9e-105">Daha fazla bilgi için [bir yükleyici paketi (Windows istemcisi) oluşturma](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="28d9e-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>
  
> [!WARNING]
>  <span data-ttu-id="28d9e-106">Bir hizmeti bilgisayarınızdan kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin.</span><span class="sxs-lookup"><span data-stu-id="28d9e-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="28d9e-107">Bunun yerine, hangi program veya yazılım paketinin yüklü kullanıma hizmeti bulun ve ardından **uygulamaları** Bu program kaldırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="28d9e-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="28d9e-108">Birçok hizmet Windows ayrılmaz olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="28d9e-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="28d9e-109">Bu makaledeki adımları kullanmak için önce Windows hizmetinize hizmeti yükleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28d9e-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="28d9e-110">Daha fazla bilgi için [izlenecek yol: Bir Windows hizmeti uygulaması oluşturma](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="28d9e-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="28d9e-111">Windows service projeleri F5 tuşuna basarak, doğrudan Visual Studio geliştirme ortamından çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="28d9e-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="28d9e-112">Proje çalıştırmadan önce hizmet projede yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28d9e-112">Before you can run the project, you must install the service in the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="28d9e-113">Kullanabileceğiniz **Sunucu Gezgini** sizin yüklü veya hizmetinizi kaldırılması doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="28d9e-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="28d9e-114">Daha fazla bilgi için [Visual Studio'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="28d9e-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>
  
### <a name="install-your-service-manually"></a><span data-ttu-id="28d9e-115">Hizmetinizi el ile yükleyin</span><span class="sxs-lookup"><span data-stu-id="28d9e-115">Install your service manually</span></span>  
  
1.  <span data-ttu-id="28d9e-116">Gelen **Başlat** menüsünde **Visual Studio \< *sürüm* >**  dizin ve select **Geliştirici komut istemi VS için \< *sürüm*>**.</span><span class="sxs-lookup"><span data-stu-id="28d9e-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="28d9e-117">Visual Studio için geliştirici komut istemi görünür.</span><span class="sxs-lookup"><span data-stu-id="28d9e-117">The Developer Command Prompt for Visual Studio appears.</span></span> 
  
2.  <span data-ttu-id="28d9e-118">Projenizin derlenmiş çalıştırılabilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="28d9e-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="28d9e-119">Çalıştırma *InstallUtil.exe* komutu istemi projenizle parametre olarak çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="28d9e-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     <span data-ttu-id="28d9e-120">Visual Studio için geliştirici komut istemi kullanıyorsanız *InstallUtil.exe* sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28d9e-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="28d9e-121">Aksi takdirde, yola ekleyin veya onu çağırmak için tam yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="28d9e-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="28d9e-122">Bu araç, .NET Framework ile yüklenir *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version >*.</span><span class="sxs-lookup"><span data-stu-id="28d9e-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version>*.</span></span>
     
     <span data-ttu-id="28d9e-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="28d9e-123">For example:</span></span>
     - <span data-ttu-id="28d9e-124">.NET Framework 4 veya 4.5 ve üzeri, eğer 32-bit sürümü için Windows yükleme dizinine olan *C:\Windows*, varsayılan yolu *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="28d9e-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="28d9e-125">.NET Framework 4 veya 4.5 ve sonraki 64-bit sürümü için varsayılan yoldur *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="28d9e-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>
  
### <a name="uninstall-your-service-manually"></a><span data-ttu-id="28d9e-126">Hizmetinizi el ile kaldırma</span><span class="sxs-lookup"><span data-stu-id="28d9e-126">Uninstall your service manually</span></span>  
  
1. <span data-ttu-id="28d9e-127">Gelen **Başlat** menüsünde **Visual Studio \< *sürüm* >**  dizin ve select **Geliştirici komut istemi VS için \< *sürüm*>**.</span><span class="sxs-lookup"><span data-stu-id="28d9e-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>
  
     <span data-ttu-id="28d9e-128">Visual Studio için geliştirici komut istemi görünür.</span><span class="sxs-lookup"><span data-stu-id="28d9e-128">The Developer Command Prompt for Visual Studio appears.</span></span>  
  
2.  <span data-ttu-id="28d9e-129">Çalıştırma *InstallUtil.exe* bir parametre olarak projenizin çıktısı ile komut isteminden:</span><span class="sxs-lookup"><span data-stu-id="28d9e-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. <span data-ttu-id="28d9e-130">Yürütülebilir dosya için bir hizmet silindikten sonra hizmet kayıt defterinde mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="28d9e-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="28d9e-131">Bu durumda, komutu kullanın [sc delete](/windows-server/administration/windows-commands/sc-delete) kayıt defterinden service girişini kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="28d9e-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d9e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28d9e-132">See also</span></span>

- [<span data-ttu-id="28d9e-133">Windows hizmeti uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="28d9e-133">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="28d9e-134">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="28d9e-134">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="28d9e-135">Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="28d9e-135">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="28d9e-136">InstallUtil.exe (Yükleme aracı)</span><span class="sxs-lookup"><span data-stu-id="28d9e-136">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
