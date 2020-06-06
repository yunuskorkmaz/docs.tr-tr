---
title: <behavior><serviceBehaviors>iş akışının
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152326"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="b97b3-102">\<behavior>\<serviceBehaviors>iş akışının</span><span class="sxs-lookup"><span data-stu-id="b97b3-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="b97b3-103">**Behavior** öğesi, bir hizmetin davranışına yönelik ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b97b3-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="b97b3-104">Her davranışın **adına**göre dizini oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b97b3-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="b97b3-105">Hizmetler, bu ad aracılığıyla her davranışa, öğesinin **behaviorConfiguration** özniteliğini kullanarak bağlanabilir [\<endpoint>](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b97b3-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="b97b3-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b97b3-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="b97b3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b97b3-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b97b3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b97b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b97b3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b97b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b97b3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b97b3-110">Attributes</span></span>  
  
|<span data-ttu-id="b97b3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b97b3-111">Attribute</span></span>|<span data-ttu-id="b97b3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b97b3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b97b3-113">name</span><span class="sxs-lookup"><span data-stu-id="b97b3-113">name</span></span>|<span data-ttu-id="b97b3-114">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="b97b3-114">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="b97b3-115">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b97b3-115">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b97b3-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b97b3-116">Child Elements</span></span>  
  
|<span data-ttu-id="b97b3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b97b3-117">Element</span></span>|<span data-ttu-id="b97b3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b97b3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="b97b3-119">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b97b3-119">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="b97b3-120">Bir hizmetin, kullanarak ETW izlemeyi kullanmasına izin veren bir hizmet davranışı <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="b97b3-120">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="b97b3-121">Önbellek paylaşım düzeylerinin özelleştirilmesine, kanal fabrikası önbelleğinin ayarlarına ve ileti gönderme etkinlikleri kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarına olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b97b3-121">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="b97b3-122"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>İş akışı hizmeti örnekleri için SQL Server 2005 veya SQL Server 2008 veritabanına yönelik kalıcı durum bilgilerini destekleyen özelliği yapılandırmanıza olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b97b3-122">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="b97b3-123">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b97b3-123">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="b97b3-124">Kalıcılık, işlenmemiş özel durum davranışı ve boşta davranış dahil, iş akışı örneklerinin nasıl çalıştırılacağını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b97b3-124">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="b97b3-125">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b97b3-125">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b97b3-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b97b3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b97b3-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="b97b3-127">Element</span></span>|<span data-ttu-id="b97b3-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b97b3-128">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="b97b3-129">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b97b3-129">A collection of service behavior elements.</span></span>|
