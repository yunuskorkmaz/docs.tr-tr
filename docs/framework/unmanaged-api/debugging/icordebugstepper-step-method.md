---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper:: Step yöntemi'
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
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717634"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="b01bf-103">ICorDebugStepper::Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b01bf-103">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="b01bf-104">Bu ICorDebugStepper, kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b01bf-104">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b01bf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b01bf-105">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b01bf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b01bf-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="b01bf-107">'ndaki `true` İş parçacığı içinde çağrılan bir işleve adım adım olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b01bf-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="b01bf-108">`false`İşlevin üzerinde adımla için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b01bf-108">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b01bf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b01bf-109">Remarks</span></span>  

 <span data-ttu-id="b01bf-110">Ortak dil çalışma zamanı, bu Stepper 'in çerçevesinde bir sonraki yönetilen yönergeyi gerçekleştirdiğinde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="b01bf-110">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="b01bf-111">`Step`Yönetilen kodda olmayan bir Stepper üzerinde çağrılırsa, sonraki yönetilen kod yönergesi iş parçacığı tarafından yürütüldüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="b01bf-111">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b01bf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b01bf-112">Requirements</span></span>  

 <span data-ttu-id="b01bf-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b01bf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b01bf-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b01bf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b01bf-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b01bf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b01bf-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b01bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
