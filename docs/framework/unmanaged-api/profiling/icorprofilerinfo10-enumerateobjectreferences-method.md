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
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452246"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="1da28-102">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="1da28-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="1da28-103">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1da28-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="1da28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1da28-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="1da28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1da28-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="1da28-106">\[içinde] başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="1da28-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="1da28-107">\[içinde] nesnenin başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="1da28-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="1da28-108">\[Profiler-`callback` işlevine geçirilecek verileri sağladı.</span><span class="sxs-lookup"><span data-stu-id="1da28-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="1da28-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1da28-109">Remarks</span></span>

<span data-ttu-id="1da28-110">`EnumerateObjectReferences` yöntemi [nesne başvurularına](icorprofilercallback-objectreferences-method.md)benzerdir, ancak başvuruları depolamak için bir diziyi önceden ayırmak yerine, Profil Oluşturucu için isteğe bağlı başvuruları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1da28-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="1da28-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1da28-111">Requirements</span></span>

<span data-ttu-id="1da28-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1da28-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="1da28-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1da28-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1da28-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1da28-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1da28-115">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da28-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1da28-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da28-116">See also</span></span>

- [<span data-ttu-id="1da28-117">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1da28-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
