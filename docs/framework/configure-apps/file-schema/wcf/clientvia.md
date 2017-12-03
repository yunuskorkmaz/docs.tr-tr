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
ms.openlocfilehash: 3782eb9cbe793fef450c8b1c58456a1d4f7b0b94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="9a00e-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="9a00e-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="9a00e-103">Taşıma kanalı oluşturulmalıdır URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a00e-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="9a00e-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9a00e-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="9a00e-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9a00e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9a00e-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="9a00e-106">\<behaviors></span></span>  
<span data-ttu-id="9a00e-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9a00e-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="9a00e-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9a00e-108">\<behavior></span></span>  
<span data-ttu-id="9a00e-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="9a00e-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a00e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a00e-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a00e-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a00e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a00e-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a00e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a00e-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a00e-113">Attributes</span></span>  
  
|<span data-ttu-id="9a00e-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9a00e-114">Attribute</span></span>|<span data-ttu-id="9a00e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a00e-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="9a00e-116">Rotayı gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a00e-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a00e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a00e-117">Child Elements</span></span>  
 <span data-ttu-id="9a00e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9a00e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a00e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a00e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9a00e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a00e-120">Element</span></span>|<span data-ttu-id="9a00e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a00e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a00e-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9a00e-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9a00e-123">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a00e-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a00e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a00e-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
