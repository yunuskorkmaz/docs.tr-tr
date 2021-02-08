---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback3 Interface'
title: ICorProfilerCallback3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 70fba8768fef5da411b566d918308989a3f6e863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788806"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="a562f-103">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a562f-103">ICorProfilerCallback3 Interface</span></span>

<span data-ttu-id="a562f-104">Ortak dil çalışma zamanının (CLR) profil oluşturucuya iliştirme ve ayır durum bilgilerini iletişim kurmak için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a562f-104">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a562f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a562f-105">Methods</span></span>  
  
|<span data-ttu-id="a562f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a562f-106">Method</span></span>|<span data-ttu-id="a562f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a562f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a562f-108">InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a562f-108">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="a562f-109">Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a562f-109">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="a562f-110">ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a562f-110">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="a562f-111">Profiler tarafından, profil oluşturucunun artık yakalama yöntemlerini çağırabelirteolabileceğini göstermek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a562f-111">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="a562f-112">ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a562f-112">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="a562f-113">Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a562f-113">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a562f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a562f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a562f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a562f-115">Requirements</span></span>  

 <span data-ttu-id="a562f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a562f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a562f-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a562f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a562f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a562f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a562f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a562f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a562f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a562f-120">See also</span></span>

- [<span data-ttu-id="a562f-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a562f-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a562f-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a562f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a562f-123">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a562f-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="a562f-124">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a562f-124">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
