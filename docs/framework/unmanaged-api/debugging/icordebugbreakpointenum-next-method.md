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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894664"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="6ae94-102">ICorDebugBreakpointEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ae94-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="6ae94-103">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugBreakpoint örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6ae94-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ae94-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ae94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ae94-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6ae94-106">'ndaki Alınacak `ICorDebugBreakpoint` örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="6ae94-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="6ae94-107">dışı Her biri bir kesme noktasını temsil eden bir `ICorDebugBreakpoint` nesneye işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="6ae94-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6ae94-108">dışı Aslında döndürülen `ICorDebugBreakpoint` örnek sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ae94-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="6ae94-109">Bu değer bir `celt` ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ae94-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae94-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ae94-110">Requirements</span></span>  
 <span data-ttu-id="6ae94-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ae94-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae94-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ae94-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ae94-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ae94-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ae94-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae94-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
