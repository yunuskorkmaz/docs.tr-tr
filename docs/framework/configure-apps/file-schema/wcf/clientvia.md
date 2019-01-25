---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6491411d8cfe5c7a5a944f3b1cd728c9f0a4b852
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641219"
---
# <a name="ltclientviagt"></a><span data-ttu-id="826a3-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="826a3-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="826a3-103">Taşıma kanalının oluşturulması gereken URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="826a3-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="826a3-104">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="826a3-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="826a3-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="826a3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="826a3-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="826a3-106">\<behaviors></span></span>  
<span data-ttu-id="826a3-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="826a3-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="826a3-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="826a3-108">\<behavior></span></span>  
<span data-ttu-id="826a3-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="826a3-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826a3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="826a3-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="826a3-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="826a3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="826a3-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="826a3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="826a3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="826a3-113">Attributes</span></span>  
  
|<span data-ttu-id="826a3-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="826a3-114">Attribute</span></span>|<span data-ttu-id="826a3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="826a3-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="826a3-116">Yol gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="826a3-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="826a3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="826a3-117">Child Elements</span></span>  
 <span data-ttu-id="826a3-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="826a3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="826a3-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="826a3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="826a3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="826a3-120">Element</span></span>|<span data-ttu-id="826a3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="826a3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="826a3-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="826a3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="826a3-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="826a3-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="826a3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="826a3-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
