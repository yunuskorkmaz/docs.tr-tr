---
title: 'Nasıl yapılır: Windows Hizmetleri Oluşturma'
description: Bir hizmet oluşturmak için Windows hizmeti proje şablonunu kullanın. ServiceName özelliğini ayarlayın, yükleyiciler oluşturun ve OnStart ve OnStop yöntemlerini geçersiz kılın.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925780"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="ec201-104">Nasıl yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec201-104">How to: Create Windows Services</span></span>
<span data-ttu-id="ec201-105">Bir hizmet oluşturduğunuzda, **Windows hizmeti**adlı bir Visual Studio proje şablonu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec201-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="ec201-106">Bu şablon uygun sınıflara ve ad alanlarına başvurarak, hizmetler için temel sınıftan devralmayı ayarlayarak ve büyük olasılıkla geçersiz kılmak istediğiniz yöntemlerin birkaçını geçersiz kılarak sizin için işin çoğunu otomatik olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="ec201-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ec201-107">Windows Hizmetleri proje şablonu, Visual Studio 'nun Express sürümünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec201-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="ec201-108">Bir işlevsel hizmet oluşturmak için en azından şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ec201-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="ec201-109">Özelliği ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec201-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="ec201-110">Hizmet uygulamanız için gerekli yükleyicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec201-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="ec201-111"><xref:System.ServiceProcess.ServiceBase.OnStart%2A>Hizmetinizin davranışını özelleştirmek için ve yöntemlerinin kodunu geçersiz kılın ve belirtin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec201-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="ec201-112">Bir Windows hizmet uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ec201-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="ec201-113">Bir **Windows hizmeti** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec201-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ec201-114">Şablon kullanmadan bir hizmet yazma yönergeleri için bkz. [nasıl yapılır: Hizmetleri program aracılığıyla yazma](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ec201-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="ec201-115">**Özellikler** penceresinde <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetinizin özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec201-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="ec201-116">![ServiceName özelliğini ayarlayın.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="ec201-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ec201-117"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A>Özelliğin değeri her zaman yükleyici sınıflarında kaydedilen adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec201-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="ec201-118">Bu özelliği değiştirirseniz, <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıflarının özelliğini de güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec201-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="ec201-119">Hizmetinizin nasıl çalışacağını öğrenmek için aşağıdaki özelliklerden herhangi birini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec201-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="ec201-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="ec201-120">Property</span></span>|<span data-ttu-id="ec201-121">Ayar</span><span class="sxs-lookup"><span data-stu-id="ec201-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="ec201-122">`True`hizmetin çalışmayı durdurmak için istekleri kabul edeceğini belirtmek için; `false`hizmetin durdurulmasını engellemek için.</span><span class="sxs-lookup"><span data-stu-id="ec201-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="ec201-123">`True`hizmetin, yaşadığı bilgisayar kapandığında bildirim almak istediğini göstermek için, yordamı çağırabileceği şekilde etkinleştirir <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec201-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="ec201-124">`True`hizmetin çalışmayı duraklatmak veya çalışmaya devam etmek için istekleri kabul edeceğini belirtmek için; `false`hizmetin duraklatılmasını ve devam ettirmasını engellemek için.</span><span class="sxs-lookup"><span data-stu-id="ec201-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="ec201-125">`True`hizmetin bilgisayarın güç durumundaki değişikliklerin bildirimini işleyebileceğini belirtmek için; `false`hizmetin bu değişiklikler hakkında bildirilmesini engellemek için.</span><span class="sxs-lookup"><span data-stu-id="ec201-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="ec201-126">`True`Hizmetiniz bir eylem gerçekleştirdiğinde Uygulama olay günlüğü 'ne bilgilendirici girişler yazmak için; `false`Bu işlevi devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="ec201-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="ec201-127">Daha fazla bilgi için bkz. [nasıl yapılır: hizmetlerle Ilgili bilgileri günlüğe kaydetme](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="ec201-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="ec201-128">**Note:**  Varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="ec201-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="ec201-129"><xref:System.ServiceProcess.ServiceBase.CanStop%2A>Veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> olarak ayarlandığında `false` , **hizmet denetimi Yöneticisi** hizmeti durdurmak, duraklatmak veya devam ettirmek için ilgili menü seçeneklerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ec201-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="ec201-130">Kod düzenleyicisine erişin ve yordamları için istediğiniz işlemeyi girin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec201-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="ec201-131">İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="ec201-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="ec201-132">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec201-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="ec201-133">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ec201-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="ec201-134">**Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec201-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ec201-135">Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="ec201-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="ec201-136">Hizmeti yükler.</span><span class="sxs-lookup"><span data-stu-id="ec201-136">Install the service.</span></span> <span data-ttu-id="ec201-137">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="ec201-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec201-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec201-138">See also</span></span>

- [<span data-ttu-id="ec201-139">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="ec201-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ec201-140">Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma</span><span class="sxs-lookup"><span data-stu-id="ec201-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="ec201-141">Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="ec201-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="ec201-142">Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="ec201-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="ec201-143">Nasıl yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="ec201-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="ec201-144">Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme</span><span class="sxs-lookup"><span data-stu-id="ec201-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="ec201-145">Nasıl yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="ec201-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="ec201-146">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec201-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
