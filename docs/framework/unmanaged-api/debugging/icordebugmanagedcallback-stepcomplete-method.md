---
title: ICorDebugManagedCallback::StepComplete Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c3ced50457519d62be44712386bdabce176c44e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761317"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="6d4d2-102">ICorDebugManagedCallback::StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d4d2-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="6d4d2-103">Hata ayıklayıcı, bir adım tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d4d2-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d4d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d4d2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6d4d2-106">[in] Hangi adımın tamamlanması iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6d4d2-107">[in] Hangi adımın tamamlanması iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="6d4d2-108">[in] Kod yürütmeyi adımda temsil eden bir ICorDebugStepper nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="6d4d2-109">[in] CorDebugStepReason sabit bir adımın sonucunu gösteren bir değeri.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d4d2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d4d2-110">Remarks</span></span>  
 <span data-ttu-id="6d4d2-111">Adımlayıcı, hata ayıklama sonlandırıldı sürece Adımlama istenirse, devam etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4d2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d4d2-112">Requirements</span></span>  
 <span data-ttu-id="6d4d2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4d2-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d4d2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d4d2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d4d2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d4d2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d4d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4d2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4d2-117">See also</span></span>

- [<span data-ttu-id="6d4d2-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d4d2-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
