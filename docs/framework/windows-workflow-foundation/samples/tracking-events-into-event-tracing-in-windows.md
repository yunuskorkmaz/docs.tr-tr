---
title: Windows'ta Olay İzleme ile Olayları İzleme
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 4350287aedae73a7ca9556de7ae3f597950e32ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549630"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="078ad-102">Windows'ta Olay İzleme ile Olayları İzleme</span><span class="sxs-lookup"><span data-stu-id="078ad-102">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="078ad-103">Bu örnek, bir iş akışı hizmetinde Windows Workflow Foundation (WF) izlemenin nasıl etkinleştirileceğini ve izleme olaylarının Windows için olay Izleme 'ye (ETW) nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="078ad-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="078ad-104">İş akışı izleme kayıtlarını ETW 'ye yaymak için örnek ETW izleme katılımcısını () kullanır <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="078ad-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="078ad-105">Örnekteki iş akışı bir istek alır, girdi verilerinin tersini giriş değişkenine atar ve istemciye geri dönüş döndürür.</span><span class="sxs-lookup"><span data-stu-id="078ad-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="078ad-106">Giriş verileri 0 olduğunda, bu, iş akışının iptal edilmesine neden olan işlenmemiş bir sıfıra bölme özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="078ad-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="078ad-107">İzleme etkinken, hata izleme kaydı ETW 'ye yayılır ve bu, daha sonra hatanın giderilmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="078ad-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="078ad-108">ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="078ad-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="078ad-109">İzleme profili Web.config dosyasında tanımlanır ve ETW izleme katılımcısına bir yapılandırma parametresi olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="078ad-110">ETW izleme katılımcısı, iş akışı hizmetinin Web.config dosyasında yapılandırılır ve hizmet olarak hizmet davranışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="078ad-111">Bu örnekte, Olay Görüntüleyicisi kullanarak olay günlüğündeki izleme olaylarını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ad-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="078ad-112">İş akışı Izleme ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="078ad-112">Workflow Tracking Details</span></span>

<span data-ttu-id="078ad-113">Windows Workflow Foundation, bir iş akışı örneğinin yürütülmesini izlemek için bir izleme altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="078ad-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="078ad-114">İzleme çalışma zamanı, iş akışı kullanım ömrü, iş akışı etkinliklerinin olayları ve özel etkinliklerle ilgili olayları göstermek için bir iş akışı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="078ad-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="078ad-115">Aşağıdaki tabloda izleme altyapısının birincil bileşenleri ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="078ad-115">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="078ad-116">Bileşen</span><span class="sxs-lookup"><span data-stu-id="078ad-116">Component</span></span>|<span data-ttu-id="078ad-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="078ad-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="078ad-118">Çalışma zamanını izleme</span><span class="sxs-lookup"><span data-stu-id="078ad-118">Tracking runtime</span></span>|<span data-ttu-id="078ad-119">İzleme kayıtlarını yaymakta olan altyapıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="078ad-119">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="078ad-120">Katılımcıları izleme</span><span class="sxs-lookup"><span data-stu-id="078ad-120">Tracking participants</span></span>|<span data-ttu-id="078ad-121">İzleme kayıtlarına erişir.</span><span class="sxs-lookup"><span data-stu-id="078ad-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="078ad-122">izleme kayıtlarını Windows için olay Izleme (ETW) olayları olarak yazan bir izleme katılımcısına sahip olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="078ad-122">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="078ad-123">İzleme profili</span><span class="sxs-lookup"><span data-stu-id="078ad-123">Tracking profile</span></span>|<span data-ttu-id="078ad-124">Bir iş akışı örneğinden yayılan izleme kayıtlarının bir alt kümesi için bir izleme katılımcısının abone olmasına izin veren bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="078ad-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="078ad-125">Aşağıdaki tabloda iş akışı çalışma zamanının yaydığı izleme kayıtlarının ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="078ad-125">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="078ad-126">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="078ad-126">Tracking record</span></span>|<span data-ttu-id="078ad-127">Description</span><span class="sxs-lookup"><span data-stu-id="078ad-127">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="078ad-128">İş akışı örneği izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="078ad-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="078ad-129">İş akışı örneğinin yaşam döngüsünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="078ad-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="078ad-130">Örneğin, iş akışı başladığında veya tamamlandığında bir örnek kayıt yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="078ad-131">Etkinlik durumu izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="078ad-131">Activity state tracking records.</span></span>|<span data-ttu-id="078ad-132">Ayrıntıları etkinlik yürütmesi.</span><span class="sxs-lookup"><span data-stu-id="078ad-132">Details activity execution.</span></span> <span data-ttu-id="078ad-133">Bu kayıtlar, bir etkinliğin zamanlandığı veya etkinliğin ne zaman tamamlandığı ya da bir hata oluşturulduğu zaman gibi bir iş akışı etkinliğinin durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="078ad-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="078ad-134">Bookmark sürdürme kaydı.</span><span class="sxs-lookup"><span data-stu-id="078ad-134">Bookmark resumption record.</span></span>|<span data-ttu-id="078ad-135">Bir iş akışı örneği içindeki bir yer işareti kaldığı zaman yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="078ad-136">Özel izleme kayıtları.</span><span class="sxs-lookup"><span data-stu-id="078ad-136">Custom tracking records.</span></span>|<span data-ttu-id="078ad-137">Bir iş akışı yazarı özel izleme kayıtları oluşturabilir ve bunları özel etkinlik içinde yayabilir.</span><span class="sxs-lookup"><span data-stu-id="078ad-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="078ad-138">Bir etkinlik başka bir etkinliği zamanlıyor ise bu kayıt yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-138">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="078ad-139">Bu kayıt, bir etkinliğin bir hata yayıldığında yayılır.</span><span class="sxs-lookup"><span data-stu-id="078ad-139">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="078ad-140">Bu kayıt, bir etkinlik başka bir etkinlik tarafından iptal edildiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-140">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="078ad-141">İzleme, izleme profilleri kullanılarak, yayılan izleme kayıtlarının bir alt kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="078ad-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="078ad-142">Bir izleme profili, belirli bir izleme kayıt türü için abone 'e izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="078ad-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="078ad-143">İzleme profilleri kodda veya yapılandırmada belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="078ad-143">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="078ad-144">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="078ad-144">To use this sample</span></span>

1. <span data-ttu-id="078ad-145">Visual Studio 2010 kullanarak EtwTrackingParticipantSample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="078ad-145">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="078ad-146">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="078ad-146">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="078ad-147">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="078ad-147">To run the solution, press F5.</span></span>

    <span data-ttu-id="078ad-148">Varsayılan olarak, hizmet 53797 () numaralı bağlantı noktasını dinler `http://localhost:53797/SampleWorkflowService.xamlx` .</span><span class="sxs-lookup"><span data-stu-id="078ad-148">By default, the service is listening on port 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`).</span></span>

4. <span data-ttu-id="078ad-149">Dosya Gezgini 'ni kullanarak WCF test istemcisini açın.</span><span class="sxs-lookup"><span data-stu-id="078ad-149">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="078ad-150">WCF Test istemcisi (WcfTestClient.exe) \<Visual Studio 2010 installation folder> \Common7\IDE\ klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="078ad-150">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="078ad-151">Varsayılan Visual Studio 2010 yükleme klasörü C:\Program Files\Microsoft Visual Studio 10,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="078ad-151">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="078ad-152">WCF test istemcisinde **Dosya** menüsünden **Hizmet Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="078ad-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="078ad-153">Giriş kutusuna uç nokta adresini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="078ad-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="078ad-154">Varsayılan değer: `http://localhost:53797/SampleWorkflowService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="078ad-154">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="078ad-155">Olay Görüntüleyicisi uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="078ad-155">Open the Event Viewer application.</span></span>

    <span data-ttu-id="078ad-156">Hizmeti çağırmadan önce, **Başlat** menüsünden Olay Görüntüleyicisi başlatın, **Çalıştır** ' ı seçin ve yazın `eventvwr.exe` .</span><span class="sxs-lookup"><span data-stu-id="078ad-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="078ad-157">Olay günlüğünün, iş akışı hizmetinden yayılan izleme olaylarını dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="078ad-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="078ad-158">Olay Görüntüleyicisi ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmet günlükleri**ve **Microsoft**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="078ad-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="078ad-159">Analitik ve hata ayıklama günlüklerini etkinleştirmek için **Microsoft** 'a sağ tıklayın ve **Görünüm** ' ü seçin ve ardından **analitik ve hata ayıklama günlüklerini göster**</span><span class="sxs-lookup"><span data-stu-id="078ad-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="078ad-160">**Analitik ve hata ayıklama günlüklerini göster** seçeneğinin işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="078ad-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="078ad-161">Olay Görüntüleyicisi 'daki ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="078ad-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="078ad-162">Analitik günlüğü etkinleştirmek için analiz ' e **sağ tıklayın ve** **günlüğü etkinleştir** ' i seçin. **Analytic**</span><span class="sxs-lookup"><span data-stu-id="078ad-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="078ad-163">Hizmeti çift tıklayarak WCF test istemcisini kullanarak test edin `GetData` .</span><span class="sxs-lookup"><span data-stu-id="078ad-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="078ad-164">Bu, `GetData` yöntemini açar.</span><span class="sxs-lookup"><span data-stu-id="078ad-164">This opens the `GetData` method.</span></span> <span data-ttu-id="078ad-165">İstek bir parametre kabul eder ve değerin varsayılan değer olan 0 olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="078ad-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="078ad-166">**Çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="078ad-166">Click **Invoke**.</span></span>

10. <span data-ttu-id="078ad-167">İş akışından yayılan olayları gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="078ad-167">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="078ad-168">Olay Görüntüleyicisi dönün ve **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="078ad-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="078ad-169">**Analitik** ' e sağ tıklayın ve **Yenile**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="078ad-169">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="078ad-170">İş akışı olayları Olay Görüntüleyicisi 'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="078ad-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="078ad-171">İş akışı yürütme olaylarının görüntülendiğini ve bunlardan birinin iş akışındaki hataya karşılık gelen işlenmemiş bir özel durum olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="078ad-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="078ad-172">Ayrıca, etkinliğin bir hata yaptığını gösteren bir uyarı olayı iş akışı etkinliğinden yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="078ad-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="078ad-173">9 ve 10 arasındaki adımları 0 dışında bir veri girişi ile tekrarlayın, böylece herhangi bir hata oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="078ad-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="078ad-174">İzleme profilleri, iş akışı örneği durumu değiştiğinde çalışma zamanı tarafından yayılan olaylara abone olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="078ad-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="078ad-175">İzleme gereksinimlerinize bağlı olarak, bir iş akışında küçük bir üst düzey durum değişikliği kümesine abone olan çok kaba bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ad-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="078ad-176">Öte yandan, çıkış daha sonra yürütmeyi yeniden oluşturmak için yeterince zengin olan çok kesin bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ad-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="078ad-177">Örnek, iş akışı çalışma zamanından, `HealthMonitoring Tracking Profile` küçük bir olay kümesi sunan KULLANıLARAK ETW 'ye yayılan olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="078ad-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="078ad-178">Adlı Web.config daha fazla iş akışı izleme olayı sağlayan farklı bir profil de sağlanır `Troubleshooting Tracking Profile` .</span><span class="sxs-lookup"><span data-stu-id="078ad-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="078ad-179">[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]Yüklendiğinde, Machine.config dosyasında boş bir ada sahip bir varsayılan profil yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="078ad-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="078ad-180">Bu profil, hiçbir profil adı veya boş profil adı belirtilmediğinde ETW izleme davranışı yapılandırması tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="078ad-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="078ad-181">Sistem durumu izleme izleme profili, iş akışı örneği kayıtları ve etkinlik hatası yayma kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="078ad-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="078ad-182">Bu profil, bir Web.config yapılandırma dosyasına aşağıdaki izleme profili eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="078ad-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
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

 <span data-ttu-id="078ad-183">Profil, `EtwTrackingParticipant` yapılandırma değiştirilerek aşağıdaki şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="078ad-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="078ad-184">Temizlemek için (Isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="078ad-184">To clean up (Optional)</span></span>

1. <span data-ttu-id="078ad-185">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="078ad-185">Open Event Viewer.</span></span>

2. <span data-ttu-id="078ad-186">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="078ad-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="078ad-187">**Analitik** öğesine sağ tıklayın ve **günlüğü devre dışı bırak**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="078ad-187">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="078ad-188">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="078ad-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="078ad-189">**Analitik** öğesine sağ tıklayın ve **Günlüğü Temizle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="078ad-189">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="078ad-190">Olayları temizlemek için **Temizle** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="078ad-190">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="078ad-191">Bilinen sorun</span><span class="sxs-lookup"><span data-stu-id="078ad-191">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="078ad-192">Olay Görüntüleyicisi içinde, ETW olaylarının kodunu çözemediği bilinen bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="078ad-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="078ad-193">Aşağıdakine benzer bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ad-193">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="078ad-194">\<id>Microsoft-Windows-Application Server-Applications kaynağından olay kimliği açıklaması bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="078ad-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="078ad-195">Bu olayı başlatan bileşen yerel bilgisayarınızda yüklü değil veya yükleme bozuk.</span><span class="sxs-lookup"><span data-stu-id="078ad-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="078ad-196">Bileşeni yerel bilgisayara yükleyebilir veya onarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="078ad-196">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="078ad-197">Bu hatayla karşılaşırsanız, Eylemler bölmesinde Yenile ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="078ad-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="078ad-198">Olay artık düzgün şekilde kod çözmelidir.</span><span class="sxs-lookup"><span data-stu-id="078ad-198">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="078ad-199">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="078ad-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="078ad-200">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="078ad-200">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="078ad-201">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="078ad-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="078ad-202">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="078ad-202">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="078ad-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="078ad-203">See also</span></span>

- <span data-ttu-id="078ad-204">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="078ad-204">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
