---
title: 'Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme'
description: Bkz. hizmet uygulamanıza yükleyiciler ekleme. Visual Studio, hizmet uygulamalarınızla ilişkili kaynakları yükleyebilen yükleme bileşenlerini sevk eder.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: f82dd6635555ccb8fcbcdf63cba2495084194731
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925650"
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="0abb2-104">Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="0abb2-104">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="0abb2-105">Visual Studio, hizmet uygulamalarınızla ilişkili kaynakları yükleyebilen yükleme bileşenlerini sevk eder.</span><span class="sxs-lookup"><span data-stu-id="0abb2-105">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="0abb2-106">Yükleme bileşenleri, yüklenmekte olan sisteme tek bir hizmeti kaydeder ve hizmetler Denetim Yöneticisi 'nin hizmetin var olduğunu bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0abb2-106">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="0abb2-107">Bir hizmet uygulamasıyla çalışırken, projenize uygun yükleyicileri otomatik olarak eklemek için Özellikler penceresi bir bağlantı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0abb2-107">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0abb2-108">Hizmetinizin özellik değerleri, hizmet sınıfından yükleyici sınıfına kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0abb2-108">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="0abb2-109">Hizmet sınıfındaki özellik değerlerini güncelleştirirseniz, bunlar yükleyicide otomatik olarak güncellenmez.</span><span class="sxs-lookup"><span data-stu-id="0abb2-109">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="0abb2-110">Projenize bir yükleyici eklediğinizde, projede yeni bir sınıf (varsayılan olarak, olarak adlandırılır `ProjectInstaller` ) oluşturulur ve ilgili yükleme bileşenlerinin örnekleri içinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0abb2-110">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="0abb2-111">Bu sınıf, projenizin ihtiyaç duyacağı tüm yükleme bileşenlerine yönelik bir merkezi nokta görevi görür.</span><span class="sxs-lookup"><span data-stu-id="0abb2-111">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="0abb2-112">Örneğin, uygulamanıza ikinci bir hizmet ekler ve Yükleyici Ekle bağlantısına tıklarsanız ikinci bir yükleyici sınıfı oluşturulmaz; Bunun yerine, ikinci hizmet için gereken ek yükleme bileşeni mevcut sınıfa eklenir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-112">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="0abb2-113">Hizmetlerinizin doğru şekilde yüklenmesini sağlamak için yükleyicilerin içinde herhangi bir özel kodlama yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0abb2-113">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="0abb2-114">Ancak, yükleme işlemine özel işlevsellik eklemeniz gerekiyorsa, bazen yükleyicilerin içeriğini değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-114">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0abb2-115">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0abb2-116">Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="0abb2-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0abb2-117">Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0abb2-117">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="0abb2-118">Hizmet uygulamanıza yükleyiciler eklemek için</span><span class="sxs-lookup"><span data-stu-id="0abb2-118">To add installers to your service application</span></span>  
  
1. <span data-ttu-id="0abb2-119">**Çözüm Gezgini**, yükleme bileşeni eklemek Istediğiniz hizmetin **Tasarım** görünümünde erişin.</span><span class="sxs-lookup"><span data-stu-id="0abb2-119">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2. <span data-ttu-id="0abb2-120">Tüm içerikleri yerine hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-120">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3. <span data-ttu-id="0abb2-121">Tasarımcı odaklanarak, öğesine sağ tıklayın ve ardından **Yükleyici Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-121">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="0abb2-122">Yeni bir sınıf, `ProjectInstaller` ve iki yükleme bileşeni <xref:System.ServiceProcess.ServiceProcessInstaller> ve <xref:System.ServiceProcess.ServiceInstaller> projenize eklenir ve hizmetin özellik değerleri bileşenlere kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0abb2-122">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4. <span data-ttu-id="0abb2-123">Bileşene tıklayın <xref:System.ServiceProcess.ServiceInstaller> ve <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliğin değerinin hizmetin kendisindeki özellik ile aynı değere ayarlandığını doğrulayın <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> .</span><span class="sxs-lookup"><span data-stu-id="0abb2-123">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5. <span data-ttu-id="0abb2-124">Hizmetinizin nasıl başlatılaceğini öğrenmek için <xref:System.ServiceProcess.ServiceInstaller> bileşene tıklayın ve <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği uygun değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-124">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="0abb2-125">Değer</span><span class="sxs-lookup"><span data-stu-id="0abb2-125">Value</span></span>|<span data-ttu-id="0abb2-126">Sonuç</span><span class="sxs-lookup"><span data-stu-id="0abb2-126">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="0abb2-127">Hizmetin, yüklemeden sonra el ile başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-127">The service must be manually started after installation.</span></span> <span data-ttu-id="0abb2-128">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="0abb2-128">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="0abb2-129">Bilgisayar her yeniden başlatıldığında hizmet kendisi tarafından başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0abb2-129">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="0abb2-130">Hizmet başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0abb2-130">The service cannot be started.</span></span>|  
  
6. <span data-ttu-id="0abb2-131">Hizmetinizin çalışacağı güvenlik bağlamını öğrenmek için <xref:System.ServiceProcess.ServiceProcessInstaller> bileşene tıklayın ve uygun özellik değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-131">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="0abb2-132">Daha fazla bilgi için bkz. [nasıl yapılır: hizmetler Için güvenlik bağlamını belirtme](how-to-specify-the-security-context-for-services.md).</span><span class="sxs-lookup"><span data-stu-id="0abb2-132">For more information, see [How to: Specify the Security Context for Services](how-to-specify-the-security-context-for-services.md).</span></span>  
  
7. <span data-ttu-id="0abb2-133">Özel işlem gerçekleştirmeniz gereken tüm yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="0abb2-133">Override any methods for which you need to perform custom processing.</span></span>  
  
8. <span data-ttu-id="0abb2-134">Projenizdeki her bir ek hizmet için 1 ile 7 arasındaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0abb2-134">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0abb2-135">Projenizdeki her bir ek hizmet için, projenin sınıfına ek bir bileşen eklemeniz gerekir <xref:System.ServiceProcess.ServiceInstaller> `ProjectInstaller` .</span><span class="sxs-lookup"><span data-stu-id="0abb2-135">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="0abb2-136"><xref:System.ServiceProcess.ServiceProcessInstaller>Adım 3 ' te eklenen bileşen, projedeki bireysel hizmet yükleyicilerinin tümü ile birlikte geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0abb2-136">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abb2-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0abb2-137">See also</span></span>

- [<span data-ttu-id="0abb2-138">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="0abb2-138">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="0abb2-139">Nasıl yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0abb2-139">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="0abb2-140">Nasıl yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="0abb2-140">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="0abb2-141">Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="0abb2-141">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
