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
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="50e2d-102">Icordebugmodule Interface1</span><span class="sxs-lookup"><span data-stu-id="50e2d-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="50e2d-103">Yürütülebilir bir dosyanın veya bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50e2d-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50e2d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50e2d-104">Methods</span></span>  
  
|<span data-ttu-id="50e2d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50e2d-105">Method</span></span>|<span data-ttu-id="50e2d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50e2d-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="50e2d-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="50e2d-108">Not implemented.</span></span>|  
|[<span data-ttu-id="50e2d-109">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="50e2d-110">Belirler olup olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri aramalar, bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="50e2d-111">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="50e2d-112">Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="50e2d-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="50e2d-113">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="50e2d-114">Bu modül için içeren derleme alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="50e2d-115">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="50e2d-116">Modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="50e2d-117">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="50e2d-118">Icordebugclass meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="50e2d-119">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="50e2d-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50e2d-120">Deprecated.</span></span>|  
|[<span data-ttu-id="50e2d-121">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="50e2d-122">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="50e2d-122">Not implemented.</span></span>|  
|[<span data-ttu-id="50e2d-123">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="50e2d-124">Meta veri simgesi tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="50e2d-125">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="50e2d-126">Belirtilen genel değişkeni için bir değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="50e2d-127">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="50e2d-128">Modül için meta verileri incelemek için kullanılan bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="50e2d-129">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="50e2d-130">Modül dosyası adını alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="50e2d-131">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="50e2d-132">Bu modül için içeren işlem alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="50e2d-133">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="50e2d-134">Modül boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="50e2d-135">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="50e2d-136">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="50e2d-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="50e2d-137">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="50e2d-138">Modül dinamik olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50e2d-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="50e2d-139">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e2d-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="50e2d-140">Bu modül yalnızca bellekte var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50e2d-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e2d-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e2d-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e2d-142">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="50e2d-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e2d-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50e2d-143">Requirements</span></span>  
 <span data-ttu-id="50e2d-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e2d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e2d-145">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50e2d-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e2d-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e2d-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e2d-147">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e2d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e2d-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50e2d-148">See Also</span></span>  
 [<span data-ttu-id="50e2d-149">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e2d-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="50e2d-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50e2d-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
