---
title: ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 2d6f34d88dd79fe350f1c018e3afa55e5b180c46
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732014"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="6d075-102">ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d075-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="6d075-103">Profil oluşturucuyu yönetilen bir iş parçacığının belirli bir işletim sistemi iş parçacığı kullanılarak uygulandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d075-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d075-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d075-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d075-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d075-105">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="6d075-106">'ndaki Yönetilen iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6d075-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="6d075-107">'ndaki İşletim sistemi iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6d075-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d075-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d075-108">Remarks</span></span>  

 <span data-ttu-id="6d075-109">`ThreadAssignedToOSThread`Geri çağırma, profil oluşturucunun, işletim sistemi iş parçacıklarının, yönetilen iş parçacıkları arasında doğru bir eşlemeyi koruyabilmesi için vardır.</span><span class="sxs-lookup"><span data-stu-id="6d075-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d075-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d075-110">Requirements</span></span>  

 <span data-ttu-id="6d075-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d075-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d075-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d075-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d075-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d075-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d075-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d075-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d075-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d075-115">See also</span></span>

- [<span data-ttu-id="6d075-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d075-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
