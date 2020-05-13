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
ms.openlocfilehash: 39d2fd0163b0e61295187461d5dbdf5742450306
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379512"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="f0050-102">ICorDebugStepper::Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0050-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="f0050-103">Bu ICorDebugStepper, kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f0050-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0050-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0050-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0050-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0050-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="f0050-106">'ndaki `true`İş parçacığı içinde çağrılan bir işleve adım adım olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f0050-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="f0050-107">`false`İşlevin üzerinde adımla için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0050-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0050-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0050-108">Remarks</span></span>  
 <span data-ttu-id="f0050-109">Ortak dil çalışma zamanı, bu Stepper 'in çerçevesinde bir sonraki yönetilen yönergeyi gerçekleştirdiğinde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="f0050-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="f0050-110">`Step`Yönetilen kodda olmayan bir Stepper üzerinde çağrılırsa, sonraki yönetilen kod yönergesi iş parçacığı tarafından yürütüldüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="f0050-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0050-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0050-111">Requirements</span></span>  
 <span data-ttu-id="f0050-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0050-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0050-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0050-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0050-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0050-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0050-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0050-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
