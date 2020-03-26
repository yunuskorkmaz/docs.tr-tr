---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 609c3f0c728e71d1bbf5335aae0b18d6f99a7181
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249044"
---
# <a name="tracking-profiles"></a><span data-ttu-id="90555-102">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="90555-102">Tracking Profiles</span></span>

<span data-ttu-id="90555-103">İzleme profilleri, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="90555-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="90555-104">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="90555-104">Tracking Profiles</span></span>

<span data-ttu-id="90555-105">İzleme profilleri, iş akışı örneği için hangi izleme bilgilerinin yayıldığıbelirtilmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90555-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="90555-106">Profil belirtilmemişse, tüm izleme olayları yayılır.</span><span class="sxs-lookup"><span data-stu-id="90555-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="90555-107">Bir profil belirtilirse, profilde belirtilen izleme olayları yayılır.</span><span class="sxs-lookup"><span data-stu-id="90555-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="90555-108">İzleme gereksinimlerinize bağlı olarak, çok genel bir profil yazabilirsiniz ve bu profil, iş akışındaki küçük bir üst düzey durum değişikliğine abone dir.</span><span class="sxs-lookup"><span data-stu-id="90555-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="90555-109">Tersine, ortaya çıkan olaylar daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok ayrıntılı bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90555-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="90555-110">İzleme profilleri, standart bir .NET Framework yapılandırma dosyasında veya kodda belirtilen XML öğeleri olarak kendini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90555-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="90555-111">Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] izleme katılımcısının iş akışı olaylarına abone `Started` `Completed` olmasını sağlayan bir yapılandırma dosyasındaki izleme profilidir.</span><span class="sxs-lookup"><span data-stu-id="90555-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

<span data-ttu-id="90555-112">Aşağıdaki örnekte, kod kullanılarak oluşturulan eşdeğer izleme profili gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90555-112">The following example shows the equivalent tracking profile created using code.</span></span>

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

<span data-ttu-id="90555-113">İzleme kayıtları öznitelik kullanılarak <xref:System.Activities.Tracking.ImplementationVisibility> izleme profili içindeki görünürlük modundan filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="90555-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="90555-114">Bileşik etkinlik, uygulanmasını oluşturan diğer etkinlikleri içeren üst düzey bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="90555-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="90555-115">Görünürlük modu, uygulamayı oluşturan etkinliklerin izlendiğini belirtmek için, bir iş akışı etkinliği içindeki bileşik etkinliklerden yayılan izleme kayıtlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90555-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="90555-116">Görünürlük modu izleme profili düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="90555-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="90555-117">İş akışı içindeki tek tek etkinliklere ait izleme kayıtlarının filtrelemi, izleme profilindeki sorgular tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="90555-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="90555-118">Daha fazla bilgi için bu belgedeki **İzleme Profili Sorgu Türleri** bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="90555-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="90555-119">İzleme profilindeki öznitelik tarafından `implementationVisibility` belirtilen iki görünürlük `RootScope` `All`modu ve .</span><span class="sxs-lookup"><span data-stu-id="90555-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="90555-120">`RootScope` Modu kullanmak, bileşik bir etkinliğin iş akışının kökü olmadığı durumlarda bir etkinliğin uygulanmasını oluşturan etkinliklerin izleme kayıtlarını bastırır.</span><span class="sxs-lookup"><span data-stu-id="90555-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="90555-121">Bu, diğer etkinlikler kullanılarak uygulanan bir etkinlik iş akışına ve RootScope `implementationVisibility` kümesine eklendiğinde, yalnızca bu bileşik etkinlik içindeki üst düzey etkinliğin izlendiğinde anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="90555-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="90555-122">Bir etkinlik iş akışının köküise, etkinliğin uygulanması iş akışının kendisidir ve izleme kayıtları uygulamayı oluşturan etkinlikler için yayılır.</span><span class="sxs-lookup"><span data-stu-id="90555-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="90555-123">Tüm modu kullanmak, tüm izleme kayıtlarının kök etkinliği ve tüm bileşik etkinlikleri için yayımlansına izin verir.</span><span class="sxs-lookup"><span data-stu-id="90555-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="90555-124">Örneğin, *MyActivity'in,* uygulaması *etkinlik1* ve *Etkinlik2*olmak üzere iki etkinlik içeren bileşik bir etkinlik olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="90555-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="90555-125">Bu etkinlik bir iş akışına eklendiğinde ve izleme `implementationVisibility` ayarlanmış `RootScope`bir izleme profili ile etkinleştirildiğinde, izleme kayıtları yalnızca *MyActivity*için yayılır.</span><span class="sxs-lookup"><span data-stu-id="90555-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="90555-126">Ancak, etkinlikler *Etkinlik1* ve *Etkinlik2*için hiçbir kayıt yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="90555-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="90555-127">`implementationVisibility` Ancak, izleme profili için öznitelik ayarlanırsa `All`, o zaman izleme kayıtları *MyActivity*için değil, aynı zamanda etkinlikler *Etkinlik1* ve *Etkinlik2*için yayılan .</span><span class="sxs-lookup"><span data-stu-id="90555-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="90555-128">Bayrak `implementationVisibility` aşağıdaki izleme kayıt türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="90555-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="90555-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="90555-129">ActivityStateRecord</span></span>

- <span data-ttu-id="90555-130">Fay YayılımıKayıt</span><span class="sxs-lookup"><span data-stu-id="90555-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="90555-131">Cancelrequestedrecord</span><span class="sxs-lookup"><span data-stu-id="90555-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="90555-132">Activityscheduledrecord</span><span class="sxs-lookup"><span data-stu-id="90555-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="90555-133">Etkinlik uygulamasından yayılan CustomTrackingRecords uygulamaGörünürlük ayarı tarafından filtreuygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="90555-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="90555-134">İşlevsellik `implementationVisibility` <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> koddaki izleme profilinde aşağıdaki gibi belirtilir:</span><span class="sxs-lookup"><span data-stu-id="90555-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="90555-135">`implementationVisibility` İşlevsellik, <xref:System.Activities.Tracking.ImplementationVisibility.All> yapılandırma dosyasındaki izleme profilinde aşağıdaki gibi belirtilir:</span><span class="sxs-lookup"><span data-stu-id="90555-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

<span data-ttu-id="90555-136">İzleme `ImplementationVisibility` profilindeki ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="90555-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="90555-137">Varsayılan olarak, değeri `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="90555-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="90555-138">Bu öznitelik için değerler de büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="90555-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="90555-139">İzleme Profili Sorgu Türleri</span><span class="sxs-lookup"><span data-stu-id="90555-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="90555-140">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanıza olanak tanıyan kayıtları izlemek için bildirimsel abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="90555-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="90555-141">Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olsanız birkaç sorgu türü vardır.</span><span class="sxs-lookup"><span data-stu-id="90555-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="90555-142">İzleme profilleri yapılandırmada veya kod aracılığıyla belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="90555-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="90555-143">En yaygın sorgu türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="90555-143">Here are the most common query types:</span></span>

- <span data-ttu-id="90555-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery>- Daha önce gösterildiği `Started` gibi iş akışı örneği yaşam döngüsü `Completed`değişiklikleri izlemek için bunu kullanın ve.</span><span class="sxs-lookup"><span data-stu-id="90555-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="90555-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="90555-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="90555-146">Abone olunabilecek durumlar <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfta belirtilir.</span><span class="sxs-lookup"><span data-stu-id="90555-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="90555-147">İş akışı örnek düzeyi izleme kayıtlarına abone olmak için `Started` <xref:System.Activities.Tracking.WorkflowInstanceQuery> kullanılan yapılandırma veya kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <span data-ttu-id="90555-148"><xref:System.Activities.Tracking.ActivityStateQuery>- İş akışı örneğini oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90555-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="90555-149">Örneğin, "E-Posta Gönder" etkinliği bir iş akışı örneği içinde her tamamlandığında izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90555-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="90555-150">Bu sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone <xref:System.Activities.Tracking.ActivityStateRecord> olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="90555-151">Abone olunacak kullanılabilir durumlar <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="90555-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="90555-152">Etkinlik için kullanılan etkinlik durumu izleme kayıtlarını <xref:System.Activities.Tracking.ActivityStateQuery> abone `SendEmailActivity` etmek için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > <span data-ttu-id="90555-153">Birden çok etkinlikStateQuery öğesi aynı ada sahipse, izleme profilinde yalnızca son öğedeki durumlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90555-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="90555-154"><xref:System.Activities.Tracking.ActivityScheduledQuery>- Bu sorgu, bir üst etkinlik tarafından yürütülmesi için zamanlanmış bir etkinliği izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="90555-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="90555-155">Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.ActivityScheduledRecord> için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="90555-156">Zamanlanan `SendEmailActivity` <xref:System.Activities.Tracking.ActivityScheduledQuery> alt etkinlikle ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="90555-157"><xref:System.Activities.Tracking.FaultPropagationQuery>- Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90555-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="90555-158">Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.FaultPropagationRecord> için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="90555-159">Hata yayılımı kullanılarak <xref:System.Activities.Tracking.FaultPropagationQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <span data-ttu-id="90555-160"><xref:System.Activities.Tracking.CancelRequestedQuery>- Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90555-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="90555-161">Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.CancelRequestedRecord> için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="90555-162">Etkinlik iptali ile <xref:System.Activities.Tracking.CancelRequestedQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="90555-163"><xref:System.Activities.Tracking.CustomTrackingQuery>- Kod etkinliklerinizde tanımladığınız olayları izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90555-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="90555-164">Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.CustomTrackingRecord> için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="90555-165">Özel izleme kayıtları kullanılarak <xref:System.Activities.Tracking.CustomTrackingQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="90555-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery>- İş akışı örneği içinde yer imi devamını izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90555-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="90555-167">Bu sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone <xref:System.Activities.Tracking.BookmarkResumptionRecord> olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90555-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="90555-168">Yer imi devamı ile <xref:System.Activities.Tracking.BookmarkResumptionQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a><span data-ttu-id="90555-169">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90555-169">Annotations</span></span>

<span data-ttu-id="90555-170">Ek açıklamalar, izleme kayıtlarını oluşturma süresinden sonra yapılandırılabilen bir değerle rasgele etiketlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="90555-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="90555-171">Örneğin, birkaç iş akışında birkaç izleme kaydının "Mail Server" == "Mail Server1" ile etiketletilmesi isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90555-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="90555-172">Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="90555-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="90555-173">Bunu gerçekleştirmek için, aşağıdaki örnekte gösterildiği gibi bir izleme sorgusuna bir ek açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="90555-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="90555-174">İzleme Profili Nasıl Oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="90555-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="90555-175">İzleme sorgusu öğeleri, Bir XML yapılandırma dosyası veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] kodu kullanarak bir izleme profili oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90555-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="90555-176">Burada, yapılandırma dosyası kullanılarak oluşturulan izleme profiline bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-176">Here is an example of a tracking profile created using a configuration file.</span></span>

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> <span data-ttu-id="90555-177">İş Akışı hizmet ana bilgisayarını kullanan bir WF için izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="90555-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="90555-178">İzleme profilini ve izleme sorgusu API'sını kullanarak kodlu bir izleme profili oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="90555-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="90555-179">XML yapılandırma dosyası olarak yapılandırılan bir profil, davranış uzantısı kullanılarak izleme katılımcısına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="90555-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="90555-180">Bu, daha sonraki bölümde açıklandığı gibi bir İş AkışıServiceHost eklenir Bir [İş Akışı için İzleme Yapılandırma.](configuring-tracking-for-a-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="90555-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="90555-181">Ana bilgisayar tarafından yayılan izleme kayıtlarının ayrıntılılığı, izleme profiliiçindeki yapılandırma ayarları yla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="90555-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="90555-182">Bir izleme katılımcısı, izleme profiline sorgular ekleyerek kayıtları izlemeye abone dir.</span><span class="sxs-lookup"><span data-stu-id="90555-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="90555-183">Tüm izleme kayıtlarına abone olmak için, izleme profilinin her\*sorgudaki ad alanlarında " " kullanarak tüm izleme sorgularını belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="90555-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="90555-184">İzleme profillerinin yaygın örneklerinden bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90555-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="90555-185">İş akışı örneği kayıtlarını ve hatalarını elde etmek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="90555-185">A tracking profile to obtain workflow instance records and faults.</span></span>

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- <span data-ttu-id="90555-186">Tüm özel izleme kayıtlarını elde etmek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="90555-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="90555-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90555-187">See also</span></span>

- [<span data-ttu-id="90555-188">SQL İzleme</span><span class="sxs-lookup"><span data-stu-id="90555-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="90555-189">[Windows Server App Kumaş İzleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="90555-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="90555-190">[Uygulama Kumaşı ile Uygulamaların İzlenmesi](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="90555-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
