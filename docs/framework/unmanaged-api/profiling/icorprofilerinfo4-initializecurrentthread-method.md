---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: InitializeCurrentThread yöntemi'
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
ms.openlocfilehash: a78816c736507a4a59da3ea1c75b078b54c34125
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781410"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="1186c-103">ICorProfilerInfo4::InitializeCurrentThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1186c-103">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="1186c-104">Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="1186c-104">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1186c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1186c-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1186c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1186c-106">Remarks</span></span>  

 <span data-ttu-id="1186c-107">`InitializeCurrentThread`Askıya alınmış iş parçacıkları varken profil oluşturucu API 'si çağıran herhangi bir iş parçacığında çağrı yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="1186c-107">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="1186c-108">Bu yöntem genellikle, hedef iş parçacığı askıya alınırken yığın izlenecek yol için [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metodunu çağırmak üzere kendi iş parçacığını oluşturan örnekleme profil oluşturucular tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1186c-108">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="1186c-109">`InitializeCurrentThread`Profil Oluşturucu ilk olarak örnekleme iş parçacığını oluşturduğunda, profil oluşturucular, clr 'nin ilk çağrı sırasında gerçekleştireceği yavaş iş parçacığı başlatma `DoStackSnapshot` işleminin, başka bir iş parçacığı askıya alınmadıkça güvenli bir şekilde gerçekleşmemesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1186c-109">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1186c-110">`InitializeCurrentThread` başlatma işlemi, kilitleri olan görevleri tamamlamak için önceden ve kilitlenme olabilir.</span><span class="sxs-lookup"><span data-stu-id="1186c-110">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="1186c-111">`InitializeCurrentThread`Yalnızca askıya alınmış iş parçacığı olmadığında çağırın.</span><span class="sxs-lookup"><span data-stu-id="1186c-111">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1186c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1186c-112">Requirements</span></span>  

 <span data-ttu-id="1186c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1186c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1186c-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1186c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1186c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1186c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1186c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1186c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1186c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1186c-117">See also</span></span>

- [<span data-ttu-id="1186c-118">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1186c-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1186c-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1186c-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1186c-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1186c-120">Profiling</span></span>](index.md)
