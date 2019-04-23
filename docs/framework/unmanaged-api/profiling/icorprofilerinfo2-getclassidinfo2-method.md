---
title: ICorProfilerInfo2::GetClassIDInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b98746be189e211572e5517aac1f06825973b39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168872"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="84871-102">ICorProfilerInfo2::GetClassIDInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84871-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="84871-103">Meta verileri ve üst modül için belirtilen sınıf, açık genel tanımını belirtecini alır `ClassID` kendi üst sınıfın ve `ClassID` her tür bağımsız değişkeni, sınıfın varsa.</span><span class="sxs-lookup"><span data-stu-id="84871-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84871-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84871-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84871-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84871-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="84871-106">[in] Bilgileri alınır sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="84871-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="84871-107">[out] Belirtilen sınıfın açık genel tanımının üst modül kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84871-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="84871-108">[out] Meta veri belirteci açık genel belirtilen sınıf tanımına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84871-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="84871-109">[out] Üst sınıf kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84871-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="84871-110">[in] Boyutu `typeArgs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="84871-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="84871-111">[out] Kullanılabilir öğeleri toplam sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84871-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="84871-112">[out] Bir dizi `ClassID` değerler, her biri bir tür bağımsız değişkeni sınıfın Kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84871-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="84871-113">Yöntem döndürüldüğünde `typeArgs` bazı veya tüm kullanılabilir içerecek `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="84871-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84871-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84871-114">Remarks</span></span>  
 <span data-ttu-id="84871-115">`GetClassIDInfo2` Yöntemi benzer [Icorprofilerınfo::getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemi, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="84871-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="84871-116">Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) almak için bir [meta verileri](../../../../docs/framework/unmanaged-api/metadata/index.md) belirli bir modül için arabirim.</span><span class="sxs-lookup"><span data-stu-id="84871-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="84871-117">Tarafından başvurulan konuma döndürülen meta veri belirteci `pTypeDefToken` sınıfı için meta veriler erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84871-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="84871-118">Sonra `GetClassIDInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="84871-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="84871-119">Bunu yapmak için değeri ile karşılaştırmak, `pcNumTypeArgs` değeriyle işaret `cNumTypeArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="84871-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="84871-120">Varsa `pcNumTypeArgs` işaret değerinden daha büyük bir değere `cNumTypeArgs`, daha büyük bir ayırma `typeArgs` arabellek, güncelleştirme `cNumTypeArgs` yeni, daha büyük bir boyut ve çağrı `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="84871-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="84871-121">Alternatif olarak, ilk çağırabilirsiniz `GetClassIDInfo2` sıfır uzunluklu ile `typeArgs` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="84871-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="84871-122">Ardından ayarlayabilirsiniz `typeArgs` arabellek boyutu döndürülen değere `pcNumTypeArgs` ve çağrı `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="84871-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84871-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84871-123">Requirements</span></span>  
 <span data-ttu-id="84871-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84871-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84871-125">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84871-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84871-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84871-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84871-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84871-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84871-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84871-128">See also</span></span>

- [<span data-ttu-id="84871-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84871-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="84871-130">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84871-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="84871-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="84871-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="84871-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="84871-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
