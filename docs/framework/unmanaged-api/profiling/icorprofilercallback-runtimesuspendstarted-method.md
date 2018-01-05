---
title: "ICorProfilerCallback::RuntimeSuspendStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc1b229a21b59a842a5bcc47620302711cecdc42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="0ba47-102">ICorProfilerCallback::RuntimeSuspendStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ba47-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="0ba47-103">Profil Oluşturucu çalışma zamanı hakkında tüm çalışma zamanı iş parçacıklarını askıya alma olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0ba47-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ba47-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ba47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ba47-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="0ba47-106">[in] Değerini [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) askıya nedenini belirten numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="0ba47-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ba47-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ba47-107">Remarks</span></span>  
 <span data-ttu-id="0ba47-108">Yönetilmeyen kod içinde tüm çalışma zamanı iş parçacıklarının bunlar çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmek için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0ba47-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="0ba47-109">Çalışma zamanı yeniden devam edene dek bu noktada bunlar da askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="0ba47-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="0ba47-110">Bu durum, çalışma zamanı girin yeni iş parçacığı için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0ba47-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="0ba47-111">Tüm iş parçacıklarının çalışma zamanında ya da kesilebilir kodda zaten oldukları veya kesilebilir kod ulaştığında askıya almak için sorulan hemen askıya ' dir.</span><span class="sxs-lookup"><span data-stu-id="0ba47-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba47-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ba47-112">Requirements</span></span>  
 <span data-ttu-id="0ba47-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ba47-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ba47-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ba47-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ba47-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ba47-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ba47-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ba47-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba47-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba47-117">See Also</span></span>  
 [<span data-ttu-id="0ba47-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba47-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0ba47-119">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ba47-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [<span data-ttu-id="0ba47-120">RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ba47-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
