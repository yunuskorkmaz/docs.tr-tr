---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: f7aa623ee387f67f3bbff32249d3695049359cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524474"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="a121d-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="a121d-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="a121d-103">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a121d-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="a121d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a121d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a121d-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a121d-105">\<behaviors></span></span>  
<span data-ttu-id="a121d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a121d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a121d-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a121d-107">\<behavior></span></span>  
<span data-ttu-id="a121d-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="a121d-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a121d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a121d-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a121d-110">Tür</span><span class="sxs-lookup"><span data-stu-id="a121d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a121d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a121d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a121d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a121d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a121d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a121d-113">Attributes</span></span>  
  
|<span data-ttu-id="a121d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a121d-114">Attribute</span></span>|<span data-ttu-id="a121d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a121d-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a121d-116">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a121d-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="a121d-117">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="a121d-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a121d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a121d-118">Child Elements</span></span>  
 <span data-ttu-id="a121d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="a121d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a121d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a121d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a121d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a121d-121">Element</span></span>|<span data-ttu-id="a121d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a121d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a121d-123">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a121d-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a121d-124">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a121d-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a121d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a121d-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
