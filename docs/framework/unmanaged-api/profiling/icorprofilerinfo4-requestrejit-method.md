---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: RequestReJIT yöntemi'
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
ms.openlocfilehash: 2da65c2db5722f689f1a8588169ea099aff71be6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799024"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="5d68a-103">ICorProfilerInfo4::RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d68a-103">ICorProfilerInfo4::RequestReJIT Method</span></span>

<span data-ttu-id="5d68a-104">Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.</span><span class="sxs-lookup"><span data-stu-id="5d68a-104">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d68a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d68a-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d68a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d68a-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="5d68a-107">'ndaki Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d68a-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="5d68a-108">'ndaki `moduleId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d68a-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="5d68a-109">'ndaki `methodId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d68a-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d68a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d68a-110">Return Value</span></span>  

 <span data-ttu-id="5d68a-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d68a-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5d68a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d68a-112">HRESULT</span></span>|<span data-ttu-id="5d68a-113">Description</span><span class="sxs-lookup"><span data-stu-id="5d68a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d68a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d68a-114">S_OK</span></span>|<span data-ttu-id="5d68a-115">JıT yeniden derleme için tüm yöntemleri işaretlemek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="5d68a-115">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="5d68a-116">Profil Oluşturucu, JıT yeniden derleme için hangi yöntemlerin başarıyla işaretlendiğini belirleyen [ICorProfilerCallback4:: ReJITError](icorprofilercallback4-rejiterror-method.md) metodunu uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d68a-116">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="5d68a-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="5d68a-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="5d68a-118">Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d68a-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="5d68a-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="5d68a-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="5d68a-120">JıT yeniden derleme etkinleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="5d68a-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="5d68a-121">Bayrağı ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmelisiniz `COR_PRF_ENABLE_REJIT` .</span><span class="sxs-lookup"><span data-stu-id="5d68a-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="5d68a-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5d68a-122">E_INVALIDARG</span></span>|<span data-ttu-id="5d68a-123">`cFunctions` 0 veya veya ' `moduleIds` dir `methodIds` `NULL` .</span><span class="sxs-lookup"><span data-stu-id="5d68a-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="5d68a-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5d68a-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5d68a-125">CLR belleği tükendiğinden isteği tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="5d68a-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d68a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d68a-126">Remarks</span></span>  

 <span data-ttu-id="5d68a-127">`RequestReJIT`Çalışma zamanının belirtilen işlev kümesini yeniden derleyeme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="5d68a-127">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="5d68a-128">Kod Profilcisi daha sonra [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimini kullanarak işlevler yeniden derlenmeye başlatıldığında oluşturulan kodu ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5d68a-128">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="5d68a-129">Bu, şu anda yürütülmekte olan işlevleri etkilemez, yalnızca gelecekteki işlev etkinleştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="5d68a-129">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="5d68a-130">Belirtilen işlevlerden herhangi biri daha önce JıT olarak yeniden derlendikten sonra yeniden derleme isteğinde bulunulmaya, işlevin geri döndürülmesi ve yeniden derlenmesi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5d68a-130">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="5d68a-131">Geri almayı korumak için, JıT derleyicisi bir işlevin orijinal sürümünü derlediğinde, iç kararları almak için yalnızca özgün sürümlerini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="5d68a-131">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="5d68a-132">JıT derleyicisi bir işlevi yeniden derlediğinde, iç içe için kendi caltaları 'nın geçerli sürümlerini (yeniden derlenir veya özgün) dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="5d68a-132">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="5d68a-133">Profil Oluşturucu tipik olarak `RequestReJIT` , profil oluşturucunun bir veya daha fazla yöntemi işaretlemesini isteyen kullanıcı girdisine yanıt olarak çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="5d68a-133">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="5d68a-134">`RequestReJIT` genellikle çalışma zamanını, işini bir kısmını yapmak için askıya alır ve bir çöp toplama tetikleyebilecek.</span><span class="sxs-lookup"><span data-stu-id="5d68a-134">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="5d68a-135">Bu nedenle, profil oluşturucu, `RequestReJIT` Şu anda profil oluşturucu geri çağrısını yürüten CLR tarafından oluşturulan bir iş parçacığından değil, daha önce oluşturduğu bir iş parçacığından çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d68a-135">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d68a-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d68a-136">Requirements</span></span>  

 <span data-ttu-id="5d68a-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d68a-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d68a-138">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d68a-138">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d68a-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d68a-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d68a-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d68a-140">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d68a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d68a-141">See also</span></span>

- [<span data-ttu-id="5d68a-142">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d68a-142">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="5d68a-143">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d68a-143">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5d68a-144">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d68a-144">Profiling</span></span>](index.md)
