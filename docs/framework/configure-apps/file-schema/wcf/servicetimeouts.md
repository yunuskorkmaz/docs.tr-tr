---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075528"
---
# <a name="servicetimeouts"></a><span data-ttu-id="6f600-101">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="6f600-101">\<serviceTimeouts></span></span>
<span data-ttu-id="6f600-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f600-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="6f600-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6f600-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f600-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6f600-104">\<behaviors></span></span>  
<span data-ttu-id="6f600-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6f600-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6f600-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6f600-106">\<behavior></span></span>  
<span data-ttu-id="6f600-107">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="6f600-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f600-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f600-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="6f600-109">Tür</span><span class="sxs-lookup"><span data-stu-id="6f600-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f600-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f600-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6f600-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f600-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f600-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f600-112">Attributes</span></span>  
  
|<span data-ttu-id="6f600-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f600-113">Attribute</span></span>|<span data-ttu-id="6f600-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f600-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="6f600-115">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6f600-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="6f600-116">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="6f600-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f600-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f600-117">Child Elements</span></span>  
 <span data-ttu-id="6f600-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f600-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f600-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f600-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f600-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f600-120">Element</span></span>|<span data-ttu-id="6f600-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f600-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f600-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6f600-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6f600-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f600-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f600-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f600-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
