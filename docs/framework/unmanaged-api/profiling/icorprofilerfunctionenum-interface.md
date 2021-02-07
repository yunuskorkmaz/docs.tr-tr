---
description: ': ICorProfilerFunctionEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0a9437ee1f5c481c2c2d1fd46361da6e938dd179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737603"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="0a99a-103">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a99a-103">ICorProfilerFunctionEnum Interface</span></span>

<span data-ttu-id="0a99a-104">Ortak dil çalışma zamanındaki bir işlevler koleksiyonunu sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a99a-104">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a99a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0a99a-105">Methods</span></span>  
  
|<span data-ttu-id="0a99a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a99a-106">Method</span></span>|<span data-ttu-id="0a99a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a99a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a99a-108">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-108">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="0a99a-109">Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` .</span><span class="sxs-lookup"><span data-stu-id="0a99a-109">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="0a99a-110">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-110">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="0a99a-111">Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0a99a-111">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="0a99a-112">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-112">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="0a99a-113">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="0a99a-113">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="0a99a-114">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-114">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="0a99a-115">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="0a99a-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="0a99a-116">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-116">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="0a99a-117">Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="0a99a-117">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a99a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a99a-118">Remarks</span></span>  

 <span data-ttu-id="0a99a-119">`ICorProfilerFunctionEnum`Arabirim bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="0a99a-119">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="0a99a-120">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a99a-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="0a99a-121">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="0a99a-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="0a99a-122">`ICorProfilerFunctionEnum` daha önce JıT olarak derlenen işlevlerin üzerine numaralandırılır, ancak Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="0a99a-122">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a99a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a99a-123">Requirements</span></span>  

 <span data-ttu-id="0a99a-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a99a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a99a-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0a99a-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a99a-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0a99a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a99a-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a99a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a99a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a99a-128">See also</span></span>

- [<span data-ttu-id="0a99a-129">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a99a-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0a99a-130">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a99a-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0a99a-131">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a99a-131">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
