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
ms.openlocfilehash: c07b37e58141f7aff747bd3772be265ae0da42ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222022"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="d7ab1-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7ab1-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="d7ab1-103">Bir nesne için bellek yığında ayrılan profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ab1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7ab1-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7ab1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7ab1-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d7ab1-106">[in] Kendisi için bellek ayrılan nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="d7ab1-107">[in] Nesnesinin bir örneği olduğu sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ab1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7ab1-108">Remarks</span></span>  
 <span data-ttu-id="d7ab1-109">`ObjectedAllocated` Yöntemi yığını veya yönetilmeyen bellek ayırmaları için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="d7ab1-110">`classId` Parametre henüz yüklü değil, yönetilen kodda bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="d7ab1-111">Profil Oluşturucu o sınıf için bir sınıf yük geri alacak hemen sonra `ObjectAllocated` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ab1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7ab1-112">Requirements</span></span>  
 <span data-ttu-id="d7ab1-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7ab1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ab1-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7ab1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7ab1-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7ab1-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d7ab1-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d7ab1-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d7ab1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7ab1-117">See also</span></span>

- [<span data-ttu-id="d7ab1-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7ab1-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d7ab1-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7ab1-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="d7ab1-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7ab1-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
