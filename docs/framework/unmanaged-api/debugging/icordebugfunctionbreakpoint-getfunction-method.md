---
title: ICorDebugFunctionBreakpoint::GetFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
ms.openlocfilehash: 4ef5728e4b13d6d3d73aef06f9f7f50ab22609ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726268"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="b14c7-102">ICorDebugFunctionBreakpoint::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b14c7-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>

<span data-ttu-id="b14c7-103">Kesme noktasının ayarlandığı işleve başvuran bir ICorDebugFunction için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b14c7-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14c7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b14c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b14c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b14c7-105">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="b14c7-106">dışı Kesme noktasının ayarlandığı işlevin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b14c7-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b14c7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b14c7-107">Requirements</span></span>  

 <span data-ttu-id="b14c7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b14c7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b14c7-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b14c7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b14c7-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b14c7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b14c7-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b14c7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
