---
title: ICorProfilerThreadEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b83706176091fd70d48e0f50a0fe5988c876f606
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447614"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="4b3a8-102">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="4b3a8-103">Ortak dil çalışma zamanındaki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b3a8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4b3a8-104">Methods</span></span>  
  
|<span data-ttu-id="4b3a8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4b3a8-105">Method</span></span>|<span data-ttu-id="4b3a8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b3a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b3a8-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="4b3a8-108">Bu `ICorProfilerThreadEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="4b3a8-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="4b3a8-110">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="4b3a8-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="4b3a8-112">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="4b3a8-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="4b3a8-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="4b3a8-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="4b3a8-116">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b3a8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b3a8-117">Remarks</span></span>  
 <span data-ttu-id="4b3a8-118">`ICorProfilerThreadEnum` arabirimi bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="4b3a8-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="4b3a8-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b3a8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b3a8-121">Requirements</span></span>  
 <span data-ttu-id="4b3a8-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b3a8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3a8-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4b3a8-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b3a8-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4b3a8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b3a8-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3a8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3a8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b3a8-126">See also</span></span>

- [<span data-ttu-id="4b3a8-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b3a8-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4b3a8-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b3a8-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
