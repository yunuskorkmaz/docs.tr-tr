---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: Getfunctionınfo2 yöntemi'
title: ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: f0534a2e8cc8a9ce24f2c2b3deaade6215e15b5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657079"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="74c54-103">ICorProfilerInfo2::GetFunctionInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74c54-103">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>

<span data-ttu-id="74c54-104">Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve `ClassID` her tür bağımsız değişkenini alır.</span><span class="sxs-lookup"><span data-stu-id="74c54-104">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c54-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74c54-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c54-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74c54-106">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="74c54-107">'ndaki Üst sınıfı ve diğer bilgileri almak için işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="74c54-107">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="74c54-108">'ndaki `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgileri gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="74c54-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="74c54-109">dışı İşlevin üst sınıfına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74c54-109">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="74c54-110">dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74c54-110">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="74c54-111">dışı İşlevin meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74c54-111">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="74c54-112">'ndaki `typeArgs` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="74c54-112">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="74c54-113">dışı Toplam değer sayısına yönelik bir işaretçi `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="74c54-113">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="74c54-114">dışı `ClassID` Her biri işlevin tür bağımsız DEĞIŞKENININ kimliği olan bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="74c54-114">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="74c54-115">Yöntemi döndürüldüğünde, `typeArgs` değerlerin bazılarını veya tümünü içerecektir `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="74c54-115">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74c54-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74c54-116">Remarks</span></span>  

 <span data-ttu-id="74c54-117">Profil Oluşturucu kodu, belirli bir modül için [meta](../metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="74c54-117">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="74c54-118">Tarafından başvurulan konuma döndürülen meta veri belirteci, `pToken` daha sonra işlevin meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74c54-118">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="74c54-119">Ve parametreleri aracılığıyla döndürülen sınıf KIMLIĞI ve tür bağımsız değişkenleri, `pClassId` `typeArgs` `frameInfo` Aşağıdaki tabloda gösterildiği gibi, parametresine geçirilen değere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74c54-119">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="74c54-120">`frameInfo`Parametrenin değeri</span><span class="sxs-lookup"><span data-stu-id="74c54-120">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="74c54-121">Sonuç</span><span class="sxs-lookup"><span data-stu-id="74c54-121">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="74c54-122">`COR_PRF_FRAME_INFO`Bir geri aramadan alınan bir değer `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="74c54-122">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="74c54-123">`ClassID`Tarafından başvurulan konumda döndürülen, `pClassId` ve dizide döndürülen tüm tür bağımsız değişkenleri `typeArgs` tam olarak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="74c54-123">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="74c54-124">`COR_PRF_FRAME_INFO`Geri çağırma dışında bir kaynaktan alınan bir `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="74c54-124">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="74c54-125">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="74c54-125">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="74c54-126">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri yeniden gelebilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="74c54-126">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="74c54-127">Sıfır</span><span class="sxs-lookup"><span data-stu-id="74c54-127">Zero</span></span>|<span data-ttu-id="74c54-128">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="74c54-128">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="74c54-129">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri yeniden gelebilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="74c54-129">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="74c54-130">`GetFunctionInfo2`Geri döndüğünde, `typeArgs` arabelleğin tüm değerleri içerecek kadar büyük olduğunu doğrulamanız gerekir `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="74c54-130">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="74c54-131">Bunu yapmak için, işaret eden değeri `pcTypeArgs` parametresinin değeriyle karşılaştırın `cTypeArgs` .</span><span class="sxs-lookup"><span data-stu-id="74c54-131">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="74c54-132">`pcTypeArgs`Değerin boyutuyla daha büyük bir değere işaret ediyorsa `cTypeArgs` `ClassID` , daha büyük bir `pcTypeArgs` arabellek ayırır, `cTypeArgs` Yeni, daha büyük boyutla güncelleştirin ve `GetFunctionInfo2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="74c54-132">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="74c54-133">Alternatif olarak, `GetFunctionInfo2` `pcTypeArgs` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74c54-133">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="74c54-134">Daha sonra, arabellek boyutunu `pcTypeArgs` bir değer boyutuna bölünen olarak döndürülen değere ayarlayabilir `ClassID` ve `GetFunctionInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74c54-134">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c54-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74c54-135">Requirements</span></span>  

 <span data-ttu-id="74c54-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c54-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c54-137">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74c54-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74c54-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74c54-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74c54-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c54-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c54-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74c54-140">See also</span></span>

- [<span data-ttu-id="74c54-141">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c54-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="74c54-142">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c54-142">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="74c54-143">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74c54-143">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="74c54-144">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74c54-144">Profiling</span></span>](index.md)
