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
ms.openlocfilehash: 09394acb07b8595f99d9ecc873eb0985cdd79316
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134591"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="80869-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80869-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="80869-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugValue" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="80869-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80869-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80869-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80869-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80869-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="80869-106">'ndaki Alınacak `ICorDebugValue` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="80869-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="80869-107">dışı Her biri bir `ICorDebugValue` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="80869-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="80869-108">dışı Aslında döndürülen `ICorDebugValue` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80869-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="80869-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="80869-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80869-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80869-110">Requirements</span></span>  
 <span data-ttu-id="80869-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80869-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80869-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80869-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80869-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80869-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80869-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80869-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80869-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80869-115">See also</span></span>
