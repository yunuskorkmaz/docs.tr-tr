---
title: ICorProfilerCallback3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3
helpviewer_keywords: ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c62dfb9b44999309ab2be7dfdcdfba3bb5dde29c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="8cc41-102">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc41-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="8cc41-103">Ortak dil çalışma zamanı (CLR) iletişim kurmak için kullandığı geri arama yöntemleri ekleme ve durum bilgilerini profil oluşturucu için ayırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cc41-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cc41-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8cc41-104">Methods</span></span>  
  
|<span data-ttu-id="8cc41-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8cc41-105">Method</span></span>|<span data-ttu-id="8cc41-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cc41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cc41-107">Initializeforattach yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc41-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="8cc41-108">Profil Oluşturucu ekleme işlemden sonra durumu başlatmak için bir fırsat vermek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8cc41-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="8cc41-109">ProfilerAttachComplete yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc41-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="8cc41-110">Profil Oluşturucu yakalama yöntemleri şimdi çağırabilir belirtmek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8cc41-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="8cc41-111">ProfilerDetachSucceeded yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cc41-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="8cc41-112">Profil Oluşturucu ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8cc41-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc41-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cc41-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc41-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cc41-114">Requirements</span></span>  
 <span data-ttu-id="8cc41-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cc41-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc41-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8cc41-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cc41-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cc41-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cc41-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc41-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc41-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cc41-119">See Also</span></span>  
 [<span data-ttu-id="8cc41-120">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cc41-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8cc41-121">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc41-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="8cc41-122">Icorprofilercallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc41-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="8cc41-123">Icorprofilercallback4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cc41-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
