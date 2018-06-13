---
title: ICorProfilerCallback4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bcddc143cacc3df016e6b8dd7907a67354c4311
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455748"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="d5670-102">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5670-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="d5670-103">Ortak dil çalışma zamanı (CLR) profil bilgilerini iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5670-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5670-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5670-104">Methods</span></span>  
  
|<span data-ttu-id="d5670-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d5670-105">Method</span></span>|<span data-ttu-id="d5670-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5670-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5670-107">GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="d5670-108">Yeni bir derlenmiş yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamak Kod Oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5670-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="d5670-109">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="d5670-110">Yeni düzenini sıkıştırma çöp toplama sonucunda yığınındaki nesnelerin raporları.</span><span class="sxs-lookup"><span data-stu-id="d5670-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="d5670-111">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="d5670-112">Profil Oluşturucu tam zamanında (JIT) derleyici işlevinin yeniden derlenmek tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5670-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="d5670-113">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="d5670-114">Profil Oluşturucu tam zamanında (JIT) derleyici işlevi yeniden derleyin başladıktan bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5670-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="d5670-115">ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="d5670-116">Bir yeniden derleyebilirsiniz isteğini işlerken karşılaşılan bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5670-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="d5670-117">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5670-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="d5670-118">Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5670-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5670-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5670-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5670-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5670-120">Requirements</span></span>  
 <span data-ttu-id="d5670-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5670-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5670-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5670-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5670-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5670-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5670-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5670-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5670-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5670-125">See Also</span></span>  
 [<span data-ttu-id="d5670-126">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5670-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="d5670-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5670-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d5670-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5670-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
