---
title: ICorProfilerCallback5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865031"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="b6aa5-102">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6aa5-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="b6aa5-103">Bir profil oluşturucunun, ICorProfilerCallback:: [ObjectReferences](icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleriyle birlikte [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) veya [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi ile birlikte kullanıldığında, canlı nesnelerin tam kapatılmasını belirlemesine yardımcı olmak için bilgileri tamamlar.</span><span class="sxs-lookup"><span data-stu-id="b6aa5-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="b6aa5-104">bağımlı tanıtıcılarla ilgili bildirimlere abone olmak için `ICorProfilerCallback5` yönetilen bir bellek Oluşturucu tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6aa5-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6aa5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6aa5-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6aa5-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b6aa5-106">Methods</span></span>  
  
|<span data-ttu-id="b6aa5-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b6aa5-107">Method</span></span>|<span data-ttu-id="b6aa5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6aa5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6aa5-109">ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6aa5-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="b6aa5-110">Doğrudan üye alan başvuruları ve `ConditionalWeakTable` bağımlılıklarıyla, bu köklerin başvurduğu nesnelerin geçişli kapatılmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="b6aa5-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6aa5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6aa5-111">Requirements</span></span>  
 <span data-ttu-id="b6aa5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6aa5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6aa5-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b6aa5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6aa5-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6aa5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aa5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6aa5-115">See also</span></span>

- [<span data-ttu-id="b6aa5-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b6aa5-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b6aa5-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6aa5-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
