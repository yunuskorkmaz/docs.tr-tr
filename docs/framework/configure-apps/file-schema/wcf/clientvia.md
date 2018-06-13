---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6218bb3f205f2825eb3f10fabf834cfd0396ac87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754138"
---
# <a name="ltclientviagt"></a><span data-ttu-id="f4728-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="f4728-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="f4728-103">Taşıma kanalı oluşturulmalıdır URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4728-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="f4728-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f4728-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="f4728-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f4728-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4728-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f4728-106">\<behaviors></span></span>  
<span data-ttu-id="f4728-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f4728-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="f4728-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f4728-108">\<behavior></span></span>  
<span data-ttu-id="f4728-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="f4728-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4728-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4728-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4728-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4728-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4728-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4728-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4728-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4728-113">Attributes</span></span>  
  
|<span data-ttu-id="f4728-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4728-114">Attribute</span></span>|<span data-ttu-id="f4728-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4728-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="f4728-116">Rotayı gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4728-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4728-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4728-117">Child Elements</span></span>  
 <span data-ttu-id="f4728-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4728-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4728-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4728-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f4728-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4728-120">Element</span></span>|<span data-ttu-id="f4728-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4728-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4728-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f4728-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f4728-123">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4728-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4728-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4728-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
