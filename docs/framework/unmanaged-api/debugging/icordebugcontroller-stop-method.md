---
title: "ICorDebugController::Stop Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="86f0a-102">ICorDebugController::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86f0a-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="86f0a-103">Yönetilen kod işlemde çalışan tüm iş parçacıklarının işbirlikçi Dur gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86f0a-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86f0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86f0a-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="86f0a-106">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="86f0a-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f0a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86f0a-107">Remarks</span></span>  
 <span data-ttu-id="86f0a-108">`Stop`üzerinde çalışan tüm iş parçacıklarının işbirlikçi durdurma yönetilen kodu işleminde gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="86f0a-109">Bir yalnızca yönetilen hata ayıklama oturumu sırasında yönetilmeyen iş parçacığı çalışmaya devam edebilir (ancak yönetilen koda çağrı çalışılırken engellenir).</span><span class="sxs-lookup"><span data-stu-id="86f0a-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="86f0a-110">Hata ayıklama oturumunun bir birlikte çalışma sırasında yönetilmeyen iş parçacığı de durdurulur.</span><span class="sxs-lookup"><span data-stu-id="86f0a-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="86f0a-111">`dwTimeoutIgnored` Değeri şu anda yoksayıldı ve SONSUZ (-1) kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="86f0a-112">İşbirlikçi Durdur bir kilitlenme nedeniyle başarısız olursa, tüm iş parçacıklarını askıya alınır ve E_TIMEOUT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="86f0a-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86f0a-113">`Stop`yalnızca zaman uyumlu hata ayıklama API'si yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="86f0a-114">Zaman `Stop` döndürür S_OK, işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="86f0a-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="86f0a-115">Geri arama yok Durdur dinleyicileri bildirmek için verilir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="86f0a-116">Hata ayıklayıcı çağırmalısınız [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) işleminin devam etmesini izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="86f0a-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="86f0a-117">Hata ayıklayıcı Dur sayaç tutar.</span><span class="sxs-lookup"><span data-stu-id="86f0a-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="86f0a-118">Sayaç sıfıra gittiğinde, denetleyici devam ettirilir.</span><span class="sxs-lookup"><span data-stu-id="86f0a-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="86f0a-119">Her çağrı `Stop` veya gönderilen her geri çağırma sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="86f0a-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="86f0a-120">Her çağrı `ICorDebugController::Continue` azaltır sayacı.</span><span class="sxs-lookup"><span data-stu-id="86f0a-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f0a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86f0a-121">Requirements</span></span>  
 <span data-ttu-id="86f0a-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f0a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f0a-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86f0a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86f0a-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f0a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f0a-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f0a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f0a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86f0a-126">See Also</span></span>  
 
