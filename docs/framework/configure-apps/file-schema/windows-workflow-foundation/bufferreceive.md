---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398841"
---
# <a name="bufferreceive"></a><span data-ttu-id="78408-101">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="78408-101">\<bufferReceive></span></span>
<span data-ttu-id="78408-102">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="78408-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="78408-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78408-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78408-104">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78408-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="78408-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78408-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="78408-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78408-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="78408-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="78408-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="78408-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bufferReceive >**</span><span class="sxs-lookup"><span data-stu-id="78408-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78408-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78408-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78408-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78408-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78408-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78408-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78408-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78408-112">Attributes</span></span>  
  
|<span data-ttu-id="78408-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78408-113">Attribute</span></span>|<span data-ttu-id="78408-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78408-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78408-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="78408-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="78408-116">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="78408-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="78408-117">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="78408-117">The default value is 512.</span></span> <span data-ttu-id="78408-118">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="78408-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78408-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78408-119">Child Elements</span></span>  
 <span data-ttu-id="78408-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="78408-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78408-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78408-121">Parent Elements</span></span>  
  
|<span data-ttu-id="78408-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="78408-122">Element</span></span>|<span data-ttu-id="78408-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78408-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78408-124">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="78408-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="78408-125">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="78408-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78408-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78408-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
