---
title: <synchronousReceive> öğesi
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399506"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="bc002-102">\<synchronousReceive > öğesi</span><span class="sxs-lookup"><span data-stu-id="bc002-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="bc002-103">Bu yapılandırma öğesi, bir hizmet veya istemci uygulamasında ileti almaya yönelik çalışma zamanı davranışını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc002-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="bc002-104">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bc002-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="bc002-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc002-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc002-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc002-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc002-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc002-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bc002-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc002-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc002-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc002-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc002-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<synchronousReceive >**</span><span class="sxs-lookup"><span data-stu-id="bc002-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc002-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc002-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc002-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc002-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bc002-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc002-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc002-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc002-114">Attributes</span></span>  
 <span data-ttu-id="bc002-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc002-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc002-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc002-116">Child Elements</span></span>  
 <span data-ttu-id="bc002-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc002-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc002-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc002-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc002-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc002-119">Element</span></span>|<span data-ttu-id="bc002-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc002-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc002-121">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="bc002-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bc002-122">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc002-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc002-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc002-123">Remarks</span></span>  
 <span data-ttu-id="bc002-124">Kanal dinleyicisine varsayılan, zaman uyumsuz yerine zaman uyumlu alma kullanmasını söylemek için bu davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc002-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="bc002-125">Windows Communication Foundation (WCF), kabul edilen her kanal için yeni bir iş parçacığı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="bc002-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="bc002-126">Çok sayıda kanal varsa, iş parçacıklarının tükenme olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="bc002-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc002-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc002-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
