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
ms.openlocfilehash: a96aadcec6cb3c4f4680499585bf1c950bc5ddd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525316"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="2c3f5-102">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="2c3f5-103">Ortak dil çalışma zamanı (CLR) profil oluşturucu bilgiler iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c3f5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c3f5-104">Methods</span></span>  
  
|<span data-ttu-id="2c3f5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2c3f5-105">Method</span></span>|<span data-ttu-id="2c3f5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3f5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c3f5-107">GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="2c3f5-108">Kod profil oluşturucu, yeni bir znovu yöntem gövdesi için başka bir kod oluşturma bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="2c3f5-109">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="2c3f5-110">Yeni düzen sıkıştırma çöp toplama sonucu olarak yığındaki nesnelerin raporları.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="2c3f5-111">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="2c3f5-112">Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi yeniden derleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="2c3f5-113">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="2c3f5-114">Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi yeniden derle başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="2c3f5-115">ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="2c3f5-116">Bir derleme isteğini işlerken karşılaşılan bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="2c3f5-117">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="2c3f5-118">Sıkıştırma dışı bir atık toplama sonucunda yığın nesnelerin yerleşimini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3f5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c3f5-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3f5-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c3f5-120">Requirements</span></span>  
 <span data-ttu-id="2c3f5-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3f5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3f5-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c3f5-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c3f5-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c3f5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c3f5-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3f5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3f5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3f5-125">See also</span></span>
- [<span data-ttu-id="2c3f5-126">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="2c3f5-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c3f5-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2c3f5-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3f5-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
