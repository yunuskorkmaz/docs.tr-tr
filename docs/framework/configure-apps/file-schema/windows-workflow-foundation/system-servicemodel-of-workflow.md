---
title: "&lt;system.serviceModel&gt; iş akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54f8ae10491ebeed683a2ec289e60b9a90afd43b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemservicemodelgt-of-workflow"></a><span data-ttu-id="9257c-102">&lt;system.serviceModel&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="9257c-102">&lt;system.serviceModel&gt; of workflow</span></span>
<span data-ttu-id="9257c-103">Bu yapılandırma bölümü tüm iş akışı yapılandırma öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9257c-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9257c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9257c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9257c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9257c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9257c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9257c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9257c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9257c-107">Attributes</span></span>  
 <span data-ttu-id="9257c-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="9257c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9257c-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9257c-109">Child Elements</span></span>  
  
|<span data-ttu-id="9257c-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="9257c-110">Element</span></span>|<span data-ttu-id="9257c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9257c-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9257c-112">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="9257c-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="9257c-113">Bu bölümde tanımlar **serviceBehaviors** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9257c-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="9257c-114">Koleksiyondaki her öğe hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9257c-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="9257c-115">Her davranış öğesi kendi benzersiz tanımlanır **adı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9257c-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="9257c-116">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9257c-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="9257c-117">Bir iş akışı hizmeti izleme ayarlarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9257c-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="9257c-118">İş akışı izleme ve yapılandırmasını daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [yapılandırma izleme iş akışı için](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="9257c-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9257c-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9257c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9257c-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9257c-120">Element</span></span>|<span data-ttu-id="9257c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9257c-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9257c-122">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9257c-122">\<configuration></span></span>|<span data-ttu-id="9257c-123">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="9257c-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
