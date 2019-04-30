---
title: < system.serviceModel > İş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 005a274df9e9ab99227a3748b7a25c9d465d020f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768881"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="d1083-102">\<system.serviceModel > İş akışı</span><span class="sxs-lookup"><span data-stu-id="d1083-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="d1083-103">Bu yapılandırma bölümü tüm iş akışı yapılandırma öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d1083-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1083-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1083-104">Syntax</span></span>  
  
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
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1083-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1083-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d1083-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1083-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1083-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1083-107">Attributes</span></span>  
 <span data-ttu-id="d1083-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1083-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1083-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1083-109">Child Elements</span></span>  
  
|<span data-ttu-id="d1083-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1083-110">Element</span></span>|<span data-ttu-id="d1083-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1083-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1083-112">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d1083-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="d1083-113">Bu bölüm tanımlar **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1083-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="d1083-114">Koleksiyondaki her öğe hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1083-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="d1083-115">Her davranışı öğesi kendi benzersiz tarafından tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d1083-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="d1083-116">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d1083-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d1083-117">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d1083-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="d1083-118">İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [yapılandırma izleme için bir iş akışı](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d1083-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1083-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1083-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d1083-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1083-120">Element</span></span>|<span data-ttu-id="d1083-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1083-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1083-122">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d1083-122">\<configuration></span></span>|<span data-ttu-id="d1083-123">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="d1083-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
