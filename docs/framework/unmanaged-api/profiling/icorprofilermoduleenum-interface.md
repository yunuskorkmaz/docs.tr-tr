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
ms.openlocfilehash: fe11c0bbe273ae07cdae43f681a558e07a291ffb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494897"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="cf776-102">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf776-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="cf776-103">Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf776-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf776-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf776-104">Methods</span></span>  
  
|<span data-ttu-id="cf776-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cf776-105">Method</span></span>|<span data-ttu-id="cf776-106">Description</span><span class="sxs-lookup"><span data-stu-id="cf776-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf776-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="cf776-108">Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerModuleEnum` .</span><span class="sxs-lookup"><span data-stu-id="cf776-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="cf776-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="cf776-110">Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cf776-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="cf776-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="cf776-112">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık bir nesne koleksiyonundan belirtilen sayıda bitişik modülü alır.</span><span class="sxs-lookup"><span data-stu-id="cf776-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="cf776-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="cf776-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="cf776-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="cf776-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="cf776-116">Numaralandırıcı imlecinizin konumunu, belirtilen sayıda öğe atlanacak şekilde ilerletir.</span><span class="sxs-lookup"><span data-stu-id="cf776-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf776-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf776-117">Remarks</span></span>  
 <span data-ttu-id="cf776-118">`ICorProfilerModuleEnum`Arabirim bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="cf776-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="cf776-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf776-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="cf776-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="cf776-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf776-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf776-121">Requirements</span></span>  
 <span data-ttu-id="cf776-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf776-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf776-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cf776-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf776-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf776-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf776-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf776-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf776-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf776-126">See also</span></span>

- [<span data-ttu-id="cf776-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf776-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cf776-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf776-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cf776-129">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf776-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
