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
ms.openlocfilehash: b9fb308f19ff09218c97b030296b9a3d4f0f2512
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868193"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="1486d-102">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1486d-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="1486d-103">Ortak dil çalışma zamanındaki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1486d-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1486d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1486d-104">Methods</span></span>  
  
|<span data-ttu-id="1486d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1486d-105">Method</span></span>|<span data-ttu-id="1486d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1486d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1486d-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1486d-107">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="1486d-108">Bu `ICorProfilerThreadEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="1486d-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="1486d-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1486d-109">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="1486d-110">Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1486d-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="1486d-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1486d-111">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="1486d-112">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="1486d-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="1486d-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1486d-113">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="1486d-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="1486d-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="1486d-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1486d-115">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="1486d-116">Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="1486d-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1486d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1486d-117">Remarks</span></span>  
 <span data-ttu-id="1486d-118">`ICorProfilerThreadEnum` arabirimi bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="1486d-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="1486d-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1486d-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="1486d-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="1486d-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1486d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1486d-121">Requirements</span></span>  
 <span data-ttu-id="1486d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1486d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1486d-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1486d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1486d-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1486d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1486d-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1486d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1486d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1486d-126">See also</span></span>

- [<span data-ttu-id="1486d-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1486d-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1486d-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1486d-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
