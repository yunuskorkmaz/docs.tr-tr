---
title: "ICLRProfiling::AttachProfiler Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IClrProfiling.AttachProfiler Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a0f1e41f7d59074f997a5812da61fdbcd692770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="fe21b-102">ICLRProfiling::AttachProfiler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe21b-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="fe21b-103">Belirtilen profil oluşturucu için belirtilen işlem ekler.</span><span class="sxs-lookup"><span data-stu-id="fe21b-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe21b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe21b-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe21b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe21b-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="fe21b-106">[in] Profil Oluşturucu eklenmesi işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="fe21b-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="fe21b-107">Bir 64-bit makine profili işlemin verileri aradığı tetikleyici işlem verileri eşleşmelidir `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="fe21b-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="fe21b-108">Altında kullanıcı hesabı `AttachProfiler` çağrılır yönetimsel ayrıcalıklara sahip, hedef işlem sistem üzerindeki herhangi bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="fe21b-109">Aksi takdirde, hedef işlem aynı kullanıcı hesabı tarafından ait olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe21b-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="fe21b-110">[in] Milisaniye cinsinden süre için `AttachProfiler` tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="fe21b-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="fe21b-111">Tetikleyici işlemi belirli profiler kendi başlatma işlemini tamamlamak yeterli olduğu bilinen bir zaman aşımı geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fe21b-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="fe21b-112">[in] Yüklenecek profil oluşturucu CLSID gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe21b-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="fe21b-113">Tetikleyici işlemi bu bellek sonra yeniden `AttachProfiler` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe21b-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="fe21b-114">[in] Yüklenecek Profil Oluşturucu'nın DLL dosyasının tam yolu.</span><span class="sxs-lookup"><span data-stu-id="fe21b-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="fe21b-115">Bu dize null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="fe21b-116">Varsa `wszProfilerPath` null veya boş bir dize ortak dil çalışma zamanı (CLR) CLSID kayıt defterinde bakarak Profil Oluşturucu'nın DLL dosyasının konumunu bulmayı dener, `pClsidProfiler` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fe21b-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="fe21b-117">[in] Profil Oluşturucu tarafından geçirilecek veriler için bir işaretçi [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe21b-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="fe21b-118">Tetikleyici işlemi bu bellek sonra yeniden `AttachProfiler` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe21b-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="fe21b-119">Varsa `pvClientData` null, `cbClientData` 0 (sıfır) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="fe21b-120">[in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fe21b-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe21b-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fe21b-121">Return Value</span></span>  
 <span data-ttu-id="fe21b-122">Bu yöntem, aşağıdaki HRESULTs döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe21b-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="fe21b-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe21b-123">HRESULT</span></span>|<span data-ttu-id="fe21b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe21b-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe21b-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe21b-125">S_OK</span></span>|<span data-ttu-id="fe21b-126">Belirtilen profil oluşturucu hedef işlem başarıyla eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="fe21b-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="fe21b-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="fe21b-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="fe21b-128">Aynı zamanda active veya düğmelere hedef işlem için zaten bir profil oluşturucu yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe21b-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="fe21b-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="fe21b-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="fe21b-130">Belirtilen profil oluşturucu desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fe21b-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="fe21b-131">Tetikleyici işlemi farklı bir profil oluşturucu ekleme girişiminde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="fe21b-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="fe21b-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="fe21b-133">Hedef işlemin sürümü çağırma geçerli işlem ile uyumlu olmadığı için bir profil oluşturucu ek istek kurulamıyor `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="fe21b-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="fe21b-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="fe21b-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="fe21b-135">Tetikleyici işleminin kullanıcının hedef işlem erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="fe21b-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="fe21b-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="fe21b-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="fe21b-137">Tetikleyici işleminin kullanıcı için belirtilen hedef işlem bir profil oluşturucu ekleme için gerekli ayrıcalıklara sahip değil.</span><span class="sxs-lookup"><span data-stu-id="fe21b-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="fe21b-138">Uygulama olay günlüğü daha fazla bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="fe21b-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="fe21b-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="fe21b-140">Hedef işlemiyle iletişim kurarken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fe21b-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="fe21b-141">Hedef işlem kapatılıyor varsa bu yaygın olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="fe21b-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="fe21b-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="fe21b-143">Hedef işlem yok veya ek destekleyen bir CLR çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="fe21b-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="fe21b-144">Bu durum, CLR çalışma zamanı numaralandırma yöntemi çağrısından itibaren kaldırıldı olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="fe21b-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="fe21b-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="fe21b-146">Profil Oluşturucu yüklemek için başlangıç olmadan süresi doldu.</span><span class="sxs-lookup"><span data-stu-id="fe21b-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="fe21b-147">Ekleme işlemi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="fe21b-147">You can retry the attach operation.</span></span> <span data-ttu-id="fe21b-148">Zaman aşımları sonlandırıcıyı hedef işleminde zaman aşımı değeri daha uzun süre çalışırsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="fe21b-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="fe21b-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fe21b-149">E_INVALIDARG</span></span>|<span data-ttu-id="fe21b-150">Bir veya daha fazla parametre geçersiz değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="fe21b-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="fe21b-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe21b-151">E_FAIL</span></span>|<span data-ttu-id="fe21b-152">Bazı diğer, belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fe21b-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="fe21b-153">Diğer hata kodları</span><span class="sxs-lookup"><span data-stu-id="fe21b-153">Other error codes</span></span>|<span data-ttu-id="fe21b-154">Varsa profil oluşturucu 's [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi döndürür hatası gösteren bir HRESULT `AttachProfiler` , aynı döndürür HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fe21b-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="fe21b-155">Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE için dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fe21b-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe21b-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe21b-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="fe21b-157">Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="fe21b-157">Memory Management</span></span>  
 <span data-ttu-id="fe21b-158">Çağıranın COM kuralları ile güvenliğini koruma açısından `AttachProfiler` (örneğin, tetikleyici kod profil oluşturucu geliştirici tarafından yazılan) ayırma ve veriler için bellek ayırmasını sorumlu, `pvClientData` parametresi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fe21b-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="fe21b-159">Ne zaman CLR yürütür `AttachProfiler` çağrısı kolaylaştırır bellek bir kopyasını, `pvClientData` işaret ve hedef işlem iletir.</span><span class="sxs-lookup"><span data-stu-id="fe21b-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="fe21b-160">Ne zaman CLR'nin hedef işlem içinde kendine ait kopyasını alır `pvClientData` bloğu, profil oluşturucu blok geçirir `InitializeForAttach` yöntemi ve kendi kopyasını kaldırır `pvClientData` hedef işlem bloğundan.</span><span class="sxs-lookup"><span data-stu-id="fe21b-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe21b-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe21b-161">Requirements</span></span>  
 <span data-ttu-id="fe21b-162">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe21b-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe21b-163">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe21b-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe21b-164">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe21b-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe21b-165">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe21b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe21b-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe21b-166">See Also</span></span>  
 [<span data-ttu-id="fe21b-167">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe21b-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fe21b-168">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe21b-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="fe21b-169">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe21b-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fe21b-170">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe21b-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
