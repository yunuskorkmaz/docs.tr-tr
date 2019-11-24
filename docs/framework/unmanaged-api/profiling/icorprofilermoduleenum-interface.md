---
title: ICorProfilerModuleEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442700"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="59c96-102">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59c96-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="59c96-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span><span class="sxs-lookup"><span data-stu-id="59c96-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59c96-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59c96-104">Methods</span></span>  
  
|<span data-ttu-id="59c96-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59c96-105">Method</span></span>|<span data-ttu-id="59c96-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59c96-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="59c96-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="59c96-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="59c96-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="59c96-110">Gets the number of managed modules that were loaded into the application.</span><span class="sxs-lookup"><span data-stu-id="59c96-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="59c96-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="59c96-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span><span class="sxs-lookup"><span data-stu-id="59c96-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="59c96-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="59c96-114">Moves the enumerator's cursor to the starting position of the sequence.</span><span class="sxs-lookup"><span data-stu-id="59c96-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="59c96-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="59c96-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="59c96-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59c96-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59c96-117">Remarks</span></span>  
 <span data-ttu-id="59c96-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span><span class="sxs-lookup"><span data-stu-id="59c96-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="59c96-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span><span class="sxs-lookup"><span data-stu-id="59c96-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="59c96-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span><span class="sxs-lookup"><span data-stu-id="59c96-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c96-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59c96-121">Requirements</span></span>  
 <span data-ttu-id="59c96-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59c96-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c96-123">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59c96-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59c96-124">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59c96-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59c96-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c96-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c96-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59c96-126">See also</span></span>

- [<span data-ttu-id="59c96-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59c96-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="59c96-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59c96-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="59c96-129">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c96-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
