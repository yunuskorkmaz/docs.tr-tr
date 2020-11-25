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
ms.openlocfilehash: b80de5e0e03f6b3a424ac59a099e361dd6c50c86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733821"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="688d0-102">ICorProfilerInfo4::RequestRevert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="688d0-102">ICorProfilerInfo4::RequestRevert Method</span></span>

<span data-ttu-id="688d0-103">Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="688d0-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="688d0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="688d0-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="688d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="688d0-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="688d0-106">'ndaki Döndürülecek işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="688d0-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="688d0-107">'ndaki Geri `moduleId` `module` `methodDef` döndürülecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="688d0-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="688d0-108">'ndaki Geri `methodId` `module` `methodDef` döndürülecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="688d0-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="688d0-109">dışı Bu konunun ilerleyen kısımlarında "durum HRESULTs" bölümünde listelenen HRESULTs dizisi.</span><span class="sxs-lookup"><span data-stu-id="688d0-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="688d0-110">Her HRESULT, paralel dizilerde belirtilen her bir işlevi döndürmeye çalışırken başarılı veya başarısız olduğunu gösterir `moduleIds` `methodIds` .</span><span class="sxs-lookup"><span data-stu-id="688d0-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="688d0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="688d0-111">Return Value</span></span>  

 <span data-ttu-id="688d0-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="688d0-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="688d0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="688d0-113">HRESULT</span></span>|<span data-ttu-id="688d0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="688d0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="688d0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="688d0-115">S_OK</span></span>|<span data-ttu-id="688d0-116">Tüm istekleri dönüştürmek için bir girişimde bulunuldu; Ancak, döndürülen durum dizisinin hangi işlevlerin başarıyla geri döndürüldüğünü belirleyebilmek için denetlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="688d0-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="688d0-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="688d0-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="688d0-118">Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="688d0-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="688d0-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="688d0-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="688d0-120">JıT yeniden derleme etkinleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="688d0-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="688d0-121">Bayrağı ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmelisiniz `COR_PRF_ENABLE_REJIT` .</span><span class="sxs-lookup"><span data-stu-id="688d0-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="688d0-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="688d0-122">E_INVALIDARG</span></span>|<span data-ttu-id="688d0-123">`cFunctions` 0 veya veya ' `moduleIds` dir `methodIds` `NULL` .</span><span class="sxs-lookup"><span data-stu-id="688d0-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="688d0-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="688d0-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="688d0-125">CLR belleği tükendiğinden isteği tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="688d0-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="688d0-126">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="688d0-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="688d0-127">Durum dizisi HRESULT</span><span class="sxs-lookup"><span data-stu-id="688d0-127">Status array HRESULT</span></span>|<span data-ttu-id="688d0-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="688d0-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="688d0-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="688d0-129">S_OK</span></span>|<span data-ttu-id="688d0-130">Karşılık gelen işlev başarıyla geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="688d0-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="688d0-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="688d0-131">E_INVALIDARG</span></span>|<span data-ttu-id="688d0-132">`moduleID`Or `methodDef` parametresi `NULL` .</span><span class="sxs-lookup"><span data-stu-id="688d0-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="688d0-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="688d0-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="688d0-134">Modül henüz tam olarak yüklenmedi veya kaldırılıyor sürecinde.</span><span class="sxs-lookup"><span data-stu-id="688d0-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="688d0-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="688d0-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="688d0-136">Belirtilen modül dinamik olarak üretildi (örneğin, `Reflection.Emit` ).</span><span class="sxs-lookup"><span data-stu-id="688d0-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="688d0-137">Bu nedenle, bu yöntem tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="688d0-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="688d0-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="688d0-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="688d0-139">Karşılık gelen bir etkin yeniden derleme isteği bulunamadığı için CLR belirtilen işlevi döndüremedi.</span><span class="sxs-lookup"><span data-stu-id="688d0-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="688d0-140">Yeniden derleme işlemi hiç istenmedi ya da işlev zaten geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="688d0-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="688d0-141">Diğer</span><span class="sxs-lookup"><span data-stu-id="688d0-141">Other</span></span>|<span data-ttu-id="688d0-142">İşletim sistemi, CLR denetimi dışında bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="688d0-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="688d0-143">Örneğin, bir bellek sayfasının erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="688d0-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="688d0-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="688d0-144">Remarks</span></span>  

 <span data-ttu-id="688d0-145">Yeniden çağrılan işlev örneklerinin bir sonraki saatinde, işlevlerin özgün sürümleri çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="688d0-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="688d0-146">Bir işlev zaten çalışıyorsa, çalıştıran sürümü yürütmeyi tamamlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="688d0-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="688d0-147">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="688d0-147">Requirements</span></span>  

 <span data-ttu-id="688d0-148">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="688d0-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="688d0-149">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="688d0-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="688d0-150">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="688d0-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="688d0-151">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="688d0-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688d0-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="688d0-152">See also</span></span>

- [<span data-ttu-id="688d0-153">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="688d0-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="688d0-154">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="688d0-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="688d0-155">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="688d0-155">Profiling</span></span>](index.md)
