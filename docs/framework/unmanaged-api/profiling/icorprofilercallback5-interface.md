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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6481d647541af40b956c38a76d281ccb84e7c7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602552"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="2926e-102">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2926e-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="2926e-103">Bir profil oluşturucu ile birlikte kullanıldığında tam kapatma Canlı nesnelerin belirlemenize yardımcı olacak bilgiler tamamlayan [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) veya [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)yöntemi ile birlikte [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2926e-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="2926e-104">`ICorProfilerCallback5` bildirimler ilgili bağımlı tanıtıcıları abone olmak için bir yönetilen bellek profili Oluşturucu tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2926e-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2926e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2926e-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2926e-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2926e-106">Methods</span></span>  
  
|<span data-ttu-id="2926e-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2926e-107">Method</span></span>|<span data-ttu-id="2926e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2926e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2926e-109">ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2926e-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="2926e-110">Hem doğrudan üyesi alan başvuruları ve aracılığıyla bu kök tarafından başvurulan nesneleri geçişli kapatılmasını tanımlayan `ConditionalWeakTable` bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="2926e-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2926e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2926e-111">Requirements</span></span>  
 <span data-ttu-id="2926e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2926e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2926e-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2926e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2926e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2926e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2926e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2926e-115">See also</span></span>
- [<span data-ttu-id="2926e-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2926e-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2926e-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2926e-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
