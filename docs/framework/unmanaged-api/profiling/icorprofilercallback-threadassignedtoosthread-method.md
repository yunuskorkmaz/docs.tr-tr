---
description: ': ICorProfilerCallback:: ThreadAssignedToOSThread yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 04fba4cabb0ac58b3afeaae1fd579865335a9e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647992"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="227d0-103">ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="227d0-103">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="227d0-104">Profil oluşturucuyu yönetilen bir iş parçacığının belirli bir işletim sistemi iş parçacığı kullanılarak uygulandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="227d0-104">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="227d0-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="227d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="227d0-106">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="227d0-107">'ndaki Yönetilen iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="227d0-107">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="227d0-108">'ndaki İşletim sistemi iş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="227d0-108">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="227d0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="227d0-109">Remarks</span></span>  

 <span data-ttu-id="227d0-110">`ThreadAssignedToOSThread`Geri çağırma, profil oluşturucunun, işletim sistemi iş parçacıklarının, yönetilen iş parçacıkları arasında doğru bir eşlemeyi koruyabilmesi için vardır.</span><span class="sxs-lookup"><span data-stu-id="227d0-110">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="227d0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="227d0-111">Requirements</span></span>  

 <span data-ttu-id="227d0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="227d0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="227d0-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="227d0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="227d0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="227d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="227d0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="227d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227d0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="227d0-116">See also</span></span>

- [<span data-ttu-id="227d0-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="227d0-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
