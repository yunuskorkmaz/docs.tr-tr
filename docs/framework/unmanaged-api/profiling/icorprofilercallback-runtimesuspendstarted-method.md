---
title: ICorProfilerCallback::RuntimeSuspendStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f07cd585ab800394569b97d103e292a5d8f36f20
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466771"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="99559-102">ICorProfilerCallback::RuntimeSuspendStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99559-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="99559-103">Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını askıya almak olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="99559-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99559-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99559-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99559-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99559-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="99559-106">[in] Değerini [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) askıya alınma nedenini belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="99559-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99559-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99559-107">Remarks</span></span>  
 <span data-ttu-id="99559-108">Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="99559-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="99559-109">Çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="99559-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="99559-110">Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99559-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="99559-111">Tüm çalışma zamanında ya da hemen kesilebilir kodda zaten olduğu ya da bunlar kesilebilir kod ulaştığınızda askıya almak için sorulan askıya akışlardır.</span><span class="sxs-lookup"><span data-stu-id="99559-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99559-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99559-112">Requirements</span></span>  
 <span data-ttu-id="99559-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99559-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99559-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="99559-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99559-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99559-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99559-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99559-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99559-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99559-117">See also</span></span>
- [<span data-ttu-id="99559-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99559-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="99559-119">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99559-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="99559-120">RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99559-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
