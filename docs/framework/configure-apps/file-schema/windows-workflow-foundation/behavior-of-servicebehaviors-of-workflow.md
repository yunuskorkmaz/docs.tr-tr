---
title: '&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 9b16aad6138d79d3dbff4994250f05d617d54140
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109543"
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="f3585-102">&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="f3585-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="f3585-103">**Davranışı** öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3585-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="f3585-104">Her davranış tarafından dizine kendi **adı**.</span><span class="sxs-lookup"><span data-stu-id="f3585-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="f3585-105">Hizmetleri bağlantısını kullanarak bu adı aracılığıyla her davranışı **behaviorConfiguration** özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="f3585-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="f3585-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3585-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="f3585-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3585-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3585-108">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f3585-108">\<behaviors></span></span>  
<span data-ttu-id="f3585-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f3585-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="f3585-110">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f3585-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3585-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3585-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3585-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3585-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f3585-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3585-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3585-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3585-114">Attributes</span></span>  
  
|<span data-ttu-id="f3585-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3585-115">Attribute</span></span>|<span data-ttu-id="f3585-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3585-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3585-117">name</span><span class="sxs-lookup"><span data-stu-id="f3585-117">name</span></span>|<span data-ttu-id="f3585-118">Davranış yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="f3585-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="f3585-119">Bu öğe için kimlik dizesi görür bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="f3585-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3585-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3585-120">Child Elements</span></span>  
  
|<span data-ttu-id="f3585-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3585-121">Element</span></span>|<span data-ttu-id="f3585-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3585-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3585-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="f3585-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="f3585-124">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f3585-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="f3585-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f3585-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="f3585-126">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışını bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="f3585-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="f3585-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="f3585-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="f3585-128">Özelleştirme düzeyleri, kanal üreteci önbellek ayarlarını ve ileti göndermek için hizmet bitiş noktası etkinlikler ileti gönderme kullanarak iş akışları için kanal önbellek ayarlarını paylaşımı önbellek sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f3585-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="f3585-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="f3585-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="f3585-130">Yapılandırmanıza olanak tanıyan bir hizmet davranışını <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> özellik, bir SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı hizmet örneklerine yönelik sürüyor durumu bilgileri destekler.</span><span class="sxs-lookup"><span data-stu-id="f3585-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="f3585-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="f3585-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="f3585-132">Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f3585-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="f3585-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="f3585-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="f3585-134">Nasıl iş akışı örnekleri, Kalıcılık, İşlenmeyen özel durum davranışını ve boşta davranışlarını çalıştırılır denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f3585-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="f3585-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="f3585-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="f3585-136">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="f3585-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3585-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3585-137">Parent Elements</span></span>  
  
|<span data-ttu-id="f3585-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3585-138">Element</span></span>|<span data-ttu-id="f3585-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3585-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3585-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f3585-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="f3585-141">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f3585-141">A collection of service behavior elements.</span></span>|
