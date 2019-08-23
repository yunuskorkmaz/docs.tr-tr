---
title: <behavior><serviceBehaviors> iş akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946074"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="9dc91-102">\<iş akışının \<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="9dc91-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="9dc91-103">**Behavior** öğesi, bir hizmetin davranışına yönelik ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9dc91-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="9dc91-104">Her davranışın **adına**göre dizini oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9dc91-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="9dc91-105">Hizmetler, [ \<uç nokta >](../wcf/endpoint-element.md) öğesinin **behaviorConfiguration** özniteliğini kullanarak bu ad aracılığıyla her davranışa bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9dc91-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="9dc91-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dc91-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="9dc91-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9dc91-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="9dc91-108">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9dc91-108">\<behaviors></span></span>  
<span data-ttu-id="9dc91-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9dc91-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="9dc91-110">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="9dc91-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc91-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dc91-111">Syntax</span></span>  
  
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
                                  hostLockRenewalPeriod="TimeSpan" 
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dc91-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dc91-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9dc91-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9dc91-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dc91-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9dc91-114">Attributes</span></span>  
  
|<span data-ttu-id="9dc91-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9dc91-115">Attribute</span></span>|<span data-ttu-id="9dc91-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dc91-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9dc91-117">name</span><span class="sxs-lookup"><span data-stu-id="9dc91-117">name</span></span>|<span data-ttu-id="9dc91-118">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="9dc91-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="9dc91-119">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9dc91-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dc91-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dc91-120">Child Elements</span></span>  
  
|<span data-ttu-id="9dc91-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dc91-121">Element</span></span>|<span data-ttu-id="9dc91-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dc91-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dc91-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="9dc91-123">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="9dc91-124">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9dc91-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="9dc91-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9dc91-125">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="9dc91-126">Bir hizmetin, kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant>etw izlemeyi kullanmasına izin veren bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="9dc91-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="9dc91-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="9dc91-128">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="9dc91-129">\<SqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="9dc91-129">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="9dc91-130">İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="9dc91-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="9dc91-131">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="9dc91-132">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="9dc91-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="9dc91-133">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="9dc91-134">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="9dc91-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="9dc91-135">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="9dc91-136">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dc91-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9dc91-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dc91-137">Parent Elements</span></span>  
  
|<span data-ttu-id="9dc91-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dc91-138">Element</span></span>|<span data-ttu-id="9dc91-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dc91-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dc91-140">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="9dc91-140">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="9dc91-141">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9dc91-141">A collection of service behavior elements.</span></span>|
