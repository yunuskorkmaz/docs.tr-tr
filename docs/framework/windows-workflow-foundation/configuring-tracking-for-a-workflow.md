---
title: İş Akışı için İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 97b25873e9f20d5d390b7a59531b3a5af32296df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802680"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="663e2-102">İş Akışı için İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="663e2-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="663e2-103">Bir iş akışı üç şekilde çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="663e2-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="663e2-104"><xref:System.ServiceModel.Activities.WorkflowServiceHost> içinde barındırılan</span><span class="sxs-lookup"><span data-stu-id="663e2-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="663e2-105"><xref:System.Activities.WorkflowApplication> olarak yürütüldü</span><span class="sxs-lookup"><span data-stu-id="663e2-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="663e2-106"><xref:System.Activities.WorkflowInvoker> kullanarak doğrudan yürütülür</span><span class="sxs-lookup"><span data-stu-id="663e2-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="663e2-107">İş akışı barındırma seçeneğine bağlı olarak, bir izleme katılımcısı kod aracılığıyla veya bir yapılandırma dosyası aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="663e2-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="663e2-108">Bu konuda, izlemenin bir <xref:System.Activities.WorkflowApplication> ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>bir izleme katılımcısı eklenerek nasıl yapılandırıldığı ve <xref:System.Activities.WorkflowInvoker>kullanılırken izlemenin nasıl etkinleştirileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="663e2-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="663e2-109">Iş akışı uygulama Izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="663e2-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="663e2-110">Bir iş akışı <xref:System.Activities.WorkflowApplication> sınıfı kullanılarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="663e2-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="663e2-111">Bu konu, <xref:System.Activities.WorkflowApplication> iş akışı konağına izleme katılımcısı ekleyerek bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] iş akışı uygulaması için izlemenin nasıl yapılandırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="663e2-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="663e2-112">Bu durumda iş akışı, iş akışı uygulaması olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="663e2-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="663e2-113">Bir iş akışı uygulamasını, <xref:System.Activities.WorkflowApplication> sınıfını kullanan şirket içinde barındırılan bir. exe dosyası olan kod aracılığıyla (bir yapılandırma dosyası kullanmak yerine) yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="663e2-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="663e2-114">İzleme katılımcısı, <xref:System.Activities.WorkflowApplication> örneğine bir uzantı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="663e2-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="663e2-115">Bu, <xref:System.Activities.Tracking.TrackingParticipant> WorkflowApplication örneği için Uzantılar koleksiyonuna eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="663e2-116">Bir iş akışı uygulaması için aşağıdaki kodda gösterildiği gibi <xref:System.Activities.Tracking.EtwTrackingParticipant> davranış uzantısını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="663e2-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="663e2-117">Iş akışı hizmeti Izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="663e2-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="663e2-118">Bir iş akışı, <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmeti konağında barındırıldığında bir WCF hizmeti olarak gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="663e2-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="663e2-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tabanlı hizmet için özelleşmiş bir .NET ServiceHost uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="663e2-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="663e2-120">Bu bölümde, <xref:System.ServiceModel.Activities.WorkflowServiceHost>çalıştıran bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı hizmeti için izlemenin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="663e2-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="663e2-121">Bir Web. config dosyası (Web 'de barındırılan bir hizmet için) veya bir App. config dosyası aracılığıyla veya hizmet ana bilgisayarı için <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonuna izlemeye özgü bir davranış ekleyerek bir hizmet davranışı belirterek veya kod aracılığıyla (konsol uygulaması gibi tek başına bir uygulamada barındırılan bir hizmet için) ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="663e2-122"><xref:System.ServiceModel.WorkflowServiceHost>barındırılan bir iş akışı hizmeti için, aşağıdaki örnekte gösterildiği gibi, bir yapılandırma dosyasındaki <`behavior`> öğesini kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant> ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="663e2-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="663e2-123">Alternatif olarak, <xref:System.ServiceModel.WorkflowServiceHost>barındırılan bir iş akışı hizmeti için, kod aracılığıyla <xref:System.Activities.Tracking.EtwTrackingParticipant> davranışı uzantısını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="663e2-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="663e2-124">Özel bir izleme katılımcısı eklemek için yeni bir davranış uzantısı oluşturun ve aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.ServiceHost> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="663e2-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="663e2-125">Özel bir izleme katılımcısı ekleyen özel bir davranış öğesinin nasıl oluşturulacağını gösteren örnek kodu görüntülemek istiyorsanız [izleme](./samples/tracking.md) örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="663e2-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="663e2-126">İzleme katılımcısı, iş akışı hizmet ana bilgisayarına davranışın uzantısı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="663e2-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="663e2-127">Aşağıdaki örnek kod, yapılandırma dosyasından bir izleme profilinin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="663e2-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="663e2-128">Bu örnek kod, bir iş akışı konağına izleme profilinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="663e2-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="663e2-129">İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="663e2-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="663e2-130">Workflowwınvoker kullanarak izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="663e2-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="663e2-131"><xref:System.Activities.WorkflowInvoker>kullanılarak yürütülen bir iş akışına yönelik izlemeyi yapılandırmak için, izleme sağlayıcısını bir <xref:System.Activities.WorkflowInvoker> örneğine uzantı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="663e2-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="663e2-132">Aşağıdaki kod örneği, [özel izleme](./samples/custom-tracking.md) örneğinden yapılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="663e2-133">Olay Görüntüleyicisi izleme kayıtlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="663e2-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="663e2-134">WF yürütmesi izlenirken, analiz günlüğü ve hata ayıklama günlüğünde görüntülemek için belirli bir ilgi çekici iki Olay Görüntüleyicisi günlüğü vardır.</span><span class="sxs-lookup"><span data-stu-id="663e2-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="663e2-135">Her ikisi de Microsoft&#124;Windows&#124;uygulama sunucusu-uygulamalar düğümü altında bulunur.</span><span class="sxs-lookup"><span data-stu-id="663e2-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="663e2-136">Bu bölümün içindeki günlüklerde, tüm sistem üzerinde bir etkisi olan olaylar yerine tek bir uygulamanın olayları bulunur.</span><span class="sxs-lookup"><span data-stu-id="663e2-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="663e2-137">Hata ayıklama izleme olayları hata ayıklama günlüğüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="663e2-138">Olay Görüntüleyicisi WF hata ayıklama izleme olaylarını toplamak için, hata ayıklama günlüğünü etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="663e2-139">Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="663e2-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="663e2-140">Çalıştır iletişim kutusunda `eventvwr`yazın.</span><span class="sxs-lookup"><span data-stu-id="663e2-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="663e2-141">Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="663e2-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="663e2-142">**Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="663e2-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="663e2-143">**Uygulama sunucusu-uygulamalar** düğümünün altındaki **hata ayıklama** düğümüne sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="663e2-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="663e2-144">İzleme olaylarını oluşturmak için izleme özellikli uygulamanızı yürütün.</span><span class="sxs-lookup"><span data-stu-id="663e2-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="663e2-145">**Hata ayıklama** düğümüne sağ tıklayın ve Yenile ' yi seçin **.**</span><span class="sxs-lookup"><span data-stu-id="663e2-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="663e2-146">İzleme olayları, Orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="663e2-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="663e2-147">WF 4, izleme kayıtlarını ETW (Windows için olay Izleme) oturumuna yazan bir izleme katılımcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="663e2-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="663e2-148">ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="663e2-149">İzleme etkinleştirildiğinde, hata izleme kayıtları ETW 'ye dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="663e2-150">ETW izleme katılımcısı tarafından yayılan izleme olaylarına karşılık gelen ETW izleme olayları (100-113 aralığı arasında) analitik günlüğe yazılır.</span><span class="sxs-lookup"><span data-stu-id="663e2-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="663e2-151">İzleme kayıtlarını görüntülemek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="663e2-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="663e2-152">Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="663e2-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="663e2-153">Çalıştır iletişim kutusunda `eventvwr`yazın.</span><span class="sxs-lookup"><span data-stu-id="663e2-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="663e2-154">Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="663e2-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="663e2-155">**Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="663e2-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="663e2-156">**Uygulama sunucusu-uygulamalar** düğümünün altındaki **analitik** düğüme sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="663e2-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="663e2-157">İzleme etkin uygulamanızı, izleme kayıtları oluşturmak için yürütün.</span><span class="sxs-lookup"><span data-stu-id="663e2-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="663e2-158">**Analitik** düğümüne sağ tıklayın ve Yenile ' yi seçin **.**</span><span class="sxs-lookup"><span data-stu-id="663e2-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="663e2-159">İzleme kayıtları, Orta bölmede görünür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="663e2-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="663e2-160">Aşağıdaki görüntüde olay görüntüleyicisinde izleme olayları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="663e2-160">The following image shows tracking events in the event viewer:</span></span>

![İzleme kayıtlarını gösteren Olay Görüntüleyicisi ekran görüntüsü.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="663e2-162">Uygulamaya özgü bir sağlayıcı KIMLIĞINI kaydetme</span><span class="sxs-lookup"><span data-stu-id="663e2-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="663e2-163">Olayların belirli bir uygulama günlüğüne yazılması gerekiyorsa, yeni sağlayıcı bildirimini kaydetmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="663e2-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="663e2-164">Uygulama yapılandırma dosyasında sağlayıcı KIMLIĞINI bildirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="663e2-165">Bildirim dosyasını%windir%\Microsoft.NET\Framework\\\<en son [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man sürümünden geçici bir konuma kopyalayın ve Microsoft. Windows. ApplicationServer. Applications_Provider1. man olarak yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="663e2-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="663e2-166">Bildirim dosyasındaki GUID 'yi yeni GUID ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="663e2-167">Varsayılan Sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="663e2-168">Önceki adımda sağlayıcı adını değiştirdiyseniz, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="663e2-169">Aşağıdaki adımları izleyerek kaynak DLL 'sini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="663e2-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="663e2-170">Windows SDK 'i yükler.</span><span class="sxs-lookup"><span data-stu-id="663e2-170">Install the Windows SDK.</span></span> <span data-ttu-id="663e2-171">Windows SDK, ileti derleyicisini ([mc. exe](/windows/win32/wes/message-compiler--mc-exe-)) ve kaynak derleyicisini ([rc. exe](/windows/win32/menurc/using-rc-the-rc-command-line-)) içerir.</span><span class="sxs-lookup"><span data-stu-id="663e2-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="663e2-172">Windows SDK komut isteminde, yeni bildirim dosyasında Mc. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="663e2-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="663e2-173">Önceki adımda oluşturulan kaynak dosyasında RC. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="663e2-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="663e2-174">NewProviderReg.cs adlı boş bir cs dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="663e2-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="663e2-175">C# Derleyiciyi kullanarak bir kaynak dll 'si oluşturun.</span><span class="sxs-lookup"><span data-stu-id="663e2-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="663e2-176">Bildirim dosyasındaki kaynak ve ileti DLL adını `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` ' dan yeni dll adına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="663e2-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="663e2-177">Bildirimi kaydetmek için [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="663e2-177">Use [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="663e2-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663e2-178">See also</span></span>

- <span data-ttu-id="663e2-179">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="663e2-179">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="663e2-180">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="663e2-180">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
