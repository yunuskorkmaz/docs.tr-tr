---
title: ICorProfilerCallback::ObjectAllocated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7d62b1b6031f6ebdd5327626f42de38b18b3fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452055"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="79b61-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79b61-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="79b61-103">Bellek öbek içinde bir nesne için ayrılan profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="79b61-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79b61-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79b61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79b61-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="79b61-106">[in] Bellek ayrılmış olan nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="79b61-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="79b61-107">[in] Nesne örneği olduğu sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="79b61-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79b61-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79b61-108">Remarks</span></span>  
 <span data-ttu-id="79b61-109">`ObjectedAllocated` Yöntemi yığınını veya yönetilmeyen bellek ayırma için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="79b61-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="79b61-110">`classId` Parametresi, henüz yüklü değil, yönetilen kodda bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="79b61-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="79b61-111">Profil Oluşturucu Bu sınıf için bir sınıf yük geri alacak hemen sonra `ObjectAllocated` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="79b61-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b61-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79b61-112">Requirements</span></span>  
 <span data-ttu-id="79b61-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b61-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b61-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79b61-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79b61-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79b61-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79b61-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b61-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b61-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79b61-117">See Also</span></span>  
 [<span data-ttu-id="79b61-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79b61-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="79b61-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79b61-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="79b61-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79b61-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
