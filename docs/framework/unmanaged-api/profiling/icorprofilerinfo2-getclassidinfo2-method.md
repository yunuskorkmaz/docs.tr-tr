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
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433428"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="f89e3-102">ICorProfilerInfo2::GetClassIDInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f89e3-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="f89e3-103">Belirtilen sınıfın açık genel tanımına, üst sınıfının `ClassID` ve varsa sınıfının her bir tür bağımsız değişkeni için `ClassID` ait üst modülü ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f89e3-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f89e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f89e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f89e3-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="f89e3-106">'ndaki Bilgilerin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f89e3-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f89e3-107">dışı Belirtilen sınıfın açık genel tanımının üst modülünün KIMLIĞINE yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f89e3-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="f89e3-108">dışı Belirtilen sınıfın açık genel tanımı için meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f89e3-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="f89e3-109">dışı Üst sınıfın KIMLIĞINE yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f89e3-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="f89e3-110">'ndaki `typeArgs` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f89e3-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="f89e3-111">dışı Kullanılabilir öğelerin toplam sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f89e3-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f89e3-112">dışı Her biri sınıfının bir tür bağımsız değişkeninin KIMLIĞINI temsil eden `ClassID` değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f89e3-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="f89e3-113">Yöntemi döndürüldüğünde `typeArgs`, kullanılabilir `ClassID` değerlerinin bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="f89e3-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f89e3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f89e3-114">Remarks</span></span>  
 <span data-ttu-id="f89e3-115">`GetClassIDInfo2` yöntemi [ICorProfilerInfo:: GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) yöntemine benzer, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgiler elde eder.</span><span class="sxs-lookup"><span data-stu-id="f89e3-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="f89e3-116">Profil Oluşturucu kodu, belirli bir modül için [meta](../../../../docs/framework/unmanaged-api/metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f89e3-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="f89e3-117">`pTypeDefToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra sınıfının meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f89e3-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="f89e3-118">`GetClassIDInfo2` çağrıldıktan sonra, `typeArgs` arabelleğinin tüm `ClassID` değerlerini içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f89e3-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="f89e3-119">Bunu yapmak için `pcNumTypeArgs` işaret eden değeri `cNumTypeArgs` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f89e3-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="f89e3-120">`pcNumTypeArgs`, `cNumTypeArgs`daha büyük bir değere işaret ediyorsa, daha büyük bir `typeArgs` arabelleği ayırın, yeni, daha büyük boyuttaki `cNumTypeArgs` güncelleştirin ve `GetClassIDInfo2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="f89e3-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="f89e3-121">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetClassIDInfo2` sıfır uzunluklu `typeArgs` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f89e3-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f89e3-122">Daha sonra `typeArgs` arabellek boyutunu `pcNumTypeArgs` döndürülen değere ayarlayabilir ve `GetClassIDInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f89e3-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f89e3-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f89e3-123">Requirements</span></span>  
 <span data-ttu-id="f89e3-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f89e3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f89e3-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f89e3-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f89e3-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f89e3-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f89e3-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f89e3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89e3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f89e3-128">See also</span></span>

- [<span data-ttu-id="f89e3-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f89e3-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f89e3-130">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f89e3-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="f89e3-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f89e3-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f89e3-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f89e3-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
