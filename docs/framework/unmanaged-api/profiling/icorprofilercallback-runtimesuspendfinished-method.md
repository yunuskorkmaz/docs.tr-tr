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
ms.openlocfilehash: e6c21e5ec9491e2ccade48a5019b284e333b5ead
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865941"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="1194d-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1194d-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="1194d-103">Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarının askıya alınma tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1194d-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1194d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1194d-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1194d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1194d-105">Remarks</span></span>  
 <span data-ttu-id="1194d-106">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1194d-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="1194d-107">Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="1194d-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="1194d-108">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1194d-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="1194d-109">Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.</span><span class="sxs-lookup"><span data-stu-id="1194d-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="1194d-110">`RuntimeSuspendFinished` geri çağrısının [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında oluşması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="1194d-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1194d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1194d-111">Requirements</span></span>  
 <span data-ttu-id="1194d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1194d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1194d-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1194d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1194d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1194d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1194d-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1194d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1194d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1194d-116">See also</span></span>

- [<span data-ttu-id="1194d-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1194d-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1194d-118">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1194d-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
