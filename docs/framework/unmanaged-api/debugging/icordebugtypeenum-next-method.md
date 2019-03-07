---
title: ICorDebugTypeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43349dd3562b4480746948a0e65cc52580e377b3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470698"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="3c967-102">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c967-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="3c967-103">Tarafından belirtilen "ICorDebugType" örnek sayısını alır `celt` öğesinden geçerli konumunda başlayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3c967-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c967-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c967-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c967-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c967-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3c967-106">[in] Sayısını `ICorDebugType` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3c967-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3c967-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugType` nesne.</span><span class="sxs-lookup"><span data-stu-id="3c967-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3c967-108">[out] İşaretçi sayısına `ICorDebugType` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3c967-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="3c967-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="3c967-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c967-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c967-110">Requirements</span></span>  
 <span data-ttu-id="3c967-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c967-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c967-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c967-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c967-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c967-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c967-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c967-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c967-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c967-115">See also</span></span>

