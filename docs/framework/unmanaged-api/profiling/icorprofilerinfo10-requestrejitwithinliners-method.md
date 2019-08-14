---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973743"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="cdbea-102">ICorProfilerInfo10:: RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbea-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>
  
<span data-ttu-id="cdbea-103">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="cdbea-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="cdbea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdbea-104">Syntax</span></span>  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdbea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdbea-105">Parameters</span></span>  
 
 `dwRejitFlags` \
 <span data-ttu-id="cdbea-106">'ndaki [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="cdbea-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>
 
 `cFunctions`  
 <span data-ttu-id="cdbea-107">'ndaki Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="cdbea-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="cdbea-108">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin bölümünübelirtir.`moduleId`</span><span class="sxs-lookup"><span data-stu-id="cdbea-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="cdbea-109">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin bölümünübelirtir.`methodId`</span><span class="sxs-lookup"><span data-stu-id="cdbea-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  

## <a name="remarks"></a><span data-ttu-id="cdbea-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdbea-110">Remarks</span></span>  
  <span data-ttu-id="cdbea-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz.</span><span class="sxs-lookup"><span data-stu-id="cdbea-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="cdbea-112">Satır içine alınmış yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için profil oluşturucunun, `RequestReJIT` tüm ınlinler için satır içi veya daha fazla izleme yapması bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="cdbea-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="cdbea-113">Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur.</span><span class="sxs-lookup"><span data-stu-id="cdbea-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="cdbea-114">Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdbea-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>  

## <a name="requirements"></a><span data-ttu-id="cdbea-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdbea-115">Requirements</span></span>  
 <span data-ttu-id="cdbea-116">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="cdbea-116">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="cdbea-117">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cdbea-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdbea-118">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cdbea-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdbea-119">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbea-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cdbea-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdbea-120">See also</span></span>
- [<span data-ttu-id="cdbea-121">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdbea-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

