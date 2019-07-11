---
title: ICorDebugController::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83bb52f7f2035605914e2fe72ce2daf78de5bc1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749909"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="62f28-102">ICorDebugController::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62f28-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="62f28-103">Yönetilen kod işlemde çalışan tüm iş parçacıkları üzerinde işbirliği yapan Durma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="62f28-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f28-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62f28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62f28-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="62f28-106">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="62f28-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f28-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62f28-107">Remarks</span></span>  
 <span data-ttu-id="62f28-108">`Stop` işlemdeki tüm iş parçacıkları üzerinde işbirliği yapan durdurma yönetilen kodu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="62f28-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="62f28-109">Yalnızca yönetilen hata ayıklama oturumu sırasında yönetilmeyen iş parçacığı çalışmaya devam edebilir (ancak yönetilen kod çağrılmaya çalışılırken engellenecek).</span><span class="sxs-lookup"><span data-stu-id="62f28-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="62f28-110">Hata ayıklama oturumu bir birlikte çalışma sırasında yönetilmeyen iş parçacığı da durdurulur.</span><span class="sxs-lookup"><span data-stu-id="62f28-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="62f28-111">`dwTimeoutIgnored` Değeri şu anda yok sayıldı ve SONSUZ (-1) kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="62f28-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="62f28-112">İşbirlikçi Durdur kilitlenme nedeniyle başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="62f28-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62f28-113">`Stop` hata ayıklama API'sindeki yalnızca zaman uyumlu yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="62f28-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="62f28-114">Zaman `Stop` döndürür: S_OK, işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="62f28-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="62f28-115">Hiçbir geri çağırma duraklarının dinleyicileri bildirmek için verilir.</span><span class="sxs-lookup"><span data-stu-id="62f28-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="62f28-116">Hata ayıklayıcı çağırmalıdır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) işleminin devam etmesini sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="62f28-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="62f28-117">Hata ayıklayıcıyı Durdur sayaç tutar.</span><span class="sxs-lookup"><span data-stu-id="62f28-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="62f28-118">Sayaç sıfıra gittiğinde, denetleyici sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="62f28-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="62f28-119">Her çağrı `Stop` veya her gönderilen geri çağırma sayacı artırır.</span><span class="sxs-lookup"><span data-stu-id="62f28-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="62f28-120">Her çağrı `ICorDebugController::Continue` azaltır sayacı.</span><span class="sxs-lookup"><span data-stu-id="62f28-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f28-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62f28-121">Requirements</span></span>  
 <span data-ttu-id="62f28-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f28-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f28-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62f28-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62f28-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f28-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f28-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f28-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f28-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f28-126">See also</span></span>
