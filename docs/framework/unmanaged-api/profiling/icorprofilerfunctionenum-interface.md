---
title: ICorProfilerFunctionEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: b69afa7676ad174725f13c1113ff3bd9972995f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503087"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="1fa41-102">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fa41-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="1fa41-103">Ortak dil çalışma zamanındaki bir işlevler koleksiyonunu sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa41-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1fa41-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1fa41-104">Methods</span></span>  
  
|<span data-ttu-id="1fa41-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1fa41-105">Method</span></span>|<span data-ttu-id="1fa41-106">Description</span><span class="sxs-lookup"><span data-stu-id="1fa41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1fa41-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-107">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="1fa41-108">Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` .</span><span class="sxs-lookup"><span data-stu-id="1fa41-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="1fa41-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-109">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="1fa41-110">Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1fa41-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="1fa41-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-111">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="1fa41-112">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="1fa41-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="1fa41-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-113">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="1fa41-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="1fa41-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="1fa41-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-115">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="1fa41-116">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="1fa41-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fa41-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fa41-117">Remarks</span></span>  
 <span data-ttu-id="1fa41-118">`ICorProfilerFunctionEnum`Arabirim bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="1fa41-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="1fa41-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa41-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="1fa41-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="1fa41-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="1fa41-121">`ICorProfilerFunctionEnum`zaten JıT olarak derlenen işlevlerin üzerine numaralandırılır, ancak Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="1fa41-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fa41-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fa41-122">Requirements</span></span>  
 <span data-ttu-id="1fa41-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fa41-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa41-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1fa41-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fa41-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1fa41-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fa41-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fa41-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa41-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fa41-127">See also</span></span>

- [<span data-ttu-id="1fa41-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fa41-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1fa41-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1fa41-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1fa41-130">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fa41-130">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
