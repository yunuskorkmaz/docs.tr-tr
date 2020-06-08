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
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500565"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="c35c1-102">ICLRProfiling::AttachProfiler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c35c1-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="c35c1-103">Belirtilen işlem oluşturucuyu belirtilen işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35c1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c35c1-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="c35c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c35c1-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="c35c1-106">\[içinde] profil oluşturucunun eklendiği işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c35c1-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="c35c1-107">64 bitlik bir makinede, profili oluşturulan işlemin bit genişliği, çağıran tetikleyici işlemin bit durumuyla aynı olmalıdır `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="c35c1-108">`AttachProfiler`İçinde çağrılan kullanıcı hesabının yönetim ayrıcalıkları varsa, hedef işlem sistemde herhangi bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="c35c1-109">Aksi takdirde, hedef işlem aynı kullanıcı hesabına ait olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c35c1-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="c35c1-110">\[' de] için milisaniye cinsinden süre `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="c35c1-111">Tetikleme işlemi, belirli bir profil oluşturucunun başlatma işlemini tamamlaması için yeterince bilinen bir zaman aşımı süresi iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="c35c1-112">\[' de] yüklenecek profil oluşturucunun CLSID 'sine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c35c1-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="c35c1-113">Tetikleme işlemi, bu belleği döndürbaşladıktan sonra yeniden kullanabilir `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="c35c1-114">\[' de] yüklenecek profil oluşturucunun DLL dosyasının tam yolu.</span><span class="sxs-lookup"><span data-stu-id="c35c1-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="c35c1-115">Bu dize, null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="c35c1-116">`wszProfilerPath`Null veya boş bir dize ise, ortak dil çalışma zamanı (CLR), öğesine işaret eden CLSID için kayıt defterine bakarak profil OLUŞTURUCUNUN dll dosyasının konumunu bulmaya çalışır `pClsidProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="c35c1-117">\[' de] [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi tarafından Profiler 'a geçirilecek verilerin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c35c1-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="c35c1-118">Tetikleme işlemi, bu belleği döndürbaşladıktan sonra yeniden kullanabilir `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="c35c1-119">`pvClientData`Null ise `cbClientData` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c35c1-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="c35c1-120">\[' de] işaret eden verilerin bayt cinsinden boyutu `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="c35c1-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c35c1-121">Return Value</span></span>  
 <span data-ttu-id="c35c1-122">Bu yöntem aşağıdaki HRESULTs 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c35c1-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="c35c1-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c35c1-123">HRESULT</span></span>|<span data-ttu-id="c35c1-124">Description</span><span class="sxs-lookup"><span data-stu-id="c35c1-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c35c1-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="c35c1-125">S_OK</span></span>|<span data-ttu-id="c35c1-126">Belirtilen profil oluşturucu hedef işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="c35c1-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="c35c1-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="c35c1-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="c35c1-128">Zaten bir profil oluşturucu etkin veya hedef işleme iliştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="c35c1-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="c35c1-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="c35c1-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="c35c1-130">Belirtilen profil oluşturucu eki desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="c35c1-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="c35c1-131">Tetikleyici işlemi, farklı bir profil oluşturucu iliştirmeye çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="c35c1-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="c35c1-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="c35c1-133">Hedef işlemin sürümü çağıran geçerli işlemle uyumsuz olduğundan profil oluşturucu eki istenmedi `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="c35c1-134">HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="c35c1-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="c35c1-135">Tetikleyici işleminin kullanıcısının hedef işleme erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="c35c1-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="c35c1-136">HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="c35c1-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="c35c1-137">Tetikleyici işleminin kullanıcısı, belirtilen hedef işleme bir profil oluşturucu eklemek için gerekli ayrıcalıklara sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c35c1-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="c35c1-138">Uygulama olay günlüğünde daha fazla bilgi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="c35c1-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="c35c1-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="c35c1-140">Hedef işlemle iletişim kurulurken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c35c1-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="c35c1-141">Bu, genellikle hedef işlem kapatıldıysa meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="c35c1-142">HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="c35c1-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="c35c1-143">Hedef işlem yok ya da eki destekleyen bir CLR çalıştırmıyor.</span><span class="sxs-lookup"><span data-stu-id="c35c1-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="c35c1-144">Bu, çalışma zamanı numaralandırma yöntemine yapılan çağrıdan bu yana CLR 'nin kaldırıldığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="c35c1-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="c35c1-145">HRESULT_FROM_WIN32 (ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="c35c1-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="c35c1-146">Zaman aşımı, profil oluşturucuyu yüklemeye başlamadan önce doldu.</span><span class="sxs-lookup"><span data-stu-id="c35c1-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="c35c1-147">İliştirme işlemini yeniden deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c35c1-147">You can retry the attach operation.</span></span> <span data-ttu-id="c35c1-148">Hedef işlemdeki bir Sonlandırıcı, zaman aşımı değerinden daha uzun bir süre çalıştığında zaman aşımları oluşur.</span><span class="sxs-lookup"><span data-stu-id="c35c1-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="c35c1-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c35c1-149">E_INVALIDARG</span></span>|<span data-ttu-id="c35c1-150">Bir veya daha fazla parametrenin geçersiz değerleri var.</span><span class="sxs-lookup"><span data-stu-id="c35c1-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="c35c1-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c35c1-151">E_FAIL</span></span>|<span data-ttu-id="c35c1-152">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c35c1-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="c35c1-153">Diğer hata kodları</span><span class="sxs-lookup"><span data-stu-id="c35c1-153">Other error codes</span></span>|<span data-ttu-id="c35c1-154">Profiler 'ın [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi hata BELIRTEN bir HRESULT döndürürse, `AttachProfiler` aynı hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="c35c1-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="c35c1-155">Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c35c1-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c35c1-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c35c1-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="c35c1-157">Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="c35c1-157">Memory Management</span></span>  
 <span data-ttu-id="c35c1-158">COM kuralları ile birlikte, çağıran `AttachProfiler` (örneğin, profil oluşturucu geliştiricisi tarafından yazılan tetikleyici kodu), parametresinin işaret ettiği veriler için bellek ayırmayı ve serbest bırakmayı sağlamaktan sorumludur `pvClientData` .</span><span class="sxs-lookup"><span data-stu-id="c35c1-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="c35c1-159">CLR çağrıyı yürüttüğünde `AttachProfiler` , ' a `pvClientData` işaret eden ve hedef işleme ileten belleğin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c35c1-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="c35c1-160">Hedef işlemin içindeki CLR kendi bloğunun kopyasını aldığında `pvClientData` , bloğunu yöntemi aracılığıyla Profiler 'a geçirir `InitializeForAttach` ve sonra `pvClientData` bloğun kopyasını hedef işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c35c1-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c35c1-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c35c1-161">Requirements</span></span>  
 <span data-ttu-id="c35c1-162">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c35c1-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c35c1-163">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c35c1-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c35c1-164">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c35c1-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c35c1-165">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c35c1-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35c1-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c35c1-166">See also</span></span>

- [<span data-ttu-id="c35c1-167">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c35c1-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c35c1-168">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c35c1-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c35c1-169">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c35c1-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c35c1-170">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c35c1-170">Profiling</span></span>](index.md)
