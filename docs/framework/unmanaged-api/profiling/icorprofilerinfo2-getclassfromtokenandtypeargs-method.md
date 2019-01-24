---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0651609e6d2597336ee42ceae752df7e561cd252
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692658"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="f58b4-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Metodu</span><span class="sxs-lookup"><span data-stu-id="f58b4-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="f58b4-103">Alır `ClassID` belirtilen meta veri belirteci kullanarak türü ve `ClassID` herhangi bir değer türü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="f58b4-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f58b4-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f58b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f58b4-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f58b4-106">[in] Türü bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="f58b4-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="f58b4-107">[in] Bir `mdTypeDef` türe başvuran meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f58b4-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f58b4-108">[in] Verilen tür için tür parametreleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="f58b4-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="f58b4-109">Bu değer, genel olmayan türler için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f58b4-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f58b4-110">[in] Bir dizi `ClassID` değerler, her biri olan bir bağımsız değişken türü.</span><span class="sxs-lookup"><span data-stu-id="f58b4-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="f58b4-111">Değerini `typeArgs` NULL olabilir `cTypeArgs` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f58b4-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="f58b4-112">[out] Bir işaretçi `ClassID` belirtilen türe ait.</span><span class="sxs-lookup"><span data-stu-id="f58b4-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f58b4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f58b4-113">Remarks</span></span>  
 <span data-ttu-id="f58b4-114">Çağırma `GetClassFromTokenAndTypeArgs` yöntemi ile bir `mdTypeRef` yerine bir `mdTypeDef` meta veri belirteci öngörülemeyen sonuçlara sahip olabilir; çağıranlar çözümlemelidir `mdTypeRef` için bir `mdTypeDef` iletmeden olduğunda.</span><span class="sxs-lookup"><span data-stu-id="f58b4-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="f58b4-115">Türü zaten yüklü değilse, çağırma `GetClassFromTokenAndTypeArgs` birçok bağlamlarda tehlikeli bir işlemi yüklemeyi tetikler.</span><span class="sxs-lookup"><span data-stu-id="f58b4-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="f58b4-116">Örneğin, çalışma zamanı, döngüsel olarak şeyler yükleme girişiminde gibi diğer türleri veya modüller yükleme sırasında bu yöntemi çağırmadan sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f58b4-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="f58b4-117">Genel olarak, kullanım `GetClassFromTokenAndTypeArgs` önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f58b4-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="f58b4-118">Profil Oluşturucular, belirli bir tür için olaylar ilgileniyorsanız depolamanız gerekir `ModuleID` ve `mdTypeDef` , türü ve kullanım [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) denetlemek için olup olmadığını bir verilen `ClassID` budur İstenen türü.</span><span class="sxs-lookup"><span data-stu-id="f58b4-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f58b4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f58b4-119">Requirements</span></span>  
 <span data-ttu-id="f58b4-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f58b4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f58b4-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f58b4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f58b4-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f58b4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f58b4-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f58b4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58b4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f58b4-124">See also</span></span>
- [<span data-ttu-id="f58b4-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f58b4-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f58b4-126">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f58b4-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
