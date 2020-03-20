---
title: <system.serviceModel> iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151955"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="1359d-102">\<system.serviceModel iş akışı></span><span class="sxs-lookup"><span data-stu-id="1359d-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="1359d-103">Bu yapılandırma bölümü tüm iş akışı yapılandırma öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1359d-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="1359d-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1359d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1359d-105">&nbsp;&nbsp;**\<Sistem. ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="1359d-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1359d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1359d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1359d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1359d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1359d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1359d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1359d-109">Attributes</span></span>  
 <span data-ttu-id="1359d-110">None</span><span class="sxs-lookup"><span data-stu-id="1359d-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1359d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359d-111">Child Elements</span></span>  
  
|<span data-ttu-id="1359d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="1359d-112">Element</span></span>|<span data-ttu-id="1359d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1359d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1359d-114">\<davranışlar></span><span class="sxs-lookup"><span data-stu-id="1359d-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="1359d-115">Bu bölümde **serviceBehaviors** koleksiyonu tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1359d-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="1359d-116">Koleksiyondaki her öğe hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1359d-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="1359d-117">Her davranış öğesi benzersiz **ad** özniteliği ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1359d-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="1359d-118">\<izleme></span><span class="sxs-lookup"><span data-stu-id="1359d-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="1359d-119">İş akışı hizmeti için izleme ayarlarını tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1359d-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="1359d-120">İş akışı izleme ve yapılandırmasında daha fazla bilgi için [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md) [bkz.](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="1359d-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1359d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1359d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1359d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1359d-122">Element</span></span>|<span data-ttu-id="1359d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1359d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1359d-124">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="1359d-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="1359d-125">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="1359d-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
