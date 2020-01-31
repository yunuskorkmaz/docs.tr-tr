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
ms.openlocfilehash: 2713fa90240cb0bf41f455b6ed65d76c568a2cf8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868271"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="0b783-102">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b783-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="0b783-103">Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b783-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b783-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b783-104">Methods</span></span>  
  
|<span data-ttu-id="0b783-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b783-105">Method</span></span>|<span data-ttu-id="0b783-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b783-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b783-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="0b783-108">Bu `ICorProfilerModuleEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0b783-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="0b783-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="0b783-110">Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0b783-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="0b783-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="0b783-112">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık bir nesne koleksiyonundan belirtilen sayıda bitişik modülü alır.</span><span class="sxs-lookup"><span data-stu-id="0b783-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="0b783-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="0b783-114">Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="0b783-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="0b783-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="0b783-116">Numaralandırıcı imlecinizin konumunu, belirtilen sayıda öğe atlanacak şekilde ilerletir.</span><span class="sxs-lookup"><span data-stu-id="0b783-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b783-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b783-117">Remarks</span></span>  
 <span data-ttu-id="0b783-118">`ICorProfilerModuleEnum` arabirimi bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="0b783-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="0b783-119">Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b783-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="0b783-120">Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="0b783-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b783-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b783-121">Requirements</span></span>  
 <span data-ttu-id="0b783-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b783-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b783-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0b783-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b783-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b783-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b783-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b783-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b783-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b783-126">See also</span></span>

- [<span data-ttu-id="0b783-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b783-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0b783-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b783-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0b783-129">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b783-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
