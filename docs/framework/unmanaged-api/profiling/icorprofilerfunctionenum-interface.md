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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e77ec9de198b673bb3b5fc4dad3cd1b0316f07c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991971"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="c39f1-102">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c39f1-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="c39f1-103">Sıralı olarak ortak dil çalışma zamanı işlevleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c39f1-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c39f1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c39f1-104">Methods</span></span>  
  
|<span data-ttu-id="c39f1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c39f1-105">Method</span></span>|<span data-ttu-id="c39f1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c39f1-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="c39f1-108">Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c39f1-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="c39f1-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="c39f1-110">Uygulama tarafından yüklenen ya da profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c39f1-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="c39f1-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="c39f1-112">Belirtilen bitişik işlev sayısı dizideki geçerli konum Numaralandırıcının başlayan İşlevler, sıralı bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="c39f1-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="c39f1-113">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="c39f1-114">Numaralandırıcının imleç dizisi başlangıç konumuna gider.</span><span class="sxs-lookup"><span data-stu-id="c39f1-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="c39f1-115">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="c39f1-116">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="c39f1-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c39f1-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c39f1-117">Remarks</span></span>  
 <span data-ttu-id="c39f1-118">`ICorProfilerFunctionEnum` Arabirimidir bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="c39f1-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="c39f1-119">Dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="c39f1-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="c39f1-120">Diğer bir deyişle, böylece büyük diziler yöntemi parametre olarak geçirmeyi ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c39f1-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="c39f1-121">`ICorProfilerFunctionEnum` JIT olarak derlenmiş zaten silinmiş, ancak Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez işlevleri üzerinden numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c39f1-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c39f1-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c39f1-122">Requirements</span></span>  
 <span data-ttu-id="c39f1-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c39f1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c39f1-124">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c39f1-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c39f1-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c39f1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c39f1-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c39f1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39f1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39f1-127">See also</span></span>

- [<span data-ttu-id="c39f1-128">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c39f1-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c39f1-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c39f1-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c39f1-130">EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39f1-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
