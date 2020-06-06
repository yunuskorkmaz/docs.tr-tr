---
title: <System. serviceModel> iş akışı
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151955"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="f0911-102">\<system.serviceModel>iş akışı</span><span class="sxs-lookup"><span data-stu-id="f0911-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="f0911-103">Bu yapılandırma bölümü tüm iş akışı yapılandırma öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f0911-103">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="f0911-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0911-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0911-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0911-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f0911-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0911-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0911-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0911-107">Attributes</span></span>  
 <span data-ttu-id="f0911-108">Yok</span><span class="sxs-lookup"><span data-stu-id="f0911-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0911-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0911-109">Child Elements</span></span>  
  
|<span data-ttu-id="f0911-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0911-110">Element</span></span>|<span data-ttu-id="f0911-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0911-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="f0911-112">Bu bölüm **Servicedavranışlar** koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0911-112">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="f0911-113">Koleksiyondaki her öğe hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0911-113">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="f0911-114">Her davranış öğesi, benzersiz **ad** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f0911-114">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="f0911-115">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0911-115">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="f0911-116">İş akışı izleme ve yapılandırması hakkında daha fazla bilgi için bkz. iş akışı [izleme ve izleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme yapılandırma](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="f0911-116">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0911-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0911-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f0911-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0911-118">Element</span></span>|<span data-ttu-id="f0911-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0911-119">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="f0911-120">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0911-120">The root element for all configuration elements in a .NET configuration file.</span></span>|
