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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493030"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="46e21-102">ICorDebugStepper::Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46e21-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="46e21-103">Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için neden olan tek Adımlama iş parçacığının içinden çağıran işlevler ile devam edin.</span><span class="sxs-lookup"><span data-stu-id="46e21-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46e21-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46e21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46e21-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="46e21-106">[in] Kümesine `true` için iş parçacığı içinde çağrılan bir işlevin içine Adımlama.</span><span class="sxs-lookup"><span data-stu-id="46e21-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="46e21-107">Kümesine `false` işlevi Adımlama için.</span><span class="sxs-lookup"><span data-stu-id="46e21-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46e21-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46e21-108">Remarks</span></span>  
 <span data-ttu-id="46e21-109">Ortak dil çalışma zamanı bu adımlayıcıdaki 's çerçevede sonraki yönetilen yönergesi gerçekleştirdiğinde adımı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="46e21-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="46e21-110">Varsa `Step` olan Adımlayıcı üzerinde çağrılır, yönetilen kod içinde değil, sonraki yönetilen kod yönergesi tarafından iş parçacığı yürütüldüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="46e21-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46e21-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46e21-111">Requirements</span></span>  
 <span data-ttu-id="46e21-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46e21-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46e21-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46e21-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46e21-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46e21-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46e21-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46e21-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
