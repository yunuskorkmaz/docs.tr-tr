---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176819"
---
# <a name="clientvia"></a><span data-ttu-id="8464b-101">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="8464b-101">\<clientVia></span></span>
<span data-ttu-id="8464b-102">Taşıma kanalının oluşturulması gereken URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="8464b-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="8464b-103">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="8464b-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="8464b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8464b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8464b-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8464b-105">\<behaviors></span></span>  
<span data-ttu-id="8464b-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8464b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8464b-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8464b-107">\<behavior></span></span>  
<span data-ttu-id="8464b-108">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="8464b-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8464b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8464b-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8464b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8464b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8464b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8464b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8464b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8464b-112">Attributes</span></span>  
  
|<span data-ttu-id="8464b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8464b-113">Attribute</span></span>|<span data-ttu-id="8464b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8464b-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="8464b-115">Yol gösteren bir URI belirten bir dize bir ileti almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8464b-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8464b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8464b-116">Child Elements</span></span>  
 <span data-ttu-id="8464b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8464b-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8464b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8464b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8464b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8464b-119">Element</span></span>|<span data-ttu-id="8464b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8464b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8464b-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8464b-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8464b-122">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8464b-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8464b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8464b-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
