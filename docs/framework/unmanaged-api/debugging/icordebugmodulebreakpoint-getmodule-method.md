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
ms.openlocfilehash: 6f9d8cd79ac4107817d19fc0632aeaee287d253a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097009"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="d129d-102">ICorDebugModuleBreakpoint::GetModule Metodu</span><span class="sxs-lookup"><span data-stu-id="d129d-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="d129d-103">Bu kesme noktasının ayarlandığı modüle başvuran bir "ICorDebugModule" için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d129d-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d129d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d129d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d129d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d129d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="d129d-106">dışı Kesme noktasının ayarlandığı modüle başvuran `ICorDebugModule` arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d129d-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d129d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d129d-107">Requirements</span></span>  
 <span data-ttu-id="d129d-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d129d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d129d-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d129d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d129d-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d129d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d129d-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d129d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d129d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d129d-112">See also</span></span>
