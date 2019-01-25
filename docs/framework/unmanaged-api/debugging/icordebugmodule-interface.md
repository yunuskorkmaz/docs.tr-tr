---
title: Icordebugmodule arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eca28f16f0430e793ad0b91b01db609f835f0a4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671258"
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="7d55f-102">Icordebugmodule arabirimi1</span><span class="sxs-lookup"><span data-stu-id="7d55f-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="7d55f-103">Bir yürütülebilir dosya ya da bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d55f-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d55f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7d55f-104">Methods</span></span>  
  
|<span data-ttu-id="7d55f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7d55f-105">Method</span></span>|<span data-ttu-id="7d55f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d55f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d55f-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="7d55f-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="7d55f-108">Not implemented.</span></span>|  
|[<span data-ttu-id="7d55f-109">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="7d55f-110">Belirler olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="7d55f-111">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="7d55f-112">Just-ın-time (JIT) derleyicinin bu modül içindeki yöntemler için hata ayıklama bilgilerini korur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7d55f-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="7d55f-113">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="7d55f-114">Bu modül için derlemeyi içeren alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="7d55f-115">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="7d55f-116">Modül temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="7d55f-117">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="7d55f-118">Icordebugclass meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="7d55f-119">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="7d55f-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7d55f-120">Deprecated.</span></span>|  
|[<span data-ttu-id="7d55f-121">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="7d55f-122">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="7d55f-122">Not implemented.</span></span>|  
|[<span data-ttu-id="7d55f-123">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="7d55f-124">Metaveri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="7d55f-125">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="7d55f-126">Belirtilen genel değişkeni için değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="7d55f-127">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="7d55f-128">Modül meta verilerini incelemek için kullanılan bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="7d55f-129">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="7d55f-130">Modül dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="7d55f-131">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="7d55f-132">Bu modül için içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="7d55f-133">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="7d55f-134">Modül boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="7d55f-135">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="7d55f-136">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="7d55f-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="7d55f-137">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="7d55f-138">Modülü dinamik olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d55f-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="7d55f-139">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d55f-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="7d55f-140">Bu modül yalnızca bellekte mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d55f-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d55f-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d55f-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d55f-142">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7d55f-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d55f-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d55f-143">Requirements</span></span>  
 <span data-ttu-id="7d55f-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d55f-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d55f-145">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d55f-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d55f-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d55f-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d55f-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d55f-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d55f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d55f-148">See also</span></span>
- [<span data-ttu-id="7d55f-149">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d55f-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="7d55f-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d55f-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
