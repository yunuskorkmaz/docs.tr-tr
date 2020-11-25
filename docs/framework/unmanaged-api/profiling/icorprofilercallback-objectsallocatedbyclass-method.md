---
title: ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 70d43d7526376c40d0f8358ebd65e4a00a41b969
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701675"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="579ad-102">ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="579ad-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="579ad-103">En son çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="579ad-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="579ad-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="579ad-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="579ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="579ad-105">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="579ad-106">'ndaki `classIds` Ve `cObjects` dizilerinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="579ad-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="579ad-107">'ndaki Her KIMLIğIN bir veya daha fazla örneğe sahip bir sınıfı belirttiği sınıf kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="579ad-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="579ad-108">'ndaki Her tamsayı dizideki karşılık gelen sınıf için örnek sayısını belirten bir tamsayılar dizisi `classIds` .</span><span class="sxs-lookup"><span data-stu-id="579ad-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="579ad-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="579ad-109">Remarks</span></span>  

 <span data-ttu-id="579ad-110">`classIds`Ve `cObjects` dizileri paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="579ad-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="579ad-111">Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıfa başvur.</span><span class="sxs-lookup"><span data-stu-id="579ad-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="579ad-112">Önceki çöp toplamadan bu yana bir sınıf örneği oluşturulmadıysa, sınıf atlanır.</span><span class="sxs-lookup"><span data-stu-id="579ad-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="579ad-113">`ObjectsAllocatedByClass`Bu geri çağırma, büyük nesne yığınında ayrılan nesneleri rapor etmez.</span><span class="sxs-lookup"><span data-stu-id="579ad-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="579ad-114">Tarafından raporlanan sayılar `ObjectsAllocatedByClass` yalnızca tahminlerdir.</span><span class="sxs-lookup"><span data-stu-id="579ad-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="579ad-115">Tam sayımlar için [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="579ad-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="579ad-116">`classIds`Karşılık gelen dizide kaldırma işlemi olan türler varsa dizi bir veya daha fazla null giriş içerebilir `cObjects` .</span><span class="sxs-lookup"><span data-stu-id="579ad-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="579ad-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="579ad-117">Requirements</span></span>  

 <span data-ttu-id="579ad-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="579ad-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="579ad-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="579ad-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="579ad-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="579ad-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="579ad-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="579ad-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579ad-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="579ad-122">See also</span></span>

- [<span data-ttu-id="579ad-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="579ad-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
