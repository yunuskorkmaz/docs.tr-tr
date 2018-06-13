---
title: ICorProfilerInfo2::GetClassIDInfo2 Metodu
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
ms.openlocfilehash: 2af0eacbff8220be7f2286f7f345f14126972261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458529"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="a58c9-102">ICorProfilerInfo2::GetClassIDInfo2 Metodu</span><span class="sxs-lookup"><span data-stu-id="a58c9-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="a58c9-103">Meta verileri ve üst modül için belirtilen sınıfın açık genel tanımını belirtecini alır `ClassID` kendi üst sınıfın ve `ClassID` sınıfının varsa, her türü değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a58c9-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a58c9-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a58c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a58c9-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a58c9-106">[in] Bilgiler alınır sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="a58c9-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="a58c9-107">[out] Belirtilen sınıf açık genel tanımı için üst modülü Kimliğini işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a58c9-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="a58c9-108">[out] Belirtilen sınıf açık genel tanımı için meta veri simgesi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a58c9-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="a58c9-109">[out] Üst sınıf kimliği için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a58c9-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="a58c9-110">[in] Boyutunu `typeArgs` dizi.</span><span class="sxs-lookup"><span data-stu-id="a58c9-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="a58c9-111">[out] İşaretçi kullanılabilir öğelerin toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="a58c9-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="a58c9-112">[out] Bir dizi `ClassID` değerleri, her biri bir tür bağımsız değişkeni sınıfının Kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a58c9-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="a58c9-113">Yöntem döndüğünde `typeArgs` bazı veya tüm kullanılabilir içerecek `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="a58c9-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a58c9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a58c9-114">Remarks</span></span>  
 <span data-ttu-id="a58c9-115">`GetClassIDInfo2` Yöntemi benzer [Icorprofilerınfo::getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemi, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="a58c9-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="a58c9-116">Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) elde etmek için bir [meta veri](../../../../docs/framework/unmanaged-api/metadata/index.md) verilen modülü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="a58c9-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="a58c9-117">Tarafından başvurulan konuma döndürülen meta veri simgesi `pTypeDefToken` sınıfı için meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a58c9-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="a58c9-118">Sonra `GetClassIDInfo2` döndürür, doğrulamalısınız `typeArgs` arabellek tüm içerecek şekilde büyük `ClassID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="a58c9-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="a58c9-119">Bunu yapmak için değeri karşılaştırın, `pcNumTypeArgs` değeriyle işaret `cNumTypeArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a58c9-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="a58c9-120">Varsa `pcNumTypeArgs` işaret eden daha büyük bir değere `cNumTypeArgs`, daha geniş bir ayırma `typeArgs` arabellek, güncelleştirme `cNumTypeArgs` yeni, büyük boyutu ve çağrı `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="a58c9-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="a58c9-121">Alternatif olarak, ilk çağırabilirsiniz `GetClassIDInfo2` sıfır uzunluklu ile `typeArgs` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="a58c9-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a58c9-122">Ardından ayarlayabilirsiniz `typeArgs` arabellek boyutu için döndürülen değer `pcNumTypeArgs` ve arama `GetClassIDInfo2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="a58c9-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58c9-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a58c9-123">Requirements</span></span>  
 <span data-ttu-id="a58c9-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a58c9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58c9-125">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a58c9-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a58c9-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58c9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58c9-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58c9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58c9-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a58c9-128">See Also</span></span>  
 [<span data-ttu-id="a58c9-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a58c9-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a58c9-130">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a58c9-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="a58c9-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a58c9-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a58c9-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a58c9-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
