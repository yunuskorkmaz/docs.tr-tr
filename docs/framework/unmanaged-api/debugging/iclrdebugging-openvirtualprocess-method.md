---
title: ICLRDebugging::OpenVirtualProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: cd43dce995c2bc9a45a0c8134a91b20cb1dec26e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111422"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="e200c-102">ICLRDebugging::OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e200c-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="e200c-103">İşlemde yüklü olan bir ortak dil çalışma zamanı (CLR) modülüne karşılık gelen ICorDebugProcess arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="e200c-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e200c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e200c-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e200c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e200c-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="e200c-106">'ndaki Hedef işlemdeki bir modülün temel adresi.</span><span class="sxs-lookup"><span data-stu-id="e200c-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="e200c-107">Belirtilen modül bir CLR modülü değilse, COR_E_NOT_CLR döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="e200c-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="e200c-108">'ndaki Yönetilen hata ayıklayıcı işlem durumunu incelemeye izin veren bir veri hedefi soyutlama.</span><span class="sxs-lookup"><span data-stu-id="e200c-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="e200c-109">Hata ayıklayıcının [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e200c-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="e200c-110">Hata ayıklanan CLR 'nin bilgisayara yerel olarak yüklenmediği senaryoları desteklemek için [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimini uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e200c-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="e200c-111">'ndaki Sürüme özgü hata ayıklama kitaplıklarının isteğe bağlı olarak konumlandırılma ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e200c-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="e200c-112">Bu parametre yalnızca `ppProcess` veya `pFlags` `null`değilse gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e200c-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="e200c-113">'ndaki Bu hata ayıklayıcının hata ayıklayabilecekleri en yüksek CLR sürümü.</span><span class="sxs-lookup"><span data-stu-id="e200c-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="e200c-114">Bu hata ayıklayıcının desteklediği en son CLR sürümünden birincil, ikincil ve derleme sürümlerini belirtmeniz ve Düzeltme numarasını gelecekteki yerinde CLR bakım yayınlarına uyum sağlayacak şekilde 65535 olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e200c-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="e200c-115">'ndaki Alınacak ICorDebugProcess arabiriminin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e200c-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="e200c-116">Şu anda kabul edilen değerler şunlardır IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="e200c-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e200c-117">dışı `riidProcess`tarafından tanımlanan COM arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e200c-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e200c-118">[in, out] CLR sürümü.</span><span class="sxs-lookup"><span data-stu-id="e200c-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="e200c-119">Girişte bu değer `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="e200c-119">On input, this value can be `null`.</span></span> <span data-ttu-id="e200c-120">Ayrıca, [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) yapısına işaret edebilir, bu durumda yapının `wStructVersion` alanı 0 (sıfır) olarak başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e200c-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="e200c-121">Çıkışta, döndürülen `CLR_DEBUGGING_VERSION` yapısı CLR için sürüm bilgileriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e200c-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="e200c-122">dışı Belirtilen çalışma zamanına ilişkin bilgilendirme bayrakları.</span><span class="sxs-lookup"><span data-stu-id="e200c-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="e200c-123">Bayrakların açıklaması için [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e200c-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e200c-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e200c-124">Return Value</span></span>  
 <span data-ttu-id="e200c-125">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e200c-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e200c-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e200c-126">HRESULT</span></span>|<span data-ttu-id="e200c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e200c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e200c-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="e200c-128">S_OK</span></span>|<span data-ttu-id="e200c-129">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e200c-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="e200c-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e200c-130">E_POINTER</span></span>|<span data-ttu-id="e200c-131">`pDataTarget` `null`.</span><span class="sxs-lookup"><span data-stu-id="e200c-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="e200c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="e200c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="e200c-133">[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) geri çağırması bir hata döndürüyor veya geçerli bir tanıtıcı sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e200c-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="e200c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="e200c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="e200c-135">`pDataTarget`, çalışma zamanının bu sürümü için gerekli veri hedefi arabirimlerini uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="e200c-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="e200c-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="e200c-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="e200c-137">Belirtilen modül bir CLR modülü değil.</span><span class="sxs-lookup"><span data-stu-id="e200c-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="e200c-138">Bu HRESULT, bellek bozulduğundan bir CLR modülü algılanmadığında da döndürülür, modül kullanılabilir değildir veya CLR sürümü dolgu sürümünden daha geç.</span><span class="sxs-lookup"><span data-stu-id="e200c-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="e200c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="e200c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="e200c-140">Bu çalışma zamanı sürümü bu hata ayıklama modelini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="e200c-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="e200c-141">Şu anda, hata ayıklama modeli .NET Framework 4 ' den önceki CLR sürümleri tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e200c-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="e200c-142">`pwszVersion` output parametresi hala bu hatadan sonra doğru değere ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="e200c-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="e200c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="e200c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="e200c-144">CLR sürümü, bu hata ayıklayıcı tarafından desteklenen sürümden daha büyük.</span><span class="sxs-lookup"><span data-stu-id="e200c-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="e200c-145">`pwszVersion` output parametresi hala bu hatadan sonra doğru değere ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="e200c-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="e200c-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="e200c-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="e200c-147">`riidProcess` arabirimi kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e200c-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="e200c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="e200c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="e200c-149">`CLR_DEBUGGING_VERSION` yapısı `wStructVersion`için tanınan bir değere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e200c-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="e200c-150">Bu zaman kabul edilen tek değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="e200c-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e200c-151">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e200c-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e200c-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e200c-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e200c-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e200c-153">Requirements</span></span>  
 <span data-ttu-id="e200c-154">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e200c-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e200c-155">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e200c-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e200c-156">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e200c-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e200c-157">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e200c-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e200c-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e200c-158">See also</span></span>

- [<span data-ttu-id="e200c-159">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e200c-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e200c-160">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e200c-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
