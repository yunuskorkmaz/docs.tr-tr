---
title: İş Akışı için İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 5ec94d6b8e58012d0c5c8ca8593c3cef81cd9ec3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248218"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="48da4-102">İş Akışı için İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48da4-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="48da4-103">İş akışı üç şekilde yürütülebilir:</span><span class="sxs-lookup"><span data-stu-id="48da4-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="48da4-104">Barındırılan<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="48da4-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="48da4-105">Bir olarak yürütülür<xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="48da4-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="48da4-106">Doğrudan kullanılarak yürütülür<xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="48da4-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="48da4-107">İş akışı barındırma seçeneğine bağlı olarak, bir izleme katılımcısı kod veya yapılandırma dosyası aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="48da4-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="48da4-108">Bu konu, bir izleme katılımcısı ve bir <xref:System.Activities.WorkflowApplication> <xref:System.ServiceModel.Activities.WorkflowServiceHost>,'ye ekleyerek izlemenin nasıl <xref:System.Activities.WorkflowInvoker>yapılandırıldığı ve kullanırken izlemeyi nasıl etkinleştireceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="48da4-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="48da4-109">İş Akışı Uygulama Takibini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48da4-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="48da4-110">İş akışı <xref:System.Activities.WorkflowApplication> sınıfı kullanarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="48da4-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="48da4-111">Bu konu, iş akışı ana [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bilgisayara bir izleme katılımcısı <xref:System.Activities.WorkflowApplication> ekleyerek bir iş akışı uygulaması için izlemenin nasıl yapılandırıldığı gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="48da4-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="48da4-112">Bu durumda, iş akışı bir iş akışı uygulaması olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="48da4-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="48da4-113">İş akışı <xref:System.Activities.WorkflowApplication> uygulamasını, sınıfı kullanarak kendi kendine barındırılan bir .exe dosyası olan kod (yapılandırma dosyası kullanmak yerine) aracılığıyla yapılandırAbilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48da4-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="48da4-114">İzleme <xref:System.Activities.WorkflowApplication> katılımcısı, örneğin uzantısı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="48da4-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="48da4-115">Bu, İş Akışı <xref:System.Activities.Tracking.TrackingParticipant> Uygulaması örneği için uzantılar koleksiyonuna eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="48da4-116">İş akışı uygulaması için, davranış <xref:System.Activities.Tracking.EtwTrackingParticipant> uzantısını aşağıdaki kodda gösterildiği gibi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48da4-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="48da4-117">İş Akışı Hizmeti Takibini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48da4-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="48da4-118">İş <xref:System.ServiceModel.Activities.WorkflowServiceHost> akışı, hizmet ana bilgisayarda barındırıldığında WCF hizmeti olarak ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="48da4-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="48da4-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>iş akışı tabanlı bir hizmet için özel bir .NET ServiceHost uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="48da4-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="48da4-120">Bu bölümde, 'de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>çalışan bir iş akışı hizmeti için izlemenin nasıl yapılandırılabildiğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="48da4-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="48da4-121">Bir hizmet davranışı belirterek veya hizmet barındırıcı için <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyona izlemeye özgü bir davranış ekleyerek Web.config dosyası (Web barındırılan bir hizmet için) veya App.config dosyası (konsol uygulaması gibi tek başına bir uygulamada barındırılan bir hizmet için) aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="48da4-122">Barındırılan bir iş <xref:System.ServiceModel.WorkflowServiceHost>akışı hizmeti <xref:System.Activities.Tracking.EtwTrackingParticipant> için, `behavior` aşağıdaki örnekte gösterildiği gibi, yapılandırma dosyasında <> öğesini kullanarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48da4-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="48da4-123">Alternatif olarak, barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>iş akışı <xref:System.Activities.Tracking.EtwTrackingParticipant> hizmeti için, davranış uzantısını kod aracılığıyla ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48da4-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="48da4-124">Özel bir izleme katılımcısı eklemek için yeni bir <xref:System.ServiceModel.ServiceHost> davranış uzantısı oluşturun ve aşağıdaki örnek kodda gösterildiği gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="48da4-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="48da4-125">Özel bir izleme katılımcısı ekleyen özel bir davranış öğesinin nasıl oluşturulabildiğini gösteren örnek kodu görüntülemek istiyorsanız, [İzleme](./samples/tracking.md) örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="48da4-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

<span data-ttu-id="48da4-126">İzleme katılımcısı, davranışın bir uzantısı olarak iş akışı hizmet ana bilgisayara eklenir.</span><span class="sxs-lookup"><span data-stu-id="48da4-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="48da4-127">Aşağıdaki örnek kod, yapılandırma dosyasından izleme profilinin nasıl okunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="48da4-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

<span data-ttu-id="48da4-128">Bu örnek kod, iş akışı ana bilgisayara izleme profilinin nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="48da4-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> <span data-ttu-id="48da4-129">İzleme profilleri hakkında daha fazla bilgi için [İzleme Profilleri'ne](tracking-profiles.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="48da4-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="48da4-130">WorkflowInvoker kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48da4-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="48da4-131">Kullanılarak <xref:System.Activities.WorkflowInvoker>yürütülen bir iş akışı için izlemeyi yapılandırmak için, <xref:System.Activities.WorkflowInvoker> izleme sağlayıcısını bir örneğin uzantısı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="48da4-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="48da4-132">Aşağıdaki kod örneği [Özel İzleme](./samples/custom-tracking.md) örneğindendir.</span><span class="sxs-lookup"><span data-stu-id="48da4-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="48da4-133">Olay Görüntüleyici'de izleme kayıtlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="48da4-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="48da4-134">WF yürütülmesini takip ederken görüntülemek için özel ilgi çekici iki Olay Görüntüleyen günlüğü vardır - Analytic günlüğü ve Hata Ayıklama günlüğü.</span><span class="sxs-lookup"><span data-stu-id="48da4-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="48da4-135">Her ikisi de Microsoft&#124;Windows&#124;Application Server-Applications düğümü altında bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48da4-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="48da4-136">Bu bölümdeki günlükler, tüm sistemi etkileyen olaylar yerine tek bir uygulamadan gelen olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="48da4-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="48da4-137">Hata ayıklama izleme olayları Hata Ayıklama Günlüğü'ne yazılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="48da4-138">Olay Görüntüleyicisi'nde WF hata ayıklama olayları toplamak için Hata Ayıklama Günlüğü'ne olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48da4-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="48da4-139">Olay Görüntüleyicisi'ni açmak için **Başlat'ı**ve ardından **Çalıştır'ı tıklatın.**</span><span class="sxs-lookup"><span data-stu-id="48da4-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="48da4-140">Çalıştır iletişim kutusunda, `eventvwr`'.</span><span class="sxs-lookup"><span data-stu-id="48da4-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="48da4-141">Olay Görüntüleyicisi iletişim kutusunda, **Uygulamalar ve Hizmetler Günlükleri** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="48da4-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="48da4-142">**Microsoft,** **Windows**ve **Application Server-Applications** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="48da4-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="48da4-143">**Application Server-Applications** düğümünün altındaki **Hata Ayıklama** düğümüne sağ tıklayın ve **Günlük'u etkinleştir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="48da4-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="48da4-144">İzleme olayları oluşturmak için izleme etkinleştirilmiş uygulamanızı yürütün.</span><span class="sxs-lookup"><span data-stu-id="48da4-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="48da4-145">**Hata Ayıklama** düğümüne sağ tıklayın ve **Yenile'yi seçin.**</span><span class="sxs-lookup"><span data-stu-id="48da4-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="48da4-146">Olayları izleme, orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48da4-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="48da4-147">WF 4, izleme kayıtlarını bir ETW (Windows için Olay İzleme) oturumuna yazan bir izleme katılımcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="48da4-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="48da4-148">ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="48da4-149">İzleme etkinleştirildiğinde, hataları izleme kayıtları ETW'ye yayılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="48da4-150">ETW izleme katılımcısı tarafından yayılan izleme olaylarına karşılık gelen ETW izleme olayları (100-113 aralığı arasında) Analytic Log'a yazılır.</span><span class="sxs-lookup"><span data-stu-id="48da4-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="48da4-151">İzleme kayıtlarını görüntülemek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="48da4-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="48da4-152">Olay Görüntüleyicisi'ni açmak için **Başlat'ı**ve ardından **Çalıştır'ı tıklatın.**</span><span class="sxs-lookup"><span data-stu-id="48da4-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="48da4-153">Çalıştır iletişim kutusunda, `eventvwr`'.</span><span class="sxs-lookup"><span data-stu-id="48da4-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="48da4-154">Olay Görüntüleyicisi iletişim kutusunda, **Uygulamalar ve Hizmetler Günlükleri** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="48da4-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="48da4-155">**Microsoft,** **Windows**ve **Application Server-Applications** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="48da4-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="48da4-156">**Application Server-Applications** düğümünün altındaki **Analitik** düğüme sağ tıklayın ve **Günlük'u Etkinleştir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="48da4-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="48da4-157">İzleme kayıtları oluşturmak için izlemeyi etkinleştiren uygulamanızı yürütün.</span><span class="sxs-lookup"><span data-stu-id="48da4-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="48da4-158">**Analitik** düğüme sağ tıklayın ve **Yenile'yi seçin.**</span><span class="sxs-lookup"><span data-stu-id="48da4-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="48da4-159">İzleme kayıtları orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48da4-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="48da4-160">Aşağıdaki resim, olay görüntüleyicideki olayları izleme gösterir:</span><span class="sxs-lookup"><span data-stu-id="48da4-160">The following image shows tracking events in the event viewer:</span></span>

![İzleme kayıtlarını gösteren Olay Görüntüleyicisi'nin ekran görüntüsü.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="48da4-162">Uygulamaya özel bir sağlayıcı kimliğini kaydetme</span><span class="sxs-lookup"><span data-stu-id="48da4-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="48da4-163">Olayların belirli bir uygulama günlüğüne yazılması gerekiyorsa, yeni sağlayıcı bildirimini kaydetmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="48da4-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="48da4-164">Uygulama yapılandırma dosyasında sağlayıcı kimliğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="48da4-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="48da4-165">Manifesto dosyasını\\\< [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] %windir%\Microsoft.NET\Framework>\Microsoft.Windows.ApplicationServer.Applications.man'ın son sürümünden geçici bir konuma kopyalayın ve Microsoft.Windows.ApplicationServer.Applications_Provider1.man olarak yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="48da4-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="48da4-166">Bildirim dosyasındaki GUID'i yeni GUID olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48da4-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="48da4-167">Varsayılan sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48da4-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="48da4-168">Önceki adımda sağlayıcı adını değiştirdiyseniz, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48da4-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="48da4-169">Bu adımları izleyerek kaynak DLL oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48da4-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="48da4-170">Windows SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="48da4-170">Install the Windows SDK.</span></span> <span data-ttu-id="48da4-171">Windows SDK ileti derleyicisi ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) ve kaynak derleyicisi[(rc.exe)](/windows/win32/menurc/using-rc-the-rc-command-line-)içerir.</span><span class="sxs-lookup"><span data-stu-id="48da4-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="48da4-172">Windows SDK komut isteminde, mc.exe'yi yeni bildirim dosyasında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48da4-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="48da4-173">Önceki adımda oluşturulan kaynak dosyasında rc.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48da4-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="48da4-174">NewProviderReg.cs adlı boş bir cs dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48da4-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="48da4-175">C# derleyicisini kullanarak bir kaynak DLL oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48da4-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="48da4-176">Bildirim dosyasındaki `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` kaynak ve ileti dll adını yeni dll adına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48da4-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="48da4-177">Bildirimi kaydetmek için [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="48da4-177">Use [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="48da4-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48da4-178">See also</span></span>

- <span data-ttu-id="48da4-179">[Windows Server App Kumaş İzleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="48da4-179">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="48da4-180">[Uygulama Kumaşı ile Uygulamaların İzlenmesi](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="48da4-180">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
