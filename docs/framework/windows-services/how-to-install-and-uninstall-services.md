---
title: 'Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
manager: douge
ms.openlocfilehash: 9d8e84280b5821f8d8df36694198bd85fb8470d4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45673993"
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="341ab-102">Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="341ab-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="341ab-103">.NET Framework kullanarak bir Windows hizmet geliştiriyorsanız, InstallUtil.exe adlı bir komut satırı yardımcı programını kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341ab-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="341ab-104">Kullanıcılar yükleme ve kaldırma, Windows hizmet yayımlamayı isteyen bir geliştiriciyseniz InstallShield kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="341ab-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="341ab-105">Bkz: [Windows Installer dağıtımı](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="341ab-105">See [Windows Installer Deployment](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="341ab-106">Bir hizmeti bilgisayarınızdan kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin.</span><span class="sxs-lookup"><span data-stu-id="341ab-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="341ab-107">Bunun yerine, hangi program veya yazılım paketinin yüklü kullanıma hizmeti bulun ve ardından **Program Ekle/Kaldır** Denetim Masası'nın bu programı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="341ab-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="341ab-108">Birçok hizmet Windows ayrılmaz olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="341ab-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="341ab-109">Bu makaledeki adımları kullanabilmek için önce Windows hizmetinizin hizmet yükleyici eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="341ab-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="341ab-110">Bkz: [izlenecek yol: bir Windows oluşturma hizmet uygulaması Bileşen Tasarımcısı'nda](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="341ab-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="341ab-111">Windows Service projeleri F5 tuşuna basarak doğrudan Visual Studio geliştirme ortamından çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="341ab-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="341ab-112">Projenin çalışabilmesi için projedeki hizmetin yüklenmiş olması gerekliliğinden budur.</span><span class="sxs-lookup"><span data-stu-id="341ab-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="341ab-113">Başlatabilirsiniz **Sunucu Gezgini** ve hizmetinizi yüklü veya kaldırılmış olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="341ab-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="341ab-114">Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="341ab-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="341ab-115">Hizmetinizi el ile yüklemek için</span><span class="sxs-lookup"><span data-stu-id="341ab-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="341ab-116">Windows üzerinde **Başlat** menüsü veya **Başlat** ekran öğesini **Visual Studio** , **Visual Studio Araçları**, **Geliştirici Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="341ab-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="341ab-117">Visual Studio komut istemi görünür.</span><span class="sxs-lookup"><span data-stu-id="341ab-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="341ab-118">Projenizin derlenmiş çalıştırılabilir dosyasının bulunduğu dizine erişin.</span><span class="sxs-lookup"><span data-stu-id="341ab-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="341ab-119">InstallUtil.exe parametre olarak projenizin yürütülebilir dosya ile komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="341ab-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="341ab-120">Visual Studio Komut İstemi'ni kullanıyorsanız, InstallUtil.exe sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="341ab-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="341ab-121">Aksi halde yola ekleyin veya onu çağırmak için tam yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="341ab-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="341ab-122">Bu araç .NET Framework ile birlikte yüklenir ve kendi yolu `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="341ab-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="341ab-123">Örneğin, .NET Framework 4 veya 4.5 32-bit sürümü için. \*, Windows yükleme dizinine C:\Windows yol ise, `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="341ab-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="341ab-124">64-bit sürümü .NET Framework 4 veya 4.5 için. \*, varsayılan yolu `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="341ab-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="341ab-125">Hizmetinizi el ile kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="341ab-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="341ab-126">Windows üzerinde **Başlat** menüsü veya **Başlat** ekran öğesini **Visual Studio**, **Visual Studio Araçları**, **Geliştirici Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="341ab-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="341ab-127">Visual Studio komut istemi görünür.</span><span class="sxs-lookup"><span data-stu-id="341ab-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="341ab-128">InstallUtil.exe parametre olarak projenizin çıktısı ile komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="341ab-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="341ab-129">Bazı durumlarda, hizmetin yürütülebilir dosya için bir hizmet silindikten sonra kayıt defterinde mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="341ab-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="341ab-130">Bu durumda, komutunu [sc delete](https://technet.microsoft.com/library/cc742045.aspx) kayıt defterinden service girişini kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="341ab-130">In that case, use the command [sc delete](https://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341ab-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="341ab-131">See Also</span></span>  
 [<span data-ttu-id="341ab-132">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="341ab-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="341ab-133">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="341ab-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="341ab-134">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="341ab-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="341ab-135">Installutil.exe (Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="341ab-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
