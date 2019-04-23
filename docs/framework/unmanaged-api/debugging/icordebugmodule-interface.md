---
title: ICorDebugModule Arabirimi
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
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225644"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="ceae4-102">ICorDebugModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceae4-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="ceae4-103">Bir yürütülebilir dosya ya da bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ceae4-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ceae4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ceae4-104">Methods</span></span>  
  
|<span data-ttu-id="ceae4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ceae4-105">Method</span></span>|<span data-ttu-id="ceae4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceae4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ceae4-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="ceae4-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ceae4-108">Not implemented.</span></span>|  
|[<span data-ttu-id="ceae4-109">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="ceae4-110">Belirler olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="ceae4-111">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="ceae4-112">Just-ın-time (JIT) derleyicinin bu modül içindeki yöntemler için hata ayıklama bilgilerini korur olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ceae4-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="ceae4-113">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="ceae4-114">Bu modül için derlemeyi içeren alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="ceae4-115">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="ceae4-116">Modül temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="ceae4-117">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="ceae4-118">Icordebugclass meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="ceae4-119">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="ceae4-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="ceae4-120">Deprecated.</span></span>|  
|[<span data-ttu-id="ceae4-121">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="ceae4-122">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ceae4-122">Not implemented.</span></span>|  
|[<span data-ttu-id="ceae4-123">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="ceae4-124">Metaveri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="ceae4-125">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="ceae4-126">Belirtilen genel değişkeni için değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="ceae4-127">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="ceae4-128">Modül meta verilerini incelemek için kullanılan bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="ceae4-129">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="ceae4-130">Modül dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="ceae4-131">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="ceae4-132">Bu modül için içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="ceae4-133">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="ceae4-134">Modül boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="ceae4-135">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="ceae4-136">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="ceae4-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="ceae4-137">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="ceae4-138">Modülü dinamik olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ceae4-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="ceae4-139">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceae4-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="ceae4-140">Bu modül yalnızca bellekte mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ceae4-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceae4-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ceae4-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceae4-142">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ceae4-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceae4-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ceae4-143">Requirements</span></span>  
 <span data-ttu-id="ceae4-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceae4-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceae4-145">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceae4-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceae4-146">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceae4-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceae4-147">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceae4-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceae4-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceae4-148">See also</span></span>

- [<span data-ttu-id="ceae4-149">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceae4-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="ceae4-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ceae4-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
