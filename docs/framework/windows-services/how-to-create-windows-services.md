---
title: 'Nasıl yapılır: Windows Hizmetleri oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: d0a450483c05a272fe799c7ee04e691cefbd2085
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533760"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="026f1-102">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="026f1-102">How to: Create Windows Services</span></span>
<span data-ttu-id="026f1-103">Bir hizmet oluşturduğu zaman, adlı bir Visual Studio Proje şablonu kullanabilirsiniz **Windows hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="026f1-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="026f1-104">Bu şablon otomatik olarak işin çoğunu sizin için uygun sınıf ve ad alanları, hizmetler için bir temel sınıftan devralmayı ayarlama başvurarak yapar ve birkaç yöntemleri geçersiz kılan, geçersiz kılmak istediğiniz kullanılma olasılığı.</span><span class="sxs-lookup"><span data-stu-id="026f1-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="026f1-105">Windows Hizmetleri Proje şablonu Visual Studio'nun Express sürümünde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="026f1-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="026f1-106">En azından, işlevsel bir hizmet oluşturmak için şunları yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="026f1-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="026f1-107">Ayarlama <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="026f1-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="026f1-108">Hizmet uygulamanız için gerekli yükleyicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="026f1-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="026f1-109">Geçersiz kılmak ve belirtmek için kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> , hizmetinizin davranış yöntemlerini özelleştirmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="026f1-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="026f1-110">Bir Windows hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="026f1-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="026f1-111">Oluşturma bir **Windows hizmeti** proje.</span><span class="sxs-lookup"><span data-stu-id="026f1-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="026f1-112">Şablon kullanmadan hizmet yazma ile ilgili yönergeler için bkz: [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="026f1-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="026f1-113">İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetiniz için özellik.</span><span class="sxs-lookup"><span data-stu-id="026f1-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="026f1-114">![ServiceName özelliğini ayarlayın. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="026f1-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="026f1-115">Değerini <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği her zaman yükleyici sınıflarda kayıtlı adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="026f1-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="026f1-116">Bu özelliği değiştirirseniz güncelleştirmelisiniz <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıflarının özelliği.</span><span class="sxs-lookup"><span data-stu-id="026f1-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="026f1-117">Hizmetinizin nasıl çalışacağını belirlemek için aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="026f1-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="026f1-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="026f1-118">Property</span></span>|<span data-ttu-id="026f1-119">Ayar</span><span class="sxs-lookup"><span data-stu-id="026f1-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="026f1-120">`True` hizmetin çalışmayı durdurmak için istekleri kabul edeceğini belirtmek için; `false` hizmetin durdurulmasını önlemek için.</span><span class="sxs-lookup"><span data-stu-id="026f1-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="026f1-121">`True` Hizmet çağıracak şekilde etkinleştirme aşağı üzerinde yaşadığı bilgisayar kapatıldığında bildirim almak istediğini belirten <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> yordamı.</span><span class="sxs-lookup"><span data-stu-id="026f1-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="026f1-122">`True` Hizmeti duraklatmak veya devam ettirmek için istekleri kabul edeceğini belirtmek için çalışan; `false` hizmetinin duraklatılmasını ve devam ettirilmesini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="026f1-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="026f1-123">`True` hizmetin bilgisayarın güç durumu değişiklikleri bildirimini işleyebileceğini belirtmek için; `false` bu değişikliklerin bildirilmesini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="026f1-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="026f1-124">`True` Hizmetiniz bir eylem gerçekleştirdiğinde uygulama olay günlüğüne bilgilendirici girdiler yazmak için; `false` bu işlevi devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="026f1-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="026f1-125">Daha fazla bilgi için [nasıl yapılır: Hizmet bilgilerini günlüğe kaydetme](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="026f1-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="026f1-126">**Not:**  Varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="026f1-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="026f1-127">Zaman <xref:System.ServiceProcess.ServiceBase.CanStop%2A> veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ayarlandığından `false`, **Hizmet Denetimi Yöneticisi** durdurmak, duraklatmak veya hizmete devam ilgili menü seçenekleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="026f1-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="026f1-128">Kod düzenleyicisine erişip ve için istediğiniz işlemeyi doldurun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları.</span><span class="sxs-lookup"><span data-stu-id="026f1-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="026f1-129">İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="026f1-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="026f1-130">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="026f1-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="026f1-131">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="026f1-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="026f1-132">Projenizi seçerek **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="026f1-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="026f1-133">Projenizi çalıştırmak için F5 tuşuna basmayın-bu şekilde bir hizmet projesi çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="026f1-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="026f1-134">Hizmetini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="026f1-134">Install the service.</span></span> <span data-ttu-id="026f1-135">Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="026f1-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026f1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="026f1-136">See also</span></span>
- [<span data-ttu-id="026f1-137">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="026f1-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="026f1-138">Nasıl yapılır: Hizmetleri programlamayla yazma</span><span class="sxs-lookup"><span data-stu-id="026f1-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [<span data-ttu-id="026f1-139">Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="026f1-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="026f1-140">Nasıl yapılır: Günlük bilgilerini hizmetleri hakkında</span><span class="sxs-lookup"><span data-stu-id="026f1-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="026f1-141">Nasıl yapılır: Başlangıç Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="026f1-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="026f1-142">Nasıl yapılır: Hizmetler için güvenlik içeriği belirtme</span><span class="sxs-lookup"><span data-stu-id="026f1-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="026f1-143">Nasıl yapılır: Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="026f1-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="026f1-144">İzlenecek yol: Bileşen tasarımcısında Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="026f1-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
