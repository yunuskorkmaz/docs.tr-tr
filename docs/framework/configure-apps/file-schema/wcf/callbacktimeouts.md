---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 48da0351d162a2143a26cc5b9eaa05b731358639
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749572"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="2bd37-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="2bd37-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="2bd37-103">Çift yönlü geri çağırma sözleşme senaryo client.in sunucusundan hareketleri akan zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bd37-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="2bd37-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2bd37-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2bd37-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="2bd37-105">\<behaviors></span></span>  
<span data-ttu-id="2bd37-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2bd37-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2bd37-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2bd37-107">\<behavior></span></span>  
<span data-ttu-id="2bd37-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="2bd37-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd37-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bd37-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="2bd37-110">Tür</span><span class="sxs-lookup"><span data-stu-id="2bd37-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bd37-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bd37-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2bd37-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2bd37-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bd37-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2bd37-113">Attributes</span></span>  
  
|<span data-ttu-id="2bd37-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2bd37-114">Attribute</span></span>|<span data-ttu-id="2bd37-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bd37-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2bd37-116">A <xref:System.TimeSpan> hangi hareketleri içinde zaman aralığını belirten değer tamamlamanız gerekir ya da otomatik olarak sona erdirilecek.</span><span class="sxs-lookup"><span data-stu-id="2bd37-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="2bd37-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="2bd37-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bd37-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bd37-118">Child Elements</span></span>  
 <span data-ttu-id="2bd37-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2bd37-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bd37-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2bd37-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2bd37-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2bd37-121">Element</span></span>|<span data-ttu-id="2bd37-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bd37-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bd37-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2bd37-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2bd37-124">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2bd37-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bd37-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bd37-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
