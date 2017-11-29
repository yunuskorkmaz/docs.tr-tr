---
title: "ICorProfilerInfo4::RequestReJIT Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestReJIT
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d62dbb2829480e8972d1d4966673ba8eb58f1831
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="847e9-102">ICorProfilerInfo4::RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="847e9-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="847e9-103">JIT derleme belirtilen işlevler tüm örneklerinin ister.</span><span class="sxs-lookup"><span data-stu-id="847e9-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="847e9-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="847e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="847e9-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="847e9-106">[in] Yeniden derleyin işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="847e9-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="847e9-107">[in] Belirtir `moduleId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="847e9-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="847e9-108">[in] Belirtir `methodId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="847e9-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="847e9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="847e9-109">Return Value</span></span>  
 <span data-ttu-id="847e9-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="847e9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="847e9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="847e9-111">HRESULT</span></span>|<span data-ttu-id="847e9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="847e9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="847e9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="847e9-113">S_OK</span></span>|<span data-ttu-id="847e9-114">JIT derleme için tüm yöntemlerini işaretlemek için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="847e9-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="847e9-115">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4::rejıterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) hangi yöntemlerin JIT yeniden derlenmek üzere başarıyla işaretlenen belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="847e9-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="847e9-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="847e9-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="847e9-117">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi için bu çağrı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="847e9-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="847e9-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="847e9-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="847e9-119">JIT derleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="847e9-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="847e9-120">JIT derleme başlatma sırasında kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlamak için yöntemin `COR_PRF_ENABLE_REJIT` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="847e9-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="847e9-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="847e9-121">E_INVALIDARG</span></span>|<span data-ttu-id="847e9-122">`cFunctions`0 ' dır veya `moduleIds` veya `methodIds` olan `NULL`.</span><span class="sxs-lookup"><span data-stu-id="847e9-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="847e9-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="847e9-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="847e9-124">Bellek yetersiz çalıştırdığınız için CLR isteği tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="847e9-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="847e9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="847e9-125">Remarks</span></span>  
 <span data-ttu-id="847e9-126">Çağrı `RequestReJIT` belirtilen sayıda işlevi yeniden derleyin çalışma zamanı için.</span><span class="sxs-lookup"><span data-stu-id="847e9-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="847e9-127">Kod profil oluşturucu sonra kullanabileceğiniz [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) işlevleri derlenir olduğunda oluşturulan kodu ayarlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="847e9-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="847e9-128">Bu, şu anda yürütülen İşlevler, yalnızca gelecekteki işlev çağrılarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="847e9-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="847e9-129">Belirtilen işlevler birini daha önce yapılmışsa JIT yeniden derlenmesi, bir derleme isteyen dönüştürülüyor ve işlevi yeniden derlenmesi için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="847e9-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="847e9-130">JIT Derleyici bir işlev özgün sürümü derlediğinde reversibility, korumak için yalnızca özgün sürümleri satır içi kullanım kararları için kendi callees dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="847e9-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="847e9-131">JIT derleme işlevi yeniden derler, geçerli sürümleri (derlenmiş veya özgün) için kendi callees dikkate satır içi kullanım.</span><span class="sxs-lookup"><span data-stu-id="847e9-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="847e9-132">Bir profil oluşturucu genellikle çağırır `RequestReJIT` profil oluşturucuyu bir veya daha fazla yöntemleri izleme isteyen kullanıcı girişine yanıt.</span><span class="sxs-lookup"><span data-stu-id="847e9-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="847e9-133">`RequestReJIT`genellikle kendi iş bazıları yapın ve potansiyel olarak tetikleyici çöp toplama olabilir için çalışma zamanı askıya alır.</span><span class="sxs-lookup"><span data-stu-id="847e9-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="847e9-134">Bu nedenle, profil oluşturucu çağırmalıdır `RequestReJIT` bir iş parçacığından, daha önce oluşturduğunuz ve bir CLR oluşturulan iş parçacığından, şu anda bir profil oluşturucu geri yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="847e9-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847e9-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="847e9-135">Requirements</span></span>  
 <span data-ttu-id="847e9-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="847e9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="847e9-137">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="847e9-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="847e9-138">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="847e9-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="847e9-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="847e9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847e9-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="847e9-140">See Also</span></span>  
 [<span data-ttu-id="847e9-141">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="847e9-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="847e9-142">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="847e9-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="847e9-143">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="847e9-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
