---
description: ': ICorDebugModuleBreakpoint:: GetModule yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugModuleBreakpoint::GetModule Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 3498f9d644d6195f2cd0f83d30417c447d200f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790795"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="5632f-103">ICorDebugModuleBreakpoint::GetModule Metodu</span><span class="sxs-lookup"><span data-stu-id="5632f-103">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="5632f-104">Bu kesme noktasının ayarlandığı modüle başvuran bir "ICorDebugModule" için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5632f-104">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5632f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5632f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5632f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5632f-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="5632f-107">dışı `ICorDebugModule` Kesme noktasının ayarlandığı modüle başvuran bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5632f-107">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5632f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5632f-108">Requirements</span></span>  

 <span data-ttu-id="5632f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5632f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5632f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5632f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5632f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5632f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5632f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5632f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5632f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5632f-113">See also</span></span>
