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
ms.openlocfilehash: 25c208c98802be540bde7532c53798e6f7b35446
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445955"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="083c7-102">ICLRProfiling::AttachProfiler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="083c7-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="083c7-103">Attaches the specified profiler to the specified process.</span><span class="sxs-lookup"><span data-stu-id="083c7-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="083c7-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="083c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="083c7-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="083c7-106">[in] The process ID of the process to which the profiler should be attached.</span><span class="sxs-lookup"><span data-stu-id="083c7-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="083c7-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="083c7-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="083c7-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span><span class="sxs-lookup"><span data-stu-id="083c7-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="083c7-109">Otherwise, the target process must be owned by the same user account.</span><span class="sxs-lookup"><span data-stu-id="083c7-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="083c7-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span><span class="sxs-lookup"><span data-stu-id="083c7-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="083c7-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span><span class="sxs-lookup"><span data-stu-id="083c7-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="083c7-112">[in] A pointer to the CLSID of the profiler to be loaded.</span><span class="sxs-lookup"><span data-stu-id="083c7-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="083c7-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span><span class="sxs-lookup"><span data-stu-id="083c7-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="083c7-114">[in] The full path to the profiler’s DLL file to be loaded.</span><span class="sxs-lookup"><span data-stu-id="083c7-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="083c7-115">This string should contain no more than 260 characters, including the null terminator.</span><span class="sxs-lookup"><span data-stu-id="083c7-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="083c7-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span><span class="sxs-lookup"><span data-stu-id="083c7-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="083c7-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="083c7-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="083c7-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span><span class="sxs-lookup"><span data-stu-id="083c7-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="083c7-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="083c7-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="083c7-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span><span class="sxs-lookup"><span data-stu-id="083c7-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="083c7-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="083c7-121">Return Value</span></span>  
 <span data-ttu-id="083c7-122">This method returns the following HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="083c7-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="083c7-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="083c7-123">HRESULT</span></span>|<span data-ttu-id="083c7-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="083c7-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="083c7-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="083c7-125">S_OK</span></span>|<span data-ttu-id="083c7-126">The specified profiler has successfully attached to the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="083c7-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="083c7-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="083c7-128">There is already a profiler active or attaching to the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="083c7-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="083c7-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="083c7-130">The specified profiler does not support attachment.</span><span class="sxs-lookup"><span data-stu-id="083c7-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="083c7-131">The trigger process may attempt to attach a different profiler.</span><span class="sxs-lookup"><span data-stu-id="083c7-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="083c7-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="083c7-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="083c7-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="083c7-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="083c7-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="083c7-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="083c7-135">The user of the trigger process does not have access to the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="083c7-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="083c7-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="083c7-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="083c7-138">The application event log may contain more information.</span><span class="sxs-lookup"><span data-stu-id="083c7-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="083c7-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="083c7-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="083c7-140">A failure occurred when communicating with the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="083c7-141">This commonly happens if the target process was shutting down.</span><span class="sxs-lookup"><span data-stu-id="083c7-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="083c7-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="083c7-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="083c7-143">The target process does not exist or is not running a CLR that supports attachment.</span><span class="sxs-lookup"><span data-stu-id="083c7-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="083c7-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span><span class="sxs-lookup"><span data-stu-id="083c7-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="083c7-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="083c7-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="083c7-146">The timeout expired without beginning to load the profiler.</span><span class="sxs-lookup"><span data-stu-id="083c7-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="083c7-147">You can retry the attach operation.</span><span class="sxs-lookup"><span data-stu-id="083c7-147">You can retry the attach operation.</span></span> <span data-ttu-id="083c7-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span><span class="sxs-lookup"><span data-stu-id="083c7-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="083c7-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="083c7-149">E_INVALIDARG</span></span>|<span data-ttu-id="083c7-150">One or more parameters have invalid values.</span><span class="sxs-lookup"><span data-stu-id="083c7-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="083c7-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="083c7-151">E_FAIL</span></span>|<span data-ttu-id="083c7-152">Some other, unspecified failure occurred.</span><span class="sxs-lookup"><span data-stu-id="083c7-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="083c7-153">Other error codes</span><span class="sxs-lookup"><span data-stu-id="083c7-153">Other error codes</span></span>|<span data-ttu-id="083c7-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span><span class="sxs-lookup"><span data-stu-id="083c7-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="083c7-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="083c7-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="083c7-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="083c7-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="083c7-157">Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="083c7-157">Memory Management</span></span>  
 <span data-ttu-id="083c7-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span><span class="sxs-lookup"><span data-stu-id="083c7-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="083c7-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="083c7-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span><span class="sxs-lookup"><span data-stu-id="083c7-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="083c7-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="083c7-161">Requirements</span></span>  
 <span data-ttu-id="083c7-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="083c7-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083c7-163">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="083c7-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="083c7-164">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="083c7-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="083c7-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083c7-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083c7-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="083c7-166">See also</span></span>

- [<span data-ttu-id="083c7-167">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="083c7-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="083c7-168">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="083c7-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="083c7-169">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="083c7-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="083c7-170">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="083c7-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
