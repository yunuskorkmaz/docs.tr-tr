---
title: "Nasıl Yapılır: Windows Hizmetleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c4d7f2f19c8d156f86513ac7138bccd59ae3b7fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="ef255-102">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef255-102">How to: Create Windows Services</span></span>
<span data-ttu-id="ef255-103">Bir hizmet oluşturduğunuzda adlı bir Visual Studio Proje şablonu kullanabilirsiniz **Windows hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="ef255-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="ef255-104">Bu şablon otomatik olarak işin çoğunu sizin için uygun sınıfları ve ad alanları, hizmetleri, temel sınıfından devralma ayarlama başvurarak yapar ve birkaç yöntemleri geçersiz kılma, büyük bir olasılıkla geçersiz kılmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="ef255-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ef255-105">Windows Hizmetleri Proje şablonu Visual Studio Express Edition'da kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="ef255-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="ef255-106">En azından, işlevsel bir hizmet oluşturmak için yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ef255-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="ef255-107">Ayarlama <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef255-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="ef255-108">Hizmet uygulamanız için gerekli yükleyicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef255-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="ef255-109">Geçersiz kılmak ve kodunu belirtmek <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> , hizmetinizin davranış yöntemlerini özelleştirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ef255-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="ef255-110">Windows hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ef255-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="ef255-111">Oluşturma bir **Windows hizmeti** projesi.</span><span class="sxs-lookup"><span data-stu-id="ef255-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef255-112">Bir hizmet şablonunu kullanmadan yazma ile ilgili yönergeler için bkz: [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ef255-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="ef255-113">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetiniz için özellik.</span><span class="sxs-lookup"><span data-stu-id="ef255-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="ef255-114">![ServiceName özelliğini ayarlayın. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="ef255-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef255-115">Değeri <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği her zaman yükleyici sınıflarda kayıtlı adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ef255-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="ef255-116">Bu özelliği değiştirirseniz, güncelleştirmelisiniz <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıfları özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef255-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="ef255-117">Hizmetinizin nasıl işlev gösterdiğini belirlemek için aşağıdaki özelliklerden herhangi birini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ef255-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="ef255-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="ef255-118">Property</span></span>|<span data-ttu-id="ef255-119">Ayar</span><span class="sxs-lookup"><span data-stu-id="ef255-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="ef255-120">`True`hizmeti çalışmayı durdurmak için istekleri kabul ettiğinizi belirtmek için; `false` hizmetin durdurulmasını önlemek için.</span><span class="sxs-lookup"><span data-stu-id="ef255-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="ef255-121">`True`hizmet üzerinde bulunduğu bilgisayar aşağı çağırmak etkinleştirmeden kapattığında bildirim almak istediği belirtmek için <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> yordamı.</span><span class="sxs-lookup"><span data-stu-id="ef255-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="ef255-122">`True`Hizmeti duraklatmak veya sürdürmek için istekleri kabul ettiğinizi belirtmek için çalışan; `false` hizmetinin duraklatılmasını ve önlemek için.</span><span class="sxs-lookup"><span data-stu-id="ef255-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="ef255-123">`True`Hizmet bildirim bilgisayarın güç durumu değişiklikleri işleyebileceğini belirtmek için; `false` bu değişikliklerden haberdar hizmetin önlemek için.</span><span class="sxs-lookup"><span data-stu-id="ef255-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="ef255-124">`True`Hizmetiniz bir eylem gerçekleştirdiğinde bilgilendirici girdiler için uygulama olay günlüğüne yazmak için; `false` bu işlev devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="ef255-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="ef255-125">Daha fazla bilgi için bkz: [nasıl yapılır: günlük Information Services'ı hakkında](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="ef255-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="ef255-126">**Not:** varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="ef255-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ef255-127">Zaman <xref:System.ServiceProcess.ServiceBase.CanStop%2A> veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ayarlanır `false`, **Hizmet Denetim Yöneticisi** durdurmak, duraklatmak veya hizmet devam etmek için ilgili menü seçenekleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ef255-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="ef255-128">Kod Düzenleyicisi'ne erişmek ve için istediğiniz işleme doldurun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları.</span><span class="sxs-lookup"><span data-stu-id="ef255-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="ef255-129">İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="ef255-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="ef255-130">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef255-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="ef255-131">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ef255-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="ef255-132">Seçerek projenizi derleme **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ef255-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef255-133">Projenizi çalıştırmak için F5 tuşuna basmayın — bir hizmet projesi bu şekilde çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="ef255-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="ef255-134">Hizmetini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ef255-134">Install the service.</span></span> <span data-ttu-id="ef255-135">Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="ef255-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef255-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef255-136">See Also</span></span>  
 [<span data-ttu-id="ef255-137">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="ef255-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="ef255-138">Nasıl yapılır: Hizmetleri programlamayla yazma</span><span class="sxs-lookup"><span data-stu-id="ef255-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="ef255-139">Nasıl yapılır: hizmet uygulamasına yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="ef255-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="ef255-140">Nasıl yapılır: hizmet bilgilerini günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="ef255-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="ef255-141">Nasıl yapılır: Hizmetleri başlatma</span><span class="sxs-lookup"><span data-stu-id="ef255-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="ef255-142">Nasıl yapılır: Hizmetleri için güvenlik bağlamı belirtin</span><span class="sxs-lookup"><span data-stu-id="ef255-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="ef255-143">Nasıl yapılır: Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="ef255-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="ef255-144">İzlenecek yol: Bileşen tasarımcısında Windows hizmet uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef255-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
