---
title: ICLRProfiling::AttachProfiler Yöntemi
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fcbc75d17f0c154671d5997d7e6cbb59ef8440e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469007"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="1f495-102">ICLRProfiling::AttachProfiler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f495-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="1f495-103">Belirtilen işleme belirtilen profil oluşturucuyu ekler.</span><span class="sxs-lookup"><span data-stu-id="1f495-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f495-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f495-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f495-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f495-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="1f495-106">[in] Profil Oluşturucu eklenmesi işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="1f495-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="1f495-107">Bir 64-bit makinede profilli işlemin bit genişliği bit genişliğinde çağıran bir tetikleyici işlem eşleşmelidir `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="1f495-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="1f495-108">Altında kullanıcı hesabı `AttachProfiler` çağrılır yönetici ayrıcalıklarına sahip, hedef işlem sistem üzerindeki herhangi bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f495-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="1f495-109">Aksi takdirde, hedef işlem, aynı kullanıcı hesabı tarafından sahiplenilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f495-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="1f495-110">[in] Milisaniye cinsinden süre için `AttachProfiler` tamamlanması.</span><span class="sxs-lookup"><span data-stu-id="1f495-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="1f495-111">Tetikleyici işlem, belirli bir profil, başlatma işlemini tamamlamak yeterli olduğu bilinen bir zaman aşımı geçmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f495-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="1f495-112">[in] Yüklenecek profil oluşturucu CLSID değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f495-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="1f495-113">Tetikleyici işlem, bu bellek sonra yeniden kullanabilirsiniz `AttachProfiler` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f495-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="1f495-114">[in] Yüklenecek profil oluşturucunun DLL dosyasının tam yolu.</span><span class="sxs-lookup"><span data-stu-id="1f495-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="1f495-115">Bu dize null Sonlandırıcı dahil olmak üzere, en fazla 260 karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1f495-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="1f495-116">Varsa `wszProfilerPath` null veya boş bir dize ortak dil çalışma zamanı (CLR) profil oluşturucunun DLL dosyasının konumunu CLSID kayıt defterinde bakarak bulmayı dener, `pClsidProfiler` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="1f495-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="1f495-117">[in] Profil Oluşturucu tarafından geçirilecek veriler için bir işaretçi [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f495-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="1f495-118">Tetikleyici işlem, bu bellek sonra yeniden kullanabilirsiniz `AttachProfiler` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f495-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="1f495-119">Varsa `pvClientData` boş `cbClientData` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f495-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="1f495-120">[in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="1f495-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f495-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f495-121">Return Value</span></span>  
 <span data-ttu-id="1f495-122">Bu yöntem, aşağıdaki HRESULT'ları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f495-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="1f495-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f495-123">HRESULT</span></span>|<span data-ttu-id="1f495-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f495-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f495-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f495-125">S_OK</span></span>|<span data-ttu-id="1f495-126">Belirtilen profil oluşturucuyu hedef işleme başarıyla eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="1f495-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="1f495-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="1f495-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="1f495-128">Aynı zamanda etkin veya düğmelere hedef işlem için zaten bir profil oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="1f495-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="1f495-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="1f495-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="1f495-130">Belirtilen profil oluşturucu bağlantısını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1f495-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="1f495-131">Tetikleyici işlem, farklı bir profil oluşturucu ekleme girişiminde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1f495-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="1f495-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="1f495-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="1f495-133">Hedef işlemin sürümü çağıran geçerli işlem ile uyumsuz olduğundan bir profil oluşturucu ek istek kurulamıyor `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="1f495-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="1f495-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="1f495-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="1f495-135">Tetikleyici işlem, kullanıcı hedef işlem erişiminiz yok.</span><span class="sxs-lookup"><span data-stu-id="1f495-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="1f495-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="1f495-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="1f495-137">Tetikleyici işlem, kullanıcı için belirtilen hedef işlemin bir profil oluşturucuyu eklemek gerekli ayrıcalıklara sahip değil.</span><span class="sxs-lookup"><span data-stu-id="1f495-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="1f495-138">Uygulama olay günlüğü daha fazla bilgi içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f495-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="1f495-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="1f495-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="1f495-140">Hedef işlemle iletişim kurulurken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f495-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="1f495-141">Hedef işlem kapatılıyor, bu yaygın olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1f495-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="1f495-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="1f495-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="1f495-143">Hedef işlem yok veya ek destekleyen bir CLR çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="1f495-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="1f495-144">Bu durum, CLR çalışma zamanı numaralandırma yöntem çağrısından sonra kaldırılmış olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f495-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="1f495-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="1f495-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="1f495-146">Profiler'ı yüklemek için başlangıç olmadan süresi doldu.</span><span class="sxs-lookup"><span data-stu-id="1f495-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="1f495-147">İliştirme işlemini yeniden deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f495-147">You can retry the attach operation.</span></span> <span data-ttu-id="1f495-148">Hedef işlem içindeki bir sonlandırıcı zaman aşımı değerinden daha uzun bir süre çalıştığında zaman aşımı oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f495-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="1f495-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1f495-149">E_INVALIDARG</span></span>|<span data-ttu-id="1f495-150">Bir veya daha fazla parametreler geçersiz değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="1f495-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="1f495-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f495-151">E_FAIL</span></span>|<span data-ttu-id="1f495-152">Bazı diğer, belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f495-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="1f495-153">Diğer hata kodları</span><span class="sxs-lookup"><span data-stu-id="1f495-153">Other error codes</span></span>|<span data-ttu-id="1f495-154">Profil oluşturucunun [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi hatası gösteren HRESULT döndürür `AttachProfiler` döndürür, aynı HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1f495-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="1f495-155">Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE için dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1f495-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f495-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f495-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="1f495-157">Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="1f495-157">Memory Management</span></span>  
 <span data-ttu-id="1f495-158">COM kuralları ile çağıran tutma içinde `AttachProfiler` (örneğin, tetikleyici kod profil oluşturucu geliştirici tarafından yazılan) ayırma ve veriler için bellek ayırmasını sorumludur, `pvClientData` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="1f495-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="1f495-159">Ne zaman CLR yürütür `AttachProfiler` , bu çağrıda bir kopyasını bellek, `pvClientData` işaret ve hedef işlem için iletir.</span><span class="sxs-lookup"><span data-stu-id="1f495-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="1f495-160">CLR'nin hedef işlemin içinde kendine ait kopyasını aldığında `pvClientData` bloğu, bloğun profil oluşturucu geçirir `InitializeForAttach` yöntemi ve kopyasını ayırmayı iptal eder `pvClientData` hedef işlem bloğundan.</span><span class="sxs-lookup"><span data-stu-id="1f495-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f495-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f495-161">Requirements</span></span>  
 <span data-ttu-id="1f495-162">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f495-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f495-163">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f495-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f495-164">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f495-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f495-165">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f495-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f495-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f495-166">See also</span></span>
- [<span data-ttu-id="1f495-167">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f495-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1f495-168">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f495-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1f495-169">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1f495-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1f495-170">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f495-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
