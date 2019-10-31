---
title: ICorDebugModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: 6c4262c18e4efcbbca1b3e2a327fec7d4b609a31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096920"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="ad615-102">ICorDebugModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad615-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="ad615-103">Geçerli konumdan başlayarak numaralandırmadan `celt` tarafından belirtilen "ICorDebugModule" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ad615-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad615-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad615-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad615-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad615-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ad615-106">'ndaki Alınacak `ICorDebugModule` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="ad615-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="ad615-107">dışı Her biri bir `ICorDebugModule` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ad615-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ad615-108">dışı Aslında döndürülen `ICorDebugModule` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad615-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="ad615-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad615-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad615-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad615-110">Requirements</span></span>  
 <span data-ttu-id="ad615-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad615-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad615-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad615-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad615-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad615-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad615-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad615-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad615-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad615-115">See also</span></span>
