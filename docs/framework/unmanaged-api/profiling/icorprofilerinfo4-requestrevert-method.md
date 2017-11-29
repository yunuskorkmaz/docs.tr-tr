---
title: "ICorProfilerInfo4::RequestRevert Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestRevert
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 014b220e0f0eea46a298b64f8f3be9f079b0d397
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="8681c-102">ICorProfilerInfo4::RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8681c-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="8681c-103">Özgün sürümlerine belirtilen işleve tüm örneklerini döner.</span><span class="sxs-lookup"><span data-stu-id="8681c-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8681c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8681c-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8681c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8681c-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="8681c-106">[in] Geri dönmek için işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="8681c-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="8681c-107">[in] Belirtir `moduleId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="8681c-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="8681c-108">[in] Belirtir `methodId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="8681c-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="8681c-109">[out] Bu konunun devamındaki "Durum HRESULTs" bölümünde listelenen HRESULTs dizisi.</span><span class="sxs-lookup"><span data-stu-id="8681c-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="8681c-110">Her HRESULT başarı veya başarısızlık paralel dizilerde belirtilen her işlevi geri çalışılırken durumunu gösteren `moduleIds` ve `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="8681c-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8681c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8681c-111">Return Value</span></span>  
 <span data-ttu-id="8681c-112">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8681c-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8681c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8681c-113">HRESULT</span></span>|<span data-ttu-id="8681c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8681c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8681c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8681c-115">S_OK</span></span>|<span data-ttu-id="8681c-116">Tüm istekleri dönmek için girişimde bulunuldu; Ancak, döndürülen durum dizi hangi işlevleri başarıyla geri belirlemek için denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8681c-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="8681c-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="8681c-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="8681c-118">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi için bu çağrı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="8681c-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="8681c-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="8681c-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="8681c-120">JIT derleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="8681c-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="8681c-121">JIT derleme başlatma sırasında kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlamak için yöntemin `COR_PRF_ENABLE_REJIT` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="8681c-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="8681c-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8681c-122">E_INVALIDARG</span></span>|<span data-ttu-id="8681c-123">`cFunctions`0 ' dır veya `moduleIds` veya `methodIds` olan `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8681c-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="8681c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8681c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8681c-125">Bellek yetersiz çalıştırdığınız için CLR isteği tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="8681c-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="8681c-126">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="8681c-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="8681c-127">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="8681c-127">Status array HRESULT</span></span>|<span data-ttu-id="8681c-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8681c-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="8681c-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="8681c-129">S_OK</span></span>|<span data-ttu-id="8681c-130">Karşılık gelen işlevi başarıyla geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8681c-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="8681c-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8681c-131">E_INVALIDARG</span></span>|<span data-ttu-id="8681c-132">`moduleID` Veya `methodDef` parametresi `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8681c-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="8681c-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="8681c-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="8681c-134">Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="8681c-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="8681c-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="8681c-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="8681c-136">Belirtilen modül dinamik olarak oluşturulan (örneğin `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="8681c-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="8681c-137">Bu nedenle, bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="8681c-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="8681c-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="8681c-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="8681c-139">Karşılık gelen bir etkin yeniden derlenmek isteği bulunamadığından CLR belirtilen işlev geri döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="8681c-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="8681c-140">Yeniden derleme hiçbir zaman istendi ya da işlevi zaten geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8681c-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="8681c-141">Diğer</span><span class="sxs-lookup"><span data-stu-id="8681c-141">Other</span></span>|<span data-ttu-id="8681c-142">İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="8681c-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="8681c-143">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8681c-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8681c-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8681c-144">Remarks</span></span>  
 <span data-ttu-id="8681c-145">Herhangi revereted işlevi örnekleri olarak da bilinen sonraki saat işlevleri özgün sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8681c-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="8681c-146">Bir işlev zaten çalışıyorsa, çalışmakta olan sürümü yürütme tamamlar.</span><span class="sxs-lookup"><span data-stu-id="8681c-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8681c-147">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8681c-147">Requirements</span></span>  
 <span data-ttu-id="8681c-148">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8681c-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8681c-149">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8681c-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8681c-150">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8681c-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8681c-151">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8681c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8681c-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8681c-152">See Also</span></span>  
 [<span data-ttu-id="8681c-153">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8681c-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="8681c-154">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8681c-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8681c-155">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="8681c-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
