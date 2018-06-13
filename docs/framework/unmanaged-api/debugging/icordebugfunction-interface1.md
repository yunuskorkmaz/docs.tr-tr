---
title: ICorDebugFunction Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 344acf109d58d0ed2fbc8a91da0761b4dd148a27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419185"
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="0adaf-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="0adaf-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="0adaf-103">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0adaf-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0adaf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0adaf-104">Methods</span></span>  
  
|<span data-ttu-id="0adaf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0adaf-105">Method</span></span>|<span data-ttu-id="0adaf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0adaf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0adaf-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="0adaf-108">Bu işlev, başında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0adaf-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="0adaf-109">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="0adaf-110">Bu işlev bir üyesidir sınıfı temsil eden bir Icordebugclass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="0adaf-111">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="0adaf-112">Bu işleve yapılan en son düzenleme sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="0adaf-113">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="0adaf-114">Bu işlev için Microsoft Ara dili (MSIL) kodu alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="0adaf-115">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="0adaf-116">Meta verileri, bu tarafından temsil edilen işlevinin yerel değişken imzası için belirteç alır `ICorDebugFunction` örneği.</span><span class="sxs-lookup"><span data-stu-id="0adaf-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="0adaf-117">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="0adaf-118">Bu işlevin tanımlı olduğu modülü alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="0adaf-119">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="0adaf-120">Bu işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="0adaf-121">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adaf-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="0adaf-122">Meta verileri bu işlev için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="0adaf-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0adaf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0adaf-123">Remarks</span></span>  
 <span data-ttu-id="0adaf-124">`ICorDebugFunction` Arabirimi genel tür parametreleri olan bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="0adaf-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="0adaf-125">Örneğin, bir `ICorDebugFunction` örneği temsil eden `Func<T>` ama `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="0adaf-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="0adaf-126">Çağrı [Icordebugılframe2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) genel tür parametreleri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="0adaf-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="0adaf-127">Bir yöntemin meta veri simgesi arasındaki ilişkiyi `mdMethodDef`ve bir yöntemin `ICorDebugFunction` Düzenle ve devam et izin verilip işlev bağlı nesne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="0adaf-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="0adaf-128">Düzenle ve devam et izin verilmez, işlev arasında bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="0adaf-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="0adaf-129">Diğer bir deyişle, işlev varsa `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="0adaf-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="0adaf-130">Düzenle ve devam et izin veriliyorsa işlev arasında çoktan bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="0adaf-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="0adaf-131">Diğer bir deyişle, birçok örneklerini işlevi olabilir `ICorDebugFunction`, bir işlev her sürümü, ancak yalnızca bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="0adaf-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0adaf-132">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0adaf-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0adaf-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0adaf-133">Requirements</span></span>  
 <span data-ttu-id="0adaf-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0adaf-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0adaf-135">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0adaf-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0adaf-136">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0adaf-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="0adaf-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0adaf-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adaf-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0adaf-138">See Also</span></span>  
 [<span data-ttu-id="0adaf-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0adaf-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
