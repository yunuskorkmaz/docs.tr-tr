---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919500"
---
# <a name="clientvia"></a><span data-ttu-id="7dfa9-101">\<> aracılığıyla Client</span><span class="sxs-lookup"><span data-stu-id="7dfa9-101">\<clientVia></span></span>
<span data-ttu-id="7dfa9-102">Taşıma kanalının oluşturulması gereken URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="7dfa9-103">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="7dfa9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7dfa9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7dfa9-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="7dfa9-105">\<behaviors></span></span>  
<span data-ttu-id="7dfa9-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="7dfa9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7dfa9-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="7dfa9-107">\<behavior></span></span>  
<span data-ttu-id="7dfa9-108">\<> aracılığıyla Client</span><span class="sxs-lookup"><span data-stu-id="7dfa9-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfa9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7dfa9-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dfa9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dfa9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7dfa9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dfa9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7dfa9-112">Attributes</span></span>  
  
|<span data-ttu-id="7dfa9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7dfa9-113">Attribute</span></span>|<span data-ttu-id="7dfa9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dfa9-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="7dfa9-115">Bir iletinin gerçekleşmesi gereken yolu gösteren bir URI belirten dize.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7dfa9-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dfa9-116">Child Elements</span></span>  
 <span data-ttu-id="7dfa9-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7dfa9-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dfa9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7dfa9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7dfa9-119">Element</span></span>|<span data-ttu-id="7dfa9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dfa9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dfa9-121">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="7dfa9-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7dfa9-122">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7dfa9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dfa9-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
