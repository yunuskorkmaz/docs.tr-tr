---
title: "&lt;synchronousReceive&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="005de-102">&lt;synchronousReceive&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="005de-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="005de-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında iletileri almak için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="005de-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="005de-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="005de-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="005de-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="005de-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="005de-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="005de-106">\<behaviors></span></span>  
<span data-ttu-id="005de-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="005de-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="005de-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="005de-108">\<behavior></span></span>  
<span data-ttu-id="005de-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="005de-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005de-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="005de-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="005de-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="005de-111">Attributes and Elements</span></span>  
 <span data-ttu-id="005de-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="005de-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="005de-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="005de-113">Attributes</span></span>  
 <span data-ttu-id="005de-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="005de-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="005de-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="005de-115">Child Elements</span></span>  
 <span data-ttu-id="005de-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="005de-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="005de-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="005de-117">Parent Elements</span></span>  
  
|<span data-ttu-id="005de-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="005de-118">Element</span></span>|<span data-ttu-id="005de-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="005de-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="005de-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="005de-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="005de-121">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="005de-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="005de-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="005de-122">Remarks</span></span>  
 <span data-ttu-id="005de-123">Bu davranış varsayılan olarak zaman uyumsuz yerine bir zaman uyumlu alma kullanım kanal dinleyicisi istemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="005de-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="005de-124">Yeni bir iş parçacığı için kabul edilen bir kanalı pompa verir.</span><span class="sxs-lookup"><span data-stu-id="005de-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="005de-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığını yoktur.</span><span class="sxs-lookup"><span data-stu-id="005de-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005de-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="005de-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
