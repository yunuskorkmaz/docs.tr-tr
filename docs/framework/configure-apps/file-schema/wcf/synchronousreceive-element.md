---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: f4a8868304ebae9a7ed5e6afbfb14fb2116afc49
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278485"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="05c66-102">\<synchronousReceive > öğesi</span><span class="sxs-lookup"><span data-stu-id="05c66-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="05c66-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti alma için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05c66-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="05c66-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="05c66-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="05c66-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05c66-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="05c66-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="05c66-106">\<behaviors></span></span>  
<span data-ttu-id="05c66-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="05c66-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="05c66-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="05c66-108">\<behavior></span></span>  
<span data-ttu-id="05c66-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="05c66-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c66-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05c66-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05c66-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c66-111">Attributes and Elements</span></span>  
 <span data-ttu-id="05c66-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05c66-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05c66-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05c66-113">Attributes</span></span>  
 <span data-ttu-id="05c66-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="05c66-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05c66-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c66-115">Child Elements</span></span>  
 <span data-ttu-id="05c66-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="05c66-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05c66-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c66-117">Parent Elements</span></span>  
  
|<span data-ttu-id="05c66-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="05c66-118">Element</span></span>|<span data-ttu-id="05c66-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c66-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c66-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="05c66-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="05c66-121">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="05c66-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05c66-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05c66-122">Remarks</span></span>  
 <span data-ttu-id="05c66-123">Eş zamanlı alma kullanmak yerine varsayılan olarak zaman uyumsuz kanal dinleyicisi istemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="05c66-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="05c66-124">Windows Communication Foundation (WCF) pompa kabul edilen her kanal için yeni bir iş parçacığı verir.</span><span class="sxs-lookup"><span data-stu-id="05c66-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="05c66-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="05c66-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c66-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05c66-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
