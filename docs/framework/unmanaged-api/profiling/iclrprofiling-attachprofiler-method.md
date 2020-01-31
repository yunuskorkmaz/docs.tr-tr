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
ms.openlocfilehash: 29aecd530d18b931420467e9127bcbf96d3a4a5f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866780"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="86746-102">ICLRProfiling::AttachProfiler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86746-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="86746-103">Belirtilen işlem oluşturucuyu belirtilen işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="86746-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86746-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86746-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="86746-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86746-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="86746-106">\[içinde] profil oluşturucunun eklendiği işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="86746-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="86746-107">64 bitlik bir makinede, profili oluşturulan işlemin bit genişliği, `AttachProfiler`çağıran tetikleyici işlemin bit durumuyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86746-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="86746-108">`AttachProfiler` altında çağrıldığı Kullanıcı hesabının yönetim ayrıcalıkları varsa, hedef işlem sistemde herhangi bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="86746-109">Aksi takdirde, hedef işlem aynı kullanıcı hesabına ait olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86746-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="86746-110">\[, `AttachProfiler` tamamlanmayacak süre (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="86746-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="86746-111">Tetikleme işlemi, belirli bir profil oluşturucunun başlatma işlemini tamamlaması için yeterince bilinen bir zaman aşımı süresi iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="86746-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="86746-112">\[içinde, yüklenecek profil oluşturucunun CLSID 'sine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86746-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="86746-113">Tetikleyici işlemi, `AttachProfiler` döndüğünde bu belleği yeniden kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="86746-114">\[içinde] yüklenecek profil oluşturucunun DLL dosyasının tam yolu.</span><span class="sxs-lookup"><span data-stu-id="86746-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="86746-115">Bu dize, null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="86746-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="86746-116">`wszProfilerPath` null ya da boş bir dize ise, ortak dil çalışma zamanı (CLR) `pClsidProfiler` işaret eden CLSID için kayıt defterine bakarak profil oluşturucunun DLL dosyasının konumunu bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="86746-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="86746-117">\[içinde, [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi tarafından Profiler 'a geçirilecek verilerin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="86746-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="86746-118">Tetikleyici işlemi, `AttachProfiler` döndüğünde bu belleği yeniden kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="86746-119">`pvClientData` null ise, `cbClientData` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86746-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="86746-120">\[, `pvClientData` tarafından işaret edilen verilerin bayt cinsinden boyutudur.</span><span class="sxs-lookup"><span data-stu-id="86746-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="86746-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86746-121">Return Value</span></span>  
 <span data-ttu-id="86746-122">Bu yöntem aşağıdaki HRESULTs 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="86746-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="86746-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86746-123">HRESULT</span></span>|<span data-ttu-id="86746-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86746-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86746-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="86746-125">S_OK</span></span>|<span data-ttu-id="86746-126">Belirtilen profil oluşturucu hedef işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="86746-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="86746-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="86746-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="86746-128">Zaten bir profil oluşturucu etkin veya hedef işleme iliştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="86746-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="86746-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="86746-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="86746-130">Belirtilen profil oluşturucu eki desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="86746-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="86746-131">Tetikleyici işlemi, farklı bir profil oluşturucu iliştirmeye çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="86746-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="86746-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="86746-133">Hedef işlemin sürümü `AttachProfiler`çağıran geçerli işlemle uyumsuz olduğundan profil oluşturucu eki istenmedi.</span><span class="sxs-lookup"><span data-stu-id="86746-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="86746-134">HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="86746-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="86746-135">Tetikleyici işleminin kullanıcısının hedef işleme erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="86746-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="86746-136">HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="86746-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="86746-137">Tetikleyici işleminin kullanıcısı, belirtilen hedef işleme bir profil oluşturucu eklemek için gerekli ayrıcalıklara sahip değil.</span><span class="sxs-lookup"><span data-stu-id="86746-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="86746-138">Uygulama olay günlüğünde daha fazla bilgi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="86746-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="86746-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="86746-140">Hedef işlemle iletişim kurulurken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="86746-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="86746-141">Bu, genellikle hedef işlem kapatıldıysa meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="86746-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="86746-142">HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="86746-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="86746-143">Hedef işlem yok ya da eki destekleyen bir CLR çalıştırmıyor.</span><span class="sxs-lookup"><span data-stu-id="86746-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="86746-144">Bu, çalışma zamanı numaralandırma yöntemine yapılan çağrıdan bu yana CLR 'nin kaldırıldığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="86746-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="86746-145">HRESULT_FROM_WIN32 (ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="86746-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="86746-146">Zaman aşımı, profil oluşturucuyu yüklemeye başlamadan önce doldu.</span><span class="sxs-lookup"><span data-stu-id="86746-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="86746-147">İliştirme işlemini yeniden deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86746-147">You can retry the attach operation.</span></span> <span data-ttu-id="86746-148">Hedef işlemdeki bir Sonlandırıcı, zaman aşımı değerinden daha uzun bir süre çalıştığında zaman aşımları oluşur.</span><span class="sxs-lookup"><span data-stu-id="86746-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="86746-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="86746-149">E_INVALIDARG</span></span>|<span data-ttu-id="86746-150">Bir veya daha fazla parametrenin geçersiz değerleri var.</span><span class="sxs-lookup"><span data-stu-id="86746-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="86746-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86746-151">E_FAIL</span></span>|<span data-ttu-id="86746-152">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="86746-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="86746-153">Diğer hata kodları</span><span class="sxs-lookup"><span data-stu-id="86746-153">Other error codes</span></span>|<span data-ttu-id="86746-154">Profiler 'ın [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi hata BELIRTEN bir HRESULT döndürürse, `AttachProfiler` aynı hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="86746-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="86746-155">Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="86746-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86746-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86746-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="86746-157">Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="86746-157">Memory Management</span></span>  
 <span data-ttu-id="86746-158">COM kurallarıyla birlikte `AttachProfiler` çağıranı (örneğin, profil oluşturucu geliştiricisi tarafından yazılan tetikleyici kodu), `pvClientData` parametresinin işaret ettiği veriler için bellek ayırmayı ve serbest bırakmayı sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="86746-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="86746-159">CLR `AttachProfiler` çağrısını yürüttüğünde, `pvClientData` işaret eden belleğin bir kopyasını oluşturur ve hedef işleme iletir.</span><span class="sxs-lookup"><span data-stu-id="86746-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="86746-160">Hedef işlemin içindeki CLR `pvClientData` bloğunun kendi kopyasını aldığında, engellemeyi `InitializeForAttach` yöntemi aracılığıyla Profiler 'a geçirir ve ardından hedef işlemden `pvClientData` bloğunun kopyasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="86746-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86746-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86746-161">Requirements</span></span>  
 <span data-ttu-id="86746-162">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86746-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86746-163">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="86746-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86746-164">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86746-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86746-165">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86746-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86746-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86746-166">See also</span></span>

- [<span data-ttu-id="86746-167">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86746-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="86746-168">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86746-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="86746-169">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86746-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="86746-170">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86746-170">Profiling</span></span>](index.md)
