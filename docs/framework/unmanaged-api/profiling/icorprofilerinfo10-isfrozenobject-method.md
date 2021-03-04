---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10:: ısfrozenobject yöntemi'
title: 'ICorProfilerInfo10:: ısfrozenobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b47204630056e2797b5cf126bd7c291830cea05
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103458"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="e2c21-103">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2c21-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="e2c21-104">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e2c21-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2c21-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2c21-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="e2c21-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2c21-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="e2c21-107">\[içinde] incelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="e2c21-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="e2c21-108">\[out] bir `BOOL` nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="e2c21-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2c21-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2c21-109">Requirements</span></span>

<span data-ttu-id="e2c21-110">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e2c21-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="e2c21-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2c21-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e2c21-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2c21-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e2c21-113">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c21-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c21-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c21-114">See also</span></span>

- [<span data-ttu-id="e2c21-115">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2c21-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
