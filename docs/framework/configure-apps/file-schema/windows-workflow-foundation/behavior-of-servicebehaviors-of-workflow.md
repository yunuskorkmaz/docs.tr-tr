---
title: '&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 303cf3a8f954b20beaa76fb46294dbb37488fd61
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="172b5-102">&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="172b5-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="172b5-103">**Davranışı** öğesi içeren bir hizmet davranışını için ayarlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="172b5-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="172b5-104">Her davranış tarafından dizine kendi **adı**.</span><span class="sxs-lookup"><span data-stu-id="172b5-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="172b5-105">Hizmetleri kullanarak bu ad aracılığıyla her davranış bağlanması **behaviorConfiguration**özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="172b5-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="172b5-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="172b5-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="172b5-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="172b5-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="172b5-108">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="172b5-108">\<behaviors></span></span>  
<span data-ttu-id="172b5-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="172b5-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="172b5-110">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="172b5-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172b5-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="172b5-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="172b5-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="172b5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="172b5-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="172b5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="172b5-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="172b5-114">Attributes</span></span>  
  
|<span data-ttu-id="172b5-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="172b5-115">Attribute</span></span>|<span data-ttu-id="172b5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="172b5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="172b5-117">name</span><span class="sxs-lookup"><span data-stu-id="172b5-117">name</span></span>|<span data-ttu-id="172b5-118">Davranış yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="172b5-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="172b5-119">Öğesinin kimlik dizesi olarak davranan bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="172b5-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="172b5-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="172b5-120">Child Elements</span></span>  
  
|<span data-ttu-id="172b5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="172b5-121">Element</span></span>|<span data-ttu-id="172b5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="172b5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="172b5-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="172b5-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="172b5-124">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="172b5-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="172b5-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="172b5-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="172b5-126">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışı bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="172b5-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="172b5-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="172b5-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="172b5-128">Paylaşım düzeyleri, kanal fabrikası önbellek ayarlarını ve ileti gönderme Mesajlaşma etkinlikleri kullanarak hizmet uç noktalarına gönderme iş akışları için kanal önbellek ayarlarını önbellek özelleştirmesini sağlar hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="172b5-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="172b5-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="172b5-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="172b5-130">Yapılandırmanıza olanak sağlayan bir hizmet davranışı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı hizmeti örneklerinin bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı durum bilgilerini destekleyen özelliği.</span><span class="sxs-lookup"><span data-stu-id="172b5-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="172b5-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="172b5-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="172b5-132">Boşta iş akışı örnekleri zaman kaldırıldı ve kalıcı denetimleri hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="172b5-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="172b5-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="172b5-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="172b5-134">Nasıl iş akışı örnekleri, Kalıcılık, işlenmemiş özel durum davranışını ve boşta davranışı dahil olmak üzere çalıştığını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="172b5-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="172b5-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="172b5-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="172b5-136">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="172b5-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="172b5-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="172b5-137">Parent Elements</span></span>  
  
|<span data-ttu-id="172b5-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="172b5-138">Element</span></span>|<span data-ttu-id="172b5-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="172b5-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="172b5-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="172b5-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="172b5-141">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="172b5-141">A collection of service behavior elements.</span></span>|
