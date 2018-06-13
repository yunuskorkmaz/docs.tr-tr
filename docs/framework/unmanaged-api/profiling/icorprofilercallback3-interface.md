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
ms.openlocfilehash: cc63a0a42c1da11daa5d38ecce505296a893616b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453941"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="5b557-102">ICorProfilerCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b557-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="5b557-103">Ortak dil çalışma zamanı (CLR) iletişim kurmak için kullandığı geri arama yöntemleri ekleme ve durum bilgilerini profil oluşturucu için ayırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b557-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b557-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5b557-104">Methods</span></span>  
  
|<span data-ttu-id="5b557-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5b557-105">Method</span></span>|<span data-ttu-id="5b557-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b557-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b557-107">InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b557-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="5b557-108">Profil Oluşturucu ekleme işlemden sonra durumu başlatmak için bir fırsat vermek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b557-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="5b557-109">ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b557-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="5b557-110">Profil Oluşturucu yakalama yöntemleri şimdi çağırabilir belirtmek için CLR tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b557-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="5b557-111">ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b557-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="5b557-112">Profil Oluşturucu ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5b557-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b557-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b557-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b557-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b557-114">Requirements</span></span>  
 <span data-ttu-id="5b557-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b557-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b557-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b557-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b557-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b557-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b557-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b557-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b557-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b557-119">See Also</span></span>  
 [<span data-ttu-id="5b557-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b557-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5b557-121">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b557-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5b557-122">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b557-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="5b557-123">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b557-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
