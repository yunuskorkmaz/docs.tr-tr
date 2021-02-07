---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: GetClassLayout yöntemi'
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
ms.openlocfilehash: 6b515ff84240e227914404379efcfc063c25c5a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760504"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="fdd17-103">ICorProfilerInfo2::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="fdd17-103">ICorProfilerInfo2::GetClassLayout Method</span></span>

<span data-ttu-id="fdd17-104">Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="fdd17-104">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="fdd17-105">Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.</span><span class="sxs-lookup"><span data-stu-id="fdd17-105">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd17-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdd17-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdd17-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdd17-107">Parameters</span></span>  

 `classID`  
 <span data-ttu-id="fdd17-108">'ndaki Düzenin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fdd17-108">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="fdd17-109">[in, out] Her biri sınıfın alanlarının belirteçlerini ve farklarını içeren [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) yapılarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="fdd17-109">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="fdd17-110">'ndaki `rFieldOffset` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="fdd17-110">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="fdd17-111">dışı Kullanılabilir öğelerin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fdd17-111">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="fdd17-112">`cFieldOffset`0 ise, bu değer gereken öğe sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdd17-112">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="fdd17-113">dışı Sınıfının bayt cinsinden boyutunu içeren konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fdd17-113">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdd17-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdd17-114">Remarks</span></span>  

 <span data-ttu-id="fdd17-115">`GetClassLayout`Yöntemi yalnızca sınıfın kendisi tarafından tanımlanan alanları döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdd17-115">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="fdd17-116">Sınıfın üst sınıfı tanımlanmış alanları da varsa, `GetClassLayout` Bu alanları almak için profil oluşturucunun üst sınıfta çağrısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd17-116">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="fdd17-117">`GetClassLayout`Dize sınıfları ile kullanıyorsanız, yöntem E_INVALIDARG hata kodu ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fdd17-117">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="fdd17-118">Bir dizenin düzeni hakkında bilgi almak için [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdd17-118">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="fdd17-119">`GetClassLayout` , bir dizi sınıfıyla çağrıldığında de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fdd17-119">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="fdd17-120">`GetClassLayout`Geri döndüğünde, `rFieldOffset` arabelleğin tüm kullanılabilir yapıları içermesi için yeterince büyük olduğunu doğrulamanız gerekir `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="fdd17-120">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="fdd17-121">Bunu yapmak için, ile işaret edilen değeri, `pcFieldOffset` `rFieldOffset` bir yapının boyutuna bölünen boyutla karşılaştırın `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="fdd17-121">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="fdd17-122">`rFieldOffset`Yeterince büyük değilse, daha büyük bir arabellek ayırın `rFieldOffset` , `cFieldOffset` Yeni, daha büyük boyutla güncelleştirin ve `GetClassLayout` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="fdd17-122">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="fdd17-123">Alternatif olarak, `GetClassLayout` `rFieldOffset` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd17-123">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fdd17-124">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcFieldOffset` ve `GetClassLayout` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd17-124">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd17-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdd17-125">Requirements</span></span>  

 <span data-ttu-id="fdd17-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd17-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd17-127">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fdd17-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdd17-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fdd17-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdd17-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd17-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd17-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdd17-130">See also</span></span>

- [<span data-ttu-id="fdd17-131">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdd17-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="fdd17-132">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdd17-132">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="fdd17-133">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fdd17-133">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fdd17-134">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fdd17-134">Profiling</span></span>](index.md)
