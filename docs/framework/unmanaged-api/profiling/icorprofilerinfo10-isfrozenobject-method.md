---
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
ms.openlocfilehash: 3755260b885768de6b5b2d6342c0ad590a95caff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548676"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="3bf34-102">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bf34-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="3bf34-103">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3bf34-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bf34-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3bf34-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="3bf34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bf34-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="3bf34-106">\[içinde] incelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="3bf34-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="3bf34-107">\[out] bir `BOOL` nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="3bf34-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="3bf34-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bf34-108">Requirements</span></span>

<span data-ttu-id="3bf34-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="3bf34-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="3bf34-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3bf34-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3bf34-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3bf34-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3bf34-112">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf34-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3bf34-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf34-113">See also</span></span>

- [<span data-ttu-id="3bf34-114">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bf34-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
