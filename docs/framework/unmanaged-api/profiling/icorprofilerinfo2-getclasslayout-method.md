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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dcb9d5b3f1f47d6613be90f181a98ce991f697a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134854"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="3b893-102">ICorProfilerInfo2::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="3b893-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="3b893-103">Belirtilen sınıf tarafından tanımlanan alanların bellekte Düzen hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="3b893-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="3b893-104">Diğer bir deyişle, bu yöntem, sınıfın alanlarının uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="3b893-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b893-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b893-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b893-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b893-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="3b893-107">[in] Düzen alınacak sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="3b893-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="3b893-108">[out içinde] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları belirteçleri ve ofsetleri sınıfın alanlarının her biri içerir.</span><span class="sxs-lookup"><span data-stu-id="3b893-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="3b893-109">[in] Boyutu `rFieldOffset` dizisi.</span><span class="sxs-lookup"><span data-stu-id="3b893-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="3b893-110">[out] Kullanılabilir öğeleri toplam sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3b893-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="3b893-111">Varsa `cFieldOffset` 0'dır, bu değer gerekli öğelerin sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b893-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="3b893-112">[out] Sınıf bayt cinsinden boyutunu içeren bir konum için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3b893-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b893-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b893-113">Remarks</span></span>  
 <span data-ttu-id="3b893-114">`GetClassLayout` Yöntemi yalnızca sınıfı tarafından tanımlanan alanları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b893-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="3b893-115">Sınıfının üst sınıfı alanlar da tanımlanmışsa, profil oluşturucu çağırmanız gerekir `GetClassLayout` alanlarla elde etmek için üst sınıfta.</span><span class="sxs-lookup"><span data-stu-id="3b893-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="3b893-116">Kullanırsanız `GetClassLayout` dize sınıflarıyla yöntemi E_INVALIDARG hata koduyla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3b893-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="3b893-117">Kullanım [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) bir dizenin düzeni hakkında bilgi almak için.</span><span class="sxs-lookup"><span data-stu-id="3b893-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> `GetClassLayout` <span data-ttu-id="3b893-118">Ayrıca bir dizi sınıfıyla çağrıldığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3b893-118">will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="3b893-119">Sonra `GetClassLayout` döndürür, doğrulamalısınız `rFieldOffset` arabellek kullanılabilir tüm içerecek şekilde büyük `COR_FIELD_OFFSET` yapıları.</span><span class="sxs-lookup"><span data-stu-id="3b893-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="3b893-120">Bunu yapmak için değeri ile karşılaştırmak, `pcFieldOffset` işaret boyutu ile `rFieldOffset` boyutu tarafından ayrılmış bir `COR_FIELD_OFFSET` yapısı.</span><span class="sxs-lookup"><span data-stu-id="3b893-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="3b893-121">Varsa `rFieldOffset` büyük değil yeterince büyük bir ayırma `rFieldOffset` arabellek, güncelleştirme `cFieldOffset` yeni, daha büyük bir boyut ve çağrı `GetClassLayout` yeniden.</span><span class="sxs-lookup"><span data-stu-id="3b893-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="3b893-122">Alternatif olarak, ilk çağırabilirsiniz `GetClassLayout` sıfır uzunluklu ile `rFieldOffset` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="3b893-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="3b893-123">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcFieldOffset` ve çağrı `GetClassLayout` yeniden.</span><span class="sxs-lookup"><span data-stu-id="3b893-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b893-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b893-124">Requirements</span></span>  
 <span data-ttu-id="3b893-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b893-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b893-126">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b893-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b893-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b893-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3b893-128">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3b893-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b893-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b893-129">See also</span></span>

- [<span data-ttu-id="3b893-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b893-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3b893-131">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b893-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="3b893-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3b893-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3b893-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b893-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
