---
title: ICorDebugObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a1c0f7deb2ef24893530797b4507e2dcc540ad2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757052"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="9bb8f-102">ICorDebugObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bb8f-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="9bb8f-103">Geçerli konumunda başlayan sabit listesi, belirli sayıda nesneleri, göreli sanal adreslerine (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bb8f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bb8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bb8f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9bb8f-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9bb8f-107">[out] Bir dizi işaretçileri, her biri bir CORDB_ADDRESS nesneye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9bb8f-108">[out] Gerçekte döndürülen nesne sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="9bb8f-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb8f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bb8f-110">Requirements</span></span>  
 <span data-ttu-id="9bb8f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb8f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb8f-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bb8f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bb8f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bb8f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bb8f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb8f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-115">See also</span></span>
