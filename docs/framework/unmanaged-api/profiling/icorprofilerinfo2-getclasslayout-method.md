---
title: ICorProfilerInfo2::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433398"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="9dd90-102">ICorProfilerInfo2::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="9dd90-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="9dd90-103">Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="9dd90-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="9dd90-104">Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.</span><span class="sxs-lookup"><span data-stu-id="9dd90-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd90-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dd90-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dd90-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="9dd90-107">'ndaki Düzenin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9dd90-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="9dd90-108">[in, out] Her biri sınıfın alanlarının belirteçlerini ve farklarını içeren [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapılarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="9dd90-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="9dd90-109">'ndaki `rFieldOffset` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="9dd90-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="9dd90-110">dışı Kullanılabilir öğelerin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9dd90-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="9dd90-111">`cFieldOffset` 0 ise, bu değer gerekli öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd90-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="9dd90-112">dışı Sınıfının bayt cinsinden boyutunu içeren konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9dd90-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dd90-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dd90-113">Remarks</span></span>  
 <span data-ttu-id="9dd90-114">`GetClassLayout` yöntemi yalnızca sınıfın kendisi tarafından tanımlanan alanları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd90-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="9dd90-115">Sınıfın üst sınıfı da tanımlı alanlar içeriyorsa, bu alanları almak için profil oluşturucunun üst sınıfta `GetClassLayout` çağrısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dd90-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="9dd90-116">Dize sınıfları ile `GetClassLayout` kullanıyorsanız, yöntem E_INVALIDARG hata kodu ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9dd90-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="9dd90-117">Bir dizenin düzeni hakkında bilgi almak için [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dd90-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="9dd90-118">`GetClassLayout`, bir dizi sınıfıyla çağrıldığında de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9dd90-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="9dd90-119">`GetClassLayout` çağrıldıktan sonra, `rFieldOffset` arabelleğinin tüm kullanılabilir `COR_FIELD_OFFSET` yapılarını içermesi için yeterince büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dd90-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="9dd90-120">Bunu yapmak için `pcFieldOffset` işaret eden değeri, `rFieldOffset` boyutuyla `COR_FIELD_OFFSET` yapısına bölünmüş şekilde karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="9dd90-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="9dd90-121">`rFieldOffset` yeterince büyük değilse, daha büyük bir `rFieldOffset` arabelleği ayırın, yeni, daha büyük boyuttaki `cFieldOffset` güncelleştirin ve `GetClassLayout` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="9dd90-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="9dd90-122">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetClassLayout` sıfır uzunluklu `rFieldOffset` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dd90-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9dd90-123">Daha sonra arabellek boyutunu `pcFieldOffset` döndürülen değere ayarlayabilir ve `GetClassLayout` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dd90-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd90-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dd90-124">Requirements</span></span>  
 <span data-ttu-id="9dd90-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd90-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd90-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9dd90-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9dd90-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9dd90-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dd90-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd90-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd90-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd90-129">See also</span></span>

- [<span data-ttu-id="9dd90-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dd90-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="9dd90-131">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dd90-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="9dd90-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9dd90-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9dd90-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dd90-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
