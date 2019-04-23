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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138482"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="4481e-102">ICorDebugController::SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4481e-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="4481e-103">İşlemdeki tüm yönetilen iş parçacığı hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4481e-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4481e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4481e-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4481e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4481e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="4481e-106">[in] Hata ayıklama için iş parçacığı durumunu belirten "CorDebugThreadState" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="4481e-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="4481e-107">[in] Bir iş parçacığı hata ayıklama durumu ayarından muaf tutulacak temsil eden bir "ICorDebugThread" nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4481e-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="4481e-108">Bu değer null ise, hiçbir iş parçacığı muaf tutulur.</span><span class="sxs-lookup"><span data-stu-id="4481e-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4481e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4481e-109">Remarks</span></span>  
 <span data-ttu-id="4481e-110">`SetAllThreadsDebugState` Yöntemi aracılığıyla görülemeyen iş parçacıkları etkileyebilir [EnumerateThreads yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), askıya alınan iş parçacıkları bunu `SetAllThreadsDebugState` yöntemi ile sürdürülmesini gerekecektir `SetAllThreadsDebugState` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4481e-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4481e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4481e-111">Requirements</span></span>  
 <span data-ttu-id="4481e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4481e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4481e-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4481e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4481e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4481e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4481e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4481e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4481e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4481e-116">See also</span></span>
