---
title: ICorProfilerInfo4::RequestRevert Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43a1954d75d37f68eb967eb714070a097573100a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460330"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="05913-102">ICorProfilerInfo4::RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05913-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="05913-103">Özgün sürümlerine belirtilen işleve tüm örneklerini döner.</span><span class="sxs-lookup"><span data-stu-id="05913-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05913-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05913-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05913-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05913-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="05913-106">[in] Geri dönmek için işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="05913-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="05913-107">[in] Belirtir `moduleId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="05913-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="05913-108">[in] Belirtir `methodId` kısmı (`module`, `methodDef`) döndürülmesi için işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="05913-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="05913-109">[out] Bu konunun devamındaki "Durum HRESULTs" bölümünde listelenen HRESULTs dizisi.</span><span class="sxs-lookup"><span data-stu-id="05913-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="05913-110">Her HRESULT başarı veya başarısızlık paralel dizilerde belirtilen her işlevi geri çalışılırken durumunu gösteren `moduleIds` ve `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="05913-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05913-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05913-111">Return Value</span></span>  
 <span data-ttu-id="05913-112">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="05913-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="05913-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05913-113">HRESULT</span></span>|<span data-ttu-id="05913-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05913-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05913-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="05913-115">S_OK</span></span>|<span data-ttu-id="05913-116">Tüm istekleri dönmek için girişimde bulunuldu; Ancak, döndürülen durum dizi hangi işlevleri başarıyla geri belirlemek için denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="05913-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="05913-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="05913-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="05913-118">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi için bu çağrı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="05913-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="05913-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="05913-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="05913-120">JIT derleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="05913-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="05913-121">JIT derleme başlatma sırasında kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlamak için yöntemin `COR_PRF_ENABLE_REJIT` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="05913-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="05913-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="05913-122">E_INVALIDARG</span></span>|<span data-ttu-id="05913-123">`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` olan `NULL`.</span><span class="sxs-lookup"><span data-stu-id="05913-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="05913-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="05913-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="05913-125">Bellek yetersiz çalıştırdığınız için CLR isteği tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="05913-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="05913-126">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="05913-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="05913-127">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="05913-127">Status array HRESULT</span></span>|<span data-ttu-id="05913-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05913-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="05913-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="05913-129">S_OK</span></span>|<span data-ttu-id="05913-130">Karşılık gelen işlevi başarıyla geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05913-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="05913-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="05913-131">E_INVALIDARG</span></span>|<span data-ttu-id="05913-132">`moduleID` Veya `methodDef` parametresi `NULL`.</span><span class="sxs-lookup"><span data-stu-id="05913-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="05913-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="05913-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="05913-134">Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="05913-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="05913-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="05913-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="05913-136">Belirtilen modül dinamik olarak oluşturulan (örneğin `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="05913-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="05913-137">Bu nedenle, bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="05913-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="05913-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="05913-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="05913-139">Karşılık gelen bir etkin yeniden derlenmek isteği bulunamadığından CLR belirtilen işlev geri döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="05913-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="05913-140">Yeniden derleme hiçbir zaman istendi ya da işlevi zaten geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="05913-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="05913-141">Diğer</span><span class="sxs-lookup"><span data-stu-id="05913-141">Other</span></span>|<span data-ttu-id="05913-142">İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="05913-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="05913-143">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05913-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05913-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05913-144">Remarks</span></span>  
 <span data-ttu-id="05913-145">Herhangi revereted işlevi örnekleri olarak da bilinen sonraki saat işlevleri özgün sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="05913-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="05913-146">Bir işlev zaten çalışıyorsa, çalışmakta olan sürümü yürütme tamamlar.</span><span class="sxs-lookup"><span data-stu-id="05913-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05913-147">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05913-147">Requirements</span></span>  
 <span data-ttu-id="05913-148">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05913-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05913-149">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05913-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05913-150">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05913-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05913-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05913-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05913-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05913-152">See Also</span></span>  
 [<span data-ttu-id="05913-153">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05913-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="05913-154">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="05913-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="05913-155">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05913-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
