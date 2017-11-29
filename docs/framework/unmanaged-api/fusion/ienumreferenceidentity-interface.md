---
title: IEnumReferenceIdentity Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="38f08-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38f08-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="38f08-103">Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="38f08-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38f08-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38f08-104">Methods</span></span>  
  
|<span data-ttu-id="38f08-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="38f08-105">Method</span></span>|<span data-ttu-id="38f08-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38f08-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="38f08-107">Arabirim işaretçisi yeni bir alır `IEnumReferenceIdentity` bu aynı üyeleri içeren `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="38f08-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="38f08-108">Belirtilen sayıda alır `IReferenceIdentity` geçerli konumdan başlayarak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="38f08-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="38f08-109">Yönerge işaretçisi başlangıcına bu taşır `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="38f08-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="38f08-110">Öğeler, geçerli konumdan başlayarak belirtilen sayıda tarafından yönerge işaretçisi İleri taşınır.</span><span class="sxs-lookup"><span data-stu-id="38f08-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38f08-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38f08-111">Requirements</span></span>  
 <span data-ttu-id="38f08-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f08-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f08-113">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="38f08-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="38f08-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f08-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38f08-115">See Also</span></span>  
 [<span data-ttu-id="38f08-116">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38f08-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="38f08-117">Ireferenceıdentity arabirimi</span><span class="sxs-lookup"><span data-stu-id="38f08-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
