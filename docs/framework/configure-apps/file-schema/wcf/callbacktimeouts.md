---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269074"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="5ed94-101">\<callbackTimeouts ></span><span class="sxs-lookup"><span data-stu-id="5ed94-101">\<callbackTimeouts></span></span>
<span data-ttu-id="5ed94-102">Bir çift yönlü bir geri çağırma anlaşması senaryosunda işlemleri sunucudan istemciye olan hareket akışındaki zaman zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ed94-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="5ed94-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ed94-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ed94-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5ed94-104">\<behaviors></span></span>  
<span data-ttu-id="5ed94-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ed94-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="5ed94-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5ed94-106">\<behavior></span></span>  
<span data-ttu-id="5ed94-107">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="5ed94-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed94-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ed94-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="5ed94-109">Tür</span><span class="sxs-lookup"><span data-stu-id="5ed94-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ed94-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed94-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ed94-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ed94-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ed94-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ed94-112">Attributes</span></span>  
  
|<span data-ttu-id="5ed94-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ed94-113">Attribute</span></span>|<span data-ttu-id="5ed94-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ed94-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="5ed94-115">A <xref:System.TimeSpan> hangi hareketleri içinde zaman aralığını belirten bir değer tamamlanması veya otomatik olarak sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="5ed94-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="5ed94-116">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="5ed94-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ed94-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed94-117">Child Elements</span></span>  
 <span data-ttu-id="5ed94-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ed94-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ed94-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ed94-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5ed94-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ed94-120">Element</span></span>|<span data-ttu-id="5ed94-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ed94-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ed94-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5ed94-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5ed94-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ed94-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ed94-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed94-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
