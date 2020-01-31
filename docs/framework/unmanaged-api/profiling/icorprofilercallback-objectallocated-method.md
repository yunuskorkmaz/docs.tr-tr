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
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866110"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="56d84-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56d84-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="56d84-103">Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="56d84-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56d84-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56d84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56d84-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="56d84-106">'ndaki Belleğin ayrıldığı nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="56d84-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="56d84-107">'ndaki Nesnenin bir örnek olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="56d84-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d84-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56d84-108">Remarks</span></span>  
 <span data-ttu-id="56d84-109">`ObjectedAllocated` yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="56d84-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="56d84-110">`classId` parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="56d84-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="56d84-111">Profil Oluşturucu, `ObjectAllocated` geri çağrısından hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır.</span><span class="sxs-lookup"><span data-stu-id="56d84-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d84-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56d84-112">Requirements</span></span>  
 <span data-ttu-id="56d84-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56d84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d84-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="56d84-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56d84-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="56d84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56d84-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d84-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d84-117">See also</span></span>

- [<span data-ttu-id="56d84-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56d84-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="56d84-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56d84-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="56d84-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56d84-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
