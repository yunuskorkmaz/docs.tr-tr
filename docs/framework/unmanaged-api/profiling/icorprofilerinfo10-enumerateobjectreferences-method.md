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
ms.openlocfilehash: bcd374aec2944977a0745177995ba8adf0cce9b7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759423"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="cfef1-103">ICorProfilerInfo10:: EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfef1-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="cfef1-104">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="cfef1-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="cfef1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfef1-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="cfef1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfef1-106">Parameters</span></span>

<span data-ttu-id="cfef1-107">`objectId` 'ndaki Başvuruların numaralandırılacağı nesne.</span><span class="sxs-lookup"><span data-stu-id="cfef1-107">`objectId` [in] The object to enumerate references on.</span></span>

<span data-ttu-id="cfef1-108">`callback` 'ndaki Nesne başvuruları ile çağrılacak işlev.</span><span class="sxs-lookup"><span data-stu-id="cfef1-108">`callback` [in] The function that will be called with the references for the object.</span></span>

<span data-ttu-id="cfef1-109">`clientData` 'ndaki Profil Oluşturucu-işleve geçirilecek veriler `callback` .</span><span class="sxs-lookup"><span data-stu-id="cfef1-109">`clientData` [in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfef1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfef1-110">Remarks</span></span>

<span data-ttu-id="cfef1-111">`EnumerateObjectReferences`Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, [ObjectReferences](icorprofilercallback-objectreferences-method.md)'a benzerdir.</span><span class="sxs-lookup"><span data-stu-id="cfef1-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="cfef1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfef1-112">Requirements</span></span>

<span data-ttu-id="cfef1-113">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="cfef1-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="cfef1-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cfef1-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cfef1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cfef1-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cfef1-116">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfef1-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cfef1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfef1-117">See also</span></span>

- [<span data-ttu-id="cfef1-118">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfef1-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
