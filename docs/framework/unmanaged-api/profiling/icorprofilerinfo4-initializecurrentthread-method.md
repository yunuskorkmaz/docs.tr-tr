---
title: ICorProfilerInfo4::InitializeCurrentThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 990ae316a780af9be96f6b91900f33cbb2db4f36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727982"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="8555e-102">ICorProfilerInfo4::InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8555e-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="8555e-103">Geçerli iş parçacığı sonraki profil oluşturucu bu kilitlenme önlenebilir şekilde aynı iş parçacığında API çağrılarının tarifelerindeki başlatır.</span><span class="sxs-lookup"><span data-stu-id="8555e-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8555e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8555e-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8555e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8555e-105">Remarks</span></span>  
 <span data-ttu-id="8555e-106">Çağırmanızı öneririz `InitializeCurrentThread` bir profil oluşturucu çağıran herhangi bir iş parçacığı üzerinde varken API iş parçacıkları askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="8555e-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="8555e-107">Bu yöntem çağırmak için kendi iş parçacığı oluşturma örnekleme profil oluşturucular tarafından genellikle kullanılan [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yığın gerçekleştirmek için yöntemi hedef iş parçacığını askıya alındığında size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="8555e-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="8555e-108">Çağırarak `InitializeCurrentThread` zaman profil oluşturucu örnekleme iş parçacığı ilk oluşturulduktan sonra profil Oluşturucular, CLR Aksi takdirde ilk çağrı sırasında gerçekleştirecek yavaş iş parçacığı başına başlatmanın sağlayabilirsiniz `DoStackSnapshot` artık güvenli bir şekilde başka bir iş parçacığı olduğunda ortaya çıkabilir askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="8555e-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8555e-109">`InitializeCurrentThread` önceden kilit alın ve kilitlenme görevleri tamamlamak için başlatma yapar.</span><span class="sxs-lookup"><span data-stu-id="8555e-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="8555e-110">Çağrı `InitializeCurrentThread` askıya alınan iş parçacığı olmadığında.</span><span class="sxs-lookup"><span data-stu-id="8555e-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8555e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8555e-111">Requirements</span></span>  
 <span data-ttu-id="8555e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8555e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8555e-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8555e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8555e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8555e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8555e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8555e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8555e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8555e-116">See also</span></span>
- [<span data-ttu-id="8555e-117">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8555e-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="8555e-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8555e-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="8555e-119">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8555e-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
