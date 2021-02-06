---
description: ': ICorProfilerCallback:: RuntimeSuspendFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: eab7111f28c77f1440c0e392a36fb2b083c138e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657547"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="5c4c2-103">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c4c2-103">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>

<span data-ttu-id="5c4c2-104">Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarının askıya alınma tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-104">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c4c2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c4c2-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5c4c2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c4c2-106">Remarks</span></span>  

 <span data-ttu-id="5c4c2-107">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-107">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="5c4c2-108">Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-108">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="5c4c2-109">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-109">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="5c4c2-110">Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-110">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="5c4c2-111">`RuntimeSuspendFinished`Geri aramanın [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında oluşması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-111">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c4c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c4c2-112">Requirements</span></span>  

 <span data-ttu-id="5c4c2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c4c2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c4c2-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5c4c2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c4c2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c4c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c4c2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c4c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4c2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c4c2-117">See also</span></span>

- [<span data-ttu-id="5c4c2-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c4c2-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5c4c2-119">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c4c2-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
