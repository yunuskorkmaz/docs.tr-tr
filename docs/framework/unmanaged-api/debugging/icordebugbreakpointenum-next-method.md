---
title: ICorDebugBreakpointEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: d29576c6f073f1d0e8e0aea417fc38c09a8327c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122739"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="84df4-102">ICorDebugBreakpointEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84df4-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="84df4-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugBreakpoint örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="84df4-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84df4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84df4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84df4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84df4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="84df4-106">'ndaki Alınacak `ICorDebugBreakpoint` örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="84df4-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="84df4-107">dışı Her biri bir kesme noktasını temsil eden bir `ICorDebugBreakpoint` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="84df4-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="84df4-108">dışı Gerçekten döndürülen `ICorDebugBreakpoint` örneklerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84df4-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="84df4-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="84df4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84df4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84df4-110">Requirements</span></span>  
 <span data-ttu-id="84df4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84df4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84df4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84df4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84df4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84df4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84df4-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84df4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
