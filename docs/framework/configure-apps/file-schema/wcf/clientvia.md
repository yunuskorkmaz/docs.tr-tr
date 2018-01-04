---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a1870a8c331aae16ab14da62c64d6fb15ecd3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="d2325-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="d2325-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="d2325-103">Taşıma kanalı oluşturulmalıdır URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2325-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="d2325-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d2325-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="d2325-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d2325-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2325-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="d2325-106">\<behaviors></span></span>  
<span data-ttu-id="d2325-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d2325-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d2325-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d2325-108">\<behavior></span></span>  
<span data-ttu-id="d2325-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="d2325-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2325-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2325-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2325-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2325-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2325-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2325-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2325-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2325-113">Attributes</span></span>  
  
|<span data-ttu-id="d2325-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2325-114">Attribute</span></span>|<span data-ttu-id="d2325-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2325-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="d2325-116">Rotayı gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2325-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2325-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2325-117">Child Elements</span></span>  
 <span data-ttu-id="d2325-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2325-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2325-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2325-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d2325-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2325-120">Element</span></span>|<span data-ttu-id="d2325-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2325-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2325-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d2325-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d2325-123">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2325-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2325-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2325-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
