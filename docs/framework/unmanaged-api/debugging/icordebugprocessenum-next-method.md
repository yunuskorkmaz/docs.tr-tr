---
title: ICorDebugProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: 0666becb5a34688d3f4cf5bddd1e2fa71785b38a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139793"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="274c1-102">ICorDebugProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="274c1-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="274c1-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugProcess örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="274c1-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="274c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="274c1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="274c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="274c1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="274c1-106">'ndaki Alınacak `ICorDebugProcess` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="274c1-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="274c1-107">dışı Her biri bir işlemi temsil eden `ICorDebugProcess` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="274c1-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="274c1-108">dışı Aslında döndürülen `ICorDebugProcess` örneklerinin sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="274c1-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="274c1-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="274c1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="274c1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="274c1-110">Requirements</span></span>  
 <span data-ttu-id="274c1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="274c1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="274c1-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="274c1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="274c1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="274c1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="274c1-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="274c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
