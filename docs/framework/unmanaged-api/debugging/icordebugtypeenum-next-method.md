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
ms.openlocfilehash: fc205e347fc39fd486d9b8a3fb256a5d29a980a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110058"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="20013-102">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20013-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="20013-103">Geçerli konumdan başlayarak, numaralandırmadan `celt` tarafından belirtilen "ICorDebugType" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="20013-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20013-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20013-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20013-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20013-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="20013-106">'ndaki Alınacak `ICorDebugType` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="20013-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="20013-107">dışı Her biri bir `ICorDebugType` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="20013-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="20013-108">dışı Aslında döndürülen `ICorDebugType` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20013-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="20013-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="20013-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20013-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20013-110">Requirements</span></span>  
 <span data-ttu-id="20013-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20013-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20013-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20013-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20013-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="20013-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20013-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20013-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20013-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20013-115">See also</span></span>
