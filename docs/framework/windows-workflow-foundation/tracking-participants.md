---
title: İzleme katılımcıları
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: e346e0df3417f6ac83854bd96d6e64dcf103ea93
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518811"
---
# <a name="tracking-participants"></a><span data-ttu-id="7e082-102">İzleme katılımcıları</span><span class="sxs-lookup"><span data-stu-id="7e082-102">Tracking Participants</span></span>
<span data-ttu-id="7e082-103">İzleme katılımcıları erişmek bir iş akışı Geliştirici tanıyan genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> nesneleri ve bunları işlem.</span><span class="sxs-lookup"><span data-stu-id="7e082-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="7e082-104"> izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan standart izleme katılımcı içerir.</span><span class="sxs-lookup"><span data-stu-id="7e082-104"> includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="7e082-105">Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e082-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="7e082-106">İzleme katılımcıları</span><span class="sxs-lookup"><span data-stu-id="7e082-106">Tracking Participants</span></span>  
 <span data-ttu-id="7e082-107">Katılımcı bir kayıt alt kümesi için abone olabilirsiniz, izleme altyapısı üzerinde giden izleme kayıtları bir filtre uygulamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e082-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="7e082-108">Bir filtre uygulamak için bir izleme profili mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="7e082-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="7e082-109">Windows Workflow Foundation (WF) [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] izleme kayıtları bir ETW oturumu Yazar izleme katılımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e082-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="7e082-110">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranışı ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="7e082-111">Etkinleştirme bir ETW İzleme katılımcı olacak şekilde kayıtları izleme Olay Görüntüleyicisi'görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e082-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="7e082-112">ETW tabanlı izleme için SDK'sı örneği ile tabanlı ETW İzleme katılımcı kullanarak WF izleme hakkında bilgi edinmek için iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="7e082-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="7e082-113">ETW İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="7e082-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="7e082-114"> bir ETW İzleme, izleme kayıtları bir ETW oturumu Yazar katılımcı içerir.</span><span class="sxs-lookup"><span data-stu-id="7e082-114"> includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="7e082-115">Bu, uygulamanızın performansını veya sunucunun aktarım hızı için minimum etkiyle çok verimli bir şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="7e082-116">Standart ETW İzleme katılımcı kullanmanın bir avantajı, aldığı izleme kayıtları başka bir uygulama ile görüntülenebilir ve Windows Olay Görüntüleyicisi'nde sistem günlükleri ' dir.</span><span class="sxs-lookup"><span data-stu-id="7e082-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="7e082-117">Standart ETW İzleme katılımcı Web.config dosyasında aşağıdaki örnekte gösterilen şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="7e082-118">Varsa bir `trackingProfile` adı belirtilmezse gibi hemen `<etwTracking/>` veya `<etwTracking profileName=""/>`, ardından varsayılan profil ile yüklü izleme [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Machine.config dosyasına dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="7e082-119">Machine.config dosyasında varsayılan profili izleme, iş akışı örneği kayıtları ve hatalar için abone olur.</span><span class="sxs-lookup"><span data-stu-id="7e082-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="7e082-120">ETW olayları ETW oturumu üzerinden bir sağlayıcı kimliği yazılır</span><span class="sxs-lookup"><span data-stu-id="7e082-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="7e082-121">ETW İzleme katılımcı kullandığı izleme yazmak için ETW kayıt kimliği Web.config dosyasının tanılama bölümünde tanımlanan sağlayıcısı (altında `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="7e082-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="7e082-122">Varsayılan olarak, bir belirtilmedi, ETW İzleme katılımcı aşağıdaki örnekte gösterildiği gibi varsayılan sağlayıcı kimliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e082-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="7e082-123">İzleme verilerini ETW İzleme katılımcı aracılığıyla akışı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7e082-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="7e082-124">İzleme verilerini ETW oturumu ulaştığında, çeşitli yollarla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="7e082-125">Olay Görüntüleyicisi, günlükler ve izlemeler, uygulamaları ve hizmetleri görüntülemek için kullanılan genel bir Windows aracı üzerinden bu olayları erişmek için en faydalı yollarından biridir.</span><span class="sxs-lookup"><span data-stu-id="7e082-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 <span data-ttu-id="7e082-126">![Akışı izleme ve ETW İzleme Sağlayıcısı](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span><span class="sxs-lookup"><span data-stu-id="7e082-126">![The flow of Tracking and ETW Tracking Provider](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span></span>  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="7e082-127">İzleme katılımcı olay verileri</span><span class="sxs-lookup"><span data-stu-id="7e082-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="7e082-128">İzleme katılımcı, izleme kaydı başına bir olay biçiminde bir ETW oturumu izlenen olay verilerini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="7e082-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="7e082-129">Bir olay 199-100 aralığında bir kimliği kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7e082-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="7e082-130">İzleme olayı tanımları için bir izleme katılımcı tarafından yayılan kayıtları görüntüle [izleme olayları başvurusu](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) konu.</span><span class="sxs-lookup"><span data-stu-id="7e082-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="7e082-131">ETW olay boyutu ETW arabellek boyutuyla sınırlıdır veya ETW olayı için en fazla yükü tarafından hangi değerin daha küçük.</span><span class="sxs-lookup"><span data-stu-id="7e082-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="7e082-132">Olay boyutu ya da ETW limitler aşarsa, olay kesilmiş ve içeriği rastgele bir şekilde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="7e082-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="7e082-133">Değişkenleri, bağımsız değişkenler, ek açıklamalar ve özel verileri seçmeli olarak kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="7e082-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="7e082-134">Kesme söz konusu olduğunda, bunların tümünün olay boyutu ETW sınırını aşmasına neden değeri bağımsız olarak kesilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="7e082-135">Kaldırılan veriler ile değiştirilir `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="7e082-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="7e082-136">Karmaşık türleri değişkenleri, bağımsız ve özel veri öğeleri, ETW olay kullanarak kayıt serileştirilme [NetDataContractSerializer sınıfı](https://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="7e082-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="7e082-137">Bu sınıf serileştirilmiş XML akışı CLR türü bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7e082-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="7e082-138">Yük verisi ETW sınırı nedeniyle kesildi yinelenen izleme kayıtları bir ETW oturumu gönderilen neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="7e082-139">Birden fazla oturum olayları dinleyen ve oturumları olaylar için farklı yükü sınırları varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="7e082-140">Alt sınır oturum olay kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="7e082-141">ETW İzleme katılımcı olayları dinleme oturum sayısı, tüm bilgilere sahip değildir; bir olay oturumu sonra bir kez olayı gönderirken ETW katılımcı yeniden denemeler için grafik kesilmişse.</span><span class="sxs-lookup"><span data-stu-id="7e082-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="7e082-142">Bu durumda daha büyük bir yükü boyutu kabul edecek şekilde yapılandırılmış oturum olayı iki kez (kesilmiş olmayan ve kesilmiş) alırsınız.</span><span class="sxs-lookup"><span data-stu-id="7e082-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="7e082-143">Çoğaltma ile aynı arabellek boyutu sınırları tüm ETW oturumlarına yapılandırarak önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="7e082-144">Olay Görüntüleyicisi'ni bir ETW Katılımcısı veri izlemeyi erişme</span><span class="sxs-lookup"><span data-stu-id="7e082-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="7e082-145">Bir ETW oturumu ETW İzleme katılımcı tarafından yazılan olayları Olay Görüntüleyicisi'ni (varsayılan sağlayıcı kimliği kullanırken) erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="7e082-146">Bu, iş akışı tarafından yayılan kayıtları izleme hızlı bir şekilde görüntülemek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e082-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e082-147">Olayların bir ETW oturumu kullanın olay kimlikleri 199-100 aralığında yayılan izleme.</span><span class="sxs-lookup"><span data-stu-id="7e082-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="7e082-148">Olay Görüntüleyicisi'nde izleme kayıtları görüntüleme olanağı</span><span class="sxs-lookup"><span data-stu-id="7e082-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1.  <span data-ttu-id="7e082-149">Olay Görüntüleyicisi'ni (EVENTVWR. başlatma EXE)</span><span class="sxs-lookup"><span data-stu-id="7e082-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2.  <span data-ttu-id="7e082-150">Seçin **Olay Görüntüleyicisi, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="7e082-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3.  <span data-ttu-id="7e082-151">Sağ tıklayın ve emin **görünümü, Analitik ve hata ayıklama günlüklerini göster** seçilir.</span><span class="sxs-lookup"><span data-stu-id="7e082-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="7e082-152">Aksi durumda, onay işaretine yanında görünecek şekilde seçin.</span><span class="sxs-lookup"><span data-stu-id="7e082-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="7e082-153">Bu görüntüler **analitik**, **Perf**, ve **hata ayıklama** günlükleri.</span><span class="sxs-lookup"><span data-stu-id="7e082-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4.  <span data-ttu-id="7e082-154">Sağ **analitik** oturum açın ve ardından **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="7e082-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="7e082-155">Günlük %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="7e082-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="7e082-156">Özel İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="7e082-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="7e082-157">API izleme katılımcı, izleme çalışma zamanı uzantısı, iş akışı çalışma zamanı tarafından yayılan izleme kayıtları işlemek için Özel mantık dahil edebilirsiniz bir kullanıcı tarafından sağlanan izleme katılımcı ile sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e082-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="7e082-158">Özel İzleme katılımcı yazmak için geliştirici uygulamalıdır `Track` metodunda <xref:System.Activities.Tracking.TrackingParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7e082-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="7e082-159">Bu yöntem, bir izleme kaydını yayılan iş akışı çalışma zamanı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="7e082-160">İzleme katılımcıları türetilen <xref:System.Activities.Tracking.TrackingParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7e082-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="7e082-161">Sistem tarafından sağlanan <xref:System.Activities.Tracking.EtwTrackingParticipant> bir olay izleme için Windows (ETW) olayı, alınan her bir izleme kaydını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e082-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="7e082-162">Özel İzleme katılımcı oluşturmak için bir sınıf oluşturulur türetildiği <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="7e082-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="7e082-163">Temel izleme işlevselliği sağlamak için geçersiz kılma <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e082-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="7e082-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> bir izleme kaydını çalışma zamanı tarafından gönderilir ve istenen şekilde işlenebilir çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="7e082-165">Aşağıdaki örnekte, tüm izleme kayıtları konsol penceresine yayan bir özel izleme katılımcı sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7e082-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="7e082-166">Aynı zamanda uygulayabileceğiniz bir <xref:System.Activities.Tracking.TrackingParticipant> izleme işlemleri nesnesini kullanarak zaman uyumsuz olarak kaydeder, `BeginTrack` ve `EndTrack` yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7e082-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="7e082-167">Belirli izleme katılımcı kullanmak için istediğiniz izlemek için aşağıdaki örnekte gösterildiği gibi iş akışı örneği ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7e082-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="7e082-168">Aşağıdaki örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> içeren etkinlik bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7e082-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="7e082-169">`ConsoleTrackingParticipant` Uzantılarını eklenir ve iş akışı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7e082-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e082-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e082-170">See Also</span></span>  
 [<span data-ttu-id="7e082-171">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="7e082-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="7e082-172">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="7e082-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
