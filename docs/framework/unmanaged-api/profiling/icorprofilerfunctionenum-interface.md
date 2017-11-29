---
title: ICorProfilerFunctionEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum
helpviewer_keywords: ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1067fa6738b23492b3a58500b4cb6ba1d030304f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="c9921-102">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9921-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="c9921-103">Ortak dil çalışma zamanı işlevleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9921-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9921-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9921-104">Methods</span></span>  
  
|<span data-ttu-id="c9921-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c9921-105">Method</span></span>|<span data-ttu-id="c9921-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9921-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9921-107">Clone yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="c9921-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c9921-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="c9921-109">GetCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="c9921-110">Uygulama tarafından yüklenen ya da zorla Profil Oluşturucu tarafından yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c9921-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="c9921-111">Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="c9921-112">Bitişik işlevleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak işlevlerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="c9921-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="c9921-113">Reset yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="c9921-114">Numaralandırıcının imleç dizisi başlangıç konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="c9921-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="c9921-115">Skip yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="c9921-116">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="c9921-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9921-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9921-117">Remarks</span></span>  
 <span data-ttu-id="c9921-118">`ICorProfilerFunctionEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="c9921-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="c9921-119">Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9921-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="c9921-120">Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c9921-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="c9921-121">`ICorProfilerFunctionEnum`JIT derlenmiş zaten silinmiş ancak Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez işlevleri üzerinden numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c9921-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9921-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9921-122">Requirements</span></span>  
 <span data-ttu-id="c9921-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9921-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9921-124">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9921-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9921-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9921-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9921-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9921-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9921-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9921-127">See Also</span></span>  
 [<span data-ttu-id="c9921-128">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9921-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c9921-129">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9921-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c9921-130">Enumjıtedfunctions yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9921-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
