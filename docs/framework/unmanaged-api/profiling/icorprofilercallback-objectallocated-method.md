---
description: ': ICorProfilerCallback:: Objectalkonumlandırılan yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 58b58aeb4bb88d0df32cebc32440317a4d23632d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745170"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="58f2a-103">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58f2a-103">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="58f2a-104">Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="58f2a-104">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58f2a-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58f2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58f2a-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="58f2a-107">'ndaki Belleğin ayrıldığı nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="58f2a-107">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="58f2a-108">'ndaki Nesnenin bir örnek olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="58f2a-108">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58f2a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58f2a-109">Remarks</span></span>  

 <span data-ttu-id="58f2a-110">`ObjectedAllocated`Yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="58f2a-110">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="58f2a-111">`classId`Parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="58f2a-111">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="58f2a-112">Profil Oluşturucu, geri aramadan hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır `ObjectAllocated` .</span><span class="sxs-lookup"><span data-stu-id="58f2a-112">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58f2a-113">Requirements</span></span>  

 <span data-ttu-id="58f2a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58f2a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f2a-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="58f2a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58f2a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="58f2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58f2a-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f2a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58f2a-118">See also</span></span>

- [<span data-ttu-id="58f2a-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58f2a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="58f2a-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58f2a-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="58f2a-121">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58f2a-121">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
