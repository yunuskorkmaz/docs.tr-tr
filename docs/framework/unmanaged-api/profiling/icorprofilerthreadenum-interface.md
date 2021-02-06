---
description: ': ICorProfilerThreadEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 035296412aabf20503588a558c8e8ccc1338210e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636399"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="8d2e9-103">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-103">ICorProfilerThreadEnum Interface</span></span>

<span data-ttu-id="8d2e9-104">Ortak dil çalışma zamanındaki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-104">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d2e9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d2e9-105">Methods</span></span>  
  
|<span data-ttu-id="8d2e9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8d2e9-106">Method</span></span>|<span data-ttu-id="8d2e9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d2e9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d2e9-108">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-108">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="8d2e9-109">Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerThreadEnum` .</span><span class="sxs-lookup"><span data-stu-id="8d2e9-109">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="8d2e9-110">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-110">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="8d2e9-111">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-111">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="8d2e9-112">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-112">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="8d2e9-113">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-113">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="8d2e9-114">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-114">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="8d2e9-115">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="8d2e9-116">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-116">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="8d2e9-117">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-117">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d2e9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d2e9-118">Remarks</span></span>  

 <span data-ttu-id="8d2e9-119">`ICorProfilerThreadEnum`Arabirim bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-119">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="8d2e9-120">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="8d2e9-121">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2e9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d2e9-122">Requirements</span></span>  

 <span data-ttu-id="8d2e9-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d2e9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d2e9-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d2e9-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d2e9-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8d2e9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d2e9-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d2e9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2e9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d2e9-127">See also</span></span>

- [<span data-ttu-id="8d2e9-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d2e9-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8d2e9-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8d2e9-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
