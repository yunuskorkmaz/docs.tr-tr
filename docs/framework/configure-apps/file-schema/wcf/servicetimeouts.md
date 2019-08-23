---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937089"
---
# <a name="servicetimeouts"></a><span data-ttu-id="3ea80-101">\<Servicetimeaşımları ></span><span class="sxs-lookup"><span data-stu-id="3ea80-101">\<serviceTimeouts></span></span>
<span data-ttu-id="3ea80-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ea80-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="3ea80-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ea80-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ea80-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3ea80-104">\<behaviors></span></span>  
<span data-ttu-id="3ea80-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3ea80-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3ea80-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="3ea80-106">\<behavior></span></span>  
<span data-ttu-id="3ea80-107">\<Servicetimeaşımları ></span><span class="sxs-lookup"><span data-stu-id="3ea80-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea80-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ea80-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="3ea80-109">Tür</span><span class="sxs-lookup"><span data-stu-id="3ea80-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea80-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ea80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea80-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ea80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea80-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ea80-112">Attributes</span></span>  
  
|<span data-ttu-id="3ea80-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3ea80-113">Attribute</span></span>|<span data-ttu-id="3ea80-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ea80-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="3ea80-115">Bir <xref:System.TimeSpan> işlemin istemciden sunucuya akışı gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3ea80-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="3ea80-116">Varsayılan değer "00:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="3ea80-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea80-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ea80-117">Child Elements</span></span>  
 <span data-ttu-id="3ea80-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ea80-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea80-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ea80-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea80-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ea80-120">Element</span></span>|<span data-ttu-id="3ea80-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ea80-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ea80-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="3ea80-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3ea80-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ea80-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea80-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ea80-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
