---
title: "ICorProfilerInfo4::InitializeCurrentThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="18b7e-102">ICorProfilerInfo4::InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18b7e-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="18b7e-103">Bu kilitlenme önlenebilir şekilde aynı iş parçacığı üzerinde API çağrılarının sonraki profil oluşturucu çalıştırılmasının geçerli iş parçacığının başlatır.</span><span class="sxs-lookup"><span data-stu-id="18b7e-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18b7e-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="18b7e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18b7e-105">Remarks</span></span>  
 <span data-ttu-id="18b7e-106">Sizi aramasını öneririz `InitializeCurrentThread` bir profil oluşturucu arayacağı herhangi bir iş parçacığı üzerinde varken API iş parçacıklarını askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="18b7e-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="18b7e-107">Bu yöntemi çağırmak için kendi iş parçacığı oluşturma örnekleme profil oluşturucular tarafından genellikle kullanılan [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yığın yapmak için yöntemi hedef iş parçacığı askıya alınmış durumdayken anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18b7e-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="18b7e-108">Çağırarak `InitializeCurrentThread` profil oluşturucu örnekleme iş parçacığı ilk oluşturduğunda sonra profil oluşturucular CLR Aksi durumda ilk çağrıda sırasında gerçekleştireceği bu yavaş iş parçacığı başına başlatma sağlayabilirsiniz `DoStackSnapshot` artık güvenli bir şekilde başka bir iş parçacığı olduğunda ortaya çıkabilir askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="18b7e-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18b7e-109">`InitializeCurrentThread`önceden kilitleri alın ve kilitlenme görevleri tamamlamak için başlatma yapar.</span><span class="sxs-lookup"><span data-stu-id="18b7e-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="18b7e-110">Çağrı `InitializeCurrentThread` yalnızca askıya alınmış iş parçacığı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="18b7e-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b7e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18b7e-111">Requirements</span></span>  
 <span data-ttu-id="18b7e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b7e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b7e-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18b7e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18b7e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18b7e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b7e-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b7e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18b7e-116">See Also</span></span>  
 [<span data-ttu-id="18b7e-117">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="18b7e-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="18b7e-118">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="18b7e-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="18b7e-119">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="18b7e-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
