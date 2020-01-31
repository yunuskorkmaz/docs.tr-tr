---
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
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862798"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="6df8f-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df8f-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="6df8f-103">Tür bağımsız değişkenlerinin belirtilen meta veri belirtecini ve `ClassID` değerlerini kullanarak bir türün `ClassID` alır.</span><span class="sxs-lookup"><span data-stu-id="6df8f-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6df8f-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="6df8f-106">'ndaki Türün bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6df8f-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="6df8f-107">'ndaki Türe başvuran bir `mdTypeDef` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6df8f-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="6df8f-108">'ndaki Verilen tür için tür parametrelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="6df8f-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="6df8f-109">Bu değer, genel olmayan türler için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6df8f-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="6df8f-110">'ndaki Her biri türünün bağımsız değişkeni olan `ClassID` değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="6df8f-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="6df8f-111">`cTypeArgs` sıfır olarak ayarlandıysa `typeArgs` değeri NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="6df8f-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="6df8f-112">dışı Belirtilen türün `ClassID` bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6df8f-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df8f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df8f-113">Remarks</span></span>  
 <span data-ttu-id="6df8f-114">`GetClassFromTokenAndTypeArgs` yönteminin `mdTypeDef` meta veri belirteci yerine `mdTypeRef` çağrılması öngörülemeyen sonuçlara neden olabilir; çağıranlar, `mdTypeRef` bir `mdTypeDef` geçirmeden çözümlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6df8f-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="6df8f-115">Tür zaten yüklü değilse, `GetClassFromTokenAndTypeArgs` çağrısı, çok sayıda bağlamda tehlikeli bir işlem olan yüklemeyi tetikleyecektir.</span><span class="sxs-lookup"><span data-stu-id="6df8f-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="6df8f-116">Örneğin, modüller veya diğer türler yüklenirken bu yöntemin çağrılması, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6df8f-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="6df8f-117">Genel olarak, `GetClassFromTokenAndTypeArgs` kullanımı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="6df8f-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="6df8f-118">Profil oluşturucular belirli bir tür için olaylarla ilgileniyorsa, bu türün `ModuleID` ve `mdTypeDef` depolarlar ve belirli bir `ClassID` istenen türde olup olmadığını denetlemek için [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6df8f-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df8f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df8f-119">Requirements</span></span>  
 <span data-ttu-id="6df8f-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df8f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df8f-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6df8f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6df8f-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6df8f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df8f-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df8f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df8f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6df8f-124">See also</span></span>

- [<span data-ttu-id="6df8f-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df8f-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6df8f-126">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df8f-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
