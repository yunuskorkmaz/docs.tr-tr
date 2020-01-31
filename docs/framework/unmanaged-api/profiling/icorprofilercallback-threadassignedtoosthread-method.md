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
ms.openlocfilehash: 0e8c91f65d4ebec07689a42d4517fc100fce136d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865850"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="bc042-102">ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc042-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="bc042-103">Profil oluşturucuyu yönetilen bir iş parçacığının belirli bir işletim sistemi iş parçacığı kullanılarak uygulandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bc042-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc042-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc042-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc042-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc042-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="bc042-106">'ndaki Yönetilen iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bc042-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="bc042-107">'ndaki İşletim sistemi iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bc042-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc042-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc042-108">Remarks</span></span>  
 <span data-ttu-id="bc042-109">`ThreadAssignedToOSThread` geri çağırması, profil oluşturucunun, işletim sistemi iş parçacıklarının, yönetilen iş parçacıkları arasında doğru bir eşlemeyi koruyabilmesi için vardır.</span><span class="sxs-lookup"><span data-stu-id="bc042-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc042-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc042-110">Requirements</span></span>  
 <span data-ttu-id="bc042-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc042-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc042-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bc042-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc042-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc042-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc042-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc042-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc042-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc042-115">See also</span></span>

- [<span data-ttu-id="bc042-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc042-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
