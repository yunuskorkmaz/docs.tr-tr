---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075528"
---
# <a name="servicetimeouts"></a><span data-ttu-id="eb4cb-101">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="eb4cb-101">\<serviceTimeouts></span></span>
<span data-ttu-id="eb4cb-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="eb4cb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb4cb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb4cb-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="eb4cb-104">\<behaviors></span></span>  
<span data-ttu-id="eb4cb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eb4cb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="eb4cb-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="eb4cb-106">\<behavior></span></span>  
<span data-ttu-id="eb4cb-107">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="eb4cb-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4cb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb4cb-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="eb4cb-109">Tür</span><span class="sxs-lookup"><span data-stu-id="eb4cb-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb4cb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb4cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eb4cb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb4cb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb4cb-112">Attributes</span></span>  
  
|<span data-ttu-id="eb4cb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eb4cb-113">Attribute</span></span>|<span data-ttu-id="eb4cb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb4cb-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="eb4cb-115">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="eb4cb-116">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="eb4cb-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb4cb-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb4cb-117">Child Elements</span></span>  
 <span data-ttu-id="eb4cb-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb4cb-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb4cb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eb4cb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb4cb-120">Element</span></span>|<span data-ttu-id="eb4cb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb4cb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb4cb-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="eb4cb-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="eb4cb-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb4cb-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
