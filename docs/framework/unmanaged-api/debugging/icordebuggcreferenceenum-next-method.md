---
title: ICorDebugGCReferenceEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f76b727511ad604c407fb2998a5ecea26f91c49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481371"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="990a2-102">ICorDebugGCReferenceEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="990a2-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="990a2-103">Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) atık olarak toplanmış olan nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="990a2-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="990a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="990a2-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="990a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="990a2-105">Parameters</span></span>  
 <span data-ttu-id="990a2-106">celt</span><span class="sxs-lookup"><span data-stu-id="990a2-106">celt</span></span>  
 <span data-ttu-id="990a2-107">[in] Alınacak kökleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="990a2-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="990a2-108">kökler</span><span class="sxs-lookup"><span data-stu-id="990a2-108">roots</span></span>  
 <span data-ttu-id="990a2-109">[out] Bir dizi işaretçileri, her biri için işaret eden bir [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) kök olarak atık olarak toplanmış bir nesneyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="990a2-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="990a2-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="990a2-110">pceltFetched</span></span>  
 <span data-ttu-id="990a2-111">[out] Bir işaretçi sayısına [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) gerçekte döndürülen nesneleri `roots`.</span><span class="sxs-lookup"><span data-stu-id="990a2-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="990a2-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="990a2-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="990a2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="990a2-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="990a2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="990a2-114">Requirements</span></span>  
 <span data-ttu-id="990a2-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="990a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="990a2-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="990a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="990a2-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="990a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="990a2-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="990a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="990a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="990a2-119">See also</span></span>
- [<span data-ttu-id="990a2-120">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="990a2-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="990a2-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="990a2-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
