---
title: ICorDebugValueEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: e1c8d94a90092b1497267c78d5fadf5a6e6de707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684336"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="d664c-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d664c-102">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="d664c-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugValue" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d664c-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d664c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d664c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d664c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d664c-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d664c-106">'ndaki `ICorDebugValue` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="d664c-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d664c-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="d664c-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d664c-108">dışı `ICorDebugValue` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d664c-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="d664c-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="d664c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d664c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d664c-110">Requirements</span></span>  

 <span data-ttu-id="d664c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d664c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d664c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d664c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d664c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d664c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d664c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d664c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d664c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d664c-115">See also</span></span>
