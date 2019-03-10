---
title: İzleme profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 2fa4d65a6f0056824b2fc9dd67b93608777fc75d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721378"
---
# <a name="tracking-profiles"></a><span data-ttu-id="0e103-102">İzleme profilleri</span><span class="sxs-lookup"><span data-stu-id="0e103-102">Tracking Profiles</span></span>

<span data-ttu-id="0e103-103">İzleme profilleri bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="0e103-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="0e103-104">İzleme profilleri</span><span class="sxs-lookup"><span data-stu-id="0e103-104">Tracking Profiles</span></span>

<span data-ttu-id="0e103-105">İzleme profilleri, bir iş akışı örneği için izleme bilgileri yayıldığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e103-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="0e103-106">Ardından profil belirtilmezse, tüm izleme olaylar gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0e103-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="0e103-107">Bir profili belirtilirse, profilde belirtilen izleme olaylarını yayılan.</span><span class="sxs-lookup"><span data-stu-id="0e103-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="0e103-108">Çok genel bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur.</span><span class="sxs-lookup"><span data-stu-id="0e103-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="0e103-109">Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok ayrıntılı profili oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e103-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="0e103-110">İzleme profilleri standart içindeki XML öğeleri olarak kendilerini bildirim [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma dosyası veya belirtilen kod.</span><span class="sxs-lookup"><span data-stu-id="0e103-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="0e103-111">Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] abone olmak izleme katılımcı izin veren bir yapılandırma dosyası profilinde izleme `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="0e103-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
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

<span data-ttu-id="0e103-112">Aşağıdaki örnek kod kullanılarak oluşturulan profil izleme eşdeğer gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e103-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="0e103-113">İzleme kayıtları filtre uygulanır aracılığıyla bir izleme profili içinde görünürlük modunu kullanarak <xref:System.Activities.Tracking.ImplementationVisibility> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0e103-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="0e103-114">Bileşik bir etkinlik uygulaması oluşturan diğer etkinlikler içeren üst düzey bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="0e103-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="0e103-115">Uygulama oluşturan etkinlikler izlenen varsa belirtmek için bir iş akışı etkinlik içinde bileşik etkinliklerden yayılan izleme kayıtları görünürlük modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e103-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="0e103-116">İzleme sırasında görünürlük modunu geçerli profil düzeyi.</span><span class="sxs-lookup"><span data-stu-id="0e103-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="0e103-117">Bir iş akışındaki etkinliklere tek tek kayıtları izleme filtreleme, sorguları izleme profilinde tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0e103-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="0e103-118">Daha fazla bilgi için **izleme profili sorgu türleri** bu belgenin bölüm.</span><span class="sxs-lookup"><span data-stu-id="0e103-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="0e103-119">Belirtilen iki görünürlük modları `implementationVisibility` izleme profilinde özniteliğinin `RootScope` ve `All`.</span><span class="sxs-lookup"><span data-stu-id="0e103-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="0e103-120">Kullanarak `RootScope` modu, bileşik bir etkinlik olduğu bir iş akışının kök durumda bir etkinlik uygulaması oluşturan etkinlikler için izleme kayıtları bastırır.</span><span class="sxs-lookup"><span data-stu-id="0e103-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="0e103-121">Bir iş akışı için diğer etkinlikleri kullanılarak uygulanan bir etkinlik eklendiğinde bu, gelir ve `implementationVisibility` için RootScope ayarlayın, yalnızca üst düzey faaliyet, bileşik bir etkinlik içinde takip edilir.</span><span class="sxs-lookup"><span data-stu-id="0e103-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="0e103-122">Bir etkinlik iş akışı köküdür. sonra iş akışı uygulamasıdır etkinliğin kendisi ve kayıtları izleme uygulaması oluşturan etkinlikler için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0e103-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="0e103-123">Tüm modu kullanılarak, tüm izleme kayıtları için Kök etkinlik yayılan ve tüm bileşik etkinlikleri izin verir.</span><span class="sxs-lookup"><span data-stu-id="0e103-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="0e103-124">Örneğin, varsayalım *MyActivity* uygulaması içeren iki etkinlik, bileşik bir etkinlik *Activity1* ve *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="0e103-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="0e103-125">Ne zaman bu etkinlik bir iş akışına eklenir ve izleme bir izleme profili ile etkinleştirilmiş `implementationVisibility` kümesine `RootScope`, izleme kayıtları yayılan yalnızca *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="0e103-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="0e103-126">Ancak, etkinlikler için hiçbir kayıtları yayılan *Activity1* ve *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="0e103-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="0e103-127">Ancak, varsa `implementationVisibility` izleme profili kümesine özniteliği `All`, yalnızca için izleme kayıtları yayılan sonra *MyActivity*, ancak etkinlikler için de *Activity1* ve  *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="0e103-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="0e103-128">`implementationVisibility` Bayrağı takip izleme kayıt türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0e103-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="0e103-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="0e103-129">ActivityStateRecord</span></span>

- <span data-ttu-id="0e103-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="0e103-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="0e103-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="0e103-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="0e103-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="0e103-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="0e103-133">Etkinlik uygulamasından yayılan CustomTrackingRecords implementationVisibility ayarı tarafından filtrelenir değil.</span><span class="sxs-lookup"><span data-stu-id="0e103-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="0e103-134">`implementationVisibility` İşlevi olarak belirtilen <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> izlemeyi kodda gibi profil:</span><span class="sxs-lookup"><span data-stu-id="0e103-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="0e103-135">`implementationVisibility` İşlevi olarak belirtilen <xref:System.Activities.Tracking.ImplementationVisibility.All> izleme profili bir yapılandırma dosyasında aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="0e103-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="0e103-136">`ImplementationVisibility` İzleme profili ayarı, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e103-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="0e103-137">Varsayılan olarak, değeri ayarlamak `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="0e103-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="0e103-138">Bu öznitelik değerlerini ayrıca büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e103-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="0e103-139">İzleme profili sorgu türleri</span><span class="sxs-lookup"><span data-stu-id="0e103-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="0e103-140">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e103-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="0e103-141">Birkaç farklı sınıfları için abone izin sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="0e103-142">İzleme profilleri yapılandırmasında veya kod aracılığıyla belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e103-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="0e103-143">En sık kullanılan sorgu türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0e103-143">Here are the most common query types:</span></span>

- <span data-ttu-id="0e103-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> -Daha önce gösterildiği gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek için bunu kullanın `Started` ve `Completed`.</span><span class="sxs-lookup"><span data-stu-id="0e103-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="0e103-145">
  <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="0e103-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

    - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

    <span data-ttu-id="0e103-146">İçin abone durumları belirtilen <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e103-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

    <span data-ttu-id="0e103-147">Yapılandırma veya iş akışı örnek düzeyi kayıtları için izleme abone olmak için kullanılan kod `Started` durumu örneği kullanarak <xref:System.Activities.Tracking.WorkflowInstanceQuery> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="0e103-148"><xref:System.Activities.Tracking.ActivityStateQuery> -Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e103-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="0e103-149">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e103-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="0e103-150">Bu sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityStateRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="0e103-151">Abone olmak için kullanılabilir durumları belirtilen <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="0e103-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

    <span data-ttu-id="0e103-152">Yapılandırma ve kullanma etkinlik durumu izleme kayıtları abone olmak için kullanılan kod <xref:System.Activities.Tracking.ActivityStateQuery> için `SendEmailActivity` etkinlik, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

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
    > <span data-ttu-id="0e103-153">Birden çok activityStateQuery öğeleri aynı ada sahipse, yalnızca son öğesinde durumları izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e103-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="0e103-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> -Bu sorgu yürütme için zamanlanan bir etkinlik üst etkinliği tarafından izlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0e103-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="0e103-155">Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityScheduledRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

    <span data-ttu-id="0e103-156">Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili `SendEmailActivity` alt etkinlik kullanarak zamanlanmasını <xref:System.Activities.Tracking.ActivityScheduledQuery> aşağıdaki örnekte gösterilen.</span><span class="sxs-lookup"><span data-stu-id="0e103-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="0e103-157"><xref:System.Activities.Tracking.FaultPropagationQuery> -Bir etkinlik içinde oluşan hataların işlenmesi izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e103-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="0e103-158">Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.FaultPropagationRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

    <span data-ttu-id="0e103-159">Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili hata yayma kullanarak <xref:System.Activities.Tracking.FaultPropagationQuery> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="0e103-160"><xref:System.Activities.Tracking.CancelRequestedQuery> -Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e103-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0e103-161">Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CancelRequestedRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

    <span data-ttu-id="0e103-162">Kayıtları abone olmak için kullanılan kod ve yapılandırmayı ilgili etkinlik iptal kullanarak <xref:System.Activities.Tracking.CancelRequestedQuery> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="0e103-163"><xref:System.Activities.Tracking.CustomTrackingQuery> -Kod etkinlikleriniz tanımlayan olayları izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e103-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="0e103-164">Sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

    <span data-ttu-id="0e103-165">Kayıtları abone olmak için kullanılan kod ve yapılandırmayı kullanarak özel izleme kayıtları için ilgili <xref:System.Activities.Tracking.CustomTrackingQuery> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="0e103-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> -İş akışı örneği içinde yer işaretinin sürdürme izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e103-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="0e103-167">Bu sorgu için gerekli bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.BookmarkResumptionRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0e103-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

    <span data-ttu-id="0e103-168">İlgili kayıtlara abone olmak için kullanılan kod ve yapılandırmayı sürdürme yer işareti kullanarak <xref:System.Activities.Tracking.BookmarkResumptionQuery> aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

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

### <a name="annotations"></a><span data-ttu-id="0e103-169">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e103-169">Annotations</span></span>

<span data-ttu-id="0e103-170">Ek açıklamaları, rasgele yapı saatinden yapılandırılabilir bir değerle kayıtları izleme etiket izin verir.</span><span class="sxs-lookup"><span data-stu-id="0e103-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="0e103-171">Örneğin, "Posta sunucusu ile" etiketlemek için birkaç iş akışları arasında birkaç izleme kayıtları isteyebilirsiniz "Posta Sunucu1" ==.</span><span class="sxs-lookup"><span data-stu-id="0e103-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="0e103-172">Bu etikete sahip tüm kayıtları izleme kayıtları daha sonra sorgulanırken bulma kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0e103-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="0e103-173">Bunu gerçekleştirmek için bir ek açıklama bir izleme sorguya aşağıdaki örnekte gösterildiği gibi eklenir.</span><span class="sxs-lookup"><span data-stu-id="0e103-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="0e103-174">Bir izleme profili oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e103-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="0e103-175">Sorgu öğeleri izleme bir izleme profili kullanarak bir XML yapılandırma dosyasını oluşturmak için kullanılan veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kod.</span><span class="sxs-lookup"><span data-stu-id="0e103-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span> <span data-ttu-id="0e103-176">Bir yapılandırma dosyası kullanılarak oluşturulan bir izleme profili bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="0e103-177">İş akışı hizmeti konağı kullanarak WF izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0e103-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="0e103-178">İzleme profili kullanarak ve sorgu API'si izleme kodu ile bir izleme profili oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0e103-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="0e103-179">Bir XML yapılandırma dosyası olarak yapılandırılan bir profili bir davranış uzantısı kullanarak bir izleme katılımcı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e103-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="0e103-180">Bu sonraki bölümde açıklandığı gibi bir WorkflowServiceHost eklenir [yapılandırma izleme için bir iş akışı](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="0e103-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="0e103-181">Ayrıntı düzeyini ana bilgisayar tarafından yayılan izleme kayıtları izleme profili yapılandırma ayarlarında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0e103-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="0e103-182">İzleme katılımcı, sorgular için bir izleme profili ekleyerek kayıtları izleme için abone olur.</span><span class="sxs-lookup"><span data-stu-id="0e103-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="0e103-183">Tüm izleme kayıtları abone olmak izleme profili kullanarak tüm izleme sorguları belirtilmesi gerekiyor "\*" her bir sorgu ad alanları.</span><span class="sxs-lookup"><span data-stu-id="0e103-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="0e103-184">İzleme profilleri, sık karşılaşılan örneklerden bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e103-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="0e103-185">İş akışı örneği kayıtlarını ve hataları elde etmek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="0e103-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

1. <span data-ttu-id="0e103-186">Tüm özel izleme kayıtları almak için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="0e103-186">A tracking profile to obtain all custom tracking records.</span></span>

```xml
<trackingProfile name="Instance_And_Custom_Records">
  <workflow activityDefinitionId="*">
    <customTrackingQueries>
      <customTrackingQuery name="*" activityName="*" />
    </customTrackingQueries>
  </workflow>
</trackingProfile>
```

## <a name="see-also"></a><span data-ttu-id="0e103-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e103-187">See also</span></span>

- [<span data-ttu-id="0e103-188">SQL İzleme</span><span class="sxs-lookup"><span data-stu-id="0e103-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- [<span data-ttu-id="0e103-189">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="0e103-189">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="0e103-190">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="0e103-190">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
