---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback4 Interface'
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
ms.openlocfilehash: 882f234cb94ccd65203b42ed213aab6355250af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788754"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="6e1c8-103">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-103">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="6e1c8-104">Ortak dil çalışma zamanının (CLR) bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-104">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e1c8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e1c8-105">Methods</span></span>  
  
|<span data-ttu-id="6e1c8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e1c8-106">Method</span></span>|<span data-ttu-id="6e1c8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e1c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e1c8-108">GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-108">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="6e1c8-109">Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-109">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="6e1c8-110">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-110">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="6e1c8-111">Sıkıştırma atık toplama işleminin sonucu olarak yığındaki nesnelerin yeni yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-111">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="6e1c8-112">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-112">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="6e1c8-113">Profil oluşturucuyu, tam zamanında (JıT) derleyicisinin bir işlevin yeniden derlemesini tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-113">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="6e1c8-114">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-114">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="6e1c8-115">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-115">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="6e1c8-116">ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-116">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="6e1c8-117">Yeniden derleme isteği işlenirken bir hatayla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-117">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="6e1c8-118">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-118">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="6e1c8-119">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-119">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e1c8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e1c8-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e1c8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e1c8-121">Requirements</span></span>  

 <span data-ttu-id="6e1c8-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e1c8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e1c8-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6e1c8-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e1c8-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e1c8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e1c8-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e1c8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1c8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e1c8-126">See also</span></span>

- [<span data-ttu-id="6e1c8-127">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-127">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="6e1c8-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e1c8-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6e1c8-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e1c8-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
