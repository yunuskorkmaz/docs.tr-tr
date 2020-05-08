---
title: ICorDebugController::SetAllThreadsDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976596"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="288b2-102">ICorDebugController::SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="288b2-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="288b2-103">İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="288b2-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="288b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="288b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="288b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="288b2-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="288b2-106">'ndaki Hata ayıklama için iş parçacığının durumunu belirten "CorDebugThreadState" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="288b2-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="288b2-107">'ndaki Hata ayıklama durumu ayarından muaf tutulan bir iş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="288b2-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="288b2-108">Bu değer null ise, hiçbir iş parçacığı muaf tutulur.</span><span class="sxs-lookup"><span data-stu-id="288b2-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="288b2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="288b2-109">Remarks</span></span>  
 <span data-ttu-id="288b2-110">Yöntemi, [EnumerateThreads yöntemi](icordebugcontroller-enumeratethreads-method.md)aracılığıyla görünmeyen iş parçacıklarını etkileyebilir, bu nedenle `SetAllThreadsDebugState` yöntemiyle askıya alınan iş parçacıklarının `SetAllThreadsDebugState` yöntemiyle sürdürülmeleri gerekir. `SetAllThreadsDebugState`</span><span class="sxs-lookup"><span data-stu-id="288b2-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="288b2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="288b2-111">Requirements</span></span>  
 <span data-ttu-id="288b2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="288b2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="288b2-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="288b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="288b2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="288b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="288b2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="288b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="288b2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="288b2-116">See also</span></span>
