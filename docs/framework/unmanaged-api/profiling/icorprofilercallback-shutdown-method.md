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
ms.openlocfilehash: 83e32b2b69d53772f8a4ebaabe1c025b95d1da47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453733"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="76e60-102">ICorProfilerCallback::Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76e60-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="76e60-103">Profil Oluşturucu uygulamanın kapanacağını bildirir.</span><span class="sxs-lookup"><span data-stu-id="76e60-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76e60-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="76e60-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76e60-105">Remarks</span></span>  
 <span data-ttu-id="76e60-106">Profil Oluşturucu kodu güvenle yöntemleri çağrılamaz [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) sonra arabirim `Shutdown` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="76e60-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="76e60-107">Yapılan her çağrı `ICorProfilerInfo` yöntemleri neden sonra tanımsız davranış `Shutdown` yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="76e60-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="76e60-108">Değişmez belirli olaylar kapatıldıktan sonra hala oluşabilir; Profil Oluşturucu hemen bu oluştuğunda döndürülecek ilgilenebilmek.</span><span class="sxs-lookup"><span data-stu-id="76e60-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="76e60-109">`Shutdown` Yöntemi çağrılır, yalnızca profili oluşturuluyor yönetilen uygulama yönetilen kod başladıysanız (diğer bir deyişle, ilk çerçeve işlem yığında yönetilen).</span><span class="sxs-lookup"><span data-stu-id="76e60-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="76e60-110">Uygulama yönetilmeyen kodu olarak başladı, ancak daha sonra yönetilen koda Atlanan, böylece örneği ortak dil çalışma zamanı (CLR), ardından oluşturmayı `Shutdown` çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="76e60-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="76e60-111">Bu durumlarda, kendi Kitaplığı'nda profil oluşturucu içermelidir bir `DllMain` DLL_PROCESS_DETACH kullanan yordamı değer tüm kaynakları serbest ve vb. diske izlemeleri temizleme gibi verilerini temizleme işlenmesini gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="76e60-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="76e60-112">Genel olarak, Profil Oluşturucu ile beklenmeyen kapatmalar başa gerekir.</span><span class="sxs-lookup"><span data-stu-id="76e60-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="76e60-113">Örneğin, bir işlem Win32 tarafından 's durdurulamaz `TerminateProcess` yöntemi (Winbase.h içinde bildirilen).</span><span class="sxs-lookup"><span data-stu-id="76e60-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="76e60-114">Diğer durumlarda, CLR düzenli yok etme iletileri kendileri için sunmakla olmadan belirli yönetilen iş parçacığı (arka plan iş parçacıkları) durdurulur.</span><span class="sxs-lookup"><span data-stu-id="76e60-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76e60-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76e60-115">Requirements</span></span>  
 <span data-ttu-id="76e60-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e60-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e60-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76e60-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76e60-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76e60-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76e60-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76e60-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e60-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76e60-120">See Also</span></span>  
 [<span data-ttu-id="76e60-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76e60-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="76e60-122">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76e60-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
