---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: ceeb0f5533bb4c637ea7df52249f5b00067d9b3d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551393"
---
# <a name="tracking-profiles"></a><span data-ttu-id="7f6a0-102">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7f6a0-102">Tracking Profiles</span></span>

<span data-ttu-id="7f6a0-103">İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="7f6a0-104">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="7f6a0-104">Tracking Profiles</span></span>

<span data-ttu-id="7f6a0-105">İzleme profilleri, bir iş akışı örneği için hangi izleme bilgilerinin yayınlandığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="7f6a0-106">Hiçbir profil belirtilmemişse, tüm izleme olayları yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="7f6a0-107">Bir profil belirtilmişse, profilde belirtilen izleme olayları yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="7f6a0-108">İzleme gereksinimlerinize bağlı olarak, çok genel olan bir profil yazabilirsiniz, bu, bir iş akışındaki küçük bir üst düzey durum değişikliği kümesine abone olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="7f6a0-109">Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok ayrıntılı bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="7f6a0-110">Profiller bildirimi, standart bir .NET Framework yapılandırma dosyası içinde veya kodda belirtilen XML öğeleri olarak kendini takip ediyor.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="7f6a0-111">Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] yapılandırma dosyasındaki izleme katılımcısının `Started` ve `Completed` iş akışı olaylarına abone olmasına izin veren bir izleme profilidir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

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

<span data-ttu-id="7f6a0-112">Aşağıdaki örnek, kod kullanılarak oluşturulan eşdeğer izleme profilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="7f6a0-113">İzleme kayıtları, bir izleme profili içindeki görünürlük modu aracılığıyla özniteliği kullanılarak filtrelenir <xref:System.Activities.Tracking.ImplementationVisibility> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="7f6a0-114">Bileşik etkinlik, uygulamasını oluşturan diğer etkinlikleri içeren en üst düzey bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="7f6a0-115">Görünürlük modu, uygulamayı oluşturan etkinliklerin izlendiğini belirtmek için bir iş akışı etkinliği içinde bileşik etkinliklerden yayılan izleme kayıtlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="7f6a0-116">Görünürlük modu, izleme profili düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="7f6a0-117">Bir iş akışı içindeki bireysel etkinliklerin izleme kayıtlarının filtrelenmesi, izleme profili içindeki sorgular tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="7f6a0-118">Daha fazla bilgi için bu belgedeki **profil sorgu türlerini izleme** bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="7f6a0-119">İzleme profilindeki özniteliği tarafından belirtilen iki görünürlük modu `implementationVisibility` `RootScope` ve ' dir `All` .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="7f6a0-120">Modunun kullanılması, `RootScope` bileşik etkinliğin bir iş akışının kökü olmadığı durumda bir etkinliğin uygulanmasını oluşturan etkinliklerin izleme kayıtlarını bastırır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="7f6a0-121">Bu, diğer etkinlikleri kullanarak uygulanan bir etkinlik bir iş akışına eklendiğinde ve `implementationVisibility` RootScope olarak ayarlandığında, yalnızca bu bileşik etkinliğin içindeki en üst düzey etkinliğin izlendiğine ilişkin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="7f6a0-122">Bir etkinlik iş akışının köküdür, etkinliğin uygulanması iş akışının kendisidir ve izleme kayıtları, uygulamayı oluşturan etkinlikler için yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="7f6a0-123">All modunun kullanılması, tüm izleme kayıtlarının kök etkinlik ve tüm bileşik etkinlikleri için oluşturulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="7f6a0-124">Örneğin, *MyActivity* , uygulamasında iki etkinlik ( *Activity1* ve *Activity2*) içeren bir bileşik etkinlik olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="7f6a0-125">Bu etkinlik bir iş akışına eklendiğinde ve izleme, olarak ayarlanmış bir izleme profili ile etkinleştirildiğinde `implementationVisibility` `RootScope` , izleme kayıtları yalnızca *MyActivity*için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="7f6a0-126">Ancak, *Activity1* ve *Activity2*etkinlikleri için hiçbir kayıt yayınlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="7f6a0-127">Ancak, `implementationVisibility` izleme profili için özniteliği olarak ayarlandıysa `All` , izleme kayıtları yalnızca *MyActivity*için değil, *Activity1* ve *Activity2*etkinlikleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="7f6a0-128">`implementationVisibility`Bayrak aşağıdaki izleme kayıt türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7f6a0-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="7f6a0-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="7f6a0-129">ActivityStateRecord</span></span>

- <span data-ttu-id="7f6a0-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="7f6a0-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="7f6a0-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="7f6a0-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="7f6a0-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="7f6a0-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="7f6a0-133">Etkinlik uygulamasından yayılan CustomTrackingRecords, ImplementationVisibility ayarı tarafından filtrelenmez.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="7f6a0-134">`implementationVisibility`İşlevsellik, <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> koddaki izleme profilinde aşağıdaki gibi belirtilir:</span><span class="sxs-lookup"><span data-stu-id="7f6a0-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="7f6a0-135">`implementationVisibility`İşlevselliği, <xref:System.Activities.Tracking.ImplementationVisibility.All> bir yapılandırma dosyasındaki izleme profilinde olarak aşağıdaki gibi belirtilir:</span><span class="sxs-lookup"><span data-stu-id="7f6a0-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="7f6a0-136">`ImplementationVisibility`İzleme profilindeki ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="7f6a0-137">Varsayılan olarak, değeri olarak ayarlanır `RootScope` .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="7f6a0-138">Bu özniteliğin değerleri de büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="7f6a0-139">İzleme profili sorgu türleri</span><span class="sxs-lookup"><span data-stu-id="7f6a0-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="7f6a0-140">İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="7f6a0-141">Farklı nesne sınıflarına abone olmanıza imkan tanıyan birkaç sorgu türü vardır <xref:System.Activities.Tracking.TrackingRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="7f6a0-142">İzleme profilleri, yapılandırma veya kod aracılığıyla belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="7f6a0-143">En yaygın sorgu türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7f6a0-143">Here are the most common query types:</span></span>

- <span data-ttu-id="7f6a0-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> -Bunu, daha önce gösterilen ve gibi iş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanın `Started` `Completed` .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="7f6a0-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="7f6a0-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="7f6a0-146">Abone olabilecek durumlar <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="7f6a0-147">Kullanılarak örnek durum için iş akışı örnek düzeyi izleme kayıtlarına abone olmak için kullanılan yapılandırma veya kod `Started` <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="7f6a0-148"><xref:System.Activities.Tracking.ActivityStateQuery> -Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7f6a0-149">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7f6a0-150">Bu sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için için gereklidir <xref:System.Activities.Tracking.ActivityStateRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="7f6a0-151">Abone olunacak durumlar içinde belirtilir <xref:System.Activities.Tracking.ActivityStates> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="7f6a0-152">Etkinlik için kullanan etkinlik durumu izleme kayıtlarını abone yapmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.ActivityStateQuery> `SendEmailActivity` Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

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
  > <span data-ttu-id="7f6a0-153">Birden çok activityStateQuery öğesi aynı ada sahip ise, izleme profilinde yalnızca son öğedeki durumlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="7f6a0-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> -Bu sorgu, bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7f6a0-155">Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.ActivityScheduledRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="7f6a0-156">Kullanılarak zamanlanmakta olan alt etkinlikle ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod `SendEmailActivity` <xref:System.Activities.Tracking.ActivityScheduledQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="7f6a0-157"><xref:System.Activities.Tracking.FaultPropagationQuery> -Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="7f6a0-158">Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.FaultPropagationRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="7f6a0-159">Kullanılarak hata yayılmaya ilişkin kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.FaultPropagationQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="7f6a0-160"><xref:System.Activities.Tracking.CancelRequestedQuery> -Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f6a0-161">Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.CancelRequestedRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="7f6a0-162">Kullanılarak etkinlik iptaline ilişkin kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.CancelRequestedQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="7f6a0-163"><xref:System.Activities.Tracking.CustomTrackingQuery> -Kod etkinliklerinizde tanımladığınız olayları izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="7f6a0-164">Sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için gereklidir <xref:System.Activities.Tracking.CustomTrackingRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="7f6a0-165">Kullanılarak özel izleme kayıtlarıyla ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.CustomTrackingQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="7f6a0-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> -Bunu, bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7f6a0-167">Bu sorgu, <xref:System.Activities.Tracking.TrackingParticipant> nesnesine abone olmak için için gereklidir <xref:System.Activities.Tracking.BookmarkResumptionRecord> .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="7f6a0-168">Kullanılarak yer işareti sürdürme ile ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod <xref:System.Activities.Tracking.BookmarkResumptionQuery> Aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

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

### <a name="annotations"></a><span data-ttu-id="7f6a0-169">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f6a0-169">Annotations</span></span>

<span data-ttu-id="7f6a0-170">Ek açıklamalar, derleme zamanından sonra yapılandırılabilecek bir değer ile izleme kayıtlarını rastgele etiketlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="7f6a0-171">Örneğin, "posta sunucusu" = = "mail Sunucu1" ile etiketlenecek birkaç iş akışı arasında birkaç izleme kaydının olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="7f6a0-172">Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="7f6a0-173">Bunu gerçekleştirmek için aşağıdaki örnekte gösterildiği gibi bir izleme sorgusuna ek açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="7f6a0-174">Izleme profili oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f6a0-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="7f6a0-175">İzleme sorgusu öğeleri, bir XML yapılandırma dosyası veya kodu kullanarak bir izleme profili oluşturmak için kullanılır [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7f6a0-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="7f6a0-176">Bir yapılandırma dosyası kullanılarak oluşturulan izleme profiline bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="7f6a0-177">Iş akışı hizmet ana bilgisayarını kullanan bir WF için, izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="7f6a0-178">İzleme profilini ve izleme sorgusu API 'sini kullanarak kodla bir izleme profili oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="7f6a0-179">XML yapılandırma dosyası olarak yapılandırılmış bir profil, bir davranış uzantısı kullanılarak bir izleme katılımcısına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="7f6a0-180">Bu, [bir Iş akışı Için Izlemeyi yapılandırırken](configuring-tracking-for-a-workflow.md)sonraki bölümde açıklandığı şekilde bir WorkflowServiceHost 'a eklenir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="7f6a0-181">Konak tarafından yayılan izleme kayıtlarının ayrıntı düzeyi, izleme profili içindeki yapılandırma ayarları tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="7f6a0-182">İzleme katılımcısı bir izleme profiline sorgular ekleyerek kayıtları izlemeye abone olur.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="7f6a0-183">Tüm izleme kayıtlarına abone olmak için, izleme profilinin \* her sorgu içindeki ad alanlarında "" kullanarak tüm izleme sorgularını belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="7f6a0-184">Aşağıda, izleme profillerinin bazı yaygın örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="7f6a0-185">İş akışı örneği kayıtlarını ve hatalarını almak için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

- <span data-ttu-id="7f6a0-186">Tüm özel izleme kayıtlarını elde etmek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="7f6a0-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f6a0-187">See also</span></span>

- [<span data-ttu-id="7f6a0-188">SQL İzleme</span><span class="sxs-lookup"><span data-stu-id="7f6a0-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="7f6a0-189">[Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7f6a0-189">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="7f6a0-190">[App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7f6a0-190">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
