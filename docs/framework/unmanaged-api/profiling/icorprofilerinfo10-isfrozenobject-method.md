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
ms.openlocfilehash: c4d31c96fd7470a153437ffb0125e81ca8ea77bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759761"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="92cad-103">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="92cad-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="92cad-104">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="92cad-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="92cad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92cad-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="92cad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92cad-106">Parameters</span></span>

<span data-ttu-id="92cad-107">`objectId` 'ndaki İncelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="92cad-107">`objectId` [in] The object to examine.</span></span>

<span data-ttu-id="92cad-108">`pbFrozen` dışı `BOOL` Nesnenin salt okunurdur bir kesimde olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92cad-108">`pbFrozen` [out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="92cad-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92cad-109">Requirements</span></span>

<span data-ttu-id="92cad-110">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="92cad-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="92cad-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92cad-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="92cad-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92cad-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="92cad-113">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92cad-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="92cad-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92cad-114">See also</span></span>

- [<span data-ttu-id="92cad-115">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92cad-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
