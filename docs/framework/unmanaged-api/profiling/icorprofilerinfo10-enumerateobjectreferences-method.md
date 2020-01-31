---
title: 'ICorProfilerInfo10:: EnumerateObjectReferences'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863315"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="1f6b7-102">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f6b7-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="1f6b7-103">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="1f6b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f6b7-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="1f6b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f6b7-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="1f6b7-106">\[içinde] başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="1f6b7-107">\[içinde] nesnenin başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="1f6b7-108">\[Profiler-`callback` işlevine geçirilecek verileri sağladı.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f6b7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f6b7-109">Remarks</span></span>

<span data-ttu-id="1f6b7-110">`EnumerateObjectReferences` yöntemi [nesne başvurularına](icorprofilercallback-objectreferences-method.md)benzerdir, ancak başvuruları depolamak için bir diziyi önceden ayırmak yerine, Profil Oluşturucu için isteğe bağlı başvuruları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f6b7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f6b7-111">Requirements</span></span>

<span data-ttu-id="1f6b7-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="1f6b7-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1f6b7-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1f6b7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f6b7-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1f6b7-115">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6b7-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1f6b7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-116">See also</span></span>

- [<span data-ttu-id="1f6b7-117">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f6b7-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
