---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758099"
---
# <a name="servicetimeouts"></a><span data-ttu-id="10e00-101">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="10e00-101">\<serviceTimeouts></span></span>
<span data-ttu-id="10e00-102">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e00-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="10e00-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10e00-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="10e00-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="10e00-104">\<behaviors></span></span>  
<span data-ttu-id="10e00-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="10e00-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="10e00-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="10e00-106">\<behavior></span></span>  
<span data-ttu-id="10e00-107">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="10e00-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e00-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10e00-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="10e00-109">Tür</span><span class="sxs-lookup"><span data-stu-id="10e00-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10e00-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e00-110">Attributes and Elements</span></span>  
 <span data-ttu-id="10e00-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10e00-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10e00-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10e00-112">Attributes</span></span>  
  
|<span data-ttu-id="10e00-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10e00-113">Attribute</span></span>|<span data-ttu-id="10e00-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e00-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="10e00-115">A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gereken zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="10e00-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="10e00-116">Varsayılan değer "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="10e00-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10e00-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e00-117">Child Elements</span></span>  
 <span data-ttu-id="10e00-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="10e00-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10e00-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10e00-119">Parent Elements</span></span>  
  
|<span data-ttu-id="10e00-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="10e00-120">Element</span></span>|<span data-ttu-id="10e00-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10e00-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10e00-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="10e00-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="10e00-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="10e00-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10e00-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10e00-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
