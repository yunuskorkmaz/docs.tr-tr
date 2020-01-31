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
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863185"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="53ac9-102">ICorProfilerInfo10:: RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="53ac9-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="53ac9-103">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="53ac9-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="53ac9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53ac9-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="53ac9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53ac9-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="53ac9-106">\[içinde] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="53ac9-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="53ac9-107">\[içinde] yeniden derlemek için işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="53ac9-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="53ac9-108">\[içinde], yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` kısmını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ac9-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="53ac9-109">\[içinde], yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` kısmını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ac9-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="53ac9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53ac9-110">Remarks</span></span>

<span data-ttu-id="53ac9-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz.</span><span class="sxs-lookup"><span data-stu-id="53ac9-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="53ac9-112">Profil oluşturucunun, satır içine alınmış bir yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için tüm ınlinler için satır içi veya daha fazla izleme yapması veya çağrı `RequestReJIT` izlemesi bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="53ac9-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="53ac9-113">Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur.</span><span class="sxs-lookup"><span data-stu-id="53ac9-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="53ac9-114">Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="53ac9-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="53ac9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53ac9-115">Requirements</span></span>

<span data-ttu-id="53ac9-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="53ac9-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="53ac9-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53ac9-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="53ac9-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="53ac9-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="53ac9-119">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ac9-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="53ac9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53ac9-120">See also</span></span>

- [<span data-ttu-id="53ac9-121">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="53ac9-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
