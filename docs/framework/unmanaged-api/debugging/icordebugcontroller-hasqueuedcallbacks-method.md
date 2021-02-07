---
description: ': ICorDebugController:: HasQueuedCallbacks yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bdc22831b912d3bad565b6abf5c73591d07ffe11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764677"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="f5e5f-103">ICorDebugController::HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5e5f-103">ICorDebugController::HasQueuedCallbacks Method</span></span>

<span data-ttu-id="f5e5f-104">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-104">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5e5f-105">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5e5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5e5f-106">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="f5e5f-107">'ndaki İş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-107">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="f5e5f-108">dışı `true` Belirtilen iş parçacığı için şu anda herhangi bir yönetilen geri çağırma sıraya alınmışsa bir değer işaretçisi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="f5e5f-108">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="f5e5f-109">Parametresi için null belirtilirse `pThread` , `HasQueuedCallbacks` `true` Şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-109">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e5f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5e5f-110">Remarks</span></span>  

 <span data-ttu-id="f5e5f-111">Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-111">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="f5e5f-112">Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-112">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="f5e5f-113">Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-113">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="f5e5f-114">( `ICorDebugController::Continue` Kuyruğu boşaltmak için çağırın.) Örneğin, kuyruk *x* iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra Iş parçacığı *x* 'i askıya alıyorsa ve sonra `ICorDebugController::Continue` , iş parçacığı askıya alınmış olsa da, iş parçacığı *x* için ikinci hata ayıklama olayı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-114">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5e5f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5e5f-115">Requirements</span></span>  

 <span data-ttu-id="f5e5f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5e5f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5e5f-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5e5f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5e5f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5e5f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5e5f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5e5f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e5f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e5f-120">See also</span></span>
