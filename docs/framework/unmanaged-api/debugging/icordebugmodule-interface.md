---
title: Icordebugmodule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ced01c9c01a32468f371a8e172c878337fb79757
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="bb108-102">Icordebugmodule Interface1</span><span class="sxs-lookup"><span data-stu-id="bb108-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="bb108-103">Yürütülebilir bir dosyanın veya bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bb108-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb108-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bb108-104">Methods</span></span>  
  
|<span data-ttu-id="bb108-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb108-105">Method</span></span>|<span data-ttu-id="bb108-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb108-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb108-107">CreateBreakpoint yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="bb108-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bb108-108">Not implemented.</span></span>|  
|[<span data-ttu-id="bb108-109">EnableClassLoadCallbacks yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="bb108-110">Belirler olup olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri aramalar, bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bb108-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="bb108-111">Enablejıtdebugging yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="bb108-112">Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bb108-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="bb108-113">GetAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="bb108-114">Bu modül için içeren derleme alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="bb108-115">GetBaseAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="bb108-116">Modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="bb108-117">GetClassFromToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="bb108-118">Icordebugclass meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="bb108-119">GetEditAndContinueSnapshot yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="bb108-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="bb108-120">Deprecated.</span></span>|  
|[<span data-ttu-id="bb108-121">GetFunctionFromRVA yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="bb108-122">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bb108-122">Not implemented.</span></span>|  
|[<span data-ttu-id="bb108-123">GetFunctionFromToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="bb108-124">Meta veri simgesi tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="bb108-125">GetGlobalVariableValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="bb108-126">Belirtilen genel değişkeni için bir değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="bb108-127">Getmetadataınterface yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="bb108-128">Modül için meta verileri incelemek için kullanılan bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="bb108-129">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="bb108-130">Modül dosyası adını alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="bb108-131">GetProcess yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="bb108-132">Bu modül için içeren işlem alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="bb108-133">GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="bb108-134">Modül boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="bb108-135">GetToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="bb108-136">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="bb108-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="bb108-137">Isdynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="bb108-138">Modül dinamik olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb108-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="bb108-139">Isınmemory yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb108-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="bb108-140">Bu modül yalnızca bellekte var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb108-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb108-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb108-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb108-142">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bb108-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb108-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb108-143">Requirements</span></span>  
 <span data-ttu-id="bb108-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb108-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb108-145">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb108-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb108-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb108-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb108-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb108-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb108-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb108-148">See Also</span></span>  
 [<span data-ttu-id="bb108-149">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb108-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="bb108-150">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb108-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
