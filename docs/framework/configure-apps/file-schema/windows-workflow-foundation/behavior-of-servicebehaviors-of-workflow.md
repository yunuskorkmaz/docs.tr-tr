---
title: <behavior><serviceBehaviors> iş akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398885"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="16c9f-102">\<iş akışının \<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="16c9f-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="16c9f-103">**Behavior** öğesi, bir hizmetin davranışına yönelik ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="16c9f-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="16c9f-104">Her davranışın **adına**göre dizini oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16c9f-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="16c9f-105">Hizmetler, [ \<uç nokta >](../wcf/endpoint-element.md) öğesinin **behaviorConfiguration** özniteliğini kullanarak bu ad aracılığıyla her davranışa bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="16c9f-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="16c9f-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="16c9f-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="16c9f-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16c9f-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16c9f-108">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="16c9f-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="16c9f-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="16c9f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="16c9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="16c9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="16c9f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<davranış >**</span><span class="sxs-lookup"><span data-stu-id="16c9f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c9f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16c9f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16c9f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16c9f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="16c9f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16c9f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16c9f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16c9f-115">Attributes</span></span>  
  
|<span data-ttu-id="16c9f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16c9f-116">Attribute</span></span>|<span data-ttu-id="16c9f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16c9f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16c9f-118">name</span><span class="sxs-lookup"><span data-stu-id="16c9f-118">name</span></span>|<span data-ttu-id="16c9f-119">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="16c9f-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="16c9f-120">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="16c9f-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16c9f-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16c9f-121">Child Elements</span></span>  
  
|<span data-ttu-id="16c9f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="16c9f-122">Element</span></span>|<span data-ttu-id="16c9f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16c9f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16c9f-124">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="16c9f-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="16c9f-125">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="16c9f-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="16c9f-126">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="16c9f-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="16c9f-127">Bir hizmetin, kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant>etw izlemeyi kullanmasına izin veren bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="16c9f-128">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="16c9f-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="16c9f-129">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="16c9f-130">\<SqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="16c9f-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="16c9f-131">İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="16c9f-132">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="16c9f-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="16c9f-133">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="16c9f-134">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="16c9f-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="16c9f-135">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="16c9f-136">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="16c9f-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="16c9f-137">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="16c9f-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16c9f-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16c9f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="16c9f-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="16c9f-139">Element</span></span>|<span data-ttu-id="16c9f-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16c9f-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16c9f-141">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="16c9f-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="16c9f-142">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="16c9f-142">A collection of service behavior elements.</span></span>|
