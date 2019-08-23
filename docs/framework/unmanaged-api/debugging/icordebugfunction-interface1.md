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
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917200"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="85930-102">ICorDebugFunction Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85930-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="85930-103">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="85930-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85930-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85930-104">Methods</span></span>  
  
|<span data-ttu-id="85930-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85930-105">Method</span></span>|<span data-ttu-id="85930-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85930-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85930-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="85930-108">Bu işlevin başlangıcında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85930-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="85930-109">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="85930-110">Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="85930-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="85930-111">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="85930-112">Bu işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="85930-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="85930-113">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="85930-114">Bu işlev için Microsoft ara dili (MSIL) kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="85930-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="85930-115">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="85930-116">Bu `ICorDebugFunction` örnekle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="85930-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="85930-117">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="85930-118">Bu işlevin tanımlandığı modülü alır.</span><span class="sxs-lookup"><span data-stu-id="85930-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="85930-119">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="85930-120">Bu işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="85930-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="85930-121">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85930-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="85930-122">Bu işlev için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="85930-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85930-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85930-123">Remarks</span></span>  
 <span data-ttu-id="85930-124">Arabirim `ICorDebugFunction` , genel tür parametrelerine sahip bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="85930-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="85930-125">Örneğin, bir `ICorDebugFunction` örnek temsil eder `Func<T>` ancak değil `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="85930-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="85930-126">Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="85930-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="85930-127">Yöntemin meta veri belirteci, `mdMethodDef`ve `ICorDebugFunction` yöntemin nesnesi arasındaki ilişki, işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="85930-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="85930-128">İşlevde Düzenle ve devam et izin verilmiyorsa, `ICorDebugFunction` nesne `mdMethodDef` ve belirteç arasında bire bir ilişki bulunur.</span><span class="sxs-lookup"><span data-stu-id="85930-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="85930-129">Diğer bir deyişle, işlevde bir `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="85930-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="85930-130">İşlevde Düzenle ve devam et izni varsa, `ICorDebugFunction` nesne `mdMethodDef` ve belirteç arasında çoktan bire bir ilişki bulunur.</span><span class="sxs-lookup"><span data-stu-id="85930-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="85930-131">Diğer bir deyişle, işlev işlevin her sürümü için bir `ICorDebugFunction`tane olmak üzere birçok örneğine, ancak yalnızca bir `mdMethodDef` belirtece sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="85930-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85930-132">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="85930-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85930-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85930-133">Requirements</span></span>  
 <span data-ttu-id="85930-134">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85930-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85930-135">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85930-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85930-136">**Kitaplığı**  Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="85930-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="85930-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85930-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85930-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85930-138">See also</span></span>

- [<span data-ttu-id="85930-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85930-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
