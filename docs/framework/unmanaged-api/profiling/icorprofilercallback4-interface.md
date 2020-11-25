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
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730298"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="2a2f0-102">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-102">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="2a2f0-103">Ortak dil çalışma zamanının (CLR) bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a2f0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a2f0-104">Methods</span></span>  
  
|<span data-ttu-id="2a2f0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a2f0-105">Method</span></span>|<span data-ttu-id="2a2f0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a2f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a2f0-107">GetReJITParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="2a2f0-108">Kod Profilcisi yeni bir yeniden derlenmiş Yöntem gövdesi için alternatif kod oluşturma bayrakları ayarlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="2a2f0-109">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="2a2f0-110">Sıkıştırma atık toplama işleminin sonucu olarak yığındaki nesnelerin yeni yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="2a2f0-111">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="2a2f0-112">Profil oluşturucuyu, tam zamanında (JıT) derleyicisinin bir işlevin yeniden derlemesini tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="2a2f0-113">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="2a2f0-114">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="2a2f0-115">ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="2a2f0-116">Yeniden derleme isteği işlenirken bir hatayla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="2a2f0-117">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="2a2f0-118">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a2f0-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a2f0-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a2f0-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a2f0-120">Requirements</span></span>  

 <span data-ttu-id="2a2f0-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a2f0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a2f0-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a2f0-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a2f0-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a2f0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a2f0-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a2f0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2f0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a2f0-125">See also</span></span>

- [<span data-ttu-id="2a2f0-126">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="2a2f0-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a2f0-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2a2f0-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a2f0-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
