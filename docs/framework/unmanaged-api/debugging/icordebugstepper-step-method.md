---
title: "ICorDebugStepper::Step Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 914773adefd2ed4c1aa98310fd27a0cbc829bf49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="3df24-102">ICorDebugStepper::Step Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df24-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="3df24-103">Tek adım üzerinden içeren kendi iş parçacığı ve isteğe bağlı olarak, bu ICorDebugStepper neden olan tek atlama iş parçacığı denir işlevler üzerinden devam edin.</span><span class="sxs-lookup"><span data-stu-id="3df24-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df24-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3df24-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3df24-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3df24-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="3df24-106">[in] Kümesine `true` iş parçacığı içinde adlı bir işlev adımla için.</span><span class="sxs-lookup"><span data-stu-id="3df24-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="3df24-107">Kümesine `false` işlevi Adımlama için.</span><span class="sxs-lookup"><span data-stu-id="3df24-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3df24-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3df24-108">Remarks</span></span>  
 <span data-ttu-id="3df24-109">Ortak dil çalışma zamanı bu Adımlayıcı 's çerçevede sonraki yönetilen yönerge gerçekleştirdiğinde adım tamamlar.</span><span class="sxs-lookup"><span data-stu-id="3df24-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="3df24-110">Varsa `Step` olan Adımlayıcı üzerinde olarak adlandırılan, yönetilen kod içinde değil, sonraki yönetilen kod yönerge iş parçacığı tarafından çalıştırıldığında adımın.</span><span class="sxs-lookup"><span data-stu-id="3df24-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df24-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3df24-111">Requirements</span></span>  
 <span data-ttu-id="3df24-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df24-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3df24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3df24-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3df24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3df24-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
