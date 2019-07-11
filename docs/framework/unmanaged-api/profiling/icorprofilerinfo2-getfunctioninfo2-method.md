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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6c45e44f68621708d05ca43857cf1e100113166
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771076"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="dc89d-102">ICorProfilerInfo2::GetFunctionInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc89d-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="dc89d-103">Üst sınıfın, meta veri belirteci alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkeninin.</span><span class="sxs-lookup"><span data-stu-id="dc89d-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc89d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc89d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc89d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc89d-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="dc89d-106">[in] Üst sınıf ve diğer bilgileri almak işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="dc89d-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="dc89d-107">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="dc89d-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="dc89d-108">[out] İşlevin üst sınıfı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="dc89d-109">[out] İşlevin üst sınıfı içinde tanımlandığı modül için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="dc89d-110">[out] Meta veri belirteci işlevine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="dc89d-111">[in] Boyutu `typeArgs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="dc89d-112">[out] Toplam sayısı için bir işaretçi `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="dc89d-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="dc89d-113">[out] Bir dizi `ClassID` değerler, her biri, bir tür bağımsız değişkeni işlevin Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="dc89d-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="dc89d-114">Yöntem döndürüldüğünde `typeArgs` bazılarını veya tümünü içerecektir `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="dc89d-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc89d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc89d-115">Remarks</span></span>  
 <span data-ttu-id="dc89d-116">Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) almak için bir [meta verileri](../../../../docs/framework/unmanaged-api/metadata/index.md) belirli bir modül için arabirim.</span><span class="sxs-lookup"><span data-stu-id="dc89d-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="dc89d-117">Tarafından başvurulan konuma döndürülen meta veri belirteci `pToken` işlevi için meta veriler erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc89d-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="dc89d-118">İle döndürülen sınıf kimliği ve tür bağımsız değişkenleri `pClassId` ve `typeArgs` geçirilen değere bağlıdır parametreleri `frameInfo` parametresi, aşağıdaki tabloda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="dc89d-119">Değeri `frameInfo` parametresi</span><span class="sxs-lookup"><span data-stu-id="dc89d-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="dc89d-120">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dc89d-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="dc89d-121">A `COR_PRF_FRAME_INFO` elde edildiği değeri bir `FunctionEnter2` geri çağırma</span><span class="sxs-lookup"><span data-stu-id="dc89d-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="dc89d-122">`ClassID`, Tarafından başvurulan konumda döndürülen `pClassId`, ve tüm tür bağımsız değişkenleri, döndürülen `typeArgs` dizi, tam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dc89d-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="dc89d-123">A `COR_PRF_FRAME_INFO` , alınan bir kaynaktan dışındaki bir `FunctionEnter2` geri çağırma</span><span class="sxs-lookup"><span data-stu-id="dc89d-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="dc89d-124">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="dc89d-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="dc89d-125">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="dc89d-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="dc89d-126">Sıfır</span><span class="sxs-lookup"><span data-stu-id="dc89d-126">Zero</span></span>|<span data-ttu-id="dc89d-127">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="dc89d-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="dc89d-128">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="dc89d-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="dc89d-129">Sonra `GetFunctionInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="dc89d-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="dc89d-130">Bunu yapmak için değeri ile karşılaştırmak, `pcTypeArgs` değeriyle işaret `cTypeArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="dc89d-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="dc89d-131">Varsa `pcTypeArgs` işaret değerinden daha büyük bir değere `cTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri, daha büyük bir ayırma `pcTypeArgs` arabellek, güncelleştirme `cTypeArgs` yeni, daha büyük bir boyut ve çağrı `GetFunctionInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="dc89d-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="dc89d-132">Alternatif olarak, ilk çağırabilirsiniz `GetFunctionInfo2` sıfır uzunluklu ile `pcTypeArgs` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="dc89d-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="dc89d-133">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri ve çağrı `GetFunctionInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="dc89d-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc89d-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc89d-134">Requirements</span></span>  
 <span data-ttu-id="dc89d-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc89d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc89d-136">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc89d-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc89d-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc89d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc89d-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc89d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc89d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc89d-139">See also</span></span>

- [<span data-ttu-id="dc89d-140">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc89d-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="dc89d-141">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc89d-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="dc89d-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc89d-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="dc89d-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc89d-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
