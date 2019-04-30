---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757930"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="a1c5a-102">\<synchronousReceive > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1c5a-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="a1c5a-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti alma için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="a1c5a-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="a1c5a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a1c5a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1c5a-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a1c5a-106">\<behaviors></span></span>  
<span data-ttu-id="a1c5a-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a1c5a-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a1c5a-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a1c5a-108">\<behavior></span></span>  
<span data-ttu-id="a1c5a-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="a1c5a-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c5a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1c5a-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1c5a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1c5a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a1c5a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1c5a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1c5a-113">Attributes</span></span>  
 <span data-ttu-id="a1c5a-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1c5a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1c5a-115">Child Elements</span></span>  
 <span data-ttu-id="a1c5a-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1c5a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1c5a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a1c5a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1c5a-118">Element</span></span>|<span data-ttu-id="a1c5a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1c5a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1c5a-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a1c5a-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a1c5a-121">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1c5a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1c5a-122">Remarks</span></span>  
 <span data-ttu-id="a1c5a-123">Eş zamanlı alma kullanmak yerine varsayılan olarak zaman uyumsuz kanal dinleyicisi istemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="a1c5a-124">Windows Communication Foundation (WCF) pompa kabul edilen her kanal için yeni bir iş parçacığı verir.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="a1c5a-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c5a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1c5a-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
