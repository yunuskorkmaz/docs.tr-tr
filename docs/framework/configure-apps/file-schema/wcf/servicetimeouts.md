---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a0f0725bffe0c3c83e412348dea97b16736ef3a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743478"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="d38e5-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="d38e5-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="d38e5-103">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d38e5-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="d38e5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d38e5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d38e5-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="d38e5-105">\<behaviors></span></span>  
<span data-ttu-id="d38e5-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d38e5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d38e5-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d38e5-107">\<behavior></span></span>  
<span data-ttu-id="d38e5-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="d38e5-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d38e5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d38e5-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="d38e5-110">Tür</span><span class="sxs-lookup"><span data-stu-id="d38e5-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d38e5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d38e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d38e5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d38e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d38e5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d38e5-113">Attributes</span></span>  
  
|<span data-ttu-id="d38e5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d38e5-114">Attribute</span></span>|<span data-ttu-id="d38e5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d38e5-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="d38e5-116">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gerekir zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d38e5-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="d38e5-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="d38e5-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d38e5-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d38e5-118">Child Elements</span></span>  
 <span data-ttu-id="d38e5-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d38e5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d38e5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d38e5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d38e5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d38e5-121">Element</span></span>|<span data-ttu-id="d38e5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d38e5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d38e5-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d38e5-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d38e5-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d38e5-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d38e5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d38e5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
