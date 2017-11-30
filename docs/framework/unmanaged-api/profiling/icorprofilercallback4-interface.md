---
title: ICorProfilerCallback4 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="5c087-102">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c087-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="5c087-103">Ortak dil çalışma zamanı (CLR) profil bilgilerini iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c087-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c087-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c087-104">Methods</span></span>  
  
|<span data-ttu-id="5c087-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c087-105">Method</span></span>|<span data-ttu-id="5c087-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c087-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c087-107">Getrejıtparameters yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="5c087-108">Yeni bir derlenmiş yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamak Kod Oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c087-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="5c087-109">MovedReferences2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="5c087-110">Yeni düzenini sıkıştırma çöp toplama sonucunda yığınındaki nesnelerin raporları.</span><span class="sxs-lookup"><span data-stu-id="5c087-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="5c087-111">Rejıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="5c087-112">Profil Oluşturucu tam zamanında (JIT) derleyici işlevinin yeniden derlenmek tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c087-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="5c087-113">Rejıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="5c087-114">Profil Oluşturucu tam zamanında (JIT) derleyici işlevi yeniden derleyin başladıktan bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c087-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="5c087-115">Rejıterror yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="5c087-116">Bir yeniden derleyebilirsiniz isteğini işlerken karşılaşılan bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c087-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="5c087-117">SurvivingReferences2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c087-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="5c087-118">Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir.</span><span class="sxs-lookup"><span data-stu-id="5c087-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c087-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c087-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c087-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c087-120">Requirements</span></span>  
 <span data-ttu-id="5c087-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c087-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c087-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c087-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c087-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c087-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c087-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c087-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c087-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c087-125">See Also</span></span>  
 [<span data-ttu-id="5c087-126">Icorprofilercallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c087-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="5c087-127">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c087-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5c087-128">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c087-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
