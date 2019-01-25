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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8966a2fc9e38594e8b2727077b7e1e85c3e52b16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705488"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="da4d7-102">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da4d7-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="da4d7-103">Sıralı olarak uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4d7-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da4d7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="da4d7-104">Methods</span></span>  
  
|<span data-ttu-id="da4d7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="da4d7-105">Method</span></span>|<span data-ttu-id="da4d7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da4d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da4d7-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="da4d7-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerModuleEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="da4d7-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="da4d7-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="da4d7-110">Uygulamaya yüklenen yönetilen modülleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="da4d7-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="da4d7-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="da4d7-112">Belirtilen bitişik modül sayısı dizideki geçerli konum Numaralandırıcının başlayarak nesnelerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="da4d7-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="da4d7-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="da4d7-114">Numaralandırıcının imleç dizisi başlangıç konumuna gider.</span><span class="sxs-lookup"><span data-stu-id="da4d7-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="da4d7-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="da4d7-116">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının İmleç konumuna ilerler.</span><span class="sxs-lookup"><span data-stu-id="da4d7-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4d7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da4d7-117">Remarks</span></span>  
 <span data-ttu-id="da4d7-118">`ICorProfilerModuleEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="da4d7-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="da4d7-119">Dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4d7-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="da4d7-120">Diğer bir deyişle, böylece büyük diziler yöntemi parametre olarak geçirmeyi ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="da4d7-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4d7-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da4d7-121">Requirements</span></span>  
 <span data-ttu-id="da4d7-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da4d7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4d7-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da4d7-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da4d7-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da4d7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da4d7-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da4d7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4d7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4d7-126">See also</span></span>
- [<span data-ttu-id="da4d7-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da4d7-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="da4d7-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="da4d7-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="da4d7-129">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da4d7-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
