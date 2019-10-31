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
ms.openlocfilehash: e044b1a2ad777868e33cd64bc8d09a9b76d547aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130663"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="e6b82-102">ICorDebugManagedCallback::StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6b82-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="e6b82-103">Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e6b82-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6b82-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6b82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6b82-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e6b82-106">'ndaki Adımın tamamlandığı iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6b82-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e6b82-107">'ndaki Adımın tamamlandığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6b82-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="e6b82-108">'ndaki Kod yürütme adımını temsil eden bir ICorDebugStepper nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6b82-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="e6b82-109">'ndaki Tek bir adımın sonucunu gösteren CorDebugStepReason numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="e6b82-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6b82-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6b82-110">Remarks</span></span>  
 <span data-ttu-id="e6b82-111">Stepper, hata ayıklama sonlandırılana kadar istenirse Adımlama ile devam etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6b82-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b82-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6b82-112">Requirements</span></span>  
 <span data-ttu-id="e6b82-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b82-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6b82-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6b82-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6b82-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6b82-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b82-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b82-117">See also</span></span>

- [<span data-ttu-id="e6b82-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b82-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
