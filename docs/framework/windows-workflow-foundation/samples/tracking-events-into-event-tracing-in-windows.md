---
title: Windows'ta Olay İzleme ile Olayları İzleme
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 129b82da068251d87bd9b0ca029b7e5a1c274936
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004815"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="d5d60-102">Windows'ta Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="d5d60-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="d5d60-103">Bu örnek, Windows Workflow Foundation (WF) iş akışı hizmeti izleme etkinleştirme ve izleme olayları, olay izleme için Windows (ETW) yayma gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="d5d60-104">Örnek iş akışı ETW kayıtları izleme yaymak için ETW İzleme katılımcı kullanır (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="d5d60-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

 <span data-ttu-id="d5d60-105">Örnek iş akışında bir istek alırsa, giriş verilerinin karşıtını giriş değişkenine atar ve istemciye karşılıklı geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5d60-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="d5d60-106">Giriş verilerini 0 olduğunda sıfır özel durum ile bir bölme, işlenmemiş oluşan iptal etmek iş akışının sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="d5d60-107">Etkin izleme ile hata izleme kaydının daha sonra hata gidermenize yardımcı olacak ETW yayılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="d5d60-108">ETW İzleme katılımcı abone izleme kayıtları için bir izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="d5d60-109">İzleme profili Web.config dosyasında tanımlanır ve ETW İzleme katılımcı için bir yapılandırma parametresi sağlanan.</span><span class="sxs-lookup"><span data-stu-id="d5d60-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="d5d60-110">ETW İzleme katılımcı iş akışı hizmetinin Web.config dosyasında yapılandırılmış ve hizmeti bir hizmet davranışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="d5d60-111">Bu örnekte, Olay Görüntüleyicisi'ni kullanarak olay günlüğüne izleme olayları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="d5d60-112">İş Akışı İzleme Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="d5d60-112">Workflow Tracking Details</span></span>
 <span data-ttu-id="d5d60-113">Windows Workflow Foundation iş akışı örneği yürütülmesini izlemek için izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="d5d60-114">İzleme çalışma zamanı olaylarını, iş akışı yaşam döngüsü için iş akışı etkinlikleri ve özel olaylar ilgili olayları yaymak için bir iş akışı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5d60-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="d5d60-115">Aşağıdaki tabloda birincil izleme altyapısının bileşenleri ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-115">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="d5d60-116">Bileşen</span><span class="sxs-lookup"><span data-stu-id="d5d60-116">Component</span></span>|<span data-ttu-id="d5d60-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5d60-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d5d60-118">Çalışma zamanı izleme</span><span class="sxs-lookup"><span data-stu-id="d5d60-118">Tracking runtime</span></span>|<span data-ttu-id="d5d60-119">İzleme kayıtları yaymak için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-119">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="d5d60-120">İzleme katılımcıları</span><span class="sxs-lookup"><span data-stu-id="d5d60-120">Tracking participants</span></span>|<span data-ttu-id="d5d60-121">İzleme kayıtları erişir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="d5d60-122">izleme kayıtları için olay izleme Windows (ETW) olayları olarak yazan bir izleme katılımcı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-122">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="d5d60-123">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="d5d60-123">Tracking profile</span></span>|<span data-ttu-id="d5d60-124">Bir iş akışı örneğinden yayılan izleme kayıtları bir alt kümesi için abone olmak izleme Katılımcısı sağlayan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="d5d60-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="d5d60-125">Aşağıdaki tabloda, iş akışı çalışma zamanı yayan izleme kayıtları ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-125">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="d5d60-126">Kayıt izleme</span><span class="sxs-lookup"><span data-stu-id="d5d60-126">Tracking record</span></span>|<span data-ttu-id="d5d60-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5d60-127">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="d5d60-128">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="d5d60-129">İş akışı örneği yaşam döngüsü açıklar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="d5d60-130">Örneğin, iş akışı başlatıldığında veya tamamlanan bir örnek kaydı yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="d5d60-131">Etkinlik durumu izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-131">Activity state tracking records.</span></span>|<span data-ttu-id="d5d60-132">Etkinlik yürütme ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-132">Details activity execution.</span></span> <span data-ttu-id="d5d60-133">Bu kayıtlar, bir etkinlik olduğunda zamanlanmış etkinlik tamamlandığında veya bir hata harekete geçirildiğinde gibi bir iş akışı etkinlik durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="d5d60-134">Sürdürme kayıt yer işareti.</span><span class="sxs-lookup"><span data-stu-id="d5d60-134">Bookmark resumption record.</span></span>|<span data-ttu-id="d5d60-135">Her bir iş akışı örneği içinde yer sürdürüldü yayılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="d5d60-136">Özel izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="d5d60-136">Custom tracking records.</span></span>|<span data-ttu-id="d5d60-137">Bir iş akışı Yazar özel izleme kayıtları oluşturabilir ve bunları özel bir etkinlik içinde gösterin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="d5d60-138">Bu kayıt, bir etkinlik başka bir etkinlik zamanlarken yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-138">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="d5d60-139">Bu kayıt, bir hata etkinliği yayıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-139">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="d5d60-140">Bu kayıt, başka bir etkinlik tarafından bir etkinlik iptal edildiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-140">This record is emitted when an activity is canceled by another activity.</span></span>|

 <span data-ttu-id="d5d60-141">İzleme profilleri kullanarak yayılan izleme kayıtları bir alt kümesi için izleme katılımcı abone.</span><span class="sxs-lookup"><span data-stu-id="d5d60-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="d5d60-142">Bir izleme profili belirli izleme kayıt türü için abone izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="d5d60-143">İzleme profilleri kod veya yapılandırma belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-143">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d5d60-144">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d5d60-144">To use this sample</span></span>

1. <span data-ttu-id="d5d60-145">Visual Studio 2010 kullanarak EtwTrackingParticipantSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-145">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="d5d60-146">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-146">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="d5d60-147">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-147">To run the solution, press F5.</span></span>

     <span data-ttu-id="d5d60-148">Varsayılan olarak, hizmet bağlantı noktasını 53797 dinlediğini (http://localhost:53797/SampleWorkflowService.xamlx).</span><span class="sxs-lookup"><span data-stu-id="d5d60-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>

4. <span data-ttu-id="d5d60-149">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>

     <span data-ttu-id="d5d60-150">WCF test istemcisi (WcfTestClient.exe) bulunan \<Visual Studio 2010 yükleme klasörü > \Common7\IDE\ klasör.</span><span class="sxs-lookup"><span data-stu-id="d5d60-150">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

     <span data-ttu-id="d5d60-151">Varsayılan Visual Studio 2010 yükleme klasörü C:\Program Files\Microsoft Visual Studio 10.0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-151">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="d5d60-152">WCF test İstemcisi'nde seçin **Hizmet Ekle** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d5d60-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>

     <span data-ttu-id="d5d60-153">Uç nokta adresi giriş kutusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="d5d60-154">Varsayılan, `http://localhost:53797/SampleWorkflowService.xamlx` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-154">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="d5d60-155">Olay Görüntüleyici uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-155">Open the Event Viewer application.</span></span>

     <span data-ttu-id="d5d60-156">Hizmeti'ni çağırmadan önce Olay Görüntüleyicisi'ni Başlat **Başlat** menüsünde **çalıştırma** ve yazın `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="d5d60-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="d5d60-157">İş akışı hizmetinden yayılan olayları izlemek için olay günlüğüne dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5d60-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="d5d60-158">Olay Görüntüleyicisi'nin ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="d5d60-159">Sağ **Microsoft** seçip **görünümü** ve ardından **Analitik ve hata ayıklama günlüklerini göster** analitik etkinleştirmek ve hata ayıklama günlükleri için</span><span class="sxs-lookup"><span data-stu-id="d5d60-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

     <span data-ttu-id="d5d60-160">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="d5d60-161">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="d5d60-162">Sağ **analitik** seçip **günlüğü etkinleştir** etkinleştirmek için **analitik** günlük.</span><span class="sxs-lookup"><span data-stu-id="d5d60-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="d5d60-163">Çift tıklayarak WCF test İstemcisi'ı kullanarak hizmeti test `GetData`.</span><span class="sxs-lookup"><span data-stu-id="d5d60-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

     <span data-ttu-id="d5d60-164">Bu açılır `GetData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5d60-164">This opens the `GetData` method.</span></span> <span data-ttu-id="d5d60-165">İstek bir parametreyi kabul eden ve varsayılan değer 0, olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="d5d60-166">Tıklayın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-166">Click **Invoke**.</span></span>

10. <span data-ttu-id="d5d60-167">Yayılan olayları gözlemektir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-167">Observe the events emitted from the workflow.</span></span>

     <span data-ttu-id="d5d60-168">Olay Görüntüleyicisi'ne geçin ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="d5d60-169">Sağ **analitik** seçip **Yenile**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-169">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="d5d60-170">İş akışı olayları Olay Görüntüleyicisi'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="d5d60-171">İş akışı yürütme olayları görüntülenir ve bunlardan birinin iş akışı hataya karşılık gelen işlenmeyen bir özel durum olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="d5d60-172">Ayrıca, bir uyarı olayı etkinliği bir hata atma olduğunu gösteren iş akışı etkinliklerine ilişkin yayılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="d5d60-173">Adım 9 ve 10 veri 0 dışında bir giriş ile hata oluşturulmayacak şekilde yineleyin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

 <span data-ttu-id="d5d60-174">İzleme profilleri, bir iş akışı örneği durumu değiştiğinde yayılan çalışma zamanı tarafından iş olaylarına abone olma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="d5d60-175">İzleme gereksinimlerinize bağlı olarak çok kaba bir profili oluşturabilmeniz için bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="d5d60-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d5d60-176">Öte yandan, çıktısı yürütme daha sonra yeniden oluşturmak için zengin çok hassas bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5d60-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="d5d60-177">Örnek iş akışı çalışma zamanını şuradan ETW kullanmaya yayılan olayları gösterir `HealthMonitoring Tracking Profile`, olayları küçük bir dizi yayar.</span><span class="sxs-lookup"><span data-stu-id="d5d60-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="d5d60-178">Daha fazla iş akışı olayları izleme yayan farklı bir profil de adlı Web.config sağlanır `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="d5d60-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="d5d60-179">Zaman [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] olan yüklü, boş bir ada sahip bir varsayılan profili Machine.config dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="d5d60-180">Bu profil davranışını yapılandırma profili adı yok ya da boş bir profil adı belirtildiğinde, izleme, ETW tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5d60-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

 <span data-ttu-id="d5d60-181">Sistem durumu izleme profili izleme, iş akışı örneği kayıtları ve etkinlik hata yayma kayıtları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5d60-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="d5d60-182">Bu profil, aşağıdaki izleme profili Web.config yapılandırma dosyasına ekleyerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5d60-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

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

 <span data-ttu-id="d5d60-183">Profil değiştirerek değiştirilebilir `EtwTrackingParticipant` aşağıdaki yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d5d60-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="d5d60-184">(İsteğe bağlı) temizlemek için</span><span class="sxs-lookup"><span data-stu-id="d5d60-184">To clean up (Optional)</span></span>

1. <span data-ttu-id="d5d60-185">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-185">Open Event Viewer.</span></span>

2. <span data-ttu-id="d5d60-186">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="d5d60-187">Sağ **analitik** seçip **devre dışı günlük**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-187">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="d5d60-188">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="d5d60-189">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="d5d60-189">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="d5d60-190">Seçin **Temizle** olayları silmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d5d60-190">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="d5d60-191">Bilinen sorun</span><span class="sxs-lookup"><span data-stu-id="d5d60-191">Known Issue</span></span>

> [!NOTE]
>  <span data-ttu-id="d5d60-192">Burada ETW olaylarının kodunu çözmek için çalışmayabilir Olay Görüntüleyicisi'nde bilinen bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="d5d60-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="d5d60-193">Aşağıdakine benzer bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5d60-193">You may see an error message that looks like the following.</span></span>
>
>  <span data-ttu-id="d5d60-194">Olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="d5d60-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="d5d60-195">Bu olayı oluşturan bileşen, yerel bilgisayarınızda yüklü değil veya yüklemenin bozuk.</span><span class="sxs-lookup"><span data-stu-id="d5d60-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="d5d60-196">Yüklediğinizde veya yerel bilgisayarda bileşen onarın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-196">You can install or repair the component on the local computer.</span></span>
>
>  <span data-ttu-id="d5d60-197">Bu hatayla karşılaşırsanız, yenileme Eylemler bölmesinde'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5d60-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="d5d60-198">Olay artık düzgün bir şekilde kod çözme.</span><span class="sxs-lookup"><span data-stu-id="d5d60-198">The event should now decode properly.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d5d60-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d5d60-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d5d60-200">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d5d60-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5d60-201">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d5d60-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5d60-202">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5d60-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="d5d60-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d60-203">See also</span></span>

- [<span data-ttu-id="d5d60-204">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5d60-204">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
