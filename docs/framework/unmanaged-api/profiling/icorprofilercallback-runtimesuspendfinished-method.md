---
title: ICorProfilerCallback::RuntimeSuspendFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: 8bad09ddb2b821d0e02d43c1e3d1585b3473ec98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446967"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="eaa01-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaa01-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="eaa01-103">Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarının askıya alınma tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="eaa01-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaa01-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="eaa01-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaa01-105">Remarks</span></span>  
 <span data-ttu-id="eaa01-106">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="eaa01-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="eaa01-107">Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="eaa01-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="eaa01-108">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eaa01-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="eaa01-109">Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.</span><span class="sxs-lookup"><span data-stu-id="eaa01-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="eaa01-110">`RuntimeSuspendFinished` geri çağrısının [ICorProfilerCallback:: RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında oluşması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="eaa01-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa01-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaa01-111">Requirements</span></span>  
 <span data-ttu-id="eaa01-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa01-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa01-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eaa01-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaa01-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eaa01-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaa01-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa01-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa01-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa01-116">See also</span></span>

- [<span data-ttu-id="eaa01-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaa01-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="eaa01-118">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaa01-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
