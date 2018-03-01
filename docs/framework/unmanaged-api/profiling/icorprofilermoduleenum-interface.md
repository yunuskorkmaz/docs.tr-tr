---
title: ICorProfilerModuleEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b337bc99f89b04145afb3994da840cff7e2c5c80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="2d192-102">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d192-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="2d192-103">Uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d192-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d192-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2d192-104">Methods</span></span>  
  
|<span data-ttu-id="2d192-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2d192-105">Method</span></span>|<span data-ttu-id="2d192-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d192-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d192-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="2d192-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerModuleEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2d192-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="2d192-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="2d192-110">Uygulamaya yüklenen yönetilen modüller sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2d192-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="2d192-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="2d192-112">Bitişik modülleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak nesnelerinin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="2d192-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="2d192-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="2d192-114">Numaralandırıcının imleç dizisi başlangıç konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="2d192-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="2d192-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="2d192-116">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç konumu ilerler.</span><span class="sxs-lookup"><span data-stu-id="2d192-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d192-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d192-117">Remarks</span></span>  
 <span data-ttu-id="2d192-118">`ICorProfilerModuleEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="2d192-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="2d192-119">Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d192-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="2d192-120">Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2d192-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d192-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d192-121">Requirements</span></span>  
 <span data-ttu-id="2d192-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d192-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d192-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d192-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d192-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d192-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d192-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d192-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d192-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d192-126">See Also</span></span>  
 [<span data-ttu-id="2d192-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d192-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2d192-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2d192-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2d192-129">EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d192-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
