---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 48e56b79f47e84122ddd4d7f55d50044510bfa66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149065"
---
# <a name="ltclientviagt"></a><span data-ttu-id="38471-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="38471-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="38471-103">Taşıma kanalının oluşturulması gereken URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="38471-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="38471-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="38471-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="38471-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="38471-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="38471-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="38471-106">\<behaviors></span></span>  
<span data-ttu-id="38471-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="38471-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="38471-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="38471-108">\<behavior></span></span>  
<span data-ttu-id="38471-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="38471-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38471-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38471-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38471-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="38471-111">Attributes and Elements</span></span>  
 <span data-ttu-id="38471-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38471-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38471-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38471-113">Attributes</span></span>  
  
|<span data-ttu-id="38471-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="38471-114">Attribute</span></span>|<span data-ttu-id="38471-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38471-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="38471-116">Yol gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38471-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38471-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="38471-117">Child Elements</span></span>  
 <span data-ttu-id="38471-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="38471-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38471-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="38471-119">Parent Elements</span></span>  
  
|<span data-ttu-id="38471-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="38471-120">Element</span></span>|<span data-ttu-id="38471-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38471-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38471-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="38471-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="38471-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="38471-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38471-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38471-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
