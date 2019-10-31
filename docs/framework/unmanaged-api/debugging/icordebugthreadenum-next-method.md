---
title: ICorDebugThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 0c455706b0d644d2444e9fbdf49c5a5d4f5295a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122396"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="e649b-102">ICorDebugThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e649b-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="e649b-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugThread örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e649b-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e649b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e649b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e649b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e649b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e649b-106">'ndaki Alınacak `ICorDebugThread` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="e649b-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="e649b-107">dışı Her biri bir iş parçacığını temsil eden `ICorDebugThread` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="e649b-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e649b-108">dışı Aslında döndürülen `ICorDebugThread` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e649b-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="e649b-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e649b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e649b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e649b-110">Requirements</span></span>  
 <span data-ttu-id="e649b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e649b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e649b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e649b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e649b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e649b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e649b-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e649b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
