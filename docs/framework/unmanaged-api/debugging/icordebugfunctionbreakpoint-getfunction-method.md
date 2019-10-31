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
ms.openlocfilehash: 0b53c80157bfd99a766eb691e8a8a2e6b9659a95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137754"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="55678-102">ICorDebugFunctionBreakpoint::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55678-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="55678-103">Kesme noktasının ayarlandığı işleve başvuran bir ICorDebugFunction için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="55678-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55678-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55678-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55678-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55678-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="55678-106">dışı Kesme noktasının ayarlandığı işlevin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="55678-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55678-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55678-107">Requirements</span></span>  
 <span data-ttu-id="55678-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55678-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55678-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55678-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55678-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55678-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55678-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55678-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
