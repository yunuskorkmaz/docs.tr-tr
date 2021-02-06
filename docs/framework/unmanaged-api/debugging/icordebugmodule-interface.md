---
description: ': ICorDebugModule arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f78023fe9975b609309c1c511380a3a394426283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660121"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="fef3f-103">ICorDebugModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fef3f-103">ICorDebugModule Interface</span></span>

<span data-ttu-id="fef3f-104">Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fef3f-104">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fef3f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fef3f-105">Methods</span></span>  
  
|<span data-ttu-id="fef3f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fef3f-106">Method</span></span>|<span data-ttu-id="fef3f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fef3f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fef3f-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-108">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="fef3f-109">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fef3f-109">Not implemented.</span></span>|  
|[<span data-ttu-id="fef3f-110">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-110">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="fef3f-111">Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="fef3f-111">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="fef3f-112">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-112">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="fef3f-113">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="fef3f-113">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="fef3f-114">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-114">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="fef3f-115">Bu modülün kapsayan derlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-115">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="fef3f-116">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-116">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="fef3f-117">Modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-117">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="fef3f-118">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-118">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="fef3f-119">Meta verilerden ICorDebugClass alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-119">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="fef3f-120">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-120">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="fef3f-121">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="fef3f-121">Deprecated.</span></span>|  
|[<span data-ttu-id="fef3f-122">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-122">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="fef3f-123">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fef3f-123">Not implemented.</span></span>|  
|[<span data-ttu-id="fef3f-124">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-124">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="fef3f-125">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-125">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="fef3f-126">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-126">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="fef3f-127">Belirtilen genel değişken için bir değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-127">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="fef3f-128">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-128">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="fef3f-129">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-129">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="fef3f-130">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-130">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="fef3f-131">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-131">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="fef3f-132">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-132">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="fef3f-133">Bu modül için kapsayan işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-133">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="fef3f-134">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-134">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="fef3f-135">Modülün boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-135">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="fef3f-136">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="fef3f-136">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="fef3f-137">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="fef3f-137">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="fef3f-138">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-138">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="fef3f-139">Modülün Dinamik olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fef3f-139">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="fef3f-140">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fef3f-140">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="fef3f-141">Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fef3f-141">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fef3f-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fef3f-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fef3f-143">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fef3f-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef3f-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fef3f-144">Requirements</span></span>  

 <span data-ttu-id="fef3f-145">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef3f-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef3f-146">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fef3f-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fef3f-147">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fef3f-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fef3f-148">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef3f-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef3f-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fef3f-149">See also</span></span>

- [<span data-ttu-id="fef3f-150">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fef3f-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="fef3f-151">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fef3f-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
