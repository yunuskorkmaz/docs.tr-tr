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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bffe293f7d29c34a22196336533202996f3fd129
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454049"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="13a5c-102">ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13a5c-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="13a5c-103">Profil Oluşturucu ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="13a5c-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13a5c-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="13a5c-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13a5c-105">Return Value</span></span>  
 <span data-ttu-id="13a5c-106">Bu geri çağırma yönteminden döndürülen değer yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="13a5c-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13a5c-107">Remarks</span></span>  
 <span data-ttu-id="13a5c-108">`ProfilerDetachSucceeded` Tüm iş parçacıklarının Profil Oluşturucu'nın kod çıkış sonra geri çağırma verildi.</span><span class="sxs-lookup"><span data-stu-id="13a5c-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="13a5c-109">Profil Oluşturucu, bu yöntem çağrıldığında, kendi kullanıcı Arabirimi veya günlük bileşeni bildiren gibi kendi yıkıcı için uygun olmayan herhangi bir son dakika görevi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="13a5c-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="13a5c-110">Ancak, profil oluşturucu işlevler CLR tarafından bu geri çağırma sırasında sağlanan arabirimlerindeki çağırmamalıdır (gibi [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri).</span><span class="sxs-lookup"><span data-stu-id="13a5c-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="13a5c-111">CLR ayırma işlemi başarılı olduğunu göstermek için Windows uygulama olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13a5c-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="13a5c-112">Profil Oluşturucu ten bu geri döndükten sonra CLR Profil Oluşturucu nesne serbest bırakır ve profil oluşturucu DLL kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13a5c-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="13a5c-113">Bu nedenle, profil oluşturucu ten bu geri döndükten sonra DLL profil oluşturucu içinde gerçekleşmesi yürütme neden olacak herhangi bir eylem gerçekleştirmeniz gerekir değil.</span><span class="sxs-lookup"><span data-stu-id="13a5c-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="13a5c-114">Örneğin, değil iş parçacığı oluşturabilir veya gerekir Zamanlayıcı geri aramaları kaydetme.</span><span class="sxs-lookup"><span data-stu-id="13a5c-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a5c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13a5c-115">Requirements</span></span>  
 <span data-ttu-id="13a5c-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a5c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a5c-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13a5c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13a5c-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a5c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13a5c-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a5c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a5c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13a5c-120">See Also</span></span>  
 [<span data-ttu-id="13a5c-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13a5c-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="13a5c-122">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13a5c-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="13a5c-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13a5c-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="13a5c-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="13a5c-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
