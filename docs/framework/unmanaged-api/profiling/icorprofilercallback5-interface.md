---
title: ICorProfilerCallback5 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0406b537f6f20d7194a0115020245ade101bd498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="42c56-102">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42c56-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="42c56-103">Bir profil oluşturucu ile birlikte kullanıldığında tam kapatma Canlı nesnelerin tanımlamak yardımcı olacak bilgiler tamamlayan [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) veya [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)yöntemi ile birlikte [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="42c56-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="42c56-104">`ICorProfilerCallback5`bildirimleri ilgili bağımlı işleyicilerine abone olmak için yönetilen bellek Profil Oluşturucu tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42c56-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c56-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42c56-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42c56-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="42c56-106">Methods</span></span>  
  
|<span data-ttu-id="42c56-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="42c56-107">Method</span></span>|<span data-ttu-id="42c56-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42c56-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42c56-109">ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42c56-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="42c56-110">Geçişli kapatma hem doğrudan üyesi alan başvuruları aracılığıyla ve aracılığıyla bu kökleri tarafından başvurulan nesne tanımlayan `ConditionalWeakTable` bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="42c56-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42c56-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42c56-111">Requirements</span></span>  
 <span data-ttu-id="42c56-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c56-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42c56-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42c56-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c56-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42c56-115">See Also</span></span>  
 [<span data-ttu-id="42c56-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="42c56-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="42c56-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42c56-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
