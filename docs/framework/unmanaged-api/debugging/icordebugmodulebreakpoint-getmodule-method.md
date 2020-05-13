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
ms.openlocfilehash: 714819504099ea978ed31d471b4ceb9fc17a6552
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212301"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="c8e43-102">ICorDebugModuleBreakpoint::GetModule Metodu</span><span class="sxs-lookup"><span data-stu-id="c8e43-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="c8e43-103">Bu kesme noktasının ayarlandığı modüle başvuran bir "ICorDebugModule" için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c8e43-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8e43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8e43-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8e43-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="c8e43-106">dışı `ICorDebugModule`Kesme noktasının ayarlandığı modüle başvuran bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8e43-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e43-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8e43-107">Requirements</span></span>  
 <span data-ttu-id="c8e43-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e43-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e43-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8e43-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8e43-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c8e43-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8e43-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8e43-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e43-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e43-112">See also</span></span>
