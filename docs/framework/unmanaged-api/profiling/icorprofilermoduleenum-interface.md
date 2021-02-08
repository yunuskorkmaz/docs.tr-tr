---
description: ': ICorProfilerModuleEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 195379e9ad6bce94fc93465fe5e1418c5d8c076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783826"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="7b8bf-103">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-103">ICorProfilerModuleEnum Interface</span></span>

<span data-ttu-id="7b8bf-104">Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-104">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b8bf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7b8bf-105">Methods</span></span>  
  
|<span data-ttu-id="7b8bf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7b8bf-106">Method</span></span>|<span data-ttu-id="7b8bf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b8bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b8bf-108">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-108">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="7b8bf-109">Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerModuleEnum` .</span><span class="sxs-lookup"><span data-stu-id="7b8bf-109">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="7b8bf-110">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-110">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="7b8bf-111">Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-111">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="7b8bf-112">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-112">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="7b8bf-113">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık bir nesne koleksiyonundan belirtilen sayıda bitişik modülü alır.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-113">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="7b8bf-114">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-114">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="7b8bf-115">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="7b8bf-116">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-116">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="7b8bf-117">Numaralandırıcı imlecinizin konumunu, belirtilen sayıda öğe atlanacak şekilde ilerletir.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-117">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b8bf-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b8bf-118">Remarks</span></span>  

 <span data-ttu-id="7b8bf-119">`ICorProfilerModuleEnum`Arabirim bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-119">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="7b8bf-120">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="7b8bf-121">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b8bf-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b8bf-122">Requirements</span></span>  

 <span data-ttu-id="7b8bf-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b8bf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b8bf-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7b8bf-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b8bf-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7b8bf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b8bf-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b8bf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8bf-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b8bf-127">See also</span></span>

- [<span data-ttu-id="7b8bf-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7b8bf-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7b8bf-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7b8bf-130">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b8bf-130">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
