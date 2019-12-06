---
title: İzleme Katılımcıları
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: a033b65125a562307c6247eeda93dcacb31f5382
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837655"
---
# <a name="tracking-participants"></a><span data-ttu-id="ab7f9-102">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="ab7f9-102">Tracking Participants</span></span>
<span data-ttu-id="ab7f9-103">Katılımcıları izlemek, iş akışı geliştiricisinin <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> nesnelere erişmesini ve bunları işlemesini sağlayan genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="ab7f9-104">, izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan standart bir izleme katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="ab7f9-105">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="ab7f9-106">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="ab7f9-106">Tracking Participants</span></span>  
 <span data-ttu-id="ab7f9-107">İzleme altyapısı, bir katılımcının kayıtların bir alt kümesine abone olabileceği gibi, giden izleme kayıtlarında bir filtrenin uygulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="ab7f9-108">Filtre uygulama mekanizması bir izleme profili aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="ab7f9-109">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Windows Workflow Foundation (WF), izleme kayıtlarını bir ETW oturumuna yazan bir izleme katılımcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ab7f9-110">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ab7f9-111">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ab7f9-112">ETW tabanlı izleme için SDK örneği, ETW tabanlı izleme katılımcısını kullanarak WF izlemeye alışmanız için iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="ab7f9-113">ETW Izleme Katılımcısı</span><span class="sxs-lookup"><span data-stu-id="ab7f9-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="ab7f9-114">, izleme kayıtlarını bir ETW oturumuna yazan bir ETW Izleme katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ab7f9-115">Bu, uygulamanın performansına veya sunucunun aktarım hızına en az etkiyle çok verimli bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="ab7f9-116">Standart ETW izleme katılımcısı kullanmanın bir avantajı, aldığı izleme kayıtlarının Windows Olay Görüntüleyicisi diğer uygulama ve sistem günlükleri ile görüntülenebilmesini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="ab7f9-117">Standart ETW izleme katılımcısı, aşağıdaki örnekte gösterildiği gibi Web. config dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="ab7f9-118">Yalnızca `<etwTracking/>` veya `<etwTracking profileName=""/>`gibi bir `trackingProfile` adı belirtilmemişse, Machine. config dosyasındaki [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ile yüklenen varsayılan izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="ab7f9-119">Machine. config dosyasında, varsayılan izleme profili iş akışı örnek kayıtlarına ve hatalarına abone olur.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="ab7f9-120">ETW 'de, olaylar bir sağlayıcı KIMLIĞI aracılığıyla ETW oturumuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="ab7f9-121">ETW izleme katılımcısı tarafından ETW 'ye izleme kayıtlarını yazmak için kullanılan sağlayıcı KIMLIĞI, Web. config dosyasının Tanılama bölümünde tanımlanır (`<system.serviceModel><diagnostics>`altında).</span><span class="sxs-lookup"><span data-stu-id="ab7f9-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="ab7f9-122">Varsayılan olarak, ETW izleme katılımcısı, aşağıdaki örnekte gösterildiği gibi, biri belirtilmediğinde varsayılan bir sağlayıcı KIMLIĞI kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="ab7f9-123">Aşağıdaki çizimde, ETW izleme katılımcısı aracılığıyla veri izleme akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="ab7f9-124">İzleme verileri ETW oturumuna ulaştığında, bir dizi şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="ab7f9-125">Bu olaylara erişmenin en yararlı yöntemlerinden biri, uygulama ve hizmetlerden günlükleri ve izlemeleri görüntülemek için kullanılan ortak bir Windows aracı olan Olay Görüntüleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![ETW izleme sağlayıcısı aracılığıyla izleme verileri akışı.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="ab7f9-127">Katılımcı olay verilerini izleme</span><span class="sxs-lookup"><span data-stu-id="ab7f9-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="ab7f9-128">Bir izleme katılımcısı, izlenen olay verilerini izleme kaydı başına bir olay biçiminde bir ETW oturumunda seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="ab7f9-129">Bir olay, 100 ile 199 arasında bir KIMLIK kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="ab7f9-130">İzleme katılımcısı tarafından yayılan izleme olayı kayıtlarının tanımları için, [olayları Izleme başvurusu](tracking-events-reference.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="ab7f9-131">Bir ETW olayının boyutu ETW arabellek boyutuyla sınırlıdır veya bir ETW olayı için en yüksek yük tarafından, hangisi daha küçükse bu değer daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="ab7f9-132">Olayın boyutu bu ETW limitlerinden birini aşarsa, olay kesilir ve içeriği rastgele bir şekilde kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="ab7f9-133">Değişkenler, bağımsız değişkenler, ek açıklamalar ve özel veriler seçmeli olarak kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="ab7f9-134">Kesme durumunda, bu durum, olay boyutunun ETW sınırını aşmasına neden olan değere bakılmaksızın kesilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="ab7f9-135">Kaldırılan veriler `<item>..<item>`ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="ab7f9-136">Değişkenlerde, bağımsız değişkenlerde ve özel veri öğelerinde karmaşık türler, <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı kullanılarak ETW olay kaydına serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="ab7f9-137">Bu sınıf, seri hale getirilen XML tarafında CLR türü bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="ab7f9-138">ETW sınırları nedeniyle yük verilerinin kesilmesi, yinelenen izleme kayıtlarının bir ETW oturumuna gönderilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="ab7f9-139">Bu durum, olayları dinlerken birden fazla oturum varsa ve oturumlar için farklı yük sınırlarına sahip olduğunda meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="ab7f9-140">Alt sınır ile oturum için olay kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="ab7f9-141">ETW izleme katılımcısı, olayları dinleyen oturum sayısı hakkında bilgi sahibi değildir; bir oturum için bir olay kesilmişse, ETW katılımcısı olayı bir kez göndermeyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="ab7f9-142">Bu durumda, daha büyük bir yük boyutunu kabul edecek şekilde yapılandırılan oturum, olayı iki kez alır (kesilmeyen ve kesilen olay).</span><span class="sxs-lookup"><span data-stu-id="ab7f9-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="ab7f9-143">Aynı arabellek boyutu limitleriyle tüm ETW oturumları yapılandırılarak çoğaltma engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="ab7f9-144">Olay Görüntüleyicisi ETW katılımcılarından Izleme verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="ab7f9-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="ab7f9-145">ETW izleme katılımcısı tarafından ETW oturumuna yazılan olaylara Olay Görüntüleyicisi aracılığıyla erişilebilir (varsayılan sağlayıcı KIMLIĞI kullanılırken).</span><span class="sxs-lookup"><span data-stu-id="ab7f9-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="ab7f9-146">Bu, iş akışı tarafından yayınlanan kayıtları izlemeyi hızlı bir şekilde görüntülemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab7f9-147">Bir ETW oturumuna yayılan kayıt olaylarını izleme, 100 ile 199 arasındaki aralıktaki olay kimliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="ab7f9-148">Olay Görüntüleyicisi Izleme kayıtlarını görüntülemeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ab7f9-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="ab7f9-149">Olay Görüntüleyicisi başlatın (EVENTVWR. EXE</span><span class="sxs-lookup"><span data-stu-id="ab7f9-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="ab7f9-150">**Olay Görüntüleyicisi, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama sunucusu-uygulamalar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="ab7f9-151">Sağ tıklayın ve **Görünüm, analitik ve hata ayıklama günlüklerini göster** ' in seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="ab7f9-152">Aksi takdirde, seçeneğinin yanında onay işaretinin görünmesi için bunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="ab7f9-153">Bu, **analitik**, **perf**ve **hata ayıklama** günlüklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="ab7f9-154">**Analitik** günlüğe sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="ab7f9-155">Günlük%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications %4 A nalytic. etl dosyasında mevcut olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="ab7f9-156">Özel Izleme Katılımcısı</span><span class="sxs-lookup"><span data-stu-id="ab7f9-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="ab7f9-157">Katılımcı izleme API 'SI, iş akışı çalışma zamanı tarafından yayılan izleme kayıtlarını işlemek için özel mantık içerebilen kullanıcı tarafından sağlanmış bir izleme katılımcısına sahip izleme çalışma zamanının uzantısına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="ab7f9-158">Özel bir izleme katılımcısı yazmak için, geliştiricinin <xref:System.Activities.Tracking.TrackingParticipant> sınıfında `Track` yöntemini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="ab7f9-159">Bu yöntem, bir izleme kaydı iş akışı çalışma zamanı tarafından yayıldığınızda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="ab7f9-160">İzleme katılımcıları <xref:System.Activities.Tracking.TrackingParticipant> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="ab7f9-161">Sistem tarafından sağlanmış <xref:System.Activities.Tracking.EtwTrackingParticipant>, alınan her izleme kaydı için bir Windows (ETW) olayı Izleme olayı yayar.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="ab7f9-162">Özel bir izleme katılımcısı oluşturmak için, <xref:System.Activities.Tracking.TrackingParticipant>türetilen bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="ab7f9-163">Temel izleme işlevlerini sağlamak için <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="ab7f9-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A>, çalışma zamanı tarafından bir izleme kaydı gönderildiğinde ve istenen şekilde işlenebiliyor olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="ab7f9-165">Aşağıdaki örnekte, tüm izleme kayıtlarını konsol penceresine yayar ve özel bir izleme katılımcı sınıfı tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="ab7f9-166">İzleme kayıtlarını zaman uyumsuz olarak işleyen bir <xref:System.Activities.Tracking.TrackingParticipant> nesnesini `BeginTrack` ve `EndTrack` yöntemlerini kullanarak da uygulayabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="ab7f9-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ab7f9-167">Belirli bir izleme katılımcısını kullanmak için, aşağıdaki örnekte gösterildiği gibi, izlemek istediğiniz iş akışı örneğiyle kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="ab7f9-168">Aşağıdaki örnekte, bir <xref:System.Activities.Statements.WriteLine> etkinliği içeren <xref:System.Activities.Statements.Sequence> etkinliğinden oluşan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="ab7f9-169">`ConsoleTrackingParticipant` uzantılara eklenir ve iş akışı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab7f9-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab7f9-170">See also</span></span>

- <span data-ttu-id="ab7f9-171">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ab7f9-171">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="ab7f9-172">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ab7f9-172">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
