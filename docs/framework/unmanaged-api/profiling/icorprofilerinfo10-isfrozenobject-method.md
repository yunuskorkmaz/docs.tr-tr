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
ms.openlocfilehash: b07e456f7fa9c328217b8779733d45dfe2793fe2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753282"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="d41ce-103">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="d41ce-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="d41ce-104">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d41ce-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="d41ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d41ce-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="d41ce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d41ce-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="d41ce-107">\[içinde] incelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="d41ce-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="d41ce-108">\[out] bir `BOOL` nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d41ce-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="d41ce-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d41ce-109">Requirements</span></span>

<span data-ttu-id="d41ce-110">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d41ce-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="d41ce-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d41ce-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d41ce-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d41ce-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d41ce-113">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d41ce-113">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d41ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41ce-114">See also</span></span>

- [<span data-ttu-id="d41ce-115">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d41ce-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
