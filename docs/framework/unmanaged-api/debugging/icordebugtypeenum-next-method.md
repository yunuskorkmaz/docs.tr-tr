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
ms.openlocfilehash: bf70d8665d3984c379da9d9058cd97315def7b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677686"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="7c9d2-102">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c9d2-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="7c9d2-103">Tarafından belirtilen "ICorDebugType" örnek sayısını alır `celt` öğesinden geçerli konumunda başlayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c9d2-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c9d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c9d2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7c9d2-106">[in] Sayısını `ICorDebugType` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7c9d2-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugType` nesne.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7c9d2-108">[out] İşaretçi sayısına `ICorDebugType` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="7c9d2-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9d2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c9d2-110">Requirements</span></span>  
 <span data-ttu-id="7c9d2-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9d2-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c9d2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c9d2-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9d2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9d2-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9d2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c9d2-115">See also</span></span>

