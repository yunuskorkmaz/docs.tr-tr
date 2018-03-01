---
title: "ICorDebugManagedCallback::StepComplete Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e7a09216284593c79c0cda6f5283ea8250678af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="5e416-102">ICorDebugManagedCallback::StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e416-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="5e416-103">Hata ayıklayıcı bir adım tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e416-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e416-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e416-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e416-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e416-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5e416-106">[in] Bir işaretçi Icordebugappdomain nesneye. adımını tamamlamış iş parçacığı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e416-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5e416-107">[in] Bir işaretçi Icordebugthread nesneye. adımını tamamlamış iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e416-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="5e416-108">[in] Kod yürütmeyi adımda temsil eden bir ICorDebugStepper nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e416-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="5e416-109">[in] Tek bir adımı sonucunu gösteren CorDebugStepReason numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="5e416-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e416-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e416-110">Remarks</span></span>  
 <span data-ttu-id="5e416-111">Adımlayıcı hata ayıklama sonlandırılır sürece atlama isterseniz, devam etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e416-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e416-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e416-112">Requirements</span></span>  
 <span data-ttu-id="5e416-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e416-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e416-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e416-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e416-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e416-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e416-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e416-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e416-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e416-117">See Also</span></span>  
 [<span data-ttu-id="5e416-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e416-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
