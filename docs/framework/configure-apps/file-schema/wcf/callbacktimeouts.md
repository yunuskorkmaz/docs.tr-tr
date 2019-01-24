---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 01932fe2b7b7e699311e2c65ec8adaf0aef82dc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557909"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="2098b-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="2098b-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="2098b-103">Bir çift yönlü bir geri çağırma anlaşması senaryosunda işlemleri sunucudan istemciye olan hareket akışındaki zaman zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2098b-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="2098b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2098b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2098b-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2098b-105">\<behaviors></span></span>  
<span data-ttu-id="2098b-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="2098b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2098b-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2098b-107">\<behavior></span></span>  
<span data-ttu-id="2098b-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="2098b-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2098b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2098b-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="2098b-110">Tür</span><span class="sxs-lookup"><span data-stu-id="2098b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2098b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2098b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2098b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2098b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2098b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2098b-113">Attributes</span></span>  
  
|<span data-ttu-id="2098b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2098b-114">Attribute</span></span>|<span data-ttu-id="2098b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2098b-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2098b-116">A <xref:System.TimeSpan> hangi hareketleri içinde zaman aralığını belirten bir değer tamamlanması veya otomatik olarak sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="2098b-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="2098b-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="2098b-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2098b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2098b-118">Child Elements</span></span>  
 <span data-ttu-id="2098b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2098b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2098b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2098b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2098b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2098b-121">Element</span></span>|<span data-ttu-id="2098b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2098b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2098b-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2098b-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2098b-124">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2098b-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2098b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2098b-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
