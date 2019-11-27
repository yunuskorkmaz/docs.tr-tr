---
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
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433183"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="19264-102">ICorProfilerInfo2::GetFunctionInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19264-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="19264-103">Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve her tür bağımsız değişkeninin `ClassID` alır.</span><span class="sxs-lookup"><span data-stu-id="19264-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19264-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19264-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="19264-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19264-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="19264-106">'ndaki Üst sınıfı ve diğer bilgileri almak için işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="19264-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="19264-107">'ndaki Yığın çerçevesi hakkındaki bilgileri gösteren `COR_PRF_FRAME_INFO` değeri.</span><span class="sxs-lookup"><span data-stu-id="19264-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="19264-108">dışı İşlevin üst sınıfına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19264-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="19264-109">dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19264-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="19264-110">dışı İşlevin meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19264-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="19264-111">'ndaki `typeArgs` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="19264-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="19264-112">dışı `ClassID` değerlerinin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19264-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="19264-113">dışı Her biri işlevin tür bağımsız değişkeninin KIMLIĞI olan `ClassID` değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="19264-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="19264-114">Yöntemi döndürüldüğünde, `typeArgs` `ClassID` değerlerinin bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="19264-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19264-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19264-115">Remarks</span></span>  
 <span data-ttu-id="19264-116">Profil Oluşturucu kodu, belirli bir modül için [meta](../../../../docs/framework/unmanaged-api/metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="19264-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="19264-117">`pToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra işlevin meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19264-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="19264-118">`pClassId` ve `typeArgs` parametreleri aracılığıyla döndürülen sınıf KIMLIĞI ve tür bağımsız değişkenleri, aşağıdaki tabloda gösterildiği gibi `frameInfo` parametresine geçirilen değere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="19264-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="19264-119">`frameInfo` parametresinin değeri</span><span class="sxs-lookup"><span data-stu-id="19264-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="19264-120">Sonuç</span><span class="sxs-lookup"><span data-stu-id="19264-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="19264-121">`FunctionEnter2` geri çağrısından alınan `COR_PRF_FRAME_INFO` değeri</span><span class="sxs-lookup"><span data-stu-id="19264-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="19264-122">`pClassId`tarafından başvurulan konumda döndürülen `ClassID`ve `typeArgs` dizisinde döndürülen tüm tür bağımsız değişkenleri, tam olarak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="19264-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="19264-123">`FunctionEnter2` geri çağırma dışında bir kaynaktan alınan `COR_PRF_FRAME_INFO`</span><span class="sxs-lookup"><span data-stu-id="19264-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="19264-124">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="19264-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="19264-125">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri <xref:System.Object>olarak geri gelebilir.</span><span class="sxs-lookup"><span data-stu-id="19264-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="19264-126">Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="19264-126">Zero</span></span>|<span data-ttu-id="19264-127">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="19264-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="19264-128">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri <xref:System.Object>olarak geri gelebilir.</span><span class="sxs-lookup"><span data-stu-id="19264-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="19264-129">`GetFunctionInfo2` çağrıldıktan sonra, `typeArgs` arabelleğinin tüm `ClassID` değerlerini içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19264-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="19264-130">Bunu yapmak için `pcTypeArgs` işaret eden değeri `cTypeArgs` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="19264-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="19264-131">`pcTypeArgs`, bir `ClassID` değerin boyutuyla `cTypeArgs` daha büyük bir değere işaret ediyorsa, daha büyük bir `pcTypeArgs` arabelleği ayırın, yeni, daha büyük boyuttaki `cTypeArgs` güncelleştirin ve `GetFunctionInfo2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="19264-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="19264-132">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetFunctionInfo2` sıfır uzunluklu `pcTypeArgs` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19264-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="19264-133">Daha sonra arabellek boyutunu `ClassID` değerinin boyutuna bölünen `pcTypeArgs` içinde döndürülen değere ayarlayabilirsiniz ve `GetFunctionInfo2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="19264-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19264-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19264-134">Requirements</span></span>  
 <span data-ttu-id="19264-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19264-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19264-136">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="19264-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19264-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19264-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19264-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19264-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19264-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19264-139">See also</span></span>

- [<span data-ttu-id="19264-140">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19264-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="19264-141">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19264-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="19264-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19264-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="19264-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="19264-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
