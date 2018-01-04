---
title: "ICorDebugController::HasQueuedCallbacks Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03d52bb31a81876a00e1af33494b14fb99fee0fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="f19c2-102">ICorDebugController::HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f19c2-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="f19c2-103">Tüm yönetilen geri aramalar için belirtilen iş parçacığı sıraya alınmış olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f19c2-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f19c2-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f19c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f19c2-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="f19c2-106">[in] İş parçacığı temsil eden bir "ICorDebugThread" nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f19c2-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="f19c2-107">[out] Bir değer için bir işaretçi `true` tüm yönetilen geri aramalar şu anda, belirtilen iş parçacığı için sıraya alınan Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f19c2-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="f19c2-108">İçin NULL belirtilirse `pThread` parametresi `HasQueuedCallbacks` döndürülecek `true` şu anda yönetilen geri aramalar için herhangi bir iş parçacığı sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="f19c2-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f19c2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f19c2-109">Remarks</span></span>  
 <span data-ttu-id="f19c2-110">Geri aramalar gönderilen birer birer, her zaman olacaktır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f19c2-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="f19c2-111">Hata ayıklayıcı, aynı anda gerçekleşen birden çok hata ayıklama olaylara rapor isterse Bu bayrak kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f19c2-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="f19c2-112">Hata ayıklama olayları sıralandığında hata ayıklayıcı ayıklayıcı durumunu emin olmak için tüm kuyruk boşaltma gerekir böylece bunlar zaten, oluştu.</span><span class="sxs-lookup"><span data-stu-id="f19c2-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="f19c2-113">(Çağrı `ICorDebugController::Continue` sıranın boşaltmak için.) Örneğin, sıranın iş parçacığı üzerinde iki hata ayıklama olayları içeriyorsa *X*, ve iş parçacığı hata ayıklayıcı bekletir *X* ilk hata ayıklama olayı ve ardından çağrıları sonra `ICorDebugController::Continue`, ikinci hata ayıklama olayı için iş parçacığı *X* iş parçacığı askıya alındı ancak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f19c2-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f19c2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f19c2-114">Requirements</span></span>  
 <span data-ttu-id="f19c2-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f19c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f19c2-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f19c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f19c2-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f19c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f19c2-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f19c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19c2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f19c2-119">See Also</span></span>  
 
