---
title: "ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c70de2b53fd428361d5404aa406d2b2be67d0914
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="b2ba4-102">ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ba4-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="b2ba4-103">Profil Oluşturucu, belirli bir işletim sistemi iş parçacığı kullanan bir yönetilen iş parçacığı uygulanan olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b2ba4-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ba4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2ba4-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2ba4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2ba4-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="b2ba4-106">[in] Yönetilen iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b2ba4-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="b2ba4-107">[in] İşletim sistemi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b2ba4-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2ba4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2ba4-108">Remarks</span></span>  
 <span data-ttu-id="b2ba4-109">`ThreadAssignedToOSThread` Geri çağırma var. böylece profil oluşturucu lifleri yönetilen iş parçacığı için işletim sistemi iş parçacıkları arasında doğru bir eşleme koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2ba4-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ba4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2ba4-110">Requirements</span></span>  
 <span data-ttu-id="b2ba4-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ba4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ba4-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2ba4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2ba4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2ba4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2ba4-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ba4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ba4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ba4-115">See Also</span></span>  
 [<span data-ttu-id="b2ba4-116">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2ba4-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
