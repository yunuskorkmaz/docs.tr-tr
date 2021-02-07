---
description: ': ICorProfilerCallback:: ObjectsAllocatedByClass yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: df9f3dde27664de7db4afb264b221f640753ddb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745066"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="ea052-103">ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea052-103">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="ea052-104">En son çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ea052-104">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea052-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea052-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea052-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea052-106">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="ea052-107">'ndaki `classIds` Ve `cObjects` dizilerinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ea052-107">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="ea052-108">'ndaki Her KIMLIğIN bir veya daha fazla örneğe sahip bir sınıfı belirttiği sınıf kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="ea052-108">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="ea052-109">'ndaki Her tamsayı dizideki karşılık gelen sınıf için örnek sayısını belirten bir tamsayılar dizisi `classIds` .</span><span class="sxs-lookup"><span data-stu-id="ea052-109">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea052-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea052-110">Remarks</span></span>  

 <span data-ttu-id="ea052-111">`classIds`Ve `cObjects` dizileri paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="ea052-111">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="ea052-112">Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıfa başvur.</span><span class="sxs-lookup"><span data-stu-id="ea052-112">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="ea052-113">Önceki çöp toplamadan bu yana bir sınıf örneği oluşturulmadıysa, sınıf atlanır.</span><span class="sxs-lookup"><span data-stu-id="ea052-113">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="ea052-114">`ObjectsAllocatedByClass`Bu geri çağırma, büyük nesne yığınında ayrılan nesneleri rapor etmez.</span><span class="sxs-lookup"><span data-stu-id="ea052-114">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="ea052-115">Tarafından raporlanan sayılar `ObjectsAllocatedByClass` yalnızca tahminlerdir.</span><span class="sxs-lookup"><span data-stu-id="ea052-115">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="ea052-116">Tam sayımlar için [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea052-116">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="ea052-117">`classIds`Karşılık gelen dizide kaldırma işlemi olan türler varsa dizi bir veya daha fazla null giriş içerebilir `cObjects` .</span><span class="sxs-lookup"><span data-stu-id="ea052-117">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea052-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea052-118">Requirements</span></span>  

 <span data-ttu-id="ea052-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea052-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea052-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ea052-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea052-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea052-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea052-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea052-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea052-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea052-123">See also</span></span>

- [<span data-ttu-id="ea052-124">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea052-124">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
