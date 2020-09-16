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
ms.openlocfilehash: a276ecfe65ed9752f39ed68a36e8e17a24255508
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558322"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="abca9-102">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="abca9-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="abca9-103">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="abca9-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="abca9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="abca9-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="abca9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abca9-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="abca9-106">\[içinde] başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="abca9-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="abca9-107">\[içinde] nesnenin başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="abca9-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="abca9-108">\[içinde] profil oluşturucu-işleve geçirilecek veriler `callback` .</span><span class="sxs-lookup"><span data-stu-id="abca9-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="abca9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abca9-109">Remarks</span></span>

<span data-ttu-id="abca9-110">`EnumerateObjectReferences`Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, [ObjectReferences](icorprofilercallback-objectreferences-method.md)'a benzerdir.</span><span class="sxs-lookup"><span data-stu-id="abca9-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="abca9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abca9-111">Requirements</span></span>

<span data-ttu-id="abca9-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="abca9-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="abca9-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="abca9-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="abca9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="abca9-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="abca9-115">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abca9-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="abca9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abca9-116">See also</span></span>

- [<span data-ttu-id="abca9-117">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abca9-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
