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
ms.openlocfilehash: 9a402b7dfc3ece9d38994ed897162fe0d81ff0b9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503308"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="b75dd-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b75dd-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="b75dd-103">Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b75dd-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75dd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b75dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b75dd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b75dd-106">'ndaki Belleğin ayrıldığı nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b75dd-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="b75dd-107">'ndaki Nesnenin bir örnek olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b75dd-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b75dd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b75dd-108">Remarks</span></span>  
 <span data-ttu-id="b75dd-109">`ObjectedAllocated`Yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="b75dd-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="b75dd-110">`classId`Parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b75dd-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="b75dd-111">Profil Oluşturucu, geri aramadan hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır `ObjectAllocated` .</span><span class="sxs-lookup"><span data-stu-id="b75dd-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75dd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b75dd-112">Requirements</span></span>  
 <span data-ttu-id="b75dd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75dd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75dd-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b75dd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b75dd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b75dd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b75dd-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b75dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75dd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b75dd-117">See also</span></span>

- [<span data-ttu-id="b75dd-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b75dd-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b75dd-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b75dd-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="b75dd-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b75dd-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
