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
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868440"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="aeca9-102">ICorProfilerInfo4::InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeca9-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="aeca9-103">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeca9-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeca9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeca9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="aeca9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeca9-105">Remarks</span></span>  
 <span data-ttu-id="aeca9-106">Askıya alınmış iş parçacıkları varken profil oluşturucu API çağrısı yapılacak herhangi bir iş parçacığında `InitializeCurrentThread` çağırmalarını öneririz.</span><span class="sxs-lookup"><span data-stu-id="aeca9-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="aeca9-107">Bu yöntem genellikle, hedef iş parçacığı askıya alınırken yığın izlenecek yol için [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metodunu çağırmak üzere kendi iş parçacığını oluşturan örnekleme profil oluşturucular tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeca9-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="aeca9-108">Profil Oluşturucu ilk olarak örnekleme iş parçacığını oluşturduğunda `InitializeCurrentThread` bir kez çağırarak, profil oluşturucular ilk çağrı sırasında CLR 'nin geçici `DoStackSnapshot` olarak gerçekleştireceği yavaş iş parçacığı başlatma işleminin başka bir iş parçacığı askıya alınmadıkça güvenli bir şekilde gerçekleşmemesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="aeca9-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeca9-109">`InitializeCurrentThread`, kilitleri kilitleyen ve kilitlenmeleri gereken görevleri tamamlamak için önceden başlatma işlemi yapar.</span><span class="sxs-lookup"><span data-stu-id="aeca9-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="aeca9-110">Yalnızca askıya alınmış iş parçacığı olmadığında `InitializeCurrentThread` çağırın.</span><span class="sxs-lookup"><span data-stu-id="aeca9-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeca9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeca9-111">Requirements</span></span>  
 <span data-ttu-id="aeca9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeca9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeca9-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="aeca9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aeca9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aeca9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeca9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeca9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeca9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeca9-116">See also</span></span>

- [<span data-ttu-id="aeca9-117">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aeca9-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="aeca9-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aeca9-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="aeca9-119">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aeca9-119">Profiling</span></span>](index.md)
