---
title: "Windows'da izleme olayı içine olayları izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03fe4d3805d79188777404de201316441b3f8831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="93e3a-102">Windows'da izleme olayı içine olayları izleme</span><span class="sxs-lookup"><span data-stu-id="93e3a-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="93e3a-103">Bu örnek nasıl etkinleştirileceğini göstermektedir [!INCLUDE[wf](../../../../includes/wf-md.md)] bir iş akışında izleme ve hizmet izleme olayları, olay izleme için Windows (ETW) yayma.</span><span class="sxs-lookup"><span data-stu-id="93e3a-103">This sample demonstrates how to enable [!INCLUDE[wf](../../../../includes/wf-md.md)] tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="93e3a-104">Örnek iş akışı kayıtları ETW İzleme yaymak üzere ETW İzleme katılımcı kullanır (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="93e3a-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>  
  
 <span data-ttu-id="93e3a-105">Örnek iş akışında bir istek alırsa, giriş verilerinin devrik giriş değişkenine atar ve istemciye karşılıklı geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="93e3a-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="93e3a-106">Giriş verisi 0 olduğunda, bir sıfıra bölünme sıfır özel durum, işlenmemiş oluşan iptal etmek iş akışı neden olur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="93e3a-107">İzleme özelliği etkinleştirilmiş olan hata izleme kaydı hata daha sonra gidermenize yardımcı olacak ETW yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="93e3a-108">ETW İzleme katılımcı kayıtları izleme için abone olmak için izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="93e3a-109">İzleme profili Web.config dosyasında tanımlanmış ve bir yapılandırma parametresi ETW İzleme katılımcı sağlanan.</span><span class="sxs-lookup"><span data-stu-id="93e3a-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="93e3a-110">ETW İzleme katılımcı iş akışı hizmeti Web.config dosyasında yapılandırılmış ve hizmet hizmet davranışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="93e3a-111">Bu örnekte, Olay Görüntüleyicisi'ni kullanarak olay günlüğünde izleme olayları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="93e3a-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>  
  
## <a name="workflow-tracking-details"></a><span data-ttu-id="93e3a-112">İş Akışı İzleme Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="93e3a-112">Workflow Tracking Details</span></span>  
 [!INCLUDE[wf2](../../../../includes/wf2-md.md)]<span data-ttu-id="93e3a-113">bir iş akışı örneğini yürütmeyi izlemek üzere bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-113"> provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="93e3a-114">İzleme çalışma zamanı iş akışı yaşam döngüsü olayları için iş akışı etkinlikleri ve özel olaylar ilgili olayları yaymak üzere bir iş akışı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="93e3a-115">Aşağıdaki tabloda birincil bileşenleri izleme altyapısının ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-115">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="93e3a-116">Bileşen</span><span class="sxs-lookup"><span data-stu-id="93e3a-116">Component</span></span>|<span data-ttu-id="93e3a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93e3a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93e3a-118">Çalışma zamanı izleme</span><span class="sxs-lookup"><span data-stu-id="93e3a-118">Tracking runtime</span></span>|<span data-ttu-id="93e3a-119">İzleme kayıtları yayma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-119">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="93e3a-120">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="93e3a-120">Tracking participants</span></span>|<span data-ttu-id="93e3a-121">İzleme kayıtları erişir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="93e3a-122">Olay izleme için Windows (ETW) olayları olarak izleme kayıtları Yazar izleme katılımcı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-122"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="93e3a-123">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="93e3a-123">Tracking profile</span></span>|<span data-ttu-id="93e3a-124">Bir iş akışı örneğinden yayılan izleme kayıtları alt kümeleri için abone olmak izleme katılımcı sağlayan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="93e3a-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="93e3a-125">Aşağıdaki tabloda, iş akışı çalışma zamanı yayar izleme kayıtları ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-125">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="93e3a-126">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="93e3a-126">Tracking record</span></span>|<span data-ttu-id="93e3a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93e3a-127">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="93e3a-128">İş akışı örneği izleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="93e3a-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="93e3a-129">İş akışı örneği yaşam döngüsü açıklar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="93e3a-130">Örneğin, iş akışı başlatıldığında veya tamamlandıktan bir örnek kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="93e3a-131">Etkinlik durumu izleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="93e3a-131">Activity state tracking records.</span></span>|<span data-ttu-id="93e3a-132">Ayrıntılar Etkinlik yürütme.</span><span class="sxs-lookup"><span data-stu-id="93e3a-132">Details activity execution.</span></span> <span data-ttu-id="93e3a-133">Bu kayıtları bir etkinlik olduğunda zamanlanmış veya etkinlik tamamlandığında veya bir hata olduğunda atılır gibi bir iş akışı etkinlik durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="93e3a-134">Sürdürme kayıt yer işareti.</span><span class="sxs-lookup"><span data-stu-id="93e3a-134">Bookmark resumption record.</span></span>|<span data-ttu-id="93e3a-135">Bir iş akışı örneği yer işareti sürdürüldü her yayılan.</span><span class="sxs-lookup"><span data-stu-id="93e3a-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="93e3a-136">Özel İzleme kaydeder.</span><span class="sxs-lookup"><span data-stu-id="93e3a-136">Custom tracking records.</span></span>|<span data-ttu-id="93e3a-137">Bir iş akışı yazarı özel izleme kayıtları oluşturmak ve bunları içinde özel Etkinlik yayma.</span><span class="sxs-lookup"><span data-stu-id="93e3a-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="93e3a-138">Bir etkinliği başka bir etkinliğin zamanlarken bu kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-138">This record is emitted when an activity schedules another activity.</span></span>|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="93e3a-139">Bir arıza etkinliği yayıldığında, bu kayıt yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-139">This record is emitted when a fault is propagated from an activity.</span></span>|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="93e3a-140">Bir etkinliği başka bir etkinlik tarafından iptal edildiğinde bu kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-140">This record is emitted when an activity is canceled by another activity.</span></span>|  
  
 <span data-ttu-id="93e3a-141">İzleme katılımcı izleme profilleri kullanarak verilmiş izleme kayıtları bir kısmı için abone olur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="93e3a-142">İzleme profili belirli izleme kayıt türü için abone izin izleme sorgularını içerir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="93e3a-143">Profilleri izleme kod veya yapılandırma belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-143">Tracking profiles can be specified in code or in configuration.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="93e3a-144">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="93e3a-144">To use this sample</span></span>  
  
1.  <span data-ttu-id="93e3a-145">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], EtwTrackingParticipantSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-145">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EtwTrackingParticipantSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="93e3a-146">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-146">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="93e3a-147">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-147">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="93e3a-148">Varsayılan olarak, hizmet 53797 (http://localhost:53797/SampleWorkflowService.xamlx) bağlantı noktasında dinliyor.</span><span class="sxs-lookup"><span data-stu-id="93e3a-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>  
  
4.  <span data-ttu-id="93e3a-149">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="93e3a-150">WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü > \Common7\IDE\ klasör.</span><span class="sxs-lookup"><span data-stu-id="93e3a-150">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="93e3a-151">Varsayılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörüdür C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="93e3a-151">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
5.  <span data-ttu-id="93e3a-152">WCF test istemcisi seçin **Hizmet Ekle** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="93e3a-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="93e3a-153">Uç nokta adresi giriş kutusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93e3a-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="93e3a-154">Http://localhost:53797/SampleWorkflowService.xamlx varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-154">The default is http://localhost:53797/SampleWorkflowService.xamlx.</span></span>  
  
6.  <span data-ttu-id="93e3a-155">Olay Görüntüleyicisi'ni uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="93e3a-156">Olay Görüntüleyicisi'nden başlatmak Hizmeti'ni çağırmadan önce **Başlat** menüsünde, select **çalıştırmak** ve yazın `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="93e3a-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="93e3a-157">Olay günlüğü iş akışı hizmetinden gösterilen olayları izlemek için dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="93e3a-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="93e3a-158">Olay Görüntüleyicisi'ni ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="93e3a-159">Sağ **Microsoft** seçip **Görünüm** ve ardından **Analitik ve hata ayıklama günlüklerini göster** etkinleştirme Analitik ve hata ayıklama günlüklerini</span><span class="sxs-lookup"><span data-stu-id="93e3a-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>  
  
     <span data-ttu-id="93e3a-160">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
8.  <span data-ttu-id="93e3a-161">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="93e3a-162">Sağ **analitik** seçip **günlüğü etkinleştir** etkinleştirmek için **analitik** günlük.</span><span class="sxs-lookup"><span data-stu-id="93e3a-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>  
  
9. <span data-ttu-id="93e3a-163">Çift tıklatarak WCF test istemcisi kullanarak hizmeti test `GetData`.</span><span class="sxs-lookup"><span data-stu-id="93e3a-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>  
  
     <span data-ttu-id="93e3a-164">Bu açılır `GetData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93e3a-164">This opens the `GetData` method.</span></span> <span data-ttu-id="93e3a-165">İstek bir parametre kabul eder ve değeri 0, varsayılan olan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>  
  
     <span data-ttu-id="93e3a-166">Tıklatın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-166">Click **Invoke**.</span></span>  
  
10. <span data-ttu-id="93e3a-167">İş akışını gösterilen olayları gözlemektir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-167">Observe the events emitted from the workflow.</span></span>  
  
     <span data-ttu-id="93e3a-168">Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="93e3a-169">Sağ **analitik** seçip **yenileme**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-169">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="93e3a-170">İş akışı olayları Olay Görüntüleyicisi'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="93e3a-171">İş akışı yürütme olayları görüntülenir ve bunlardan birini iş akışında hata karşılık gelen işlenmeyen bir özel durum olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="93e3a-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="93e3a-172">Ayrıca, bir uyarı olayı etkinliği bir arıza atma olduğunu gösteren iş akışı etkinliğinden yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>  
  
11. <span data-ttu-id="93e3a-173">Herhangi bir hata durum 9 ve 10 veri 0 dışında bir girdi ile adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="93e3a-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>  
  
 <span data-ttu-id="93e3a-174">İzleme profili, bir iş akışı örneğinin durumu değiştiğinde, çalışma zamanı tarafından gösterilen olaylarına abone olma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="93e3a-175">İzleme gereksinimlerinize bağlı olarak çok kaba bir profili oluşturabilirsiniz, üst düzey durum değişiklikleri bir iş akışında, küçük bir kümesini için abone olur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="93e3a-176">Diğer taraftan, çıktısı yürütme daha sonra yeniden oluşturmak için zengin çok hassas bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="93e3a-177">Örnek iş akışı çalışma zamanı ETW kullanmaya gösterilen olayları gösterir `HealthMonitoring Tracking Profile`, olaylar, küçük bir kümesini yayar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="93e3a-178">Daha fazla iş akışı olayları izleme yayar farklı bir profil de adlı Web.config dosyasında sağlanan `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="93e3a-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="93e3a-179">Zaman [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] olan yüklü, boş bir ada sahip bir varsayılan profili Machine.config dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="93e3a-180">Bu profil profil adı yok veya boş profil adı belirtildiğinde davranış yapılandırma izleme ETW tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>  
  
 <span data-ttu-id="93e3a-181">Sistem durumu izleme profili izleme, iş akışı örneği kayıtları ve etkinlik hataya yayma kayıtları yayar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="93e3a-182">Bu profili, bir Web.config yapılandırma dosyası için aşağıdaki izleme profili ekleyerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="93e3a-183">Profil değiştirerek değiştirilebilir `EtwTrackingParticipant` aşağıdaki yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="93e3a-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="93e3a-184">(İsteğe bağlı) temizlemek için</span><span class="sxs-lookup"><span data-stu-id="93e3a-184">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="93e3a-185">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-185">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="93e3a-186">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="93e3a-187">Sağ **analitik** seçip **günlüğü devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-187">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="93e3a-188">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="93e3a-189">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="93e3a-189">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="93e3a-190">Seçin **temizleyin** olayları temizlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="93e3a-190">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="93e3a-191">Bilinen bir sorun</span><span class="sxs-lookup"><span data-stu-id="93e3a-191">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93e3a-192">Olay burada ETW olayları çözecek başlatılamayabilir Görüntüleyicisi'nde bilinen bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="93e3a-193">Aşağıdakine benzer bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-193">You may see an error message that looks like the following.</span></span>  
>   
>  <span data-ttu-id="93e3a-194">Olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="93e3a-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="93e3a-195">Bu olayı oluşturan bileşen, yerel bilgisayarda yüklü değil ya da yüklemesi bozuk.</span><span class="sxs-lookup"><span data-stu-id="93e3a-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="93e3a-196">Yükleme veya yerel bilgisayarda bileşen onarın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-196">You can install or repair the component on the local computer.</span></span>  
>   
>  <span data-ttu-id="93e3a-197">Bu hatayla karşılaşırsanız, Eylemler bölmesinde Yenile'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="93e3a-198">Olay şimdi düzgün bir şekilde kod çözme.</span><span class="sxs-lookup"><span data-stu-id="93e3a-198">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93e3a-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="93e3a-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93e3a-200">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="93e3a-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93e3a-201">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="93e3a-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93e3a-202">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="93e3a-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-203">See Also</span></span>  
 [<span data-ttu-id="93e3a-204">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="93e3a-204">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
