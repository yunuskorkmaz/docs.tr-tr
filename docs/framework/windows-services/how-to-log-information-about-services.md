---
title: 'Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: dfcfb7370ffd59a50cf6d0b01e84e581ddc6fc52
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306527"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="cd6b4-102">Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="cd6b4-102">How to: Log Information About Services</span></span>
<span data-ttu-id="cd6b4-103">Varsayılan olarak, tüm Windows Service projeleri uygulama olay günlüğü ile etkileşimli ve bilgi ve özel durumlar yazma olanağı vardır.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="cd6b4-104">Kullandığınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> uygulamanızda bu işlevi isteyip istemediğinizi belirtmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="cd6b4-105">Varsayılan olarak, Windows hizmeti proje şablonu ile oluşturduğunuz herhangi bir hizmeti için günlüğe kaydetme açıktır.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="cd6b4-106">Statik bir formu kullanabilirsiniz <xref:System.Diagnostics.EventLog> sınıfı örneğini oluşturmak zorunda kalmadan hizmet bilgilerini günlüğe yazılacak bir <xref:System.Diagnostics.EventLog> bileşen veya el ile bir kaynak kaydı.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="cd6b4-107">Hizmetiniz için yükleyici, projenizdeki her hizmet günlüğe kaydetme açık olduğunda, hizmet, yüklü olduğu geçerli bir kaynak bilgisayardaki Uygulama günlüğünü içeren olayların sayısını otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="cd6b4-108">Hizmet, hizmet çalışmaya, durdurulmuş, duraklatılmış, sürdürüldü, yüklü veya her saat bilgilerini günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="cd6b4-109">Ayrıca, oluşan tüm hataları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-109">It also logs any failures that occur.</span></span> <span data-ttu-id="cd6b4-110">Varsayılan davranış kullanırken girişleri günlüğüne yazmak için kod yazmanız gerekmez; Hizmet bunu sizin için otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="cd6b4-111">Uygulama günlüğünü dışındaki bir olay günlüğüne yazmak istiyorsanız, ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini `false`, kendi özel olay günlüğü Hizmetleri kodunuz içinde oluşturup hizmetiniz, günlük girişlerinin geçerli bir kaynak olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="cd6b4-112">Ardından, girişlerini ilginizi çeken bir eylem olduğunda günlüğe kaydetmek için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd6b4-113">Eğer özel bir olay günlüğü'nün ve yazma service uygulamanızı yapılandırma, hizmetin ayarlamadan önce olay günlüğüne erişmek kullanmamanız gerekir <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> kodunuzdaki özellik.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="cd6b4-114">Olay günlüğü, hizmet geçerli bir olay kaynağı kaydetmek için bu özelliğin değerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="cd6b4-115">Hizmetiniz için varsayılan olay günlüğünü etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cd6b4-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="cd6b4-116">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `true`.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd6b4-117">Varsayılan olarak, bu özellik kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="cd6b4-118">Bir koşulu değerlendirmek ve ardından ayarlar gibi daha karmaşık bir işlem, oluşturmakta olduğunuz sürece bu açıkça ayarlamanız gerekmez <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna bağlı.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="cd6b4-119">Hizmetiniz için olay günlüğünü devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="cd6b4-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="cd6b4-120">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `false`.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="cd6b4-121">Özel günlük için'günlük kaydı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cd6b4-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="cd6b4-122">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd6b4-123">Ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özel bir günlük kullanmak için false.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="cd6b4-124">Bir örneği bir <xref:System.Diagnostics.EventLog> Windows hizmeti uygulamanızda bileşen.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="cd6b4-125">Özel günlük çağırarak oluşturmak <xref:System.Diagnostics.EventLog.CreateEventSource%2A> yöntemi ve kaynak dizeyi ve günlük adını dosyasını belirtme oluşturmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="cd6b4-126">Ayarlama <xref:System.Diagnostics.EventLog.Source%2A> özelliği <xref:System.Diagnostics.EventLog> bileşen örneği için 3. adımda oluşturduğunuz kaynak dizesi.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="cd6b4-127">Girdilerinizi erişerek yazma <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodunda <xref:System.Diagnostics.EventLog> bileşen örneği.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="cd6b4-128">Aşağıdaki kod, özel bir günlük için günlük kaydı ayarlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd6b4-129">Bu kod örneğinde, örneği bir <xref:System.Diagnostics.EventLog> bileşeni adlı `eventLog1` (`EventLog1` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="cd6b4-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="cd6b4-130">2. adımda başka bir adla örneği oluşturduysanız, kodu uygun şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="cd6b4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd6b4-131">See also</span></span>

- [<span data-ttu-id="cd6b4-132">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="cd6b4-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
