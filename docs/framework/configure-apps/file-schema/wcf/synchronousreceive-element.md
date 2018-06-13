---
title: '&lt;synchronousReceive&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753267"
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="bca91-102">&lt;synchronousReceive&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="bca91-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="bca91-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında iletileri almak için çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bca91-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="bca91-104">Herhangi bir öznitelik veya alt öğe yok.</span><span class="sxs-lookup"><span data-stu-id="bca91-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="bca91-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bca91-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bca91-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="bca91-106">\<behaviors></span></span>  
<span data-ttu-id="bca91-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bca91-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="bca91-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="bca91-108">\<behavior></span></span>  
<span data-ttu-id="bca91-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="bca91-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca91-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca91-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca91-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca91-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bca91-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bca91-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca91-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bca91-113">Attributes</span></span>  
 <span data-ttu-id="bca91-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="bca91-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bca91-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca91-115">Child Elements</span></span>  
 <span data-ttu-id="bca91-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="bca91-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca91-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca91-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bca91-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="bca91-118">Element</span></span>|<span data-ttu-id="bca91-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bca91-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bca91-120">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="bca91-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bca91-121">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca91-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca91-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bca91-122">Remarks</span></span>  
 <span data-ttu-id="bca91-123">Bu davranış varsayılan olarak zaman uyumsuz yerine bir zaman uyumlu alma kullanım kanal dinleyicisi istemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bca91-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="bca91-124">Windows Communication Foundation (WCF) pompa kabul edilen her kanal için yeni bir iş parçacığı verir.</span><span class="sxs-lookup"><span data-stu-id="bca91-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="bca91-125">Çok sayıda kanalları varsa, çalışan iş parçacığı dışında olasılığını yoktur.</span><span class="sxs-lookup"><span data-stu-id="bca91-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca91-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bca91-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
