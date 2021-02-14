---
description: 'Şu konuda daha fazla bilgi edinin: IEnumReferenceIdentity arabirimi'
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
ms.openlocfilehash: a7f17793fd737b5153c27dae59fb2aa87b46cf48
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465307"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="38223-103">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38223-103">IEnumReferenceIdentity Interface</span></span>

<span data-ttu-id="38223-104">Bir nesne koleksiyonu için bir Numaralandırıcı görevi görür `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="38223-104">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38223-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38223-105">Methods</span></span>  
  
|<span data-ttu-id="38223-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="38223-106">Method</span></span>|<span data-ttu-id="38223-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38223-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="38223-108">İle aynı üyeleri içeren yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="38223-108">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="38223-109">`IReferenceIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="38223-109">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="38223-110">Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="38223-110">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="38223-111">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="38223-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38223-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38223-112">Requirements</span></span>  

 <span data-ttu-id="38223-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38223-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38223-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="38223-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="38223-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38223-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38223-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38223-116">See also</span></span>

- [<span data-ttu-id="38223-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38223-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="38223-118">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38223-118">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
