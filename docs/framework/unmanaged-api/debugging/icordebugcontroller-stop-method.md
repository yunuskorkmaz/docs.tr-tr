---
description: ': ICorDebugController:: Stop yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 613fd81a03114580ae3d826a94d855023895b694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764612"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="6e6d8-103">ICorDebugController::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6d8-103">ICorDebugController::Stop Method</span></span>

<span data-ttu-id="6e6d8-104">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-104">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e6d8-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e6d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e6d8-106">Parameters</span></span>  

 `dwTimeoutIgnored`  
 <span data-ttu-id="6e6d8-107">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-107">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e6d8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e6d8-108">Remarks</span></span>  

 <span data-ttu-id="6e6d8-109">`Stop` işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-109">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="6e6d8-110">Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir).</span><span class="sxs-lookup"><span data-stu-id="6e6d8-110">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="6e6d8-111">Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-111">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="6e6d8-112">`dwTimeoutIgnored`Değer şu anda yoksayıldı ve sonsuz (-1) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-112">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="6e6d8-113">Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-113">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e6d8-114">`Stop` , hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-114">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="6e6d8-115">`Stop`S_OK döndüğünde işlem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-115">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="6e6d8-116">Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-116">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="6e6d8-117">Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-117">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="6e6d8-118">Hata ayıklayıcı bir durdurma sayacı tutar.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-118">The debugger maintains a stop counter.</span></span> <span data-ttu-id="6e6d8-119">Sayaç sıfıra gittiğinde, denetleyici sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-119">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="6e6d8-120">Dağıtılan her bir `Stop` geri çağırma veya her bir çağrı sayacı arttırır.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-120">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="6e6d8-121">Her bir çağrı `ICorDebugController::Continue` sayacı azaltır.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-121">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e6d8-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e6d8-122">Requirements</span></span>  

 <span data-ttu-id="6e6d8-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e6d8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e6d8-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e6d8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e6d8-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e6d8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e6d8-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6d8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6d8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6d8-127">See also</span></span>
