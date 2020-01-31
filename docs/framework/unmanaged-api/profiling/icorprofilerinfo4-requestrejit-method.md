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
ms.openlocfilehash: d2f8d538adb965864915fb1195bf9f2b8488aac8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868414"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="b6707-102">ICorProfilerInfo4::RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6707-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="b6707-103">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="b6707-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6707-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6707-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6707-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6707-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="b6707-106">'ndaki Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6707-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="b6707-107">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6707-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="b6707-108">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b6707-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6707-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6707-109">Return Value</span></span>  
 <span data-ttu-id="b6707-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6707-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b6707-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6707-111">HRESULT</span></span>|<span data-ttu-id="b6707-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6707-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6707-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6707-113">S_OK</span></span>|<span data-ttu-id="b6707-114">JıT yeniden derleme için tüm yöntemleri işaretlemek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="b6707-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="b6707-115">Profil Oluşturucu, JıT yeniden derleme için hangi yöntemlerin başarıyla işaretlendiğini belirleyen [ICorProfilerCallback4:: ReJITError](icorprofilercallback4-rejiterror-method.md) metodunu uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6707-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="b6707-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="b6707-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="b6707-117">Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6707-117">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="b6707-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="b6707-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="b6707-119">JıT yeniden derleme etkinleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="b6707-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="b6707-120">`COR_PRF_ENABLE_REJIT` bayrağını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6707-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="b6707-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b6707-121">E_INVALIDARG</span></span>|<span data-ttu-id="b6707-122">`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b6707-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="b6707-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b6707-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b6707-124">CLR belleği tükendiğinden isteği tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="b6707-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6707-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6707-125">Remarks</span></span>  
 <span data-ttu-id="b6707-126">Çalışma zamanının belirtilen bir işlev kümesini yeniden derlemek için `RequestReJIT` çağırın.</span><span class="sxs-lookup"><span data-stu-id="b6707-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="b6707-127">Kod Profilcisi daha sonra [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimini kullanarak işlevler yeniden derlenmeye başlatıldığında oluşturulan kodu ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6707-127">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="b6707-128">Bu, şu anda yürütülmekte olan işlevleri etkilemez, yalnızca gelecekteki işlev etkinleştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="b6707-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="b6707-129">Belirtilen işlevlerden herhangi biri daha önce JıT olarak yeniden derlendikten sonra yeniden derleme isteğinde bulunulmaya, işlevin geri döndürülmesi ve yeniden derlenmesi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b6707-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="b6707-130">Geri almayı korumak için, JıT derleyicisi bir işlevin orijinal sürümünü derlediğinde, iç kararları almak için yalnızca özgün sürümlerini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="b6707-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="b6707-131">JıT derleyicisi bir işlevi yeniden derlediğinde, iç içe için kendi caltaları 'nın geçerli sürümlerini (yeniden derlenir veya özgün) dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="b6707-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="b6707-132">Profil Oluşturucu tipik olarak, profil oluşturucunun bir veya daha fazla yöntemi işaretlemesini isteyen kullanıcı girdisine yanıt olarak `RequestReJIT` çağırır.</span><span class="sxs-lookup"><span data-stu-id="b6707-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="b6707-133">`RequestReJIT` genellikle çalışma zamanını bir kısmını yapmak için askıya alır ve bir çöp toplamayı tetikleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="b6707-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="b6707-134">Bu nedenle, profil oluşturucu, şu anda profil oluşturucu geri çağrısını yürüten CLR tarafından oluşturulan bir iş parçacığından değil, önceden oluşturduğu bir iş parçacığından `RequestReJIT` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6707-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6707-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6707-135">Requirements</span></span>  
 <span data-ttu-id="b6707-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6707-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6707-137">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b6707-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6707-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6707-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6707-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6707-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6707-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6707-140">See also</span></span>

- [<span data-ttu-id="b6707-141">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6707-141">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b6707-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b6707-142">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b6707-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6707-143">Profiling</span></span>](index.md)
