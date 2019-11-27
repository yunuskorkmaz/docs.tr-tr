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
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447801"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="4e7db-102">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e7db-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="4e7db-103">Ortak dil çalışma zamanındaki bir işlevler koleksiyonunu sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e7db-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e7db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e7db-104">Methods</span></span>  
  
|<span data-ttu-id="4e7db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e7db-105">Method</span></span>|<span data-ttu-id="4e7db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e7db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e7db-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="4e7db-108">Bu `ICorProfilerFunctionEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4e7db-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="4e7db-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="4e7db-110">Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4e7db-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="4e7db-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="4e7db-112">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="4e7db-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="4e7db-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="4e7db-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="4e7db-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="4e7db-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="4e7db-116">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="4e7db-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7db-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e7db-117">Remarks</span></span>  
 <span data-ttu-id="4e7db-118">`ICorProfilerFunctionEnum` arabirimi bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="4e7db-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="4e7db-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e7db-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="4e7db-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="4e7db-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="4e7db-121">`ICorProfilerFunctionEnum`, zaten JıT olarak derlenen işlevlerin üzerine numaralandırılır, ancak Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="4e7db-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7db-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e7db-122">Requirements</span></span>  
 <span data-ttu-id="4e7db-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7db-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7db-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4e7db-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e7db-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e7db-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e7db-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7db-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7db-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e7db-127">See also</span></span>

- [<span data-ttu-id="4e7db-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e7db-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4e7db-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e7db-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4e7db-130">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e7db-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
