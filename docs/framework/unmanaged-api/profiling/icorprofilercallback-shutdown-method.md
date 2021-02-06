---
description: ': ICorProfilerCallback:: kapanıyor yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::Shutdown Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 7afc274579f248ee190e379160f2709b5cb9881a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657326"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="ff565-103">ICorProfilerCallback::Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff565-103">ICorProfilerCallback::Shutdown Method</span></span>

<span data-ttu-id="ff565-104">Profil oluşturucuyu uygulamanın kapandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ff565-104">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff565-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff565-105">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff565-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff565-106">Remarks</span></span>  

 <span data-ttu-id="ff565-107">Profil Oluşturucu kodu, yöntemi çağrıldıktan sonra [ICorProfilerInfo](icorprofilerinfo-interface.md) arabiriminin yöntemlerini güvenli bir şekilde çağıramaz `Shutdown` .</span><span class="sxs-lookup"><span data-stu-id="ff565-107">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="ff565-108">Yöntemlere yapılan çağrılar `ICorProfilerInfo` , yöntemin dönüşden sonra tanımsız davranışa neden olur `Shutdown` .</span><span class="sxs-lookup"><span data-stu-id="ff565-108">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="ff565-109">Bazı sabit olaylar, kapatmadan sonra yine de gerçekleşebilir; Profil Oluşturucu, bu gerçekleştiğinde hemen döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff565-109">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="ff565-110">`Shutdown`Yöntemi yalnızca, profili oluşturulan yönetilen uygulama yönetilen kod olarak (yani, işlem yığınındaki ilk çerçeve yönetiliyorsa) başlatıldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ff565-110">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="ff565-111">Uygulama, yönetilmeyen kod olarak başlatıldıysa ancak daha sonra yönetilen koda atlamışsa, bu nedenle ortak dil çalışma zamanının (CLR) bir örneğini oluşturur, ardından `Shutdown` çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="ff565-111">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="ff565-112">Bu gibi durumlarda, profil oluşturucu kendi kitaplığına `DllMain` , herhangi bir kaynağı boşaltmak ve verilerin temizleme işlemini gerçekleştirmek için DLL_PROCESS_DETACH değerini kullanan bir yordamı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ff565-112">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="ff565-113">Genel olarak, profil oluşturucunun beklenmedik kapanmalar ile Cope olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff565-113">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="ff565-114">Örneğin, bir işlem Win32's yöntemi tarafından durdurulur `TerminateProcess` (Winbase. h içinde bildirilmiştir).</span><span class="sxs-lookup"><span data-stu-id="ff565-114">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="ff565-115">Diğer durumlarda CLR, belirli yönetilen iş parçacıklarını (arka plan iş parçacıkları) bunlar için düzenli olarak yok etme iletileri teslim etmeden durdurur.</span><span class="sxs-lookup"><span data-stu-id="ff565-115">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff565-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff565-116">Requirements</span></span>  

 <span data-ttu-id="ff565-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff565-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff565-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ff565-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff565-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff565-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff565-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff565-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff565-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff565-121">See also</span></span>

- [<span data-ttu-id="ff565-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff565-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ff565-123">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff565-123">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
