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
ms.openlocfilehash: 14c89e808ea8e41bbee46a59a60bc1876f3800d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730194"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="72fd2-102">ICorDebugBreakpointEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72fd2-102">ICorDebugBreakpointEnum::Next Method</span></span>

<span data-ttu-id="72fd2-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugBreakpoint örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="72fd2-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fd2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72fd2-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72fd2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72fd2-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="72fd2-106">'ndaki `ICorDebugBreakpoint` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="72fd2-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="72fd2-107">dışı Her biri `ICorDebugBreakpoint` bir kesme noktasını temsil eden bir nesneye işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="72fd2-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="72fd2-108">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="72fd2-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="72fd2-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="72fd2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72fd2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72fd2-110">Requirements</span></span>  

 <span data-ttu-id="72fd2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72fd2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72fd2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72fd2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72fd2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72fd2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72fd2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72fd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
