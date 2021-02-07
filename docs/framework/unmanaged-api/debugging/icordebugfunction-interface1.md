---
description: ': ICorDebugFunction Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 835625341889e89e15ceb66ca71531cf7b8311c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692400"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="bc8b9-103">ICorDebugFunction Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-103">ICorDebugFunction Interface</span></span>

<span data-ttu-id="bc8b9-104">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-104">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc8b9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bc8b9-105">Methods</span></span>  
  
|<span data-ttu-id="bc8b9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bc8b9-106">Method</span></span>|<span data-ttu-id="bc8b9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc8b9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc8b9-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-108">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="bc8b9-109">Bu işlevin başlangıcında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-109">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="bc8b9-110">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-110">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="bc8b9-111">Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-111">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="bc8b9-112">GetCurrentVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-112">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="bc8b9-113">Bu işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-113">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="bc8b9-114">GetILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-114">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="bc8b9-115">Bu işlev için Microsoft ara dili (MSIL) kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-115">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="bc8b9-116">GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="bc8b9-116">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="bc8b9-117">Bu örnekle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır `ICorDebugFunction` .</span><span class="sxs-lookup"><span data-stu-id="bc8b9-117">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="bc8b9-118">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-118">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="bc8b9-119">Bu işlevin tanımlandığı modülü alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-119">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="bc8b9-120">GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc8b9-120">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="bc8b9-121">Bu işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-121">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="bc8b9-122">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="bc8b9-122">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="bc8b9-123">Bu işlev için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-123">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc8b9-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc8b9-124">Remarks</span></span>  

 <span data-ttu-id="bc8b9-125">`ICorDebugFunction`Arabirim, genel tür parametrelerine sahip bir işlevi temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-125">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="bc8b9-126">Örneğin, bir `ICorDebugFunction` örnek temsil eder `Func<T>` ancak değil `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="bc8b9-126">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="bc8b9-127">Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-127">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="bc8b9-128">Yöntemin meta veri belirteci, `mdMethodDef` ve yöntemin nesnesi arasındaki ilişki, `ICorDebugFunction` işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="bc8b9-128">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="bc8b9-129">İşlevde Düzenle ve devam et izin verilmiyorsa, nesne ve belirteç arasında bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="bc8b9-129">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="bc8b9-130">Diğer bir deyişle, işlevde bir `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-130">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="bc8b9-131">İşlevde Düzenle ve devam et izni varsa, nesne ve belirteç arasında çoktan bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="bc8b9-131">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="bc8b9-132">Diğer bir deyişle, işlev `ICorDebugFunction` işlevin her sürümü için bir tane olmak üzere birçok örneğine, ancak yalnızca bir belirtece sahip olabilir `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="bc8b9-132">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc8b9-133">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-133">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc8b9-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc8b9-134">Requirements</span></span>  

 <span data-ttu-id="bc8b9-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc8b9-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc8b9-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc8b9-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc8b9-137">**Kitaplık:**  Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bc8b9-137">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc8b9-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc8b9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8b9-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8b9-139">See also</span></span>

- [<span data-ttu-id="bc8b9-140">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc8b9-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
