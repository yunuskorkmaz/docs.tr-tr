---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback3::P Rodosyasıçıkarılabilir başarılı yöntemi'
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
ms.openlocfilehash: bc80b5bd5301bb5b0278534cfba6ac23e5968620
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788780"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="05edf-103">ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05edf-103">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>

<span data-ttu-id="05edf-104">Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="05edf-104">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05edf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="05edf-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05edf-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05edf-106">Return Value</span></span>  

 <span data-ttu-id="05edf-107">Bu geri çağırmada döndürülen değer yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="05edf-107">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05edf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05edf-108">Remarks</span></span>  

 <span data-ttu-id="05edf-109">`ProfilerDetachSucceeded`Tüm iş parçacıkları profil oluşturucunun kodundan çıktıktan sonra geri çağırma yapılır.</span><span class="sxs-lookup"><span data-stu-id="05edf-109">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="05edf-110">Bu yöntem çağrıldığında, profil oluşturucu, Kullanıcı arabirimine veya günlüğe kaydetme bileşenine bildirimde bulunmak gibi yıkıcısı için uygun olmayan son dakika görevleri gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="05edf-110">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="05edf-111">Ancak profil oluşturucu, bu geri çağırma sırasında CLR tarafından sunulan arabirimlerde işlevleri çağırmamalıdır ( [ICorProfilerInfo](icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri gibi).</span><span class="sxs-lookup"><span data-stu-id="05edf-111">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="05edf-112">CLR, ayırma işleminin başarılı olduğunu göstermek için Windows uygulama olay günlüğü 'nde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05edf-112">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="05edf-113">Profil Oluşturucu bu geri aramadan döndüğünde, CLR Profil Oluşturucu nesnesini serbest bırakır ve profil oluşturucu DLL 'yi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05edf-113">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="05edf-114">Bu nedenle, profil oluşturucunun, yürütme bu geri çağrısından sonra profil oluşturucu DLL içinde oluşmasına neden olacak herhangi bir eylem gerçekleştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="05edf-114">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="05edf-115">Örneğin, iş parçacığı oluşturmamalıdır veya zamanlayıcı geri çağırmaları kaydetmemelidir.</span><span class="sxs-lookup"><span data-stu-id="05edf-115">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05edf-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05edf-116">Requirements</span></span>  

 <span data-ttu-id="05edf-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05edf-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05edf-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05edf-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05edf-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05edf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05edf-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05edf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05edf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05edf-121">See also</span></span>

- [<span data-ttu-id="05edf-122">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05edf-122">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="05edf-123">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05edf-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="05edf-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05edf-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="05edf-125">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05edf-125">Profiling</span></span>](index.md)
