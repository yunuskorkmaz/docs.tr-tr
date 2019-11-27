---
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
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446936"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="bb767-102">ICorProfilerCallback::Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb767-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="bb767-103">Profil oluşturucuyu uygulamanın kapandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bb767-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb767-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb767-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb767-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb767-105">Remarks</span></span>  
 <span data-ttu-id="bb767-106">Profil Oluşturucu kodu, `Shutdown` yöntemi çağrıldıktan sonra [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabiriminin yöntemlerini güvenli bir şekilde çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="bb767-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="bb767-107">`ICorProfilerInfo` yöntemlere yapılan çağrılar, `Shutdown` yöntemi döndüğünde tanımsız davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="bb767-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="bb767-108">Bazı sabit olaylar, kapatmadan sonra yine de gerçekleşebilir; Profil Oluşturucu, bu gerçekleştiğinde hemen döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="bb767-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="bb767-109">`Shutdown` yöntemi yalnızca, profili oluşturulan yönetilen uygulama yönetilen kod olarak (yani, işlem yığınında ilk çerçeve yönetiliyorsa) başlatıldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bb767-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="bb767-110">Uygulama, yönetilmeyen kod olarak başlatıldıysa ancak daha sonra yönetilen koda atlamışsa, bu nedenle ortak dil çalışma zamanının (CLR) bir örneğini oluşturup `Shutdown` çağırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="bb767-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="bb767-111">Bu gibi durumlarda, profil oluşturucu, tüm kaynakları serbest bırakmak ve verilerin temizleme işlemini gerçekleştirmek (örneğin, verileri diske bırakmak vb.) için DLL_PROCESS_DETACH değerini kullanan bir `DllMain` yordamını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bb767-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="bb767-112">Genel olarak, profil oluşturucunun beklenmedik kapanmalar ile Cope olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb767-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="bb767-113">Örneğin, bir işlem Win32's `TerminateProcess` yöntemi tarafından durdurulur (Winbase. h içinde bildirilmiştir).</span><span class="sxs-lookup"><span data-stu-id="bb767-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="bb767-114">Diğer durumlarda CLR, belirli yönetilen iş parçacıklarını (arka plan iş parçacıkları) bunlar için düzenli olarak yok etme iletileri teslim etmeden durdurur.</span><span class="sxs-lookup"><span data-stu-id="bb767-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb767-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb767-115">Requirements</span></span>  
 <span data-ttu-id="bb767-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb767-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb767-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bb767-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb767-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bb767-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb767-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb767-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb767-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb767-120">See also</span></span>

- [<span data-ttu-id="bb767-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb767-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bb767-122">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb767-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
