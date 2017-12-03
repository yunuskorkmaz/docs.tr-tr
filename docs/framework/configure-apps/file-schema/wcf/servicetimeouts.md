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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6d2940a4c4615a922efcc74802a82adbe10267c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="83d35-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="83d35-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="83d35-103">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="83d35-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="83d35-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="83d35-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="83d35-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="83d35-105">\<behaviors></span></span>  
<span data-ttu-id="83d35-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="83d35-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="83d35-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="83d35-107">\<behavior></span></span>  
<span data-ttu-id="83d35-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="83d35-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d35-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83d35-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="83d35-110">Tür</span><span class="sxs-lookup"><span data-stu-id="83d35-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83d35-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83d35-111">Attributes and Elements</span></span>  
 <span data-ttu-id="83d35-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83d35-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83d35-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83d35-113">Attributes</span></span>  
  
|<span data-ttu-id="83d35-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="83d35-114">Attribute</span></span>|<span data-ttu-id="83d35-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83d35-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="83d35-116">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gerekir zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="83d35-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="83d35-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="83d35-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83d35-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83d35-118">Child Elements</span></span>  
 <span data-ttu-id="83d35-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="83d35-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83d35-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83d35-120">Parent Elements</span></span>  
  
|<span data-ttu-id="83d35-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="83d35-121">Element</span></span>|<span data-ttu-id="83d35-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83d35-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83d35-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="83d35-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="83d35-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="83d35-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83d35-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83d35-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
