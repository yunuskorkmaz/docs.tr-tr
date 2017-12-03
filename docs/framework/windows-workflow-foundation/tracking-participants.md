---
title: "Katılımcıların izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8159be53ed202be5e0338cbf671122661f0d814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-participants"></a><span data-ttu-id="06dda-102">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="06dda-102">Tracking Participants</span></span>
<span data-ttu-id="06dda-103">İzleme katılımcıları erişmek bir iş akışı Geliştirici izin genişletilebilirlik noktaları olan <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> nesneleri ve bunları işlem.</span><span class="sxs-lookup"><span data-stu-id="06dda-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="06dda-104">Olay izleme için Windows (ETW) olayları olarak izleme kayıtları yazan standart izleme katılımcı içerir.</span><span class="sxs-lookup"><span data-stu-id="06dda-104"> includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="06dda-105">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06dda-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="06dda-106">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="06dda-106">Tracking Participants</span></span>  
 <span data-ttu-id="06dda-107">İzleme altyapı, katılımcı kayıtların bir alt kümesini için abone olabilirsiniz gibi bir filtre uygulamayı giden izleme kayıtlarda sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dda-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="06dda-108">Bir filtre uygulamak için bir izleme profili mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="06dda-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="06dda-109">içinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] izleme kayıtları ETW oturumuna Yazar izleme katılımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dda-109"> in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="06dda-110">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="06dda-111">Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dda-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="06dda-112">SDK'sı örneği ETW tabanlı izleme, ETW tabanlı izleme katılımcı kullanılarak WF izlemeyle hakkında bilgi edinmek için iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="06dda-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="06dda-113">ETW İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="06dda-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="06dda-114">bir ETW İzleme izleme kayıtları ETW oturumuna yazan Katılımcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="06dda-114"> includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="06dda-115">Bu, uygulamanızın performansı veya sunucunun işleme için en az etkiyle çok verimli bir şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="06dda-116">Standart ETW İzleme katılımcı kullanmanın avantajı, aldığı izleme kayıtları başka bir uygulama ile görüntülenebilir ve Windows Olay Görüntüleyicisi'nde sistem günlüklerini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="06dda-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="06dda-117">Standart ETW İzleme katılımcı Web.config dosyasında aşağıdaki örnekte gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="06dda-118">Varsa bir `trackingProfile` adı belirtilmezse, gibi yalnızca `<etwTracking/>` veya `<etwTracking profileName=""/>`, ardından varsayılan profil yüklenmiş izleme [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Machine.config dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="06dda-119">Machine.config dosyasının varsayılan profili izleme, iş akışı örneği kayıtlarını ve hataları için abone olur.</span><span class="sxs-lookup"><span data-stu-id="06dda-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="06dda-120">ETW ETW oturum sağlayıcı kimliğini üzerinden yazılır</span><span class="sxs-lookup"><span data-stu-id="06dda-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="06dda-121">Sağlayıcı için ETW İzleme yazma katılımcı kullanır izleme ETW kayıt kimliği, Web.config dosyasının tanılama bölümünde tanımlanır (altında `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="06dda-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="06dda-122">Varsayılan olarak, bir belirtilmemiş olduğunda ETW İzleme katılımcı aşağıdaki örnekte gösterildiği gibi bir varsayılan sağlayıcı kimliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="06dda-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="06dda-123">Aşağıdaki çizimde ETW İzleme katılımcı verilerine izleme akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06dda-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="06dda-124">İzleme verilerini ETW oturum ulaştığında, çeşitli yollarla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="06dda-125">Bu olaylar erişmek için en kullanışlı yollarından biri, Olay Görüntüleyicisi'ni günlüklerine ve izlemelere uygulamaları ve hizmetleri görüntülemek için kullanılan genel bir Windows aracı aracılığıyladır.</span><span class="sxs-lookup"><span data-stu-id="06dda-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 <span data-ttu-id="06dda-126">![İzleme ve ETW İzleme Sağlayıcısı akışını](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span><span class="sxs-lookup"><span data-stu-id="06dda-126">![The flow of Tracking and ETW Tracking Provider](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span></span>  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="06dda-127">Katılımcı olay verilerini izleme</span><span class="sxs-lookup"><span data-stu-id="06dda-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="06dda-128">İzleme katılımcı ETW oturum izleme kaydı başına bir olay biçiminde izlenen olay verilerini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="06dda-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="06dda-129">Bir olay kimliği 100 199 ile aralığında kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="06dda-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="06dda-130">İzleme olay tanımları için bkz: kayıtları izleme katılımcı tarafından gösterilen [olayları başvuru izleme](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) konu.</span><span class="sxs-lookup"><span data-stu-id="06dda-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="06dda-131">ETW olay boyutu ETW arabellek boyutuyla sınırlıdır veya ETW olay en fazla yük tarafından hangi küçük değerdir.</span><span class="sxs-lookup"><span data-stu-id="06dda-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="06dda-132">Olay boyutu ya da bu ETW sınırları aşarsa, olay kesilir ve içeriği rasgele bir şekilde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="06dda-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="06dda-133">Değişkenleri, bağımsız değişken, ek açıklamalar ve özel verileri seçmeli olarak kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="06dda-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="06dda-134">Kesilmesi durumunda, bunların tümü olay boyutu ETW sınırının aşılmasına neden değer bağımsız olarak kısaltılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="06dda-135">Kaldırılan verileri ile değiştirilir `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="06dda-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="06dda-136">Karmaşık türleri değişkenleri, bağımsız ve özel veri öğeleri ETW olayını kullanarak kaydı serileştirilir [NetDataContractSerializer sınıfı](http://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="06dda-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](http://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="06dda-137">Bu sınıf CLR türünün serileştirilmiş XML akışı bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="06dda-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="06dda-138">ETW sınırları nedeniyle yük verilerinin kesilmesi ETW oturumuna gönderilen yinelenen izleme kayıtları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="06dda-139">Birden fazla oturum olaylarını dinleme ve oturumları olayları için farklı yükü sınırları varsa bu durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="06dda-140">Alt sınırı ile oturumu için olay kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="06dda-141">ETW İzleme katılımcı olaylarını dinleme oturum sayısını bilgisi yok; bir olay bir oturum sonra bir kez olay gönderme ETW katılımcı yeniden deneme kesilirse.</span><span class="sxs-lookup"><span data-stu-id="06dda-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="06dda-142">Bu durumda daha büyük bir yükü boyutu kabul edecek şekilde yapılandırılmış oturum olay iki kez (kesilmiş olmayan ve kesilmiş olay) alır.</span><span class="sxs-lookup"><span data-stu-id="06dda-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="06dda-143">Çoğaltma ile aynı arabellek boyutu sınırları tüm ETW oturumları yapılandırarak engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="06dda-144">Olay Görüntüleyicisi'ni bir ETW Katılımcısı veri izlemeyi erişme</span><span class="sxs-lookup"><span data-stu-id="06dda-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="06dda-145">ETW oturumuna ETW İzleme katılımcı tarafından yazılan olaylar (varsayılan sağlayıcı kimliği kullanırken) Olay Görüntüleyicisi'ni erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="06dda-146">Bu iş akışı tarafından gösterilen kayıtları izleme hızlı bir şekilde görüntülemek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dda-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06dda-147">Bir ETW oturum kullanım olay kimlikleri 100 199 ile aralığında yayılan kayıt olayları izleme.</span><span class="sxs-lookup"><span data-stu-id="06dda-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="06dda-148">Olay Görüntüleyicisi'nde izleme kayıtları görüntüleme etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="06dda-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1.  <span data-ttu-id="06dda-149">Olay Görüntüleyicisi'ni (EVENTVWR. Başlat EXE)</span><span class="sxs-lookup"><span data-stu-id="06dda-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2.  <span data-ttu-id="06dda-150">Seçin **Olay Görüntüleyicisi'ni, uygulama ve hizmet günlükleri, Microsoft, Windows, uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="06dda-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3.  <span data-ttu-id="06dda-151">Sağ tıklayın ve emin **görünümü, Analitik ve hata ayıklama günlüklerini göster** seçilir.</span><span class="sxs-lookup"><span data-stu-id="06dda-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="06dda-152">Aksi durumda, yanındaki onay işareti göründüğü şekilde seçin.</span><span class="sxs-lookup"><span data-stu-id="06dda-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="06dda-153">Bu görüntüler **analitik**, **Perf**, ve **hata ayıklama** günlükleri.</span><span class="sxs-lookup"><span data-stu-id="06dda-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4.  <span data-ttu-id="06dda-154">Sağ **analitik** oturum açın ve ardından **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="06dda-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="06dda-155">Günlük %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="06dda-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="06dda-156">Özel İzleme katılımcı</span><span class="sxs-lookup"><span data-stu-id="06dda-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="06dda-157">İzleme katılımcı API izleme kayıtları iş akışı çalışma zamanı tarafından gösterilen işlemek için Özel mantık içerebilir bir kullanıcı tarafından sağlanan izleme katılımcı ile izleme çalışma zamanı uzantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="06dda-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="06dda-158">Özel İzleme katılımcı yazmak için geliştirici uygulamalıdır `Track` yöntemi <xref:System.Activities.Tracking.TrackingParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06dda-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="06dda-159">Bir izleme kaydı iş akışı çalışma zamanı tarafından gösterilen zaman bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="06dda-160">İzleme katılımcıları türetilen <xref:System.Activities.Tracking.TrackingParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06dda-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="06dda-161">Sistem tarafından sağlanan <xref:System.Activities.Tracking.EtwTrackingParticipant> alınan her izleme kaydı için bir olay izleme için Windows (ETW) olayı yayar.</span><span class="sxs-lookup"><span data-stu-id="06dda-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="06dda-162">Özel İzleme katılımcı oluşturmak için bir sınıf oluşturulur türetilen <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="06dda-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="06dda-163">Temel izleme işlevselliği sağlamak için geçersiz kılma <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="06dda-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="06dda-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A>bir izleme kaydını çalışma zamanı tarafından gönderilen ve istenen biçimde işlenen olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="06dda-165">Aşağıdaki örnekte, bir özel izleme katılımcı sınıf konsol penceresine tüm izleme kayıtları gösterdiği tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="06dda-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="06dda-166">Ayrıca uygulayabileceğiniz bir <xref:System.Activities.Tracking.TrackingParticipant> izleme işlemleri nesne kayıtları zaman uyumsuz olarak kullanarak kendi `BeginTrack` ve `EndTrack` yöntemleri</span><span class="sxs-lookup"><span data-stu-id="06dda-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="06dda-167">Belirli izleme katılımcı kullanmak için aşağıdaki örnekte gösterildiği gibi izlemek için istediğiniz iş akışı örneği ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="06dda-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="06dda-168">Aşağıdaki örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> içeren etkinliği bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="06dda-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="06dda-169">`ConsoleTrackingParticipant` Uzantılara eklenir ve iş akışı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="06dda-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06dda-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06dda-170">See Also</span></span>  
 [<span data-ttu-id="06dda-171">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="06dda-171">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="06dda-172">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="06dda-172">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
