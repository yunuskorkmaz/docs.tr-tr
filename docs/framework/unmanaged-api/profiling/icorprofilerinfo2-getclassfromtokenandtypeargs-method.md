---
description: ': ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 810445d2617beff55e00df6bb30130d81c740ba4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760513"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="dea7f-103">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dea7f-103">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="dea7f-104">`ClassID`Belirtilen meta veri belirtecini ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir türün türünü alır.</span><span class="sxs-lookup"><span data-stu-id="dea7f-104">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea7f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea7f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dea7f-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="dea7f-107">'ndaki Türün bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dea7f-107">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="dea7f-108">'ndaki `mdTypeDef` Türe başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="dea7f-108">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="dea7f-109">'ndaki Verilen tür için tür parametrelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="dea7f-109">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="dea7f-110">Bu değer, genel olmayan türler için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dea7f-110">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="dea7f-111">'ndaki `ClassID` Her biri türünün bağımsız değişkeni olan bir değerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="dea7f-111">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="dea7f-112">`typeArgs` `cTypeArgs` Sıfır olarak AYARLANDıYSA değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="dea7f-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="dea7f-113">dışı Belirtilen türün bir işaretçisi `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="dea7f-113">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea7f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dea7f-114">Remarks</span></span>  

 <span data-ttu-id="dea7f-115">`GetClassFromTokenAndTypeArgs`Yöntemi `mdTypeRef` meta veri belirteci yerine bir ile çağırmak `mdTypeDef` öngörülemeyen sonuçlara neden olabilir; çağıranlar, verileri geçirirken bir ile çözmelidir `mdTypeRef` `mdTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="dea7f-115">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="dea7f-116">Tür zaten yüklü değilse, çağıran, `GetClassFromTokenAndTypeArgs` çok sayıda bağlamda tehlikeli bir işlem olan yüklemeyi tetikler.</span><span class="sxs-lookup"><span data-stu-id="dea7f-116">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="dea7f-117">Örneğin, modüller veya diğer türler yüklenirken bu yöntemin çağrılması, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dea7f-117">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="dea7f-118">Genel olarak, kullanımı `GetClassFromTokenAndTypeArgs` önerilmez.</span><span class="sxs-lookup"><span data-stu-id="dea7f-118">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="dea7f-119">Profil oluşturucular belirli bir tür için olaylar ile ilgileniyorsa, bu türden ve ' ı depolamalıdır `ModuleID` `mdTypeDef` ve belirli bir, istenen türde olup olmadığını denetlemek için [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) kullanın `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="dea7f-119">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea7f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dea7f-120">Requirements</span></span>  

 <span data-ttu-id="dea7f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea7f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea7f-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dea7f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dea7f-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dea7f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dea7f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea7f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea7f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dea7f-125">See also</span></span>

- [<span data-ttu-id="dea7f-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="dea7f-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
