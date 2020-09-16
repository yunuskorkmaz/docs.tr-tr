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
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540574"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="b9268-102">ICorProfilerInfo10:: RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9268-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="b9268-103">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="b9268-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9268-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b9268-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="b9268-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9268-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="b9268-106">\[içinde] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="b9268-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="b9268-107">\[içinde] yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="b9268-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="b9268-108">\[içinde] `moduleId` `module` yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9268-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="b9268-109">\[içinde] `methodId` `module` yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9268-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9268-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9268-110">Remarks</span></span>

<span data-ttu-id="b9268-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz.</span><span class="sxs-lookup"><span data-stu-id="b9268-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="b9268-112">`RequestReJIT`Satır içine alınmış yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için profil oluşturucunun, tüm ınlinler için satır içi veya daha fazla izleme yapması bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="b9268-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="b9268-113">Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur.</span><span class="sxs-lookup"><span data-stu-id="b9268-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="b9268-114">Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9268-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9268-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9268-115">Requirements</span></span>

<span data-ttu-id="b9268-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b9268-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b9268-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9268-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b9268-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b9268-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b9268-119">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9268-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b9268-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9268-120">See also</span></span>

- [<span data-ttu-id="b9268-121">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9268-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
