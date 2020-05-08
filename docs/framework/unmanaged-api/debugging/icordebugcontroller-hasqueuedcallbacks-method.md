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
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892787"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="86993-102">ICorDebugController::HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86993-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="86993-103">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="86993-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86993-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86993-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86993-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86993-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="86993-106">'ndaki İş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86993-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="86993-107">dışı Belirtilen iş parçacığı için şu anda herhangi `true` bir yönetilen geri çağırmalar sıraya alınmışsa bir değer işaretçisi; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="86993-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="86993-108">`pThread` Parametresi için null belirtilirse, `HasQueuedCallbacks` Şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="86993-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86993-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86993-109">Remarks</span></span>  
 <span data-ttu-id="86993-110">Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="86993-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="86993-111">Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="86993-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="86993-112">Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86993-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="86993-113">(Kuyruğu `ICorDebugController::Continue` boşaltmak için çağırın.) Örneğin, kuyruk *x*iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra Iş parçacığı *x* 'i askıya alıyorsa ve sonra `ICorDebugController::Continue`, iş parçacığı askıya alınmış olsa da, iş parçacığı *x* için ikinci hata ayıklama olayı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="86993-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86993-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86993-114">Requirements</span></span>  
 <span data-ttu-id="86993-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86993-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86993-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86993-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86993-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86993-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86993-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86993-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86993-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86993-119">See also</span></span>
