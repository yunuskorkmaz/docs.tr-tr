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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa341c726ba84dc1d12b6c5628253a100d65a719
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167108"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="96248-102">ICorDebugModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96248-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="96248-103">Tarafından belirtilen "ICorDebugModule" örnek sayısını alır `celt` öğesinden geçerli konumunda başlayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="96248-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96248-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96248-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96248-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96248-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="96248-106">[in] Sayısını `ICorDebugModule` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="96248-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="96248-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugModule` nesne.</span><span class="sxs-lookup"><span data-stu-id="96248-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="96248-108">[out] İşaretçi sayısına `ICorDebugModule` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="96248-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="96248-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="96248-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96248-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96248-110">Requirements</span></span>  
 <span data-ttu-id="96248-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96248-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96248-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96248-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96248-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96248-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96248-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96248-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96248-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96248-115">See also</span></span>
