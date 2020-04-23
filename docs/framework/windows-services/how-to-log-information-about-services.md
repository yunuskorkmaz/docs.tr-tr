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
ms.openlocfilehash: 3c974d5a98f8056e45899b109878e5a28ab2938e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053614"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="ee3c8-102">Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="ee3c8-102">How to: Log Information About Services</span></span>
<span data-ttu-id="ee3c8-103">Varsayılan olarak, tüm Windows hizmeti projelerinin uygulama olay günlüğü ile etkileşim kurma ve bu bilgilere yazma bilgileri ve özel durumları vardır.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="ee3c8-104">Uygulamanızda bu işlevselliği <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> isteyip istemediğinizi belirtmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="ee3c8-105">Varsayılan olarak, Windows hizmeti proje şablonuyla oluşturduğunuz her hizmet için günlük kaydı açıktır.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="ee3c8-106">Bir <xref:System.Diagnostics.EventLog> bileşenin örneğini oluşturmak veya bir kaynağı el <xref:System.Diagnostics.EventLog> ile kaydetmek zorunda kalmadan hizmet bilgilerini bir günlüğe yazmak için sınıfının statik bir biçimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="ee3c8-107">Hizmetiniz için yükleyici, günlük kaydı açık olduğunda, hizmetin yüklendiği bilgisayardaki uygulama günlüğü ile projenizdeki her hizmeti otomatik olarak geçerli bir olay kaynağı olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="ee3c8-108">Hizmetin başlatıldığı, durdurulduğu, duraklatıldığı, kaldığı, yüklendiği veya kaldırıldığı her seferinde hizmet bilgileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="ee3c8-109">Ayrıca oluşan tüm sorunları günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-109">It also logs any failures that occur.</span></span> <span data-ttu-id="ee3c8-110">Varsayılan davranışı kullanırken günlüğe giriş yazmak için herhangi bir kod yazmanız gerekmez; hizmet bunu sizin için otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="ee3c8-111">Uygulama günlüğü dışında bir olay günlüğüne yazmak isterseniz, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği olarak `false`ayarlamanız, hizmet kodunuzda kendi özel olay günlüğlerinizi oluşturmanız ve hizmetinizi bu günlük için geçerli bir giriş kaynağı olarak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="ee3c8-112">Ardından, ilgilendiğiniz bir eylem olduğunda günlüğe girdileri kaydetmek için kod yazmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee3c8-113">Özel bir olay günlüğü kullanır ve hizmet uygulamanızı ona yazacak şekilde yapılandırırsanız, kodunuzda hizmetin <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliğini ayarlamadan önce olay günlüğüne erişmeye çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="ee3c8-114">Olay günlüğü, hizmetinizi geçerli bir olay kaynağı olarak kaydetmek için bu özelliğin değerine ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="ee3c8-115">Hizmetiniz için varsayılan olay günlüğünü etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ee3c8-115">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="ee3c8-116">Bileşeninizin <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee3c8-117">Varsayılan olarak, bu özellik olarak `true`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="ee3c8-118">Bir koşulu değerlendirme ve sonra <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliği bu koşulun sonucuna göre ayarlama gibi daha karmaşık bir işlem oluşturulmadığınız sürece bunu açıkça ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="ee3c8-119">Hizmetiniz için olay günlüğünü devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="ee3c8-119">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="ee3c8-120">Bileşeninizin <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> özelliğini olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="ee3c8-121">Özel bir günlüğe günlük kaydı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ee3c8-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="ee3c8-122"><xref:System.ServiceProcess.ServiceBase.AutoLog%2A> Özelliğini olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee3c8-123">Özel bir günlük <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> kullanabilmeniz için false olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="ee3c8-124">Windows hizmet uygulamanızda bir <xref:System.Diagnostics.EventLog> bileşen örneği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="ee3c8-125"><xref:System.Diagnostics.EventLog.CreateEventSource%2A> Yöntemini çağırarak ve kaynak dizeyi ve oluşturmak istediğiniz günlük dosyasının adını belirterek özel bir günlük oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="ee3c8-126"><xref:System.Diagnostics.EventLog> Bileşen örneğindeki <xref:System.Diagnostics.EventLog.Source%2A> özelliği adım 3 ' te oluşturduğunuz kaynak dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="ee3c8-127"><xref:System.Diagnostics.EventLog> Bileşen örneğindeki <xref:System.Diagnostics.EventLog.WriteEntry%2A> yöntemine erişerek girdilerinizi yazın.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="ee3c8-128">Aşağıdaki kod, özel bir günlüğe kaydetmenin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee3c8-129">Bu kod örneğinde, bir <xref:System.Diagnostics.EventLog> bileşenin örneği ( `eventLog1` `EventLog1` Visual Basic) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="ee3c8-130">2. adımda başka bir ada sahip bir örnek oluşturduysanız, kodu uygun şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="ee3c8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee3c8-131">See also</span></span>

- [<span data-ttu-id="ee3c8-132">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="ee3c8-132">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
