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
ms.openlocfilehash: 668b27932ea7a2bdc244e1ac0bb8e6891cbd4d17
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726307"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="1a34e-102">ICorDebugFunction Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a34e-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="1a34e-103">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a34e-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a34e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a34e-104">Methods</span></span>  
  
|<span data-ttu-id="1a34e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a34e-105">Method</span></span>|<span data-ttu-id="1a34e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a34e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a34e-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="1a34e-108">Bu işlevin başlangıcında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a34e-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="1a34e-109">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="1a34e-110">Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="1a34e-111">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="1a34e-112">Bu işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="1a34e-113">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="1a34e-114">Bu işlev için Microsoft ara dili (MSIL) kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="1a34e-115">GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="1a34e-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="1a34e-116">Bu örnekle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır `ICorDebugFunction` .</span><span class="sxs-lookup"><span data-stu-id="1a34e-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="1a34e-117">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="1a34e-118">Bu işlevin tanımlandığı modülü alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="1a34e-119">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a34e-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="1a34e-120">Bu işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="1a34e-121">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="1a34e-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="1a34e-122">Bu işlev için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a34e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a34e-123">Remarks</span></span>  

 <span data-ttu-id="1a34e-124">`ICorDebugFunction`Arabirim, genel tür parametrelerine sahip bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="1a34e-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="1a34e-125">Örneğin, bir `ICorDebugFunction` örnek temsil eder `Func<T>` ancak değil `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="1a34e-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="1a34e-126">Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="1a34e-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="1a34e-127">Yöntemin meta veri belirteci, `mdMethodDef` ve yöntemin nesnesi arasındaki ilişki, `ICorDebugFunction` işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="1a34e-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="1a34e-128">İşlevde Düzenle ve devam et izin verilmiyorsa, nesne ve belirteç arasında bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="1a34e-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1a34e-129">Diğer bir deyişle, işlevde bir `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="1a34e-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="1a34e-130">İşlevde Düzenle ve devam et izni varsa, nesne ve belirteç arasında çoktan bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="1a34e-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1a34e-131">Diğer bir deyişle, işlev `ICorDebugFunction` işlevin her sürümü için bir tane olmak üzere birçok örneğine, ancak yalnızca bir belirtece sahip olabilir `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="1a34e-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a34e-132">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1a34e-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a34e-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a34e-133">Requirements</span></span>  

 <span data-ttu-id="1a34e-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a34e-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a34e-135">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a34e-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a34e-136">**Kitaplık:**  Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a34e-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a34e-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a34e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a34e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a34e-138">See also</span></span>

- [<span data-ttu-id="1a34e-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a34e-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
