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
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865889"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="5e166-102">ICorProfilerCallback::RuntimeSuspendStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e166-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="5e166-103">Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarını askıya almak için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e166-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e166-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e166-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e166-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e166-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="5e166-106">'ndaki Askıya alma nedenini gösteren [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="5e166-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e166-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e166-107">Remarks</span></span>  
 <span data-ttu-id="5e166-108">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5e166-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="5e166-109">Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="5e166-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="5e166-110">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5e166-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="5e166-111">Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.</span><span class="sxs-lookup"><span data-stu-id="5e166-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e166-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e166-112">Requirements</span></span>  
 <span data-ttu-id="5e166-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e166-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e166-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e166-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e166-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e166-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e166-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e166-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e166-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e166-117">See also</span></span>

- [<span data-ttu-id="5e166-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e166-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5e166-119">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e166-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="5e166-120">RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e166-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
