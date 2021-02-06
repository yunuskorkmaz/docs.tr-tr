---
description: ': ICorDebugManagedCallback:: Steptamamlanmıştır yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 653abee26f09ac8877be9fa4183763739845666a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660368"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="18b58-103">ICorDebugManagedCallback::StepComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18b58-103">ICorDebugManagedCallback::StepComplete Method</span></span>

<span data-ttu-id="18b58-104">Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="18b58-104">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b58-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18b58-105">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b58-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18b58-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="18b58-107">'ndaki Adımın tamamlandığı iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18b58-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="18b58-108">'ndaki Adımın tamamlandığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18b58-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="18b58-109">'ndaki Kod yürütme adımını temsil eden bir ICorDebugStepper nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18b58-109">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="18b58-110">'ndaki Tek bir adımın sonucunu gösteren CorDebugStepReason numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="18b58-110">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18b58-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18b58-111">Remarks</span></span>  

 <span data-ttu-id="18b58-112">Stepper, hata ayıklama sonlandırılana kadar istenirse Adımlama ile devam etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18b58-112">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b58-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18b58-113">Requirements</span></span>  

 <span data-ttu-id="18b58-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b58-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b58-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="18b58-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18b58-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="18b58-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b58-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b58-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b58-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18b58-118">See also</span></span>

- [<span data-ttu-id="18b58-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18b58-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
