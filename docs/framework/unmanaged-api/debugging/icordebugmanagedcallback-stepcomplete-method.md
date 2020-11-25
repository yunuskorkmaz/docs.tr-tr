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
ms.openlocfilehash: 8de0858abe7db9ae1225f449083e417e13507b3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703063"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="a5c9d-102">ICorDebugManagedCallback::StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5c9d-102">ICorDebugManagedCallback::StepComplete Method</span></span>

<span data-ttu-id="a5c9d-103">Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c9d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a5c9d-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5c9d-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a5c9d-106">'ndaki Adımın tamamlandığı iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a5c9d-107">'ndaki Adımın tamamlandığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="a5c9d-108">'ndaki Kod yürütme adımını temsil eden bir ICorDebugStepper nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="a5c9d-109">'ndaki Tek bir adımın sonucunu gösteren CorDebugStepReason numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c9d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5c9d-110">Remarks</span></span>  

 <span data-ttu-id="a5c9d-111">Stepper, hata ayıklama sonlandırılana kadar istenirse Adımlama ile devam etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c9d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5c9d-112">Requirements</span></span>  

 <span data-ttu-id="a5c9d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c9d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c9d-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5c9d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5c9d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5c9d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c9d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c9d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5c9d-117">See also</span></span>

- [<span data-ttu-id="a5c9d-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5c9d-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
