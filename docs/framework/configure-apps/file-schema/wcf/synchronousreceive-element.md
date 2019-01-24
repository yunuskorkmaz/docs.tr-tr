---
title: '&lt;synchronousReceive&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: dedbe156dea79c78f05acdb3a044c9080665675a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598901"
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="b6b0d-102">&lt;synchronousReceive&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="b6b0d-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="b6b0d-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti alma için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="b6b0d-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="b6b0d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6b0d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6b0d-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="b6b0d-106">\<behaviors></span></span>  
<span data-ttu-id="b6b0d-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b6b0d-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="b6b0d-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b6b0d-108">\<behavior></span></span>  
<span data-ttu-id="b6b0d-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="b6b0d-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b0d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6b0d-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6b0d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b0d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b6b0d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6b0d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b6b0d-113">Attributes</span></span>  
 <span data-ttu-id="b6b0d-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6b0d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b0d-115">Child Elements</span></span>  
 <span data-ttu-id="b6b0d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6b0d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b6b0d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b6b0d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b6b0d-118">Element</span></span>|<span data-ttu-id="b6b0d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6b0d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6b0d-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b6b0d-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b6b0d-121">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6b0d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6b0d-122">Remarks</span></span>  
 <span data-ttu-id="b6b0d-123">Eş zamanlı alma kullanmak yerine varsayılan olarak zaman uyumsuz kanal dinleyicisi istemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="b6b0d-124">Windows Communication Foundation (WCF) pompa kabul edilen her kanal için yeni bir iş parçacığı verir.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="b6b0d-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b0d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6b0d-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
