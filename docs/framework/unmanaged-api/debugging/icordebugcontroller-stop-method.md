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
ms.openlocfilehash: 3a107176e48a88a0a04534f7044c1e416caf4091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788887"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="ba227-102">ICorDebugController::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba227-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="ba227-103">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba227-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba227-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba227-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba227-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba227-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="ba227-106">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ba227-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba227-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba227-107">Remarks</span></span>  
 <span data-ttu-id="ba227-108">`Stop`, işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba227-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="ba227-109">Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir).</span><span class="sxs-lookup"><span data-stu-id="ba227-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="ba227-110">Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="ba227-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="ba227-111">`dwTimeoutIgnored` değeri şu anda yoksayıldı ve sonsuz (-1) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ba227-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="ba227-112">Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ba227-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba227-113">`Stop`, hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="ba227-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="ba227-114">`Stop` S_OK döndürdüğünde işlem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="ba227-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="ba227-115">Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez.</span><span class="sxs-lookup"><span data-stu-id="ba227-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="ba227-116">Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba227-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="ba227-117">Hata ayıklayıcı bir durdurma sayacı tutar.</span><span class="sxs-lookup"><span data-stu-id="ba227-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="ba227-118">Sayaç sıfıra gittiğinde, denetleyici sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="ba227-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="ba227-119">`Stop` veya dağıtılan her bir geri çağırma çağrısı sayacı arttırır.</span><span class="sxs-lookup"><span data-stu-id="ba227-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="ba227-120">`ICorDebugController::Continue` yapılan her çağrı sayacı azaltır.</span><span class="sxs-lookup"><span data-stu-id="ba227-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba227-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba227-121">Requirements</span></span>  
 <span data-ttu-id="ba227-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba227-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba227-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba227-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba227-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba227-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba227-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba227-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba227-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba227-126">See also</span></span>
