---
description: ': ICLRDebugging:: OpenVirtualProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f9f195e1202a26a13b09cace74328c3937a9fcf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723302"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="9a67e-103">ICLRDebugging::OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a67e-103">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="9a67e-104">İşlemde yüklü olan bir ortak dil çalışma zamanı (CLR) modülüne karşılık gelen ICorDebugProcess arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="9a67e-104">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a67e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a67e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9a67e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a67e-106">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="9a67e-107">'ndaki Hedef işlemdeki bir modülün temel adresi.</span><span class="sxs-lookup"><span data-stu-id="9a67e-107">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="9a67e-108">COR_E_NOT_CLR, belirtilen modül bir CLR modülü değilse döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="9a67e-108">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="9a67e-109">'ndaki Yönetilen hata ayıklayıcı işlem durumunu incelemeye izin veren bir veri hedefi soyutlama.</span><span class="sxs-lookup"><span data-stu-id="9a67e-109">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="9a67e-110">Hata ayıklayıcının [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a67e-110">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="9a67e-111">Hata ayıklanan CLR 'nin bilgisayara yerel olarak yüklenmediği senaryoları desteklemek için [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimini uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9a67e-111">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="9a67e-112">'ndaki Sürüme özgü hata ayıklama kitaplıklarının isteğe bağlı olarak konumlandırılma ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9a67e-112">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="9a67e-113">Bu parametre yalnızca veya değilse gereklidir `ppProcess` `pFlags` `null` .</span><span class="sxs-lookup"><span data-stu-id="9a67e-113">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="9a67e-114">'ndaki Bu hata ayıklayıcının hata ayıklayabilecekleri en yüksek CLR sürümü.</span><span class="sxs-lookup"><span data-stu-id="9a67e-114">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="9a67e-115">Bu hata ayıklayıcının desteklediği en son CLR sürümünden birincil, ikincil ve derleme sürümlerini belirtmeniz ve Düzeltme numarasını gelecekteki yerinde CLR bakım yayınlarına uyum sağlayacak şekilde 65535 olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a67e-115">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="9a67e-116">'ndaki Alınacak ICorDebugProcess arabiriminin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9a67e-116">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="9a67e-117">Şu anda kabul edilen değerler IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 ve IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="9a67e-117">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="9a67e-118">dışı Tarafından tanımlanan COM arabirimine yönelik bir işaretçi `riidProcess` .</span><span class="sxs-lookup"><span data-stu-id="9a67e-118">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="9a67e-119">[in, out] CLR sürümü.</span><span class="sxs-lookup"><span data-stu-id="9a67e-119">[in, out] The version of the CLR.</span></span> <span data-ttu-id="9a67e-120">Girişte bu değer olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="9a67e-120">On input, this value can be `null`.</span></span> <span data-ttu-id="9a67e-121">Ayrıca, bir [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) yapısına işaret edebilir, bu durumda yapının `wStructVersion` alanı 0 (sıfır) olarak başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a67e-121">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="9a67e-122">Çıkışta, döndürülen `CLR_DEBUGGING_VERSION` Yapı CLR için sürüm bilgileriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9a67e-122">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="9a67e-123">dışı Belirtilen çalışma zamanına ilişkin bilgilendirme bayrakları.</span><span class="sxs-lookup"><span data-stu-id="9a67e-123">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="9a67e-124">Bayrakların açıklaması için [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="9a67e-124">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a67e-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a67e-125">Return Value</span></span>  

 <span data-ttu-id="9a67e-126">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a67e-126">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9a67e-127">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a67e-127">HRESULT</span></span>|<span data-ttu-id="9a67e-128">Description</span><span class="sxs-lookup"><span data-stu-id="9a67e-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a67e-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a67e-129">S_OK</span></span>|<span data-ttu-id="9a67e-130">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9a67e-130">The method completed successfully.</span></span>|  
|<span data-ttu-id="9a67e-131">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9a67e-131">E_POINTER</span></span>|<span data-ttu-id="9a67e-132">`pDataTarget`, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9a67e-132">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="9a67e-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="9a67e-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="9a67e-134">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) geri çağırması bir hata döndürüyor veya geçerli bir tanıtıcı sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9a67e-134">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="9a67e-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="9a67e-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="9a67e-136">`pDataTarget` çalışma zamanının bu sürümü için gerekli veri hedefi arabirimlerini uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="9a67e-136">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="9a67e-137">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="9a67e-137">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="9a67e-138">Belirtilen modül bir CLR modülü değil.</span><span class="sxs-lookup"><span data-stu-id="9a67e-138">The indicated module is not a CLR module.</span></span> <span data-ttu-id="9a67e-139">Bu HRESULT, bellek bozulduğundan bir CLR modülü algılanmadığında da döndürülür, modül kullanılabilir değildir veya CLR sürümü dolgu sürümünden daha geç.</span><span class="sxs-lookup"><span data-stu-id="9a67e-139">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="9a67e-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="9a67e-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="9a67e-141">Bu çalışma zamanı sürümü bu hata ayıklama modelini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="9a67e-141">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="9a67e-142">Şu anda, hata ayıklama modeli .NET Framework 4 ' den önceki CLR sürümleri tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9a67e-142">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="9a67e-143">`pwszVersion`Output parametresi hala bu hatadan sonra doğru değere ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="9a67e-143">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="9a67e-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="9a67e-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="9a67e-145">CLR sürümü, bu hata ayıklayıcı tarafından desteklenen sürümden daha büyük.</span><span class="sxs-lookup"><span data-stu-id="9a67e-145">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="9a67e-146">`pwszVersion`Output parametresi hala bu hatadan sonra doğru değere ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="9a67e-146">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="9a67e-147">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="9a67e-147">E_NO_INTERFACE</span></span>|<span data-ttu-id="9a67e-148">`riidProcess`Arabirim kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9a67e-148">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="9a67e-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="9a67e-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="9a67e-150">`CLR_DEBUGGING_VERSION`Yapının için tanınan bir değeri yok `wStructVersion` .</span><span class="sxs-lookup"><span data-stu-id="9a67e-150">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="9a67e-151">Bu zaman kabul edilen tek değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="9a67e-151">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9a67e-152">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="9a67e-152">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a67e-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a67e-153">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a67e-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a67e-154">Requirements</span></span>  

 <span data-ttu-id="9a67e-155">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a67e-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a67e-156">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a67e-156">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a67e-157">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9a67e-157">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a67e-158">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a67e-158">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a67e-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a67e-159">See also</span></span>

- [<span data-ttu-id="9a67e-160">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a67e-160">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9a67e-161">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9a67e-161">Debugging</span></span>](index.md)
