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
ms.openlocfilehash: 92137e1a5b0923bc34745513715934c483616700
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179848"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="8fa77-102">ICorProfilerInfo4::RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fa77-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="8fa77-103">Tüm örneklerinin özgünlüğünü belirtilen işleve döner.</span><span class="sxs-lookup"><span data-stu-id="8fa77-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fa77-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fa77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fa77-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="8fa77-106">[in] Geri almak için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="8fa77-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="8fa77-107">[in] Belirtir `moduleId` kısmı (`module`, `methodDef`) geri döndürülmesi işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="8fa77-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="8fa77-108">[in] Belirtir `methodId` kısmı (`module`, `methodDef`) geri döndürülmesi işlevleri tanımlamak çiftleri.</span><span class="sxs-lookup"><span data-stu-id="8fa77-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="8fa77-109">[out] Bu konunun ilerleyen bölümlerindeki "Durumu HRESULTs" bölümünde listelenen HRESULTs dizisi.</span><span class="sxs-lookup"><span data-stu-id="8fa77-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="8fa77-110">Başarı veya başarısızlık paralel dizilerde belirtilen her bir işlevin geri çalışılırken, her HRESULT gösterir `moduleIds` ve `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="8fa77-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fa77-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8fa77-111">Return Value</span></span>  
 <span data-ttu-id="8fa77-112">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8fa77-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8fa77-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8fa77-113">HRESULT</span></span>|<span data-ttu-id="8fa77-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fa77-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8fa77-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fa77-115">S_OK</span></span>|<span data-ttu-id="8fa77-116">Tüm istekleri dönmek için girişimde bulunuldu; Ancak, hangi işlevlerin başarıyla geri alındığını belirlemek için döndürülen durum dizisi denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fa77-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="8fa77-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="8fa77-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="8fa77-118">Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi, bu çağrı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="8fa77-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="8fa77-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="8fa77-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="8fa77-120">JIT yeniden derlemesi etkin değil.</span><span class="sxs-lookup"><span data-stu-id="8fa77-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="8fa77-121">Başlatma sırasında JIT yeniden derlemesi kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlanacak yöntemi `COR_PRF_ENABLE_REJIT` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="8fa77-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="8fa77-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8fa77-122">E_INVALIDARG</span></span>|<span data-ttu-id="8fa77-123">`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` olduğu `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8fa77-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="8fa77-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8fa77-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8fa77-125">CLR, belleği tükendiğinden, isteği tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="8fa77-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="8fa77-126">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="8fa77-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="8fa77-127">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="8fa77-127">Status array HRESULT</span></span>|<span data-ttu-id="8fa77-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fa77-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="8fa77-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fa77-129">S_OK</span></span>|<span data-ttu-id="8fa77-130">İlgili işlevi başarıyla geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8fa77-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="8fa77-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8fa77-131">E_INVALIDARG</span></span>|<span data-ttu-id="8fa77-132">`moduleID` Veya `methodDef` parametresi `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8fa77-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="8fa77-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="8fa77-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="8fa77-134">Modül henüz tam yüklü değil veya yüklenmemiş sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="8fa77-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="8fa77-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="8fa77-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="8fa77-136">Belirtilen modül dinamik olarak oluşturulan (örneğin `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="8fa77-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="8fa77-137">Bu nedenle, bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="8fa77-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="8fa77-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="8fa77-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="8fa77-139">CLR, karşılık gelen bir etkin yeniden derleme isteği bulunamadığından belirtilen işlevi döndürülemedi.</span><span class="sxs-lookup"><span data-stu-id="8fa77-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="8fa77-140">Yeniden derleme hiçbir zaman istenen ya da işlev zaten döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8fa77-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="8fa77-141">Diğer</span><span class="sxs-lookup"><span data-stu-id="8fa77-141">Other</span></span>|<span data-ttu-id="8fa77-142">İşletim sistemi CLR denetimin dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="8fa77-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="8fa77-143">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fa77-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fa77-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fa77-144">Remarks</span></span>  
 <span data-ttu-id="8fa77-145">Herhangi bir revereted işlevi örnekleri olarak adlandırılır, sonraki açışınızda işlevlerin özgün sürümleri çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8fa77-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="8fa77-146">Bir işlev zaten çalışıyorsa, çalışmakta olan sürümü yürütme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="8fa77-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fa77-147">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fa77-147">Requirements</span></span>  
 <span data-ttu-id="8fa77-148">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa77-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa77-149">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fa77-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fa77-150">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fa77-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fa77-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fa77-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa77-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa77-152">See also</span></span>

- [<span data-ttu-id="8fa77-153">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fa77-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="8fa77-154">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fa77-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="8fa77-155">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fa77-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
