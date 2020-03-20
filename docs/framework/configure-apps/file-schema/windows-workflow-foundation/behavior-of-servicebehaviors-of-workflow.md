---
title: <behavior>iş <serviceBehaviors> akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152326"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="a6b08-102">\<hizmet davranış \<>İş akışı> Davranışlar</span><span class="sxs-lookup"><span data-stu-id="a6b08-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="a6b08-103">**Davranış** öğesi, bir hizmetin davranışı için ayarlar bir koleksiyon içerir.</span><span class="sxs-lookup"><span data-stu-id="a6b08-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="a6b08-104">Her davranış **kendi adıyla**dizine dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="a6b08-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="a6b08-105">Hizmetler, [ \<bitiş noktası>](../wcf/endpoint-element.md) öğesinin **davranışYapılandırma** özniteliğini kullanarak her davranışa bu ad üzerinden bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a6b08-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="a6b08-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6b08-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="a6b08-107">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6b08-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6b08-108">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a6b08-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a6b08-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a6b08-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="a6b08-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a6b08-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="a6b08-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<davranış>**</span><span class="sxs-lookup"><span data-stu-id="a6b08-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b08-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6b08-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6b08-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6b08-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a6b08-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6b08-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6b08-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6b08-115">Attributes</span></span>  
  
|<span data-ttu-id="a6b08-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6b08-116">Attribute</span></span>|<span data-ttu-id="a6b08-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6b08-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6b08-118">ad</span><span class="sxs-lookup"><span data-stu-id="a6b08-118">name</span></span>|<span data-ttu-id="a6b08-119">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6b08-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="a6b08-120">Bu değer, öğenin tanımlama dizesi olarak hareket ettiği için benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a6b08-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6b08-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6b08-121">Child Elements</span></span>  
  
|<span data-ttu-id="a6b08-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6b08-122">Element</span></span>|<span data-ttu-id="a6b08-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6b08-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6b08-124">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="a6b08-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="a6b08-125">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a6b08-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="a6b08-126">\<yönlendirme></span><span class="sxs-lookup"><span data-stu-id="a6b08-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="a6b08-127">Bir hizmetin ETW izlemesini kullanmasına izin <xref:System.Activities.Tracking.EtwTrackingParticipant>veren bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="a6b08-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="a6b08-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="a6b08-129">İleti gönder etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerinin, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmeyi sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="a6b08-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="a6b08-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="a6b08-131">İş akışı hizmeti örnekleri için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı durum bilgilerini bir SQL Server 2005 veya SQL Server 2008 veritabanında destekleyen özelliği yapılandırmanızı sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="a6b08-132">\<iş akışıBoş></span><span class="sxs-lookup"><span data-stu-id="a6b08-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="a6b08-133">Boşta kalan iş akışı örnekleri boşaldığında ve kalıcı olduğunda denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="a6b08-134">\<iş akışıInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="a6b08-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="a6b08-135">Kalıcılık, işlenmemiş Özel Durum davranışı ve boşta kalan davranışlar dahil olmak üzere iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenizi sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="a6b08-136">\<iş akışıUnhandledException></span><span class="sxs-lookup"><span data-stu-id="a6b08-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="a6b08-137">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6b08-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6b08-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6b08-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a6b08-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6b08-139">Element</span></span>|<span data-ttu-id="a6b08-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6b08-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6b08-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a6b08-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="a6b08-142">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a6b08-142">A collection of service behavior elements.</span></span>|
