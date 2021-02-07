---
description: ': ICorDebugBreakpointEnum:: Next yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 966494bbabaca99b6b5168db6fb7616c15c537e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711680"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="68d4c-103">ICorDebugBreakpointEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68d4c-103">ICorDebugBreakpointEnum::Next Method</span></span>

<span data-ttu-id="68d4c-104">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugBreakpoint örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="68d4c-104">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d4c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68d4c-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68d4c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68d4c-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="68d4c-107">'ndaki `ICorDebugBreakpoint` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="68d4c-107">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="68d4c-108">dışı Her biri `ICorDebugBreakpoint` bir kesme noktasını temsil eden bir nesneye işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="68d4c-108">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="68d4c-109">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="68d4c-109">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="68d4c-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="68d4c-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d4c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68d4c-111">Requirements</span></span>  

 <span data-ttu-id="68d4c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68d4c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d4c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68d4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68d4c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="68d4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68d4c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
