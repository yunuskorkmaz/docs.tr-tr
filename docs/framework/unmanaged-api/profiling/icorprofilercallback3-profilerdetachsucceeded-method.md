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
ms.openlocfilehash: efe3070b41b1d71e0cf533a7f9f211f4c6626726
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197872"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="fe141-102">ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe141-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="fe141-103">Profil Oluşturucu, ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fe141-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe141-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe141-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fe141-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fe141-105">Return Value</span></span>  
 <span data-ttu-id="fe141-106">Bu geri dönüş değeri yok sayıldı.</span><span class="sxs-lookup"><span data-stu-id="fe141-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe141-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe141-107">Remarks</span></span>  
 <span data-ttu-id="fe141-108">`ProfilerDetachSucceeded` Tüm iş parçacığı profil oluşturucu kodu çıkılana sonra geri çağırma verildiği.</span><span class="sxs-lookup"><span data-stu-id="fe141-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="fe141-109">Bu yöntem çağrıldığında, profil oluşturucu, kullanıcı Arabirimi veya günlük bileşeni bildirme gibi yok edici, uygun olmayan herhangi bir son dakika görevi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe141-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="fe141-110">Ancak, profil oluşturucu işlevleri bu geri çağırma sırasındaki CLR tarafından sağlanan arabirimlerindeki çağırmamalıdır (gibi [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri).</span><span class="sxs-lookup"><span data-stu-id="fe141-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="fe141-111">CLR ayırma işlemi başarılı olduğunu göstermek için Windows uygulama olay günlüğünde bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe141-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="fe141-112">Profil Oluşturucu bu geri çağrısından döndükten sonra CLR Profil Oluşturucu nesnesini serbest bırakır ve profil oluşturucu DLL kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fe141-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="fe141-113">Bu nedenle, profil oluşturucu bu geri çağrısından döndürdükten sonra Profil Oluşturucu DLL içinde gerçekleşmesi yürütme neden olan herhangi bir eylem gerçekleştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fe141-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="fe141-114">Örneğin, bu olmayan iş parçacıkları oluşturmalı veya Zamanlayıcı geri aramaları kaydetme.</span><span class="sxs-lookup"><span data-stu-id="fe141-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe141-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe141-115">Requirements</span></span>  
 <span data-ttu-id="fe141-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe141-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe141-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe141-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe141-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe141-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fe141-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fe141-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe141-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe141-120">See also</span></span>

- [<span data-ttu-id="fe141-121">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe141-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="fe141-122">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe141-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fe141-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe141-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fe141-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe141-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
