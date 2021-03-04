---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10:: EnumerateObjectReferences yöntemi'
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
ms.openlocfilehash: c18532450e420f38413028a18630dbf3e308fa61
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106728"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="df58b-103">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="df58b-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="df58b-104">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="df58b-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="df58b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df58b-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="df58b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df58b-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="df58b-107">\[içinde] başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="df58b-107">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="df58b-108">\[içinde] nesnenin başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="df58b-108">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="df58b-109">\[içinde] profil oluşturucu-işleve geçirilecek veriler `callback` .</span><span class="sxs-lookup"><span data-stu-id="df58b-109">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="df58b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df58b-110">Remarks</span></span>

<span data-ttu-id="df58b-111">`EnumerateObjectReferences`Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, [ObjectReferences](icorprofilercallback-objectreferences-method.md)'a benzerdir.</span><span class="sxs-lookup"><span data-stu-id="df58b-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="df58b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df58b-112">Requirements</span></span>

<span data-ttu-id="df58b-113">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="df58b-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="df58b-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="df58b-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="df58b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df58b-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="df58b-116">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df58b-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="df58b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df58b-117">See also</span></span>

- [<span data-ttu-id="df58b-118">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df58b-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
