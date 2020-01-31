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
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866084"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="e7546-102">ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7546-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="e7546-103">En son çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="e7546-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7546-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7546-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7546-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7546-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="e7546-106">'ndaki `classIds` ve `cObjects` dizilerinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e7546-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="e7546-107">'ndaki Her KIMLIğIN bir veya daha fazla örneğe sahip bir sınıfı belirttiği sınıf kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="e7546-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="e7546-108">'ndaki Her bir tamsayının, `classIds` dizisindeki karşılık gelen sınıf için örnek sayısını belirttiği tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="e7546-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7546-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7546-109">Remarks</span></span>  
 <span data-ttu-id="e7546-110">`classIds` ve `cObjects` dizileri paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="e7546-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="e7546-111">Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıfa başvuru.</span><span class="sxs-lookup"><span data-stu-id="e7546-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="e7546-112">Önceki çöp toplamadan bu yana bir sınıf örneği oluşturulmadıysa, sınıf atlanır.</span><span class="sxs-lookup"><span data-stu-id="e7546-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="e7546-113">`ObjectsAllocatedByClass` geri çağırması, büyük nesne yığınında ayrılan nesneleri rapor etmez.</span><span class="sxs-lookup"><span data-stu-id="e7546-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="e7546-114">`ObjectsAllocatedByClass` tarafından bildirilen sayılar yalnızca tahminlerdir.</span><span class="sxs-lookup"><span data-stu-id="e7546-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="e7546-115">Tam sayımlar için [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7546-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="e7546-116">Karşılık gelen `cObjects` dizisinde kaldırma işlemi olan türler varsa `classIds` dizisi bir veya daha fazla null giriş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e7546-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7546-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7546-117">Requirements</span></span>  
 <span data-ttu-id="e7546-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7546-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7546-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7546-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7546-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e7546-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7546-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7546-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7546-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7546-122">See also</span></span>

- [<span data-ttu-id="e7546-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7546-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
