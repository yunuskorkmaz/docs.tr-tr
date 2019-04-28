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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66e6a67ce022365fa8c9e1005dfecbe4b23abd10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598889"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="a77e5-102">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a77e5-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="a77e5-103">Ortak dil çalışma zamanı (CLR) iletişim kurmak için kullandığı geri çağırma yöntemleri ekleme ve ayırma profil oluşturucu için durum bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a77e5-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a77e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a77e5-104">Methods</span></span>  
  
|<span data-ttu-id="a77e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a77e5-105">Method</span></span>|<span data-ttu-id="a77e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a77e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a77e5-107">InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a77e5-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="a77e5-108">Profil Oluşturucu bir iliştirme işleminden sonra kendi durumunu başlatmak üzere bir fırsat vermek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a77e5-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="a77e5-109">ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a77e5-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="a77e5-110">Profil Oluşturucu yakalama yöntemleri artık çağırabilir belirtmek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a77e5-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="a77e5-111">ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a77e5-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="a77e5-112">Profil Oluşturucu, ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a77e5-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a77e5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a77e5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a77e5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a77e5-114">Requirements</span></span>  
 <span data-ttu-id="a77e5-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a77e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a77e5-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a77e5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a77e5-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a77e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a77e5-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a77e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77e5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a77e5-119">See also</span></span>

- [<span data-ttu-id="a77e5-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a77e5-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a77e5-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a77e5-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a77e5-122">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a77e5-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="a77e5-123">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a77e5-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
