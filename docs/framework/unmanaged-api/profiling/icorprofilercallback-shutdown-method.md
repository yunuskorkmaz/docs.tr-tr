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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041762"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="7561f-102">ICorProfilerCallback::Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7561f-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="7561f-103">Profil Oluşturucu, uygulamanın kapanacağını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7561f-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7561f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7561f-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7561f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7561f-105">Remarks</span></span>  
 <span data-ttu-id="7561f-106">Profil Oluşturucu kodu güvenli bir şekilde yöntemlerine çağrılamıyor [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) sonra arabirim `Shutdown` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7561f-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="7561f-107">Çağrıları `ICorProfilerInfo` yöntemleri sonra tanımsız davranışa neden `Shutdown` yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7561f-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="7561f-108">Sabit belirli olaylar kapatıldıktan sonra yine de oluşabilir. Profil Oluşturucu hemen bu oluştuğunda döndürülecek ilgileniriz.</span><span class="sxs-lookup"><span data-stu-id="7561f-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="7561f-109">`Shutdown` Yöntemin çağrılacağı, profili oluşturulan yönetilen uygulama yönetilen kod başladıysanız (diğer bir deyişle, ilk çerçeve işlem yığın üzerinde yönetilen).</span><span class="sxs-lookup"><span data-stu-id="7561f-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="7561f-110">Uygulamanın yönetilmeyen kod olarak başlatıldı, ancak daha sonra yönetilen koda Atlanan, dolayısıyla örneği ortak dil çalışma zamanı (CLR), ardından oluşturma `Shutdown` çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="7561f-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="7561f-111">Bu durumlarda, kitaplıkta profil oluşturucu içermelidir bir `DllMain` DLL_PROCESS_DETACH kullanan yordamı değeri tüm kaynakları serbest bırakın ve izlemeleri ve disk temizleme gibi verileri temizleme işlemini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="7561f-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="7561f-112">Genel olarak, Profil Oluşturucu ile beklenmeyen kapatma başa gerekir.</span><span class="sxs-lookup"><span data-stu-id="7561f-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="7561f-113">Örneğin, bir işlem Win32's durdu `TerminateProcess` yöntemi (Winbase.h içinde bildirilen).</span><span class="sxs-lookup"><span data-stu-id="7561f-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="7561f-114">Diğer durumlarda, belirli yönetilen iş parçacıkları (arka plan iş parçacıkları) sıralı yok etme iletileri için bunları sunmakla olmadan CLR durdurulur.</span><span class="sxs-lookup"><span data-stu-id="7561f-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7561f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7561f-115">Requirements</span></span>  
 <span data-ttu-id="7561f-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7561f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7561f-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7561f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7561f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7561f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7561f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7561f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7561f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7561f-120">See also</span></span>

- [<span data-ttu-id="7561f-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7561f-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7561f-122">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7561f-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
