---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc89a4b9735c13429b31d8cd7c5995f641afa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="fdddd-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="fdddd-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="fdddd-103">Çift yönlü geri çağırma sözleşme senaryo client.in sunucusundan hareketleri akan zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdddd-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="fdddd-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fdddd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fdddd-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="fdddd-105">\<behaviors></span></span>  
<span data-ttu-id="fdddd-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fdddd-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="fdddd-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fdddd-107">\<behavior></span></span>  
<span data-ttu-id="fdddd-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="fdddd-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdddd-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdddd-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="fdddd-110">Tür</span><span class="sxs-lookup"><span data-stu-id="fdddd-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdddd-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdddd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fdddd-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdddd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdddd-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fdddd-113">Attributes</span></span>  
  
|<span data-ttu-id="fdddd-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fdddd-114">Attribute</span></span>|<span data-ttu-id="fdddd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdddd-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="fdddd-116">A <xref:System.TimeSpan> hangi hareketleri içinde zaman aralığını belirten değer tamamlamanız gerekir ya da otomatik olarak sona erdirilecek.</span><span class="sxs-lookup"><span data-stu-id="fdddd-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="fdddd-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="fdddd-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdddd-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdddd-118">Child Elements</span></span>  
 <span data-ttu-id="fdddd-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdddd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdddd-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdddd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fdddd-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fdddd-121">Element</span></span>|<span data-ttu-id="fdddd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdddd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdddd-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fdddd-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fdddd-124">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdddd-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdddd-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdddd-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
