---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60a9ba78211cd02300cccc7d150bb08fa68b0604
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556187"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="9a4f6-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu</span><span class="sxs-lookup"><span data-stu-id="9a4f6-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="9a4f6-103">Alır `FunctionID` sınıf içeren belirtilen meta veri belirteci kullanarak bir işlevin ve `ClassID` herhangi bir değer türü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a4f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a4f6-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a4f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a4f6-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="9a4f6-106">[in] İşlev bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="9a4f6-107">[in] Bir `mdMethodDef` işlevi başvuran meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="9a4f6-108">[in] Kapsayan işlevin sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="9a4f6-109">[in] Belirtilen işlev için tür parametreleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="9a4f6-110">Bu değer, genel olmayan işlevler için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="9a4f6-111">[in] Bir dizi `ClassID` işlevi bağımsız değişkeninin her biri olan değerleri.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="9a4f6-112">Değerini `typeArgs` NULL olabilir `cTypeArgs` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="9a4f6-113">[out] Bir işaretçi `FunctionID` belirtilen işlevin.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a4f6-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a4f6-114">Remarks</span></span>  
 <span data-ttu-id="9a4f6-115">Çağırma `GetFunctionFromTokenAndTypeArgs` yöntemi ile bir `mdMethodRef` meta verileri yerine bir `mdMethodDef` meta veri belirteci öngörülemeyen sonuçlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="9a4f6-116">Çağıranlar çözümlemelidir `mdMethodRef` için bir `mdMethodDef` iletmeden olduğunda.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="9a4f6-117">İşlev zaten yüklü değilse, çağırma `GetFunctionFromTokenAndTypeArgs` birçok bağlamlarda tehlikeli bir işlemi gerçekleşmesi, yükleme neden olur.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="9a4f6-118">Örneğin, çalışma zamanı, döngüsel olarak şeyler yükleme girişiminde türleri veya modüller yükleme sırasında bu yöntemin çağrılması sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="9a4f6-119">Genel olarak, kullanım `GetFunctionFromTokenAndTypeArgs` önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="9a4f6-120">Profil oluşturucular için belirli bir işleve olaylarda ilgileniyorsanız depolamanız gerekir `ModuleID` ve `mdMethodDef` bu işlevi ve kullanım [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) denetlemek için olup olmadığını bir verilen `FunctionID` olduğu İstenen işlevi.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a4f6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a4f6-121">Requirements</span></span>  
 <span data-ttu-id="9a4f6-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a4f6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a4f6-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a4f6-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a4f6-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a4f6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a4f6-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a4f6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a4f6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a4f6-126">See also</span></span>
- [<span data-ttu-id="9a4f6-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a4f6-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="9a4f6-128">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a4f6-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
