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
ms.openlocfilehash: c33193bd64030852441c7ca60cee4a000b09156c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788920"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="ab0ca-102">ICorDebugController::HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0ca-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="ab0ca-103">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab0ca-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab0ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab0ca-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="ab0ca-106">'ndaki İş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="ab0ca-107">dışı Belirtilen iş parçacığı için şu anda herhangi bir yönetilen geri çağırma sıraya alınmışsa `true` bir değere yönelik işaretçi. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="ab0ca-108">`pThread` parametresi için null belirtilirse `HasQueuedCallbacks`, şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa `true` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab0ca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab0ca-109">Remarks</span></span>  
 <span data-ttu-id="ab0ca-110">Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="ab0ca-111">Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="ab0ca-112">Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="ab0ca-113">(Kuyruğu boşaltmak için `ICorDebugController::Continue` çağırın.) Örneğin, kuyruk *x*iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra iş parçacığını askıya alıyorsa ve `ICorDebugController::Continue`çağırırsa, iş parçacığı askıya alınmış olsa bile *x* *iş parçacığı için* ikinci hata ayıklama olayı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0ca-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab0ca-114">Requirements</span></span>  
 <span data-ttu-id="ab0ca-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0ca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0ca-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab0ca-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab0ca-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab0ca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab0ca-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab0ca-119">See also</span></span>
