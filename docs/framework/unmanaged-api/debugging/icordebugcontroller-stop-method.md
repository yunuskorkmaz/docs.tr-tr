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
ms.openlocfilehash: bb7eee0997a6c8671693accf2c95e6e06e0a4f2e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976583"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="d092f-102">ICorDebugController::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d092f-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="d092f-103">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d092f-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d092f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d092f-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d092f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d092f-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="d092f-106">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="d092f-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d092f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d092f-107">Remarks</span></span>  
 <span data-ttu-id="d092f-108">`Stop`işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d092f-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="d092f-109">Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir).</span><span class="sxs-lookup"><span data-stu-id="d092f-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="d092f-110">Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak.</span><span class="sxs-lookup"><span data-stu-id="d092f-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="d092f-111">`dwTimeoutIgnored` Değer şu anda YOKSAYıLDı ve sonsuz (-1) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d092f-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="d092f-112">Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d092f-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d092f-113">`Stop`, hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d092f-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="d092f-114">S_OK `Stop` döndüğünde işlem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="d092f-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="d092f-115">Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez.</span><span class="sxs-lookup"><span data-stu-id="d092f-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="d092f-116">Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d092f-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="d092f-117">Hata ayıklayıcı bir durdurma sayacı tutar.</span><span class="sxs-lookup"><span data-stu-id="d092f-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="d092f-118">Sayaç sıfıra gittiğinde, denetleyici sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="d092f-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="d092f-119">Dağıtılan her bir `Stop` geri çağırma veya her bir çağrı sayacı arttırır.</span><span class="sxs-lookup"><span data-stu-id="d092f-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="d092f-120">Her bir çağrı `ICorDebugController::Continue` sayacı azaltır.</span><span class="sxs-lookup"><span data-stu-id="d092f-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d092f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d092f-121">Requirements</span></span>  
 <span data-ttu-id="d092f-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d092f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d092f-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d092f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d092f-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d092f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d092f-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d092f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d092f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d092f-126">See also</span></span>
