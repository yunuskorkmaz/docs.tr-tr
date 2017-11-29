---
title: ICorProfilerInfo2::GetFunctionInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b0c288b88c868bc6e324ec57b3956344f03f34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="20ec7-102">ICorProfilerInfo2::GetFunctionInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="20ec7-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="20ec7-103">Üst sınıf, meta veri simgesi alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkenin.</span><span class="sxs-lookup"><span data-stu-id="20ec7-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ec7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20ec7-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="20ec7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20ec7-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="20ec7-106">[in] Üst sınıf ve diğer bilgileri almak üzere işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="20ec7-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="20ec7-107">[in] A `COR_PRF_FRAME_INFO` noktalarını yığın çerçevesi hakkında bilgi için değer.</span><span class="sxs-lookup"><span data-stu-id="20ec7-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="20ec7-108">[out] İşlev üst sınıfı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20ec7-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="20ec7-109">[out] İşlevin üst sınıf tanımlandığı modül için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20ec7-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="20ec7-110">[out] İşlev için meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20ec7-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="20ec7-111">[in] Boyutunu `typeArgs` dizi.</span><span class="sxs-lookup"><span data-stu-id="20ec7-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="20ec7-112">[out] Toplam sayısını gösteren bir işaretçi `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="20ec7-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="20ec7-113">[out] Bir dizi `ClassID` değerleri, her biri kimliğidir işlevinin tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="20ec7-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="20ec7-114">Yöntem döndüğünde `typeArgs` bazılarını veya tümünü içerecek `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="20ec7-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20ec7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20ec7-115">Remarks</span></span>  
 <span data-ttu-id="20ec7-116">Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) elde etmek için bir [meta veri](../../../../docs/framework/unmanaged-api/metadata/index.md) verilen modülü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="20ec7-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="20ec7-117">Tarafından başvurulan konuma döndürülen meta veri simgesi `pToken` işlevi için meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20ec7-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="20ec7-118">Aracılığıyla döndürülen sınıfı kimliği ve tür bağımsız değişkenleri `pClassId` ve `typeArgs` geçirilen değer parametreleri bağlı `frameInfo` aşağıdaki tabloda gösterildiği gibi parametre.</span><span class="sxs-lookup"><span data-stu-id="20ec7-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="20ec7-119">Değeri `frameInfo` parametresi</span><span class="sxs-lookup"><span data-stu-id="20ec7-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="20ec7-120">Sonuç</span><span class="sxs-lookup"><span data-stu-id="20ec7-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="20ec7-121">A `COR_PRF_FRAME_INFO` uygulamasından edinilen değeri bir `FunctionEnter2` geri çağırma</span><span class="sxs-lookup"><span data-stu-id="20ec7-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="20ec7-122">`ClassID`, Döndürülen başvurduğu konumda `pClassId`, ve tüm tür bağımsız değişkenleri, döndürülen `typeArgs` dizisi, tam olacaktır.</span><span class="sxs-lookup"><span data-stu-id="20ec7-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="20ec7-123">A `COR_PRF_FRAME_INFO` , elde bir kaynaktan dışındaki bir `FunctionEnter2` geri çağırma</span><span class="sxs-lookup"><span data-stu-id="20ec7-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="20ec7-124">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="20ec7-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="20ec7-125">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="20ec7-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="20ec7-126">Sıfır</span><span class="sxs-lookup"><span data-stu-id="20ec7-126">Zero</span></span>|<span data-ttu-id="20ec7-127">Tam `ClassID` ve tür bağımsız değişkenleri belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="20ec7-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="20ec7-128">Diğer bir deyişle, `ClassID` null olabilir ve bazı tür bağımsız değişkenleri gelebilir olarak geri <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="20ec7-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="20ec7-129">Sonra `GetFunctionInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="20ec7-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="20ec7-130">Bunu yapmak için değeri karşılaştırın, `pcTypeArgs` değeriyle işaret `cTypeArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="20ec7-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="20ec7-131">Varsa `pcTypeArgs` işaret eden daha büyük bir değere `cTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri, daha geniş bir ayırma `pcTypeArgs` arabellek, güncelleştirme `cTypeArgs` yeni, büyük boyutu ve çağrı `GetFunctionInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="20ec7-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="20ec7-132">Alternatif olarak, ilk çağırabilirsiniz `GetFunctionInfo2` sıfır uzunluklu ile `pcTypeArgs` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="20ec7-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="20ec7-133">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcTypeArgs` boyutu tarafından ayrılmış bir `ClassID` değeri ve çağrı `GetFunctionInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="20ec7-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ec7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20ec7-134">Requirements</span></span>  
 <span data-ttu-id="20ec7-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20ec7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ec7-136">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20ec7-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20ec7-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20ec7-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20ec7-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ec7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ec7-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20ec7-139">See Also</span></span>  
 [<span data-ttu-id="20ec7-140">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="20ec7-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="20ec7-141">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="20ec7-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="20ec7-142">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="20ec7-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="20ec7-143">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="20ec7-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
