---
title: IEnumReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f2ea9d0e20cb67cc36d0b5883e483ce98941b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743224"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="c6451-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6451-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="c6451-103">Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c6451-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6451-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c6451-104">Methods</span></span>  
  
|<span data-ttu-id="c6451-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6451-105">Method</span></span>|<span data-ttu-id="c6451-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6451-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="c6451-107">Yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` bu aynı üyeleri içeren `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c6451-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="c6451-108">Belirtilen sayıda alır `IReferenceIdentity` nesneleri, geçerli konumdan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="c6451-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="c6451-109">Yönerge işaretçisini bu başlangıcına taşır `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c6451-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="c6451-110">Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.</span><span class="sxs-lookup"><span data-stu-id="c6451-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6451-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6451-111">Requirements</span></span>  
 <span data-ttu-id="c6451-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6451-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6451-113">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c6451-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c6451-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6451-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6451-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6451-115">See also</span></span>
- [<span data-ttu-id="c6451-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c6451-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="c6451-117">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6451-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
