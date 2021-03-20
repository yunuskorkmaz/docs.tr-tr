---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10:: RequestReJITWithInliners yöntemi'
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
ms.openlocfilehash: 3d85537030e042d53bb4ff859eb1d2c3a24a45a5
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760788"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="b9269-103">ICorProfilerInfo10:: RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9269-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="b9269-104">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="b9269-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9269-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9269-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="b9269-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9269-106">Parameters</span></span>

<span data-ttu-id="b9269-107">`dwRejitFlags` 'ndaki [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="b9269-107">`dwRejitFlags` [in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

<span data-ttu-id="b9269-108">`cFunctions` 'ndaki Yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="b9269-108">`cFunctions` [in] The number of functions to recompile.</span></span>

<span data-ttu-id="b9269-109">`moduleIds` 'ndaki `moduleId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9269-109">`moduleIds` [in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

<span data-ttu-id="b9269-110">`methodIds` 'ndaki `methodId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9269-110">`methodIds` [in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9269-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9269-111">Remarks</span></span>

<span data-ttu-id="b9269-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz.</span><span class="sxs-lookup"><span data-stu-id="b9269-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="b9269-113">`RequestReJIT`Satır içine alınmış yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için profil oluşturucunun, tüm ınlinler için satır içi veya daha fazla izleme yapması bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="b9269-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="b9269-114">Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur.</span><span class="sxs-lookup"><span data-stu-id="b9269-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="b9269-115">Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9269-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9269-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9269-116">Requirements</span></span>

<span data-ttu-id="b9269-117">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b9269-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b9269-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9269-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b9269-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b9269-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b9269-120">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9269-120">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b9269-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9269-121">See also</span></span>

- [<span data-ttu-id="b9269-122">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9269-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
