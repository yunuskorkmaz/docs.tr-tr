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
ms.openlocfilehash: bea357fe9a154ffb8f69228c7332c026dc2759e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728983"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="64d89-102">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d89-102">IEnumReferenceIdentity Interface</span></span>

<span data-ttu-id="64d89-103">Bir nesne koleksiyonu için bir Numaralandırıcı görevi görür `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="64d89-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64d89-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="64d89-104">Methods</span></span>  
  
|<span data-ttu-id="64d89-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="64d89-105">Method</span></span>|<span data-ttu-id="64d89-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d89-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="64d89-107">İle aynı üyeleri içeren yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="64d89-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="64d89-108">`IReferenceIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="64d89-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="64d89-109">Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="64d89-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="64d89-110">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="64d89-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64d89-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d89-111">Requirements</span></span>  

 <span data-ttu-id="64d89-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d89-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d89-113">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="64d89-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="64d89-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d89-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d89-115">See also</span></span>

- [<span data-ttu-id="64d89-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64d89-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="64d89-117">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d89-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
