---
title: ICorDebugBreakpoint::Activate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 24dc55cc9a49c3602829ca627d584c761b4088ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894741"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="c83c6-102">ICorDebugBreakpoint::Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c83c6-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="c83c6-103">Bunun `ICorDebugBreakpoint`etkin durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c83c6-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c83c6-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c83c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c83c6-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="c83c6-106">'ndaki Durumu etkin olarak belirtmek `true` için bu değeri olarak ayarlayın; Aksi takdirde, bu değeri olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c83c6-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83c6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c83c6-107">Requirements</span></span>  
 <span data-ttu-id="c83c6-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c83c6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c83c6-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c83c6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c83c6-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c83c6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c83c6-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c83c6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
