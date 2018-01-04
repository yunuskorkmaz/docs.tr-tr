---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="19993-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="19993-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="19993-103">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19993-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19993-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19993-104">Methods</span></span>  
  
|<span data-ttu-id="19993-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="19993-105">Method</span></span>|<span data-ttu-id="19993-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19993-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19993-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="19993-108">Bu işlev, başında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19993-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="19993-109">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="19993-110">Bu işlev bir üyesidir sınıfı temsil eden bir Icordebugclass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="19993-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="19993-111">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="19993-112">Bu işleve yapılan en son düzenleme sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="19993-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="19993-113">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="19993-114">Bu işlev için Microsoft Ara dili (MSIL) kodu alır.</span><span class="sxs-lookup"><span data-stu-id="19993-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="19993-115">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="19993-116">Meta verileri, bu tarafından temsil edilen işlevinin yerel değişken imzası için belirteç alır `ICorDebugFunction` örneği.</span><span class="sxs-lookup"><span data-stu-id="19993-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="19993-117">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="19993-118">Bu işlevin tanımlı olduğu modülü alır.</span><span class="sxs-lookup"><span data-stu-id="19993-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="19993-119">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="19993-120">Bu işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="19993-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="19993-121">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19993-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="19993-122">Meta verileri bu işlev için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="19993-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19993-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19993-123">Remarks</span></span>  
 <span data-ttu-id="19993-124">`ICorDebugFunction` Arabirimi genel tür parametreleri olan bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="19993-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="19993-125">Örneğin, bir `ICorDebugFunction` örneği temsil eden `Func<T>` ama `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="19993-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="19993-126">Çağrı [Icordebugılframe2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) genel tür parametreleri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="19993-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="19993-127">Bir yöntemin meta veri simgesi arasındaki ilişkiyi `mdMethodDef`ve bir yöntemin `ICorDebugFunction` Düzenle ve devam et izin verilip işlev bağlı nesne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="19993-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="19993-128">Düzenle ve devam et izin verilmez, işlev arasında bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="19993-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="19993-129">Diğer bir deyişle, işlev varsa `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="19993-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="19993-130">Düzenle ve devam et izin veriliyorsa işlev arasında çoktan bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="19993-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="19993-131">Diğer bir deyişle, birçok örneklerini işlevi olabilir `ICorDebugFunction`, bir işlev her sürümü, ancak yalnızca bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="19993-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19993-132">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="19993-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19993-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19993-133">Requirements</span></span>  
 <span data-ttu-id="19993-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19993-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19993-135">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19993-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19993-136">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19993-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="19993-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19993-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19993-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19993-138">See Also</span></span>  
 [<span data-ttu-id="19993-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19993-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
