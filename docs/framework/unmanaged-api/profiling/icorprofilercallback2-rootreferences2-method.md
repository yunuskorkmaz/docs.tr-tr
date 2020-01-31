---
title: ICorProfilerCallback2::RootReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: a9ce9a7a56847efcadf09924ffc56c41f20a1c58
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865733"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="57acf-102">ICorProfilerCallback2::RootReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57acf-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="57acf-103">Çöp toplama gerçekleştirildikten sonra profil oluşturucuyu kök başvuruları hakkında bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="57acf-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="57acf-104">Bu yöntem [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) yönteminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="57acf-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57acf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57acf-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57acf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57acf-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="57acf-107">'ndaki `rootRefIds`, `rootKinds`, `rootFlags`ve `rootIds` dizilerindeki öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="57acf-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="57acf-108">'ndaki Her biri bir statik nesneye veya yığında bir nesneye başvuran bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="57acf-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="57acf-109">`rootKinds` dizisindeki öğeler, `rootRefIds` dizisinde karşılık gelen öğeleri sınıflandırmak için bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="57acf-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="57acf-110">'ndaki Çöp toplama kökünün türünü belirten [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="57acf-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="57acf-111">'ndaki Bir çöp toplama kökünün özelliklerini tanımlayan [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="57acf-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="57acf-112">'ndaki `rootKinds` parametresinin değerine bağlı olarak çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden UINT_PTR değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="57acf-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="57acf-113">Kök türü bir yığın ise, kök KIMLIĞI değişkeni içeren işleve yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="57acf-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="57acf-114">Bu kök KIMLIĞI 0 ise, işlev CLR 'ye iç olan adlandırılmamış bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="57acf-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="57acf-115">Kök türü bir tanıtıcı ise, kök KIMLIĞI çöp toplama tutamacı içindir.</span><span class="sxs-lookup"><span data-stu-id="57acf-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="57acf-116">Diğer kök türleri için KIMLIK donuk bir değerdir ve göz ardı edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="57acf-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57acf-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57acf-117">Remarks</span></span>  
 <span data-ttu-id="57acf-118">`rootRefIds`, `rootKinds`, `rootFlags`ve `rootIds` dizileri paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="57acf-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="57acf-119">Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`ve `rootIds[i]` hepsi aynı köke sorun.</span><span class="sxs-lookup"><span data-stu-id="57acf-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="57acf-120">Profil oluşturucuyu bildirmek için hem `RootReferences` hem de `RootReferences2` çağırılır.</span><span class="sxs-lookup"><span data-stu-id="57acf-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="57acf-121">Profil oluşturucular, genellikle bir yöntemi veya diğerini uygular, çünkü `RootReferences2` geçirilen bilgiler, `RootReferences`geçirilen bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="57acf-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="57acf-122">`rootRefIds` içindeki girişlerin sıfır olması mümkündür. Bu, karşılık gelen kök başvurusunun null olduğunu ve yönetilen yığında bir nesneye başvurmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57acf-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="57acf-123">Çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabileceğinden, `RootReferences2` tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="57acf-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="57acf-124">Bu nedenle, profil oluşturucular `RootReferences2` çağrısı sırasında nesneleri incelemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="57acf-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="57acf-125">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="57acf-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57acf-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57acf-126">Requirements</span></span>  
 <span data-ttu-id="57acf-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57acf-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57acf-128">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="57acf-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57acf-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57acf-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57acf-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57acf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57acf-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57acf-131">See also</span></span>

- [<span data-ttu-id="57acf-132">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57acf-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="57acf-133">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57acf-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
