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
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212249"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="78f73-102">ICorDebugModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f73-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="78f73-103">Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="78f73-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78f73-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="78f73-104">Methods</span></span>  
  
|<span data-ttu-id="78f73-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="78f73-105">Method</span></span>|<span data-ttu-id="78f73-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78f73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78f73-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="78f73-108">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="78f73-108">Not implemented.</span></span>|  
|[<span data-ttu-id="78f73-109">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="78f73-110">Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="78f73-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="78f73-111">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="78f73-112">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="78f73-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="78f73-113">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="78f73-114">Bu modülün kapsayan derlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="78f73-115">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="78f73-116">Modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="78f73-117">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="78f73-118">Meta verilerden ICorDebugClass alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="78f73-119">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="78f73-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="78f73-120">Deprecated.</span></span>|  
|[<span data-ttu-id="78f73-121">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="78f73-122">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="78f73-122">Not implemented.</span></span>|  
|[<span data-ttu-id="78f73-123">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="78f73-124">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="78f73-125">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="78f73-126">Belirtilen genel değişken için bir değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="78f73-127">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="78f73-128">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="78f73-129">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="78f73-130">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="78f73-131">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="78f73-132">Bu modül için kapsayan işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="78f73-133">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="78f73-134">Modülün boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="78f73-135">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="78f73-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="78f73-136">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="78f73-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="78f73-137">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="78f73-138">Modülün Dinamik olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78f73-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="78f73-139">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f73-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="78f73-140">Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78f73-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f73-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78f73-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78f73-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="78f73-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f73-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78f73-143">Requirements</span></span>  
 <span data-ttu-id="78f73-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f73-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f73-145">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78f73-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78f73-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78f73-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78f73-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f73-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f73-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78f73-148">See also</span></span>

- [<span data-ttu-id="78f73-149">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f73-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="78f73-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78f73-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
