---
title: ICorProfilerInfo2::GetClassIDInfo2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassIDInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bfa970acd21a518112dd6ee9228b621758e49f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="0c8fe-102">ICorProfilerInfo2::GetClassIDInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="0c8fe-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="0c8fe-103">Meta verileri ve üst modül için belirtilen sınıfın açık genel tanımını belirtecini alır `ClassID` kendi üst sınıfın ve `ClassID` sınıfının varsa, her türü değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c8fe-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0c8fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c8fe-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0c8fe-106">[in] Bilgiler alınır sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0c8fe-107">[out] Belirtilen sınıf açık genel tanımı için üst modülü Kimliğini işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="0c8fe-108">[out] Belirtilen sınıf açık genel tanımı için meta veri simgesi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="0c8fe-109">[out] Üst sınıf kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="0c8fe-110">[in] Boyutunu `typeArgs` dizi.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="0c8fe-111">[out] İşaretçi kullanılabilir öğelerin toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="0c8fe-112">[out] Bir dizi `ClassID` değerleri, her biri bir tür bağımsız değişkeni sınıfının Kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="0c8fe-113">Yöntem döndüğünde `typeArgs` bazı veya tüm kullanılabilir içerecek `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c8fe-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c8fe-114">Remarks</span></span>  
 <span data-ttu-id="0c8fe-115">`GetClassIDInfo2` Yöntemi benzer [Icorprofilerınfo::getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemi, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="0c8fe-116">Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) elde etmek için bir [meta veri](../../../../docs/framework/unmanaged-api/metadata/index.md) verilen modülü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="0c8fe-117">Tarafından başvurulan konuma döndürülen meta veri simgesi `pTypeDefToken` sınıfı için meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="0c8fe-118">Sonra `GetClassIDInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="0c8fe-119">Bunu yapmak için değeri karşılaştırın, `pcNumTypeArgs` değeriyle işaret `cNumTypeArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="0c8fe-120">Varsa `pcNumTypeArgs` işaret eden daha büyük bir değere `cNumTypeArgs`, daha geniş bir ayırma `typeArgs` arabellek, güncelleştirme `cNumTypeArgs` yeni, büyük boyutu ve çağrı `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="0c8fe-121">Alternatif olarak, ilk çağırabilirsiniz `GetClassIDInfo2` sıfır uzunluklu ile `typeArgs` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0c8fe-122">Ardından ayarlayabilirsiniz `typeArgs` arabellek boyutu için döndürülen değer `pcNumTypeArgs` ve arama `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8fe-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c8fe-123">Requirements</span></span>  
 <span data-ttu-id="0c8fe-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8fe-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8fe-125">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c8fe-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c8fe-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c8fe-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8fe-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8fe-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8fe-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8fe-128">See Also</span></span>  
 [<span data-ttu-id="0c8fe-129">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8fe-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="0c8fe-130">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8fe-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="0c8fe-131">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c8fe-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="0c8fe-132">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c8fe-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
