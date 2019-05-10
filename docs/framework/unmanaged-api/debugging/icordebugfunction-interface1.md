---
title: ICorDebugFunction Arabirimi
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
ms.openlocfilehash: 550b85474c1ccd7e125549e86df906439caf410e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621491"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="2f819-102">ICorDebugFunction Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f819-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="2f819-103">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f819-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f819-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f819-104">Methods</span></span>  
  
|<span data-ttu-id="2f819-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2f819-105">Method</span></span>|<span data-ttu-id="2f819-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f819-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f819-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="2f819-108">Bu işlevin başında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f819-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="2f819-109">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="2f819-110">Bu işlev bir üyesi, sınıfın temsil ettiği bir Icordebugclass nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="2f819-111">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="2f819-112">Bu işleve yapılan en son düzenleme sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="2f819-113">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="2f819-114">Bu işlev için Microsoft Ara dil (MSIL) kodu alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="2f819-115">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="2f819-116">Yerel değişken bu tarafından temsil edilen işlev imzası için meta veri belirteci alır `ICorDebugFunction` örneği.</span><span class="sxs-lookup"><span data-stu-id="2f819-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="2f819-117">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="2f819-118">Bu işlev tanımlandığı modül alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="2f819-119">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="2f819-120">Yerel kod için bu işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="2f819-121">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f819-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="2f819-122">Meta veriler, bu işlev için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="2f819-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f819-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f819-123">Remarks</span></span>  
 <span data-ttu-id="2f819-124">`ICorDebugFunction` Arabirimi, genel tür parametreleri olan bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="2f819-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="2f819-125">Örneğin, bir `ICorDebugFunction` örneği gösterir `Func<T>` ama `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="2f819-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="2f819-126">Çağrı [Icordebugılframe2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) genel tür parametreleri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="2f819-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="2f819-127">Bir yöntemin meta veri belirteci arasındaki ilişkiyi `mdMethodDef`ve bir yöntemin `ICorDebugFunction` Düzenle ve devam et izin verilip işlev üzerinde nesne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="2f819-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="2f819-128">Düzenle ve devam et izin verilmez, işlev arasında bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f819-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="2f819-129">Diğer bir deyişle, bir işleve sahip `ICorDebugFunction` nesnesi ve bir `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f819-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="2f819-130">Düzenle ve devam et izin veriliyorsa işlev arasında çok bir ilişkinin var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f819-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="2f819-131">İşlevin birçok örneğini diğer bir deyişle, olabilir `ICorDebugFunction`, işlevin her sürüm için ancak tek `mdMethodDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f819-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f819-132">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2f819-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f819-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f819-133">Requirements</span></span>  
 <span data-ttu-id="2f819-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f819-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f819-135">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f819-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f819-136">**Kitaplığı:**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f819-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f819-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f819-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f819-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f819-138">See also</span></span>

- [<span data-ttu-id="2f819-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2f819-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
