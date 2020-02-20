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
ms.openlocfilehash: 21f9cb415f913a9c865a487f6e80523344db811e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452194"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="f2135-102">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2135-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="f2135-103">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f2135-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2135-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2135-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="f2135-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2135-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="f2135-106">\[içinde] incelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="f2135-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="f2135-107">\[out] nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir `BOOL`.</span><span class="sxs-lookup"><span data-stu-id="f2135-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2135-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2135-108">Requirements</span></span>

<span data-ttu-id="f2135-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f2135-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="f2135-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2135-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f2135-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2135-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f2135-112">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2135-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f2135-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2135-113">See also</span></span>

- [<span data-ttu-id="f2135-114">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2135-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
