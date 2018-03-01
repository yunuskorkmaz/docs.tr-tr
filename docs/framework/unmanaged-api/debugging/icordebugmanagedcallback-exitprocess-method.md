---
title: "ICorDebugManagedCallback::ExitProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7be74520fff65b113f54d82305a84dd183286876
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="84870-102">ICorDebugManagedCallback::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84870-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="84870-103">Hata ayıklayıcı işlem yaptı bildirir.</span><span class="sxs-lookup"><span data-stu-id="84870-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84870-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84870-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84870-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84870-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="84870-106">[in] Bir işaretçi Icordebugprocess nesneye işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84870-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84870-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84870-107">Remarks</span></span>  
 <span data-ttu-id="84870-108">Devam edilemiyor bir `ExitProcess` olay.</span><span class="sxs-lookup"><span data-stu-id="84870-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="84870-109">İşlemi durdurulacak görüntülenirken bu olay için diğer olaylar zaman uyumsuz olarak tetikleyin.</span><span class="sxs-lookup"><span data-stu-id="84870-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="84870-110">Bu durum genellikle bazı dış zorla nedeniyle durduruldu sırada işlemi sonlandırır ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="84870-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="84870-111">Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor, bu geri döndü sonra bu olay kadar geciktirilir.</span><span class="sxs-lookup"><span data-stu-id="84870-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="84870-112">`ExitProcess` Kapanışında çağrılmadığı garanti yalnızca çıkış/unload olayı bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="84870-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84870-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84870-113">Requirements</span></span>  
 <span data-ttu-id="84870-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84870-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84870-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84870-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84870-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84870-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84870-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84870-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84870-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84870-118">See Also</span></span>  
 [<span data-ttu-id="84870-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84870-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
