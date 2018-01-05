---
title: "ICorProfilerCallback::ObjectAllocated Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectAllocated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37f4701271f299698d7cd323b7d701f4cb7adb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="afdc6-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afdc6-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="afdc6-103">Bellek öbek içinde bir nesne için ayrılan profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="afdc6-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afdc6-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afdc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afdc6-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="afdc6-106">[in] Bellek ayrılmış olan nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="afdc6-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="afdc6-107">[in] Nesne örneği olduğu sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="afdc6-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afdc6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afdc6-108">Remarks</span></span>  
 <span data-ttu-id="afdc6-109">`ObjectedAllocated` Yöntemi yığınını veya yönetilmeyen bellek ayırma için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="afdc6-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="afdc6-110">`classId` Parametresi, henüz yüklü değil, yönetilen kodda bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="afdc6-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="afdc6-111">Profil Oluşturucu Bu sınıf için bir sınıf yük geri alacak hemen sonra `ObjectAllocated` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="afdc6-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdc6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afdc6-112">Requirements</span></span>  
 <span data-ttu-id="afdc6-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afdc6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afdc6-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="afdc6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afdc6-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afdc6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afdc6-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afdc6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdc6-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afdc6-117">See Also</span></span>  
 [<span data-ttu-id="afdc6-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdc6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="afdc6-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afdc6-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="afdc6-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afdc6-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
