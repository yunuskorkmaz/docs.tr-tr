---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173647"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="e5702-101">\<callbackTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e5702-101">\<callbackTimeouts></span></span>
<span data-ttu-id="e5702-102">Bir çift yönlü bir geri çağırma anlaşması senaryosunda işlemleri sunucudan istemciye olan hareket akışındaki zaman zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5702-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="e5702-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5702-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5702-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e5702-104">\<behaviors></span></span>  
<span data-ttu-id="e5702-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5702-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="e5702-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e5702-106">\<behavior></span></span>  
<span data-ttu-id="e5702-107">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="e5702-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5702-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5702-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="e5702-109">Tür</span><span class="sxs-lookup"><span data-stu-id="e5702-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5702-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5702-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e5702-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5702-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5702-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5702-112">Attributes</span></span>  
  
|<span data-ttu-id="e5702-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5702-113">Attribute</span></span>|<span data-ttu-id="e5702-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5702-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e5702-115">A <xref:System.TimeSpan> hangi hareketleri içinde zaman aralığını belirten bir değer tamamlanması veya otomatik olarak sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="e5702-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="e5702-116">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="e5702-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5702-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5702-117">Child Elements</span></span>  
 <span data-ttu-id="e5702-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5702-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5702-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5702-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e5702-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5702-120">Element</span></span>|<span data-ttu-id="e5702-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5702-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5702-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e5702-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e5702-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5702-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5702-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5702-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
