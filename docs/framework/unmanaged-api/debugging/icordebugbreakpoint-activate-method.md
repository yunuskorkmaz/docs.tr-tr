---
description: ': ICorDebugBreakpoint:: Activate yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1a3613ae071b3fc6c4f1005eafd515946d6b2685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711875"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="2e336-103">ICorDebugBreakpoint::Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e336-103">ICorDebugBreakpoint::Activate Method</span></span>

<span data-ttu-id="2e336-104">Bunun etkin durumunu ayarlar `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="2e336-104">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e336-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e336-105">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e336-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e336-106">Parameters</span></span>  

 `bActive`  
 <span data-ttu-id="2e336-107">'ndaki `true` Durumu etkin olarak belirtmek için bu değeri olarak ayarlayın; Aksi takdirde, bu değeri olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="2e336-107">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e336-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e336-108">Requirements</span></span>  

 <span data-ttu-id="2e336-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e336-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e336-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e336-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e336-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e336-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e336-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e336-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
