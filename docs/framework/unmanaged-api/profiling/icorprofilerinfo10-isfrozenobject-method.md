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
ms.openlocfilehash: 250021c9eb475d0cbcb1bd14c8515b969fc9d30b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449830"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="961ef-102">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="961ef-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="961ef-103">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="961ef-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="961ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="961ef-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="961ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="961ef-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="961ef-106">'ndaki İncelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="961ef-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="961ef-107">dışı Nesnenin salt okunurdur bir kesimde olup olmadığını belirten `BOOL`.</span><span class="sxs-lookup"><span data-stu-id="961ef-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="961ef-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="961ef-108">Requirements</span></span>

<span data-ttu-id="961ef-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="961ef-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="961ef-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="961ef-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="961ef-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="961ef-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="961ef-112">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="961ef-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="961ef-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="961ef-113">See also</span></span>

- [<span data-ttu-id="961ef-114">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="961ef-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
