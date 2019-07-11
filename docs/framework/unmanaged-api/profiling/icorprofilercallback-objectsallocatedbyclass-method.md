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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4229332ef3a079a5a294e27b624dde0e1fb46691
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782957"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="0946a-102">ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0946a-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="0946a-103">En son çöp toplamadan beri oluşturulan her belirtilen sınıf örneklerini sayısı hakkında daha fazla profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0946a-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0946a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0946a-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0946a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0946a-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="0946a-106">[in] Boyutu `classIds` ve `cObjects` dizileri.</span><span class="sxs-lookup"><span data-stu-id="0946a-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="0946a-107">[in] Bir dizi sınıfının kimlikleri, burada her kimliği ile bir veya daha fazla örneğini bir sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0946a-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="0946a-108">[in] Burada her tamsayı karşılık gelen sınıf için örnek sayısını belirtir, tamsayı dizisi `classIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0946a-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0946a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0946a-109">Remarks</span></span>  
 <span data-ttu-id="0946a-110">`classIds` Ve `cObjects` paralel diziler dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="0946a-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="0946a-111">Örneğin, `classIds[i]` ve `cObjects[i]` başvuru aynı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0946a-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="0946a-112">Sınıfı, önceki çöp toplama işleminden itibaren hiçbir bir sınıf örneği oluşturulmuşsa atlanır.</span><span class="sxs-lookup"><span data-stu-id="0946a-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="0946a-113">`ObjectsAllocatedByClass` Geri çağırma büyük nesne yığınında nesneleri bildirmez.</span><span class="sxs-lookup"><span data-stu-id="0946a-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="0946a-114">Sayıları tarafından bildirilen `ObjectsAllocatedByClass` yalnızca biriminizdeki tahmini fiyatlardır.</span><span class="sxs-lookup"><span data-stu-id="0946a-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="0946a-115">Tam sayıları için kullanmak [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="0946a-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="0946a-116">`classIds` Varsa, dizi bir veya daha fazla null girişler içeriyor olabilir karşılık gelen `cObjects` dizi kaldırma tür vardır.</span><span class="sxs-lookup"><span data-stu-id="0946a-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0946a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0946a-117">Requirements</span></span>  
 <span data-ttu-id="0946a-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0946a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0946a-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0946a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0946a-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0946a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0946a-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0946a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0946a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0946a-122">See also</span></span>

- [<span data-ttu-id="0946a-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0946a-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
