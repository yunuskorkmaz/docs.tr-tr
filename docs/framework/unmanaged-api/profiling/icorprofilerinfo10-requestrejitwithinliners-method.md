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
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449810"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="00db3-102">ICorProfilerInfo10:: RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="00db3-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="00db3-103">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="00db3-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="00db3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00db3-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a><span data-ttu-id="00db3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00db3-105">Parameters</span></span>

`dwRejitFlags` \
<span data-ttu-id="00db3-106">'ndaki [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="00db3-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>

`cFunctions` \
<span data-ttu-id="00db3-107">'ndaki Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="00db3-107">[in] The number of functions to recompile.</span></span>

`moduleIds` \
<span data-ttu-id="00db3-108">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00db3-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

`methodIds` \
<span data-ttu-id="00db3-109">'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00db3-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="00db3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00db3-110">Remarks</span></span>

<span data-ttu-id="00db3-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz.</span><span class="sxs-lookup"><span data-stu-id="00db3-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="00db3-112">Profil oluşturucunun, satır içine alınmış bir yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için tüm ınlinler için satır içi veya daha fazla izleme yapması veya çağrı `RequestReJIT` izlemesi bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="00db3-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="00db3-113">Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur.</span><span class="sxs-lookup"><span data-stu-id="00db3-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="00db3-114">Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="00db3-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="00db3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00db3-115">Requirements</span></span>

<span data-ttu-id="00db3-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="00db3-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="00db3-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00db3-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="00db3-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00db3-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="00db3-119">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00db3-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="00db3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00db3-120">See also</span></span>

- [<span data-ttu-id="00db3-121">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="00db3-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
