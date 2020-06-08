---
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
ms.openlocfilehash: db07e2afa64ea2bf80416e6ab8cba5a4dcdc8dcf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499681"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="00f9a-102">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00f9a-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="00f9a-103">Ortak dil çalışma zamanının (CLR) profil oluşturucuya iliştirme ve ayır durum bilgilerini iletişim kurmak için kullandığı geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="00f9a-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00f9a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="00f9a-104">Methods</span></span>  
  
|<span data-ttu-id="00f9a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="00f9a-105">Method</span></span>|<span data-ttu-id="00f9a-106">Description</span><span class="sxs-lookup"><span data-stu-id="00f9a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00f9a-107">InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00f9a-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="00f9a-108">Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="00f9a-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="00f9a-109">ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00f9a-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="00f9a-110">Profiler tarafından, profil oluşturucunun artık yakalama yöntemlerini çağırabelirteolabileceğini göstermek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="00f9a-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="00f9a-111">ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00f9a-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="00f9a-112">Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00f9a-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00f9a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00f9a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f9a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00f9a-114">Requirements</span></span>  
 <span data-ttu-id="00f9a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f9a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f9a-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00f9a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00f9a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00f9a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f9a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f9a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00f9a-119">See also</span></span>

- [<span data-ttu-id="00f9a-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00f9a-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="00f9a-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00f9a-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="00f9a-122">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00f9a-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="00f9a-123">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00f9a-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
