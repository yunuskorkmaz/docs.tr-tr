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
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497172"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="f45ff-102">ICorProfilerInfo2::GetClassIDInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f45ff-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="f45ff-103">Belirtilen sınıfın açık genel tanımının, `ClassID` üst sınıfının ve varsa `ClassID` sınıfının her tür bağımsız değişkeni için üst modülü ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f45ff-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f45ff-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f45ff-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f45ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f45ff-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="f45ff-106">'ndaki Bilgilerin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f45ff-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f45ff-107">dışı Belirtilen sınıfın açık genel tanımının üst modülünün KIMLIĞINE yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f45ff-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="f45ff-108">dışı Belirtilen sınıfın açık genel tanımı için meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f45ff-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="f45ff-109">dışı Üst sınıfın KIMLIĞINE yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f45ff-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="f45ff-110">'ndaki `typeArgs`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f45ff-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="f45ff-111">dışı Kullanılabilir öğelerin toplam sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f45ff-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f45ff-112">dışı `ClassID`Her biri sınıfının bir tür bağımsız DEĞIŞKENININ kimliğini temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="f45ff-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="f45ff-113">Yöntemi döndüğünde, `typeArgs` kullanılabilir değerlerin bazılarını veya tümünü içerecektir `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="f45ff-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f45ff-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f45ff-114">Remarks</span></span>  
 <span data-ttu-id="f45ff-115">`GetClassIDInfo2`Yöntemi [ICorProfilerInfo:: GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) yöntemine benzer, ancak `GetClassIDInfo2` genel bir tür hakkında ek bilgiler edinir.</span><span class="sxs-lookup"><span data-stu-id="f45ff-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="f45ff-116">Profil Oluşturucu kodu, belirli bir modül için [meta](../metadata/index.md) veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f45ff-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="f45ff-117">Tarafından başvurulan konuma döndürülen meta veri belirteci, `pTypeDefToken` daha sonra sınıfının meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f45ff-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="f45ff-118">`GetClassIDInfo2`Geri döndüğünde, `typeArgs` arabelleğin tüm değerleri içerecek kadar büyük olduğunu doğrulamanız gerekir `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="f45ff-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="f45ff-119">Bunu yapmak için, işaret eden değeri `pcNumTypeArgs` parametresinin değeriyle karşılaştırın `cNumTypeArgs` .</span><span class="sxs-lookup"><span data-stu-id="f45ff-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="f45ff-120">Daha `pcNumTypeArgs` büyük bir değere işaret ediyorsa `cNumTypeArgs` , daha büyük bir `typeArgs` arabellek ayırır, `cNumTypeArgs` Yeni, daha büyük boyutla güncelleştirin ve `GetClassIDInfo2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="f45ff-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="f45ff-121">Alternatif olarak, `GetClassIDInfo2` `typeArgs` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f45ff-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f45ff-122">Daha sonra `typeArgs` arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcNumTypeArgs` ve `GetClassIDInfo2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f45ff-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f45ff-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f45ff-123">Requirements</span></span>  
 <span data-ttu-id="f45ff-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f45ff-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f45ff-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f45ff-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f45ff-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f45ff-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f45ff-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f45ff-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45ff-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f45ff-128">See also</span></span>

- [<span data-ttu-id="f45ff-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f45ff-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f45ff-130">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f45ff-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="f45ff-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f45ff-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f45ff-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f45ff-132">Profiling</span></span>](index.md)
