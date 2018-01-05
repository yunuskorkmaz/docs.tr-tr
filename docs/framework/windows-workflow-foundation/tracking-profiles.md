---
title: Profillerini izleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3b1e96451eb89544d0902a1f3498263dec981a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-profiles"></a><span data-ttu-id="808b3-102">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="808b3-102">Tracking Profiles</span></span>
<span data-ttu-id="808b3-103">İzleme profilleri çalışma zamanında bir iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir.</span><span class="sxs-lookup"><span data-stu-id="808b3-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>  
  
## <a name="tracking-profiles"></a><span data-ttu-id="808b3-104">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="808b3-104">Tracking Profiles</span></span>  
 <span data-ttu-id="808b3-105">İzleme profilleri hangi izleme bilgileri için bir iş akışı örneği gösterilen belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="808b3-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="808b3-106">Profil yok belirtilmişse, tüm izleme olaylarını yayılan.</span><span class="sxs-lookup"><span data-stu-id="808b3-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="808b3-107">Bir profili belirtilirse, profilinde belirtilen izleme olaylarını yayılan.</span><span class="sxs-lookup"><span data-stu-id="808b3-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="808b3-108">İzleme gereksinimlerinize bağlı olarak çok genel bir profili yazabilir, üst düzey durum değişiklikleri bir iş akışında, küçük bir kümesini için abone olur.</span><span class="sxs-lookup"><span data-stu-id="808b3-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="808b3-109">Buna karşılık, sonuçta ortaya çıkan, olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin çok ayrıntılı bir profil oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="808b3-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="808b3-110">İzleme profili XML öğeleri içinde bir standart olarak kendilerini bildirim [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma dosyası veya belirtilen kod.</span><span class="sxs-lookup"><span data-stu-id="808b3-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="808b3-111">Aşağıdaki örnek sahip bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] abone olmak izleme katılımcı izin veren bir yapılandırma dosyası profilinde izleme `Started` ve `Completed` iş akışı olayları.</span><span class="sxs-lookup"><span data-stu-id="808b3-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
 <span data-ttu-id="808b3-112">Aşağıdaki örnek kod kullanılarak oluşturulan profili izleme eşdeğer gösterir.</span><span class="sxs-lookup"><span data-stu-id="808b3-112">The following example shows the equivalent tracking profile created using code.</span></span>  
  
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
  
 <span data-ttu-id="808b3-113">İzleme kayıtları izleme profilindeki görünürlük modunu aracılığıyla kullanılarak filtrelenir <xref:System.Activities.Tracking.ImplementationVisibility> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="808b3-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="808b3-114">Bileşik etkinlik uygulaması form diğer etkinlikler içeren üst düzey bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="808b3-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="808b3-115">Uygulama form etkinlikleri izlenen olmadığını belirtmek için bir iş akışı aktivitesi içinde bileşik etkinliklerden yayılan izleme kayıtları görünürlük modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="808b3-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span>  <span data-ttu-id="808b3-116">İzleme sırasında görünürlük modunu uygular profil düzeyi.</span><span class="sxs-lookup"><span data-stu-id="808b3-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="808b3-117">Bir iş akışındaki etkinliklere tek tek kayıtları izleme filtreleme izleme profili sorgulara tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="808b3-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="808b3-118">Daha fazla bilgi için bkz: **izleme profili sorgu türleri** bu belgede bölüm.</span><span class="sxs-lookup"><span data-stu-id="808b3-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>  
  
 <span data-ttu-id="808b3-119">Belirtilen iki görünürlük modları `implementationVisibility` özniteliğinin izleme profilinde `RootScope` ve `All`.</span><span class="sxs-lookup"><span data-stu-id="808b3-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="808b3-120">Kullanarak `RootScope` modu bileşik bir etkinlik olduğu bir iş akışının kök durumda bir etkinlik uyarlamasını form etkinlikler için izleme kayıtları gizler.</span><span class="sxs-lookup"><span data-stu-id="808b3-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span>  <span data-ttu-id="808b3-121">Diğer etkinlikler kullanılarak uygulanan bir etkinlik bir iş akışına eklendiğinde bu, gelir ve `implementationVisibility` RootScope için ayarlanırsa, bu bileşik etkinlik içinde yalnızca üst düzey etkinlik izlenir.</span><span class="sxs-lookup"><span data-stu-id="808b3-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="808b3-122">Bir etkinlik iş akışı köküdür. ardından etkinliği iş akışı uygulamasıdır kendisi ve kayıtları izleme uygulaması form etkinlikler için gösterilen.</span><span class="sxs-lookup"><span data-stu-id="808b3-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="808b3-123">Tüm modunu kullanan tüm izleme kayıtları için Kök etkinlik yayınlaması ve tüm bileşik etkinliklerini izin verir.</span><span class="sxs-lookup"><span data-stu-id="808b3-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>  
  
 <span data-ttu-id="808b3-124">Örneğin, varsayalım *MyActivity* olan uygulaması içeren iki etkinlik, bileşik bir etkinliği *Activity1* ve *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="808b3-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span>  <span data-ttu-id="808b3-125">Ne zaman bu etkinlik bir iş akışına eklenir ve izleme sahip bir izleme profili etkinleştirilmiş `implementationVisibility` kümesine `RootScope`, izleme kayıtları yalnızca yayılan *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="808b3-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span>  <span data-ttu-id="808b3-126">Ancak, hiçbir kayıt etkinlikler için gösterilen *Activity1* ve *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="808b3-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="808b3-127">Ancak, varsa `implementationVisisbility` izleme profili kümesine özniteliğinin `All`, izleme kayıtları yalnızca için gösterilen sonra *MyActivity*, ancak etkinlikler için de *Activity1* ve  *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="808b3-127">However, if the `implementationVisisbility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="808b3-128">`implementationVisibility` Bayrağı uygulanır şu izleme kayıt türlerini için:</span><span class="sxs-lookup"><span data-stu-id="808b3-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>  
  
-   <span data-ttu-id="808b3-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="808b3-129">ActivityStateRecord</span></span>  
  
-   <span data-ttu-id="808b3-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="808b3-130">FaultPropagationRecord</span></span>  
  
-   <span data-ttu-id="808b3-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="808b3-131">CancelRequestedRecord</span></span>  
  
-   <span data-ttu-id="808b3-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="808b3-132">ActivityScheduledRecord</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="808b3-133">Etkinlik uygulamasından yayılan CustomTrackingRecords implementationVisibility ayarıyla filtrelendi değil.</span><span class="sxs-lookup"><span data-stu-id="808b3-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>  
  
 <span data-ttu-id="808b3-134">`implementationVisibility` İşlevselliği olarak belirtildiğinde <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> izlemeyi kodunun profilini oluşturma gibi:</span><span class="sxs-lookup"><span data-stu-id="808b3-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 <span data-ttu-id="808b3-135">`implementationVisibility` İşlevselliği olarak belirtildiğinde <xref:System.Activities.Tracking.ImplementationVisibility.All> izleme profili, yapılandırma dosyasında aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="808b3-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>  
  
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
  
 <span data-ttu-id="808b3-136">`ImplementationVisibility` İzleme profilindeki ayardır isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="808b3-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="808b3-137">Varsayılan olarak, değerini ayarlamak `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="808b3-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="808b3-138">Bu öznitelik değerlerini da büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="808b3-138">The values for this attribute are also case-sensitive.</span></span>  
  
### <a name="tracking-profile-query-types"></a><span data-ttu-id="808b3-139">İzleme profili sorgu türleri</span><span class="sxs-lookup"><span data-stu-id="808b3-139">Tracking Profile Query Types</span></span>  
 <span data-ttu-id="808b3-140">İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgu izin kayıtları izleme için bildirim temelli abonelikler olarak yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="808b3-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="808b3-141">Farklı sınıflardaki abone izin birkaç sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="808b3-142">Profilleri izleme yapılandırmasında veya kod aracılığıyla belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="808b3-143">En yaygın sorgu türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="808b3-143">Here are the most common query types:</span></span>  
  
-   <span data-ttu-id="808b3-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery>-Daha önce gösterildiği gibi iş akışı örneği yaşam döngüsü değişiklikleri izlemek için bunu kullanın `Started` ve `Completed`.</span><span class="sxs-lookup"><span data-stu-id="808b3-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="808b3-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:</span><span class="sxs-lookup"><span data-stu-id="808b3-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     <span data-ttu-id="808b3-146">İçin abone durumları belirtilen <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="808b3-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>  
  
     <span data-ttu-id="808b3-147">Yapılandırma veya iş akışı örneği düzeyi kayıtları için izleme abone olmak için kullanılan kod `Started` durumu örneğini kullanarak <xref:System.Activities.Tracking.WorkflowInstanceQuery> aşağıdaki örnekte gösterilen.</span><span class="sxs-lookup"><span data-stu-id="808b3-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
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
  
-   <span data-ttu-id="808b3-148"><xref:System.Activities.Tracking.ActivityStateQuery>-Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="808b3-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="808b3-149">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="808b3-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="808b3-150">Bu sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityStateRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="808b3-151">Abone olmak için kullanılabilir durumları belirtilen <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="808b3-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>  
  
     <span data-ttu-id="808b3-152">Yapılandırma ve kullanma etkinlik durumu izleme kayıtları abone olmak için kullanılan kod <xref:System.Activities.Tracking.ActivityStateQuery> için `SendEmailActivity` etkinlik, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
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
    >  <span data-ttu-id="808b3-153">Birden çok activityStateQuery öğeleri aynı ada sahipse, yalnızca son öğesinde durumları izleme profili kullanılır.</span><span class="sxs-lookup"><span data-stu-id="808b3-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>  
  
-   <span data-ttu-id="808b3-154"><xref:System.Activities.Tracking.ActivityScheduledQuery>-Bu sorgu, çalıştırılmak üzere zamanlanmış bir etkinlik üst etkinliği tarafından izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="808b3-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="808b3-155">Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.ActivityScheduledRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>  
  
     <span data-ttu-id="808b3-156">Kayıtlara abone olmak için kullanılan kod ve yapılandırma ile ilgili `SendEmailActivity` alt etkinlik kullanarak zamanlanma <xref:System.Activities.Tracking.ActivityScheduledQuery> aşağıdaki örnekte gösterilen.</span><span class="sxs-lookup"><span data-stu-id="808b3-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
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
  
-   <span data-ttu-id="808b3-157"><xref:System.Activities.Tracking.FaultPropagationQuery>-İçinde bir etkinlik oluşan hataların işlenmesi izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="808b3-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="808b3-158">Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.FaultPropagationRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>  
  
     <span data-ttu-id="808b3-159">Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili yayma hataya kullanmaya <xref:System.Activities.Tracking.FaultPropagationQuery> aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
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
  
-   <span data-ttu-id="808b3-160"><xref:System.Activities.Tracking.CancelRequestedQuery>-Alt etkinliği üst etkinlik tarafından iptal etme istekleri izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="808b3-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="808b3-161">Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CancelRequestedRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>  
  
     <span data-ttu-id="808b3-162">Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili iptal etkinlik kullanmaya <xref:System.Activities.Tracking.CancelRequestedQuery> aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
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
  
-   <span data-ttu-id="808b3-163"><xref:System.Activities.Tracking.CustomTrackingQuery>-Kod etkinliklerinizi tanımladığınız olaylarını izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="808b3-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="808b3-164">Sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.CustomTrackingRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>  
  
     <span data-ttu-id="808b3-165">Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili kullanarak özel izleme kayıtları <xref:System.Activities.Tracking.CustomTrackingQuery> aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
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
  
-   <span data-ttu-id="808b3-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery>-Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="808b3-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="808b3-167">Bu sorgu için gerekli olan bir <xref:System.Activities.Tracking.TrackingParticipant> abone olmak için <xref:System.Activities.Tracking.BookmarkResumptionRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="808b3-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>  
  
     <span data-ttu-id="808b3-168">Yapılandırma ve kayıtlara abone olmak için kullanılan kod ilgili sürdürme yer işareti kullanmaya <xref:System.Activities.Tracking.BookmarkResumptionQuery> aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="808b3-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
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
  
### <a name="annotations"></a><span data-ttu-id="808b3-169">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="808b3-169">Annotations</span></span>  
 <span data-ttu-id="808b3-170">Ek açıklamalar, rasgele yapı zamanından sonra yapılandırılmış bir değerle kayıtları izleme etiketi izin verir.</span><span class="sxs-lookup"><span data-stu-id="808b3-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="808b3-171">Örneğin, "Posta sunucusuyla" etiketli için çeşitli iş akışları arasında birkaç izleme kayıtları istiyor olabilirsiniz "Posta Sunucu1" ==.</span><span class="sxs-lookup"><span data-stu-id="808b3-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="808b3-172">Bu izleme kayıtları daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="808b3-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
 <span data-ttu-id="808b3-173">Bunu başarmak için ek açıklamanın izleme sorguda aşağıdaki örnekte gösterildiği gibi eklenir.</span><span class="sxs-lookup"><span data-stu-id="808b3-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>  
  
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
  
### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="808b3-174">İzleme profili oluşturma</span><span class="sxs-lookup"><span data-stu-id="808b3-174">How to Create a Tracking Profile</span></span>  
 <span data-ttu-id="808b3-175">İzleme sorgu öğeleri bir XML yapılandırma dosyası kullanarak bir izleme profili oluşturmak için kullanılan veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu.</span><span class="sxs-lookup"><span data-stu-id="808b3-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span>  <span data-ttu-id="808b3-176">Bir yapılandırma dosyası kullanılarak oluşturulan bir izleme profili bir örneği burada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="808b3-176">Here is an example of a tracking profile created using a configuration file.</span></span>  
  
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
>  <span data-ttu-id="808b3-177">İş akışı hizmeti ana bilgisayarı kullanarak WF izleme profili genellikle bir yapılandırma dosyası kullanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="808b3-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="808b3-178">İzleme profili kullanarak ve sorgu API izleme koduyla bir izleme profili oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="808b3-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>  
  
 <span data-ttu-id="808b3-179">XML yapılandırma dosyası olarak yapılandırılmış bir profil bir davranış uzantısı kullanılarak izleme Katılımcısı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="808b3-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="808b3-180">Bu sonraki bölümde açıklandığı gibi bir WorkflowServiceHost eklenir [yapılandırma izleme iş akışı için](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="808b3-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="808b3-181">Ana bilgisayar tarafından gösterilen izleme kayıtları ayrıntı izleme profilindeki yapılandırma ayarları tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="808b3-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="808b3-182">İzleme katılımcı bir izleme profili sorguları ekleyerek kayıtları izleme için abone olur.</span><span class="sxs-lookup"><span data-stu-id="808b3-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="808b3-183">Tüm izleme kayıtları abone olmak için izleme profili kullanarak tüm izleme sorguları belirtilmesi gerekiyor "*" ad alanlarında her sorgular.</span><span class="sxs-lookup"><span data-stu-id="808b3-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "*" in the name fields in each of the queries.</span></span>  
  
 <span data-ttu-id="808b3-184">Profilleri izleme ortak örnekleri bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="808b3-184">Here are some of the common examples of tracking profiles.</span></span>  
  
-   <span data-ttu-id="808b3-185">İş akışı örneği kayıtlarını ve hataları elde etmek için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="808b3-185">A tracking profile to obtain workflow instance records and faults.</span></span>  
  
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
  
1.  <span data-ttu-id="808b3-186">Tüm özel izleme kayıtları almak için bir izleme profili.</span><span class="sxs-lookup"><span data-stu-id="808b3-186">A tracking profile to obtain all custom tracking records.</span></span>  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a><span data-ttu-id="808b3-187">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="808b3-187">See Also</span></span>  
 [<span data-ttu-id="808b3-188">SQL İzleme</span><span class="sxs-lookup"><span data-stu-id="808b3-188">SQL Tracking</span></span>](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [<span data-ttu-id="808b3-189">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="808b3-189">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="808b3-190">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="808b3-190">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
