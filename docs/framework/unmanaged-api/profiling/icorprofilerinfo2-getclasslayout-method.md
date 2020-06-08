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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497159"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="5d43a-102">ICorProfilerInfo2::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="5d43a-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="5d43a-103">Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="5d43a-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="5d43a-104">Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.</span><span class="sxs-lookup"><span data-stu-id="5d43a-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d43a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5d43a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d43a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d43a-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="5d43a-107">'ndaki Düzenin alınacağı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5d43a-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="5d43a-108">[in, out] Her biri sınıfın alanlarının belirteçlerini ve farklarını içeren [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) yapılarından oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="5d43a-108">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="5d43a-109">'ndaki `rFieldOffset`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5d43a-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="5d43a-110">dışı Kullanılabilir öğelerin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d43a-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="5d43a-111">`cFieldOffset`0 ise, bu değer gereken öğe sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d43a-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="5d43a-112">dışı Sınıfının bayt cinsinden boyutunu içeren konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d43a-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d43a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d43a-113">Remarks</span></span>  
 <span data-ttu-id="5d43a-114">`GetClassLayout`Yöntemi yalnızca sınıfın kendisi tarafından tanımlanan alanları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d43a-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="5d43a-115">Sınıfın üst sınıfı tanımlanmış alanları da varsa, `GetClassLayout` Bu alanları almak için profil oluşturucunun üst sınıfta çağrısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d43a-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="5d43a-116">`GetClassLayout`Dize sınıfları ile kullanıyorsanız, yöntem E_INVALIDARG hata kodu ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5d43a-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="5d43a-117">Bir dizenin düzeni hakkında bilgi almak için [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d43a-117">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="5d43a-118">`GetClassLayout`, bir dizi sınıfıyla çağrıldığında de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5d43a-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="5d43a-119">`GetClassLayout`Geri döndüğünde, `rFieldOffset` arabelleğin tüm kullanılabilir yapıları içermesi için yeterince büyük olduğunu doğrulamanız gerekir `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="5d43a-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="5d43a-120">Bunu yapmak için, ile işaret edilen değeri, `pcFieldOffset` `rFieldOffset` bir yapının boyutuna bölünen boyutla karşılaştırın `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="5d43a-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="5d43a-121">`rFieldOffset`Yeterince büyük değilse, daha büyük bir arabellek ayırın `rFieldOffset` , `cFieldOffset` Yeni, daha büyük boyutla güncelleştirin ve `GetClassLayout` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="5d43a-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="5d43a-122">Alternatif olarak, `GetClassLayout` `rFieldOffset` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d43a-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5d43a-123">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcFieldOffset` ve `GetClassLayout` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d43a-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d43a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d43a-124">Requirements</span></span>  
 <span data-ttu-id="5d43a-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d43a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d43a-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d43a-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d43a-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d43a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d43a-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d43a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d43a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d43a-129">See also</span></span>

- [<span data-ttu-id="5d43a-130">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d43a-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5d43a-131">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d43a-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="5d43a-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d43a-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5d43a-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d43a-133">Profiling</span></span>](index.md)
