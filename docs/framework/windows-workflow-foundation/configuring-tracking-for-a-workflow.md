---
title: İş Akışı için İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 098b295be00b1b8283e26e79ea14e78634fdb504
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557560"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="3f56f-102">İş Akışı için İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f56f-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="3f56f-103">Bir iş akışı üç şekilde çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="3f56f-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="3f56f-104">Barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="3f56f-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="3f56f-105">Bir olarak yürütüldü <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="3f56f-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="3f56f-106">Kullanarak doğrudan yürütülür <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="3f56f-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="3f56f-107">İş akışı barındırma seçeneğine bağlı olarak, bir izleme katılımcısı kod aracılığıyla veya bir yapılandırma dosyası aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3f56f-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="3f56f-108">Bu konuda, izlemenin bir ve ' a bir izleme katılımcısı eklenerek nasıl yapılandırıldığı <xref:System.Activities.WorkflowApplication> <xref:System.ServiceModel.Activities.WorkflowServiceHost> ve kullanılırken izlemenin nasıl etkinleştirileceği açıklanmaktadır <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="3f56f-109">Iş akışı uygulama Izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f56f-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="3f56f-110">Bir iş akışı sınıfı kullanılarak çalıştırılabilir <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="3f56f-111">Bu konu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] , iş akışı konağına izleme katılımcısı ekleyerek bir iş akışı uygulaması için izlemenin nasıl yapılandırıldığını gösterir <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="3f56f-112">Bu durumda iş akışı, iş akışı uygulaması olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="3f56f-113">Bir iş akışı uygulamasını, sınıfını kullanan, kendi kendine barındırılan bir. exe dosyası olan kod aracılığıyla (bir yapılandırma dosyası kullanmak yerine) yapılandırırsınız <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="3f56f-114">İzleme katılımcısı örneğe bir uzantı olarak eklenir <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="3f56f-115">Bu, <xref:System.Activities.Tracking.TrackingParticipant> WorkflowApplication örneği için Uzantılar koleksiyonuna eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="3f56f-116">Bir iş akışı uygulaması için <xref:System.Activities.Tracking.EtwTrackingParticipant> aşağıdaki kodda gösterildiği gibi davranış uzantısını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f56f-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="3f56f-117">Iş akışı hizmeti Izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f56f-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="3f56f-118">Bir iş akışı, hizmet ana bilgisayarında barındırıldığında bir WCF hizmeti olarak gösterilebilir <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="3f56f-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> , iş akışı tabanlı hizmet için özelleşmiş bir .NET ServiceHost uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="3f56f-120">Bu bölümde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] , içinde çalışan bir iş akışı hizmeti için izlemenin nasıl yapılandırılacağı açıklanmaktadır <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3f56f-121">Hizmet ana bilgisayarı için koleksiyona belirli bir davranış ekleyerek bir hizmet davranışı belirterek veya bir App.config dosyası (konsol uygulaması gibi tek başına bir uygulamada barındırılan bir hizmet için) veya bir Web.config dosyası aracılığıyla yapılandırılır <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="3f56f-122">İçinde barındırılan bir iş akışı hizmeti için, <xref:System.ServiceModel.WorkflowServiceHost> <xref:System.Activities.Tracking.EtwTrackingParticipant> `behavior` Aşağıdaki örnekte gösterildiği gibi, bir yapılandırma dosyasında <> öğesini kullanarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f56f-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="3f56f-123">Alternatif olarak, içinde barındırılan bir iş akışı hizmeti için <xref:System.ServiceModel.WorkflowServiceHost> <xref:System.Activities.Tracking.EtwTrackingParticipant> davranış uzantısını kod aracılığıyla ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f56f-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="3f56f-124">Özel bir izleme katılımcısı eklemek için yeni bir davranış uzantısı oluşturun ve <xref:System.ServiceModel.ServiceHost> Aşağıdaki örnek kodda gösterildiği gibi öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="3f56f-125">Özel bir izleme katılımcısı ekleyen özel bir davranış öğesinin nasıl oluşturulacağını gösteren örnek kodu görüntülemek istiyorsanız [izleme](./samples/tracking.md) örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="3f56f-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="3f56f-126">İzleme katılımcısı, iş akışı hizmet ana bilgisayarına davranışın uzantısı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="3f56f-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="3f56f-127">Aşağıdaki örnek kod, yapılandırma dosyasından bir izleme profilinin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f56f-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="3f56f-128">Bu örnek kod, bir iş akışı konağına izleme profilinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f56f-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="3f56f-129">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3f56f-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="3f56f-130">Workflowwınvoker kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f56f-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="3f56f-131">Kullanılarak yürütülen bir iş akışını izlemeyi yapılandırmak için <xref:System.Activities.WorkflowInvoker> , izleme sağlayıcısını bir örneğe uzantı olarak ekleyin <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="3f56f-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="3f56f-132">Aşağıdaki kod örneği, [özel izleme](./samples/custom-tracking.md) örneğinden yapılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="3f56f-133">Olay Görüntüleyicisi izleme kayıtlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3f56f-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="3f56f-134">WF yürütmesi izlenirken, analiz günlüğü ve hata ayıklama günlüğünde görüntülemek için belirli bir ilgi çekici iki Olay Görüntüleyicisi günlüğü vardır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="3f56f-135">Her ikisi de Microsoft&#124;Windows&#124;uygulama sunucusu-uygulamalar düğümünün altında bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f56f-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="3f56f-136">Bu bölümün içindeki günlüklerde, tüm sistem üzerinde bir etkisi olan olaylar yerine tek bir uygulamanın olayları bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f56f-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="3f56f-137">Hata ayıklama izleme olayları hata ayıklama günlüğüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="3f56f-138">Olay Görüntüleyicisi WF hata ayıklama izleme olaylarını toplamak için, hata ayıklama günlüğünü etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="3f56f-139">Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="3f56f-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="3f56f-140">Çalıştır iletişim kutusunda, yazın `eventvwr` .</span><span class="sxs-lookup"><span data-stu-id="3f56f-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="3f56f-141">Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="3f56f-142">**Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="3f56f-143">**Uygulama sunucusu-uygulamalar** düğümünün altındaki **hata ayıklama** düğümüne sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="3f56f-144">İzleme olaylarını oluşturmak için izleme özellikli uygulamanızı yürütün.</span><span class="sxs-lookup"><span data-stu-id="3f56f-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="3f56f-145">**Hata ayıklama** düğümüne sağ tıklayın ve Yenile ' yi seçin **.**</span><span class="sxs-lookup"><span data-stu-id="3f56f-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="3f56f-146">İzleme olayları, Orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="3f56f-147">WF 4, izleme kayıtlarını ETW (Windows için olay Izleme) oturumuna yazan bir izleme katılımcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f56f-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="3f56f-148">ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="3f56f-149">İzleme etkinleştirildiğinde, hata izleme kayıtları ETW 'ye dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="3f56f-150">ETW izleme katılımcısı tarafından yayılan izleme olaylarına karşılık gelen ETW izleme olayları (100-113 aralığı arasında) analitik günlüğe yazılır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="3f56f-151">İzleme kayıtlarını görüntülemek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="3f56f-152">Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="3f56f-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="3f56f-153">Çalıştır iletişim kutusunda, yazın `eventvwr` .</span><span class="sxs-lookup"><span data-stu-id="3f56f-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="3f56f-154">Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="3f56f-155">**Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="3f56f-156">**Uygulama sunucusu-uygulamalar** düğümünün altındaki **analitik** düğüme sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="3f56f-157">İzleme etkin uygulamanızı, izleme kayıtları oluşturmak için yürütün.</span><span class="sxs-lookup"><span data-stu-id="3f56f-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="3f56f-158">**Analitik** düğümüne sağ tıklayın ve Yenile ' yi seçin **.**</span><span class="sxs-lookup"><span data-stu-id="3f56f-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="3f56f-159">İzleme kayıtları, Orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f56f-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="3f56f-160">Aşağıdaki görüntüde olay görüntüleyicisinde izleme olayları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3f56f-160">The following image shows tracking events in the event viewer:</span></span>

![İzleme kayıtlarını gösteren Olay Görüntüleyicisi ekran görüntüsü.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="3f56f-162">Uygulamaya özgü bir sağlayıcı KIMLIĞINI kaydetme</span><span class="sxs-lookup"><span data-stu-id="3f56f-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="3f56f-163">Olayların belirli bir uygulama günlüğüne yazılması gerekiyorsa, yeni sağlayıcı bildirimini kaydetmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="3f56f-164">Uygulama yapılandırma dosyasında sağlayıcı KIMLIĞINI bildirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="3f56f-165">Bildirim dosyasını%windir%\Microsoft.NET\Framework \\ \<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.Man konumundan geçici bir konuma kopyalayın ve Microsoft. Windows. applicationserver. Applications_Provider1. man olarak yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="3f56f-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="3f56f-166">Bildirim dosyasındaki GUID 'yi yeni GUID ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="3f56f-167">Varsayılan Sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="3f56f-168">Önceki adımda sağlayıcı adını değiştirdiyseniz, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="3f56f-169">Aşağıdaki adımları izleyerek kaynak DLL 'sini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f56f-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="3f56f-170">Windows SDK 'i yükler.</span><span class="sxs-lookup"><span data-stu-id="3f56f-170">Install the Windows SDK.</span></span> <span data-ttu-id="3f56f-171">Windows SDK, ileti derleyicisi ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) ve kaynak derleyicisi ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)) içerir.</span><span class="sxs-lookup"><span data-stu-id="3f56f-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="3f56f-172">Windows SDK komut isteminde, yeni bildirim dosyasında mc.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3f56f-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="3f56f-173">Önceki adımda oluşturulan kaynak dosyasında rc.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3f56f-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="3f56f-174">NewProviderReg.cs adlı boş bir cs dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f56f-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="3f56f-175">C# derleyicisini kullanarak bir kaynak DLL 'SI oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f56f-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="3f56f-176">Bildirim dosyasındaki kaynak ve ileti DLL adını ' dan `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` Yeni dll adına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f56f-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="3f56f-177">Bildirimi kaydetmek için [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f56f-177">Use [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="3f56f-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f56f-178">See also</span></span>

- <span data-ttu-id="3f56f-179">[Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3f56f-179">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="3f56f-180">[App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3f56f-180">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
