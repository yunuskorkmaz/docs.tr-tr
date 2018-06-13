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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408258"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="a528c-102">ICLRDebugging::OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a528c-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="a528c-103">Bir ortak dil çalışma zamanı (CLR) modülü işleminde yüklenen karşılık gelen Icordebugprocess arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="a528c-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a528c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a528c-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="a528c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a528c-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="a528c-106">[in] Hedef işlemin modülünde temel adres.</span><span class="sxs-lookup"><span data-stu-id="a528c-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="a528c-107">Belirtilen modül CLR modül değilse COR_E_NOT_CLR döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a528c-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="a528c-108">[in] İşlem durumu denetlemek yönetilen hata ayıklayıcı sağlayan veri hedef özeti.</span><span class="sxs-lookup"><span data-stu-id="a528c-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="a528c-109">Hata ayıklayıcı uygulamalıdır [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a528c-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="a528c-110">Uygulamanız gerekir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , ayıklanacak CLR yüklü olmayan yerel bilgisayarda senaryoları desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="a528c-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="a528c-111">[in] Sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olmasını sağlayan bir kitaplığı sağlayıcısı geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a528c-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="a528c-112">Bu parametre yalnızca gerekli ise `ppProcess` veya `pFlags` değil `null`.</span><span class="sxs-lookup"><span data-stu-id="a528c-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="a528c-113">[in] Bu hata ayıklayıcı ayıklayabilirsiniz CLR yüksek sürümü.</span><span class="sxs-lookup"><span data-stu-id="a528c-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="a528c-114">Ana, ikincil, belirtin ve bu hata ayıklayıcı destekleyen en son CLR sürümü sürümlerden yapı ve düzeltme numarası 65535 sürümleri bakım gelecekteki yerinde CLR uyum sağlayacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a528c-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="a528c-115">[in] Alınacak Icordebugprocess arabirimi kimliği.</span><span class="sxs-lookup"><span data-stu-id="a528c-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="a528c-116">Şu anda, kabul edilen değerler yalnızca IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS ' dir.</span><span class="sxs-lookup"><span data-stu-id="a528c-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a528c-117">[out] Tarafından tanımlanan COM arabirimi için bir işaretçi `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="a528c-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a528c-118">[içinde out] CLR sürümü.</span><span class="sxs-lookup"><span data-stu-id="a528c-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="a528c-119">Giriş, bu değer olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="a528c-119">On input, this value can be `null`.</span></span> <span data-ttu-id="a528c-120">Bu da işaret edebilir bir [clr_debuggıng_versıon](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) yapısı, bu durumda yapısı `wStructVersion` alan 0 (sıfır) başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a528c-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="a528c-121">Çıktıyı, döndürülen `CLR_DEBUGGING_VERSION` yapısı, CLR sürüm bilgileri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a528c-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="a528c-122">[out] Belirtilen çalışma zamanı hakkında bilgi bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a528c-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="a528c-123">Bkz: [clr_debuggıng_process_flags](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) konu bayrakları açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a528c-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a528c-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a528c-124">Return Value</span></span>  
 <span data-ttu-id="a528c-125">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="a528c-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a528c-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a528c-126">HRESULT</span></span>|<span data-ttu-id="a528c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a528c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a528c-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="a528c-128">S_OK</span></span>|<span data-ttu-id="a528c-129">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a528c-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="a528c-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a528c-130">E_POINTER</span></span>|<span data-ttu-id="a528c-131">`pDataTarget` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="a528c-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="a528c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="a528c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="a528c-133">[Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) geri çağırma bir hata döndürür veya geçerli bir tanıtıcı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a528c-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="a528c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="a528c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="a528c-135">`pDataTarget` çalışma zamanı bu sürümü için gerekli verileri hedef arabirimleri uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="a528c-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="a528c-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="a528c-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="a528c-137">Belirtilen modül bir CLR modül değil.</span><span class="sxs-lookup"><span data-stu-id="a528c-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="a528c-138">Bir CLR modül bozuk belleği, modülü kullanılamıyor veya CLR sürümü dolgusu sürümünden daha yeni olduğundan algılanamıyor olduğunda bu HRESULT da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a528c-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="a528c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="a528c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="a528c-140">Bu çalışma zamanı sürümü bu hata ayıklama modelini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a528c-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="a528c-141">Şu anda, hata ayıklama model CLR sürümlerinden önce tarafından desteklenmiyor [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a528c-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a528c-142">`pwszVersion` Çıktı parametresi hala olarak bu hatadan sonra doğru değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a528c-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="a528c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="a528c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="a528c-144">Bu hata ayıklayıcı desteği iddia sürümünden büyük CLR sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a528c-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="a528c-145">`pwszVersion` Çıktı parametresi hala olarak bu hatadan sonra doğru değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a528c-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="a528c-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="a528c-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="a528c-147">`riidProcess` Arabirimi kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="a528c-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="a528c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="a528c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="a528c-149">`CLR_DEBUGGING_VERSION` Yapısı için tanınan bir değer yok `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="a528c-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="a528c-150">Şu anda yalnızca kabul edilen değeri 0'dır.</span><span class="sxs-lookup"><span data-stu-id="a528c-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a528c-151">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a528c-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a528c-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a528c-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a528c-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a528c-153">Requirements</span></span>  
 <span data-ttu-id="a528c-154">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a528c-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a528c-155">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a528c-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a528c-156">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a528c-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a528c-157">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a528c-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a528c-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a528c-158">See Also</span></span>  
 [<span data-ttu-id="a528c-159">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a528c-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a528c-160">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a528c-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
