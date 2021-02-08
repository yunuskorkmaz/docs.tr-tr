---
description: ': ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4b4bb8631a5f33c939666af68226b19d2e4d666d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799044"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="e805f-103">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Metodu</span><span class="sxs-lookup"><span data-stu-id="e805f-103">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="e805f-104">`FunctionID`Belirtilen meta veri belirtecini, sınıfını ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="e805f-104">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e805f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e805f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e805f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e805f-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="e805f-107">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e805f-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="e805f-108">'ndaki `mdMethodDef` İşleve başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e805f-108">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="e805f-109">'ndaki İşlevin kapsayan sınıfının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e805f-109">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="e805f-110">'ndaki Verilen işlev için tür parametrelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="e805f-110">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="e805f-111">Bu değer, genel olmayan işlevler için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e805f-111">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="e805f-112">'ndaki `ClassID` Her biri işlevin bağımsız değişkeni olan bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="e805f-112">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="e805f-113">`typeArgs` `cTypeArgs` Sıfır olarak AYARLANDıYSA değeri null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e805f-113">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="e805f-114">dışı `FunctionID` Belirtilen işlevin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e805f-114">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e805f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e805f-115">Remarks</span></span>  

 <span data-ttu-id="e805f-116">`GetFunctionFromTokenAndTypeArgs`Yöntemi `mdMethodRef` meta veri belirteci yerine meta verilerle çağırmak `mdMethodDef` öngörülemeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e805f-116">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="e805f-117">Çağıranlar, `mdMethodRef` geçişini yaparken öğesine çözmelidir `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="e805f-117">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="e805f-118">İşlev zaten yüklü değilse, çağırma, `GetFunctionFromTokenAndTypeArgs` çok sayıda bağlamda tehlikeli bir işlem olan yüklemenin oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e805f-118">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="e805f-119">Örneğin, modül veya tür yükleme sırasında bu yöntemi çağırmak, çalışma zamanı döngüsel olarak yükleme yapmayı denediğinde sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e805f-119">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="e805f-120">Genel olarak, kullanımı `GetFunctionFromTokenAndTypeArgs` önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e805f-120">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="e805f-121">Profil oluşturucular belirli bir işlev için olaylar ile ilgileniyorsa, `ModuleID` `mdMethodDef` Bu işlevin ve bu işlevi depolamalıdır ve [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) kullanarak belirli bir işlevin istenen işlevden olup olmadığını denetler `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="e805f-121">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e805f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e805f-122">Requirements</span></span>  

 <span data-ttu-id="e805f-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e805f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e805f-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e805f-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e805f-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e805f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e805f-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e805f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e805f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e805f-127">See also</span></span>

- [<span data-ttu-id="e805f-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e805f-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e805f-129">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e805f-129">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
