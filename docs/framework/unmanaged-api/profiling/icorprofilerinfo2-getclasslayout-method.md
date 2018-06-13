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
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459159"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="4421b-102">ICorProfilerInfo2::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="4421b-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="4421b-103">Belirtilen sınıf tarafından tanımlanan alanların bellekte düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="4421b-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="4421b-104">Diğer bir deyişle, bu yöntem sınıfın alanları uzaklıklarını alır.</span><span class="sxs-lookup"><span data-stu-id="4421b-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4421b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4421b-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4421b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4421b-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="4421b-107">[in] Düzen alınır sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4421b-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="4421b-108">[içinde out] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları, belirteçleri ve uzaklıkları sınıfının alanlarının her biri içerir.</span><span class="sxs-lookup"><span data-stu-id="4421b-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="4421b-109">[in] Boyutunu `rFieldOffset` dizi.</span><span class="sxs-lookup"><span data-stu-id="4421b-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="4421b-110">[out] Kullanılabilir öğeleri toplam sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4421b-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="4421b-111">Varsa `cFieldOffset` 0'dır, bu değer gerekli öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4421b-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="4421b-112">[out] Sınıfının bayt cinsinden boyutu içeren bir konuma bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4421b-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4421b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4421b-113">Remarks</span></span>  
 <span data-ttu-id="4421b-114">`GetClassLayout` Yöntemi yalnızca sınıf tarafından tanımlanan alanları döndürür.</span><span class="sxs-lookup"><span data-stu-id="4421b-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="4421b-115">Profil Oluşturucu sınıfın üst sınıfı'de alanları tanımlamış ise çağırmalıdır `GetClassLayout` alanlarla elde etmek için üst sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4421b-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="4421b-116">Kullanırsanız `GetClassLayout` dize sınıflarıyla yöntemi E_INVALIDARG hata koduyla başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4421b-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="4421b-117">Kullanım [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) bir dize Düzen hakkında bilgi almak için.</span><span class="sxs-lookup"><span data-stu-id="4421b-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="4421b-118">`GetClassLayout` Ayrıca bir dizi sınıf çağrıldığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4421b-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="4421b-119">Sonra `GetClassLayout` döndürür, doğrulamalısınız `rFieldOffset` arabellek tüm kullanılabilir içerecek şekilde büyük `COR_FIELD_OFFSET` yapıları.</span><span class="sxs-lookup"><span data-stu-id="4421b-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="4421b-120">Bunu yapmak için değeri karşılaştırın, `pcFieldOffset` işaret boyutu ile `rFieldOffset` boyutu tarafından ayrılmış bir `COR_FIELD_OFFSET` yapısı.</span><span class="sxs-lookup"><span data-stu-id="4421b-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="4421b-121">Varsa `rFieldOffset` büyük değil yeterince büyük bir ayırma `rFieldOffset` arabellek, güncelleştirme `cFieldOffset` yeni, büyük boyutu ve çağrı `GetClassLayout` yeniden.</span><span class="sxs-lookup"><span data-stu-id="4421b-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="4421b-122">Alternatif olarak, ilk çağırabilirsiniz `GetClassLayout` sıfır uzunluklu ile `rFieldOffset` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="4421b-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4421b-123">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcFieldOffset` ve arama `GetClassLayout` yeniden.</span><span class="sxs-lookup"><span data-stu-id="4421b-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4421b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4421b-124">Requirements</span></span>  
 <span data-ttu-id="4421b-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4421b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4421b-126">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4421b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4421b-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4421b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4421b-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4421b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4421b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4421b-129">See Also</span></span>  
 [<span data-ttu-id="4421b-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4421b-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4421b-131">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4421b-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="4421b-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4421b-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4421b-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4421b-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
