---
title: ICorProfilerCallback3 Arabirimi
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1419dfff7005b33fd1f8a545d168a410e7a88a76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="837c2-102">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="837c2-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="837c2-103">Ortak dil çalışma zamanı (CLR) iletişim kurmak için kullandığı geri arama yöntemleri ekleme ve durum bilgilerini profil oluşturucu için ayırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="837c2-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="837c2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="837c2-104">Methods</span></span>  
  
|<span data-ttu-id="837c2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="837c2-105">Method</span></span>|<span data-ttu-id="837c2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="837c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="837c2-107">InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837c2-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="837c2-108">Profil Oluşturucu ekleme işlemden sonra durumu başlatmak için bir fırsat vermek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="837c2-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="837c2-109">ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837c2-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="837c2-110">Profil Oluşturucu yakalama yöntemleri şimdi çağırabilir belirtmek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="837c2-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="837c2-111">ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="837c2-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="837c2-112">Profil Oluşturucu ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="837c2-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="837c2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="837c2-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837c2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="837c2-114">Requirements</span></span>  
 <span data-ttu-id="837c2-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="837c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837c2-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="837c2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="837c2-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="837c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="837c2-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837c2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="837c2-119">See Also</span></span>  
 [<span data-ttu-id="837c2-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="837c2-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="837c2-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="837c2-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="837c2-122">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="837c2-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="837c2-123">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="837c2-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
