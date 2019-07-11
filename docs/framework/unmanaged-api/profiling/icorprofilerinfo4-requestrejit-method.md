---
title: ICorProfilerInfo4::RequestReJIT Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f4ad89c821e9b8e9b52e3369a347eae27ab2231
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748677"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="66450-102">ICorProfilerInfo4::RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66450-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="66450-103">Belirtilen işlevler tüm örneklerinin bir JIT yeniden derlemesi ister.</span><span class="sxs-lookup"><span data-stu-id="66450-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66450-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66450-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66450-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66450-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="66450-106">[in] Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="66450-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="66450-107">[in] Belirtir `moduleId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="66450-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="66450-108">[in] Belirtir `methodId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="66450-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66450-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66450-109">Return Value</span></span>  
 <span data-ttu-id="66450-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="66450-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="66450-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66450-111">HRESULT</span></span>|<span data-ttu-id="66450-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66450-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66450-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="66450-113">S_OK</span></span>|<span data-ttu-id="66450-114">JIT yeniden derlemesi için tüm yöntemlerini işaretlemek için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="66450-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="66450-115">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4::rejıterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) hangi yöntemlerin JIT yeniden derlenmek üzere başarıyla işaretlenen belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66450-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="66450-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="66450-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="66450-117">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi, bu çağrı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="66450-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="66450-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="66450-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="66450-119">JIT yeniden derlemesi etkin değil.</span><span class="sxs-lookup"><span data-stu-id="66450-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="66450-120">Başlatma sırasında JIT yeniden derlemesi kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlanacak yöntemi `COR_PRF_ENABLE_REJIT` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="66450-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="66450-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="66450-121">E_INVALIDARG</span></span>|<span data-ttu-id="66450-122">`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` olduğu `NULL`.</span><span class="sxs-lookup"><span data-stu-id="66450-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="66450-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="66450-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="66450-124">CLR, belleği tükendiğinden, isteği tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="66450-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66450-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66450-125">Remarks</span></span>  
 <span data-ttu-id="66450-126">Çağrı `RequestReJIT` belirtilen bir işlevler kümesi derlemeniz çalışma zamanı sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="66450-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="66450-127">Bir kod profil oluşturucu ardından kullanabilirsiniz [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) işlevleri derlenir, oluşturulan kodu ayarlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="66450-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="66450-128">Bu, şu anda yürütülen İşlevler, yalnızca gelecekteki işlev çağrılarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="66450-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="66450-129">JIT yeniden derlenen belirtilen işlevlerden herhangi birinin daha önce, öyle isteme geri alma ve işlevi yeniden derlemeden eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="66450-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="66450-130">Reversibility, JIT Derleyici bir işlevi orijinal sürümünü derlediğinde korumak için yalnızca özgün sürümlerini kendi çağrılanlar inlining'i kararları için değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="66450-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="66450-131">JIT Derleyici bir işlevi yeniden derlenir, geçerli sürümleri (znovu veya özgün) için kendi çağrılanlar düşünür. satır içi kullanım.</span><span class="sxs-lookup"><span data-stu-id="66450-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="66450-132">Bir profil oluşturucu genellikle çağrıları `RequestReJIT` profil oluşturucu yöntemleri bir veya daha fazla izleme isteyen kullanıcı girişine yanıt.</span><span class="sxs-lookup"><span data-stu-id="66450-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="66450-133">`RequestReJIT` genellikle bazı iş yapın ve büyük olasılıkla tetikleyici bir çöp toplama için için çalışma zamanı askıya alır.</span><span class="sxs-lookup"><span data-stu-id="66450-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="66450-134">Bu nedenle, profil oluşturucu çağırmalıdır `RequestReJIT` bir iş parçacığından, daha önce oluşturduğunuz ve bir CLR tarafından oluşturulan iş parçacığından, şu anda bir profil oluşturucu geri çağırma yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="66450-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66450-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66450-135">Requirements</span></span>  
 <span data-ttu-id="66450-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66450-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66450-137">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66450-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66450-138">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66450-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66450-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66450-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66450-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66450-140">See also</span></span>

- [<span data-ttu-id="66450-141">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66450-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="66450-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="66450-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="66450-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="66450-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
