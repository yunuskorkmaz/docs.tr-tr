---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399557"
---
# <a name="servicetimeouts"></a><span data-ttu-id="bc696-101">\<Servicetimeaşımları ></span><span class="sxs-lookup"><span data-stu-id="bc696-101">\<serviceTimeouts></span></span>
<span data-ttu-id="bc696-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc696-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="bc696-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc696-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc696-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc696-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc696-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc696-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bc696-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc696-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bc696-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc696-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bc696-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Servicetimeaşımları >**</span><span class="sxs-lookup"><span data-stu-id="bc696-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc696-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc696-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="bc696-110">Tür</span><span class="sxs-lookup"><span data-stu-id="bc696-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc696-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc696-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc696-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc696-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc696-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc696-113">Attributes</span></span>  
  
|<span data-ttu-id="bc696-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc696-114">Attribute</span></span>|<span data-ttu-id="bc696-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc696-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="bc696-116">Bir <xref:System.TimeSpan> işlemin istemciden sunucuya akışı gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bc696-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="bc696-117">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="bc696-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc696-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc696-118">Child Elements</span></span>  
 <span data-ttu-id="bc696-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc696-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc696-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc696-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bc696-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc696-121">Element</span></span>|<span data-ttu-id="bc696-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc696-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc696-123">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="bc696-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bc696-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc696-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc696-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc696-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
