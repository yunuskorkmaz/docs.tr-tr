---
description: ': ICorDebugController:: SetAllThreadsDebugState yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3bce5360833ae18c68bc8d7ea24f0dec7615f7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710744"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="cf922-103">ICorDebugController::SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf922-103">ICorDebugController::SetAllThreadsDebugState Method</span></span>

<span data-ttu-id="cf922-104">İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf922-104">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf922-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf922-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf922-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf922-106">Parameters</span></span>  

 `state`  
 <span data-ttu-id="cf922-107">'ndaki Hata ayıklama için iş parçacığının durumunu belirten "CorDebugThreadState" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="cf922-107">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="cf922-108">'ndaki Hata ayıklama durumu ayarından muaf tutulan bir iş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf922-108">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="cf922-109">Bu değer null ise, hiçbir iş parçacığı muaf tutulur.</span><span class="sxs-lookup"><span data-stu-id="cf922-109">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf922-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf922-110">Remarks</span></span>  

 <span data-ttu-id="cf922-111">`SetAllThreadsDebugState`Yöntemi, [EnumerateThreads yöntemi](icordebugcontroller-enumeratethreads-method.md)aracılığıyla görünmeyen iş parçacıklarını etkileyebilir, bu nedenle yöntemiyle askıya alınan iş parçacıklarının `SetAllThreadsDebugState` yöntemiyle sürdürülmeleri gerekir `SetAllThreadsDebugState` .</span><span class="sxs-lookup"><span data-stu-id="cf922-111">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf922-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf922-112">Requirements</span></span>  

 <span data-ttu-id="cf922-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf922-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf922-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf922-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf922-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf922-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf922-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf922-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf922-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf922-117">See also</span></span>
