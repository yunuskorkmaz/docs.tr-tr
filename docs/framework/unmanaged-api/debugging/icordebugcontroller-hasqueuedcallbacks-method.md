---
title: ICorDebugController::HasQueuedCallbacks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce6ad24e5e670db21d3a6942ab4650a68ae44568
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749561"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="26ba6-102">ICorDebugController::HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ba6-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="26ba6-103">Tüm yönetilen geri çağırmaları belirtilen iş parçacığı için sıraya alınmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="26ba6-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ba6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26ba6-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26ba6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26ba6-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="26ba6-106">[in] İş parçacığını temsil eden bir "ICorDebugThread" nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="26ba6-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="26ba6-107">[out] Bir değer için bir işaretçi `true` tüm yönetilen geri çağırmaları şu anda, belirtilen iş parçacığı için kuyruğa alınan; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="26ba6-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="26ba6-108">Null için belirtilirse `pThread` parametresi `HasQueuedCallbacks` döndürür `true` şu anda yönetilen geri çağırmaları herhangi bir iş parçacığı için kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="26ba6-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26ba6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26ba6-109">Remarks</span></span>  
 <span data-ttu-id="26ba6-110">Geri çağırmaları gönderilen birer birer, her zaman olacaktır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26ba6-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="26ba6-111">Aynı anda birden çok hata ayıklama olayları bildirmek istiyorsa, hata ayıklayıcı bu bayrağı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26ba6-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="26ba6-112">Hata ayıklama olaylarını sıralandığında, hata ayıklayıcı hata ayıklanan durumunu emin olmak için tüm kuyruk boşaltma gerekir böylece bunlar zaten, oluştu.</span><span class="sxs-lookup"><span data-stu-id="26ba6-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="26ba6-113">(Çağrı `ICorDebugController::Continue` boşaltma kuyruğu için.) Örneğin, sıranın iş parçacığı üzerinde iki hata ayıklama olaylarını içeriyorsa *X*, ve hata ayıklayıcı iş parçacığını askıya alır *X* ilk hata ayıklama olayı ve ardından aramaları `ICorDebugController::Continue`, ikinci hata ayıklama olayı için iş parçacığı *X* iş parçacığını askıya alındı ancak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="26ba6-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26ba6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26ba6-114">Requirements</span></span>  
 <span data-ttu-id="26ba6-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26ba6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26ba6-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26ba6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26ba6-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26ba6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26ba6-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26ba6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ba6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ba6-119">See also</span></span>
