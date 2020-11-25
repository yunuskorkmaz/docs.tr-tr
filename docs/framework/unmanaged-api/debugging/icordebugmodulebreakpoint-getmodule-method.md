---
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
ms.openlocfilehash: b6363ef901d5297862ca46e685bb783aaaeb4123
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709628"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="64f02-102">ICorDebugModuleBreakpoint::GetModule Metodu</span><span class="sxs-lookup"><span data-stu-id="64f02-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="64f02-103">Bu kesme noktasının ayarlandığı modüle başvuran bir "ICorDebugModule" için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="64f02-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f02-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="64f02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64f02-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64f02-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="64f02-106">dışı `ICorDebugModule` Kesme noktasının ayarlandığı modüle başvuran bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64f02-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64f02-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64f02-107">Requirements</span></span>  

 <span data-ttu-id="64f02-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64f02-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64f02-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64f02-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64f02-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64f02-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64f02-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64f02-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f02-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64f02-112">See also</span></span>
