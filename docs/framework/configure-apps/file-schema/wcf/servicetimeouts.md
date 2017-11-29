---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecefda0a3447aa029079fbb3633b05054f42195a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="9fec1-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="9fec1-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="9fec1-103">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fec1-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="9fec1-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9fec1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9fec1-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="9fec1-105">\<behaviors></span></span>  
<span data-ttu-id="9fec1-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9fec1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9fec1-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9fec1-107">\<behavior></span></span>  
<span data-ttu-id="9fec1-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="9fec1-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fec1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fec1-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="9fec1-110">Tür</span><span class="sxs-lookup"><span data-stu-id="9fec1-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fec1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fec1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9fec1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9fec1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fec1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9fec1-113">Attributes</span></span>  
  
|<span data-ttu-id="9fec1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9fec1-114">Attribute</span></span>|<span data-ttu-id="9fec1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fec1-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="9fec1-116">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gerekir zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="9fec1-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="9fec1-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="9fec1-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fec1-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fec1-118">Child Elements</span></span>  
 <span data-ttu-id="9fec1-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="9fec1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fec1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fec1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9fec1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9fec1-121">Element</span></span>|<span data-ttu-id="9fec1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fec1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fec1-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9fec1-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9fec1-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fec1-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fec1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fec1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
