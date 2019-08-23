---
title: < System. serviceModel > iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: faa8154c4d7ac5c6aa2f9f1707cf8f0d39eefad5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947361"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="aca62-102">\<iş akışının System. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="aca62-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="aca62-103">Bu yapılandırma bölümü tüm iş akışı yapılandırma öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="aca62-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aca62-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aca62-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aca62-105">Attributes and Elements</span></span>  
 <span data-ttu-id="aca62-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aca62-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aca62-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aca62-107">Attributes</span></span>  
 <span data-ttu-id="aca62-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="aca62-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aca62-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aca62-109">Child Elements</span></span>  
  
|<span data-ttu-id="aca62-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="aca62-110">Element</span></span>|<span data-ttu-id="aca62-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aca62-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aca62-112">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="aca62-112">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="aca62-113">Bu bölüm **Servicedavranışlar** koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aca62-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="aca62-114">Koleksiyondaki her öğe hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aca62-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="aca62-115">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="aca62-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="aca62-116">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="aca62-116">\<tracking></span></span>](tracking.md)|<span data-ttu-id="aca62-117">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aca62-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="aca62-118">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="aca62-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aca62-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aca62-119">Parent Elements</span></span>  
  
|<span data-ttu-id="aca62-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="aca62-120">Element</span></span>|<span data-ttu-id="aca62-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aca62-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aca62-122">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="aca62-122">\<configuration></span></span>|<span data-ttu-id="aca62-123">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="aca62-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
