---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938961"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="43ab5-102">\<synchronousReceive > öğesi</span><span class="sxs-lookup"><span data-stu-id="43ab5-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="43ab5-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43ab5-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="43ab5-104">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="43ab5-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="43ab5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43ab5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="43ab5-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="43ab5-106">\<behaviors></span></span>  
<span data-ttu-id="43ab5-107">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="43ab5-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="43ab5-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="43ab5-108">\<behavior></span></span>  
<span data-ttu-id="43ab5-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="43ab5-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ab5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43ab5-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ab5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ab5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43ab5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43ab5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ab5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43ab5-113">Attributes</span></span>  
 <span data-ttu-id="43ab5-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="43ab5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43ab5-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ab5-115">Child Elements</span></span>  
 <span data-ttu-id="43ab5-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="43ab5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43ab5-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ab5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="43ab5-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="43ab5-118">Element</span></span>|<span data-ttu-id="43ab5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43ab5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43ab5-120">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="43ab5-120">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="43ab5-121">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="43ab5-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ab5-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43ab5-122">Remarks</span></span>  
 <span data-ttu-id="43ab5-123">Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="43ab5-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="43ab5-124">Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="43ab5-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="43ab5-125">Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="43ab5-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ab5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ab5-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
