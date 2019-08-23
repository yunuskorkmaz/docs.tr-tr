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
ms.openlocfilehash: b9bb5a2629e435d76691d48feef6689191b66373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957895"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="cf4db-102">ICorProfilerInfo4::InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf4db-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="cf4db-103">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf4db-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf4db-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf4db-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf4db-105">Remarks</span></span>  
 <span data-ttu-id="cf4db-106">Askıya alınmış iş parçacıkları varken `InitializeCurrentThread` profil oluşturucu API 'si çağıran herhangi bir iş parçacığında çağrı yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="cf4db-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="cf4db-107">Bu yöntem genellikle, hedef iş parçacığı askıya alınırken yığın izlenecek yol için [ICorProfilerInfo2::D oStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodunu çağırmak üzere kendi iş parçacığını oluşturan örnekleme profil oluşturucular tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf4db-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="cf4db-108">Profil Oluşturucu `InitializeCurrentThread` ilk olarak `DoStackSnapshot` örnekleme iş parçacığını oluşturduğunda bir kez çağırarak, profil oluşturucular, clr 'nin ilk çağrılması sırasında başka bir iş parçacığı olmadığında daha sonra yerine getirebileceği, yavaş iş parçacığı başına başlatmanın bu şekilde gerçekleşmemesini sağlayabilir alın.</span><span class="sxs-lookup"><span data-stu-id="cf4db-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf4db-109">`InitializeCurrentThread`başlatma işlemi, kilitleri olan görevleri tamamlamak için önceden ve kilitlenme olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf4db-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="cf4db-110">Yalnızca `InitializeCurrentThread` askıya alınmış iş parçacığı olmadığında çağırın.</span><span class="sxs-lookup"><span data-stu-id="cf4db-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf4db-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf4db-111">Requirements</span></span>  
 <span data-ttu-id="cf4db-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf4db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4db-113">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cf4db-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf4db-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf4db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf4db-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4db-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf4db-116">See also</span></span>

- [<span data-ttu-id="cf4db-117">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf4db-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="cf4db-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf4db-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cf4db-119">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf4db-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
