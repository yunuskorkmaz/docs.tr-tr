---
title: ICorDebugStepper::Step Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137527"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="15e3d-102">ICorDebugStepper::Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15e3d-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="15e3d-103">Bu ICorDebugStepper, kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="15e3d-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15e3d-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15e3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15e3d-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="15e3d-106">'ndaki İş parçacığı içinde çağrılan bir işleve adımla `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="15e3d-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="15e3d-107">İşlevin üzerinde adımla `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="15e3d-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15e3d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15e3d-108">Remarks</span></span>  
 <span data-ttu-id="15e3d-109">Ortak dil çalışma zamanı, bu Stepper 'in çerçevesinde bir sonraki yönetilen yönergeyi gerçekleştirdiğinde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="15e3d-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="15e3d-110">`Step` yönetilen kodda olmayan bir Stepper üzerinde çağrılırsa, sonraki yönetilen kod yönergesi iş parçacığı tarafından yürütüldüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="15e3d-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e3d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15e3d-111">Requirements</span></span>  
 <span data-ttu-id="15e3d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e3d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e3d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15e3d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15e3d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="15e3d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15e3d-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e3d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
