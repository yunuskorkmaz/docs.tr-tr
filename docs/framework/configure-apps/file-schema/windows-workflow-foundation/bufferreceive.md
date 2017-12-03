---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fc3fb901e0f70b616f403b98abc7b9645b2b44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="0a19f-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="0a19f-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="0a19f-103">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="0a19f-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="0a19f-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0a19f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a19f-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="0a19f-105">\<behaviors></span></span>  
<span data-ttu-id="0a19f-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0a19f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0a19f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="0a19f-107">\<behavior></span></span>  
<span data-ttu-id="0a19f-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="0a19f-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a19f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a19f-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a19f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a19f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a19f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a19f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a19f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a19f-112">Attributes</span></span>  
  
|<span data-ttu-id="0a19f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a19f-113">Attribute</span></span>|<span data-ttu-id="0a19f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a19f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a19f-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="0a19f-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="0a19f-116">Bekleyen iletileri her kanal için izin verilen maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0a19f-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="0a19f-117">Varsayılan değer 512'dır.</span><span class="sxs-lookup"><span data-stu-id="0a19f-117">The default value is 512.</span></span> <span data-ttu-id="0a19f-118">Bu özellik, bir iş akışı hizmeti tarafından alınan sırası iletilerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="0a19f-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a19f-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a19f-119">Child Elements</span></span>  
 <span data-ttu-id="0a19f-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="0a19f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a19f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a19f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0a19f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a19f-122">Element</span></span>|<span data-ttu-id="0a19f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a19f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a19f-124">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0a19f-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0a19f-125">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a19f-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a19f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a19f-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
