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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cdc85c23202154728610ab4721bf830004928c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="5bba9-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="5bba9-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="5bba9-103">Taşıma kanalı oluşturulmalıdır URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bba9-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="5bba9-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="5bba9-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="5bba9-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5bba9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5bba9-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5bba9-106">\<behaviors></span></span>  
<span data-ttu-id="5bba9-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5bba9-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="5bba9-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5bba9-108">\<behavior></span></span>  
<span data-ttu-id="5bba9-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="5bba9-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bba9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bba9-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bba9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bba9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5bba9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bba9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bba9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bba9-113">Attributes</span></span>  
  
|<span data-ttu-id="5bba9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5bba9-114">Attribute</span></span>|<span data-ttu-id="5bba9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bba9-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="5bba9-116">Rotayı gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bba9-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bba9-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bba9-117">Child Elements</span></span>  
 <span data-ttu-id="5bba9-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bba9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bba9-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bba9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5bba9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bba9-120">Element</span></span>|<span data-ttu-id="5bba9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bba9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bba9-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5bba9-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5bba9-123">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bba9-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bba9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5bba9-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
