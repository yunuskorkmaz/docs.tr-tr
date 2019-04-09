---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166549"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="d9a87-102">\<synchronousReceive > öğesi</span><span class="sxs-lookup"><span data-stu-id="d9a87-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="d9a87-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti alma için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9a87-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="d9a87-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="d9a87-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="d9a87-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9a87-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9a87-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d9a87-106">\<behaviors></span></span>  
<span data-ttu-id="d9a87-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9a87-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d9a87-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d9a87-108">\<behavior></span></span>  
<span data-ttu-id="d9a87-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="d9a87-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a87-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9a87-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9a87-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9a87-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d9a87-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9a87-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9a87-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9a87-113">Attributes</span></span>  
 <span data-ttu-id="d9a87-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9a87-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9a87-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9a87-115">Child Elements</span></span>  
 <span data-ttu-id="d9a87-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9a87-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9a87-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9a87-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d9a87-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9a87-118">Element</span></span>|<span data-ttu-id="d9a87-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9a87-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9a87-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d9a87-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d9a87-121">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9a87-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9a87-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9a87-122">Remarks</span></span>  
 <span data-ttu-id="d9a87-123">Eş zamanlı alma kullanmak yerine varsayılan olarak zaman uyumsuz kanal dinleyicisi istemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9a87-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="d9a87-124">Windows Communication Foundation (WCF) pompa kabul edilen her kanal için yeni bir iş parçacığı verir.</span><span class="sxs-lookup"><span data-stu-id="d9a87-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="d9a87-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9a87-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a87-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9a87-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
