---
title: 'Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme'
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
manager: douge
ms.openlocfilehash: a046c62de8789cbe438dcc849ffc23991a803ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="5a134-102">Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="5a134-102">How to: Log Information About Services</span></span>
<span data-ttu-id="5a134-103">Varsayılan olarak, tüm Windows hizmeti projelerinin uygulama olay günlüğü ile etkileşim ve bilgi ve özel durumları yazma özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="5a134-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="5a134-104">Kullandığınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği, bu işlev, uygulamanızda isteyip istemediğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="5a134-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="5a134-105">Varsayılan olarak, Windows hizmeti proje şablonu ile oluşturduğunuz herhangi bir hizmeti için günlüğe kaydetme açıktır.</span><span class="sxs-lookup"><span data-stu-id="5a134-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="5a134-106">Statik bir form, kullanabileceğiniz <xref:System.Diagnostics.EventLog> sınıfının bir örneğini oluşturmak zorunda kalmadan hizmet bilgilerini günlüğe yazma bir <xref:System.Diagnostics.EventLog> bileşeni veya el ile bir kaynak kaydı.</span><span class="sxs-lookup"><span data-stu-id="5a134-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="5a134-107">Hizmetiniz için yükleyici projenizde her bir hizmet olarak geçerli bir kaynak günlük kaydı etkinken hizmet, yüklendiği bilgisayarda uygulama günlüğü ile olayların otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5a134-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="5a134-108">Hizmet bilgileri hizmet başlatıldı, durduruldu, sürdürüldü, yüklü, kaldırıldı veya duraklatıldı her zaman günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5a134-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="5a134-109">Ortaya çıkan hataları günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5a134-109">It also logs any failures that occur.</span></span> <span data-ttu-id="5a134-110">Varsayılan davranışı kullanırken girişleri günlüğüne yazılması için herhangi bir kod yazmak zorunda kalmazsınız; Hizmet bunu sizin için otomatik olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="5a134-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="5a134-111">Uygulama günlüğü dışında bir olay günlüğüne yazmak istiyorsanız, ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğine `false`, kendi özel olay günlüğü Hizmetleri kodunuzu içinde oluşturun ve hizmetiniz, günlük girişlerinin geçerli bir kaynak olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5a134-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="5a134-112">Ardından oluşur girişlerini ilgilendiğiniz bir eylem olduğunda günlüğe kaydetmek için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a134-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a134-113">Özel bir olay günlüğü kullanın ve hizmet uygulamanızın yazma yapılandırırsanız, hizmetin ayarlamadan önce olay günlüğüne erişmek çalışmamalısınız <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> kodunuzda özelliği.</span><span class="sxs-lookup"><span data-stu-id="5a134-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="5a134-114">Olay günlüğü hizmetinizi olayların geçerli bir kaynak kaydetmek için bu özelliğin değeri gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a134-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="5a134-115">Hizmetiniz için varsayılan olay günlüğünü etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="5a134-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="5a134-116">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `true`.</span><span class="sxs-lookup"><span data-stu-id="5a134-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a134-117">Varsayılan olarak, bu özelliği ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="5a134-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="5a134-118">Bir koşulu değerlendirmek ve ardından ayarlama gibi daha karmaşık işlem oluşturmakta olduğunuz sürece açıkça ayarlamanız gerekmez <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna bağlı.</span><span class="sxs-lookup"><span data-stu-id="5a134-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="5a134-119">Hizmetiniz için olay günlüğünü devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="5a134-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="5a134-120">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bileşeniniz için özellik `false`.</span><span class="sxs-lookup"><span data-stu-id="5a134-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="5a134-121">Özel günlük günlüğünü ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5a134-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="5a134-122">Ayarlama <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="5a134-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a134-123">Ayarlamalısınız <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özel bir günlük kullanmak için false.</span><span class="sxs-lookup"><span data-stu-id="5a134-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="5a134-124">Ayarlanan örneği bir <xref:System.Diagnostics.EventLog> Windows hizmeti uygulamanızda bileşen.</span><span class="sxs-lookup"><span data-stu-id="5a134-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="5a134-125">Özel günlük çağırarak oluşturun <xref:System.Diagnostics.EventLog.CreateEventSource%2A> yöntemi ve kaynak dizesi ve günlük adını dosyası belirterek oluşturmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="5a134-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="5a134-126">Ayarlama <xref:System.Diagnostics.EventLog.Source%2A> özellikte <xref:System.Diagnostics.EventLog> bileşen örneği için 3. adımda oluşturduğunuz kaynak dizesi.</span><span class="sxs-lookup"><span data-stu-id="5a134-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="5a134-127">Erişerek girişlerinizi yazma <xref:System.Diagnostics.EventLog.WriteEntry%2A> yöntemi <xref:System.Diagnostics.EventLog> bileşen örneği.</span><span class="sxs-lookup"><span data-stu-id="5a134-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="5a134-128">Aşağıdaki kod, özel bir günlük günlüklerini ayarlayın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5a134-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a134-129">Bu kod örneğinde, örneği bir <xref:System.Diagnostics.EventLog> bileşen adlandırılan `eventLog1` (`EventLog1` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="5a134-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="5a134-130">2. adımda başka bir adla örneğini oluşturduysanız, kodu uygun şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5a134-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="5a134-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a134-131">See Also</span></span>  
 [<span data-ttu-id="5a134-132">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="5a134-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
