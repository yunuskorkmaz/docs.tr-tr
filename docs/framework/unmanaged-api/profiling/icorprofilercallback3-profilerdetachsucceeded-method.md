---
title: ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: 93406dddf7babd8cf61032666737b993c2f721f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499603"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="181c0-102">ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="181c0-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="181c0-103">Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="181c0-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="181c0-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="181c0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="181c0-105">Return Value</span></span>  
 <span data-ttu-id="181c0-106">Bu geri çağırmada döndürülen değer yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="181c0-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="181c0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="181c0-107">Remarks</span></span>  
 <span data-ttu-id="181c0-108">`ProfilerDetachSucceeded`Tüm iş parçacıkları profil oluşturucunun kodundan çıktıktan sonra geri çağırma yapılır.</span><span class="sxs-lookup"><span data-stu-id="181c0-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="181c0-109">Bu yöntem çağrıldığında, profil oluşturucu, Kullanıcı arabirimine veya günlüğe kaydetme bileşenine bildirimde bulunmak gibi yıkıcısı için uygun olmayan son dakika görevleri gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="181c0-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="181c0-110">Ancak profil oluşturucu, bu geri çağırma sırasında CLR tarafından sunulan arabirimlerde işlevleri çağırmamalıdır ( [ICorProfilerInfo](icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri gibi).</span><span class="sxs-lookup"><span data-stu-id="181c0-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="181c0-111">CLR, ayırma işleminin başarılı olduğunu göstermek için Windows uygulama olay günlüğü 'nde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="181c0-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="181c0-112">Profil Oluşturucu bu geri aramadan döndüğünde, CLR Profil Oluşturucu nesnesini serbest bırakır ve profil oluşturucu DLL 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="181c0-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="181c0-113">Bu nedenle, profil oluşturucunun, yürütme bu geri çağrısından sonra profil oluşturucu DLL içinde oluşmasına neden olacak herhangi bir eylem gerçekleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="181c0-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="181c0-114">Örneğin, iş parçacığı oluşturmamalıdır veya zamanlayıcı geri çağırmaları kaydetmemelidir.</span><span class="sxs-lookup"><span data-stu-id="181c0-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="181c0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="181c0-115">Requirements</span></span>  
 <span data-ttu-id="181c0-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="181c0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="181c0-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="181c0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="181c0-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="181c0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="181c0-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="181c0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181c0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="181c0-120">See also</span></span>

- [<span data-ttu-id="181c0-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="181c0-121">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="181c0-122">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="181c0-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="181c0-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="181c0-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="181c0-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="181c0-124">Profiling</span></span>](index.md)
