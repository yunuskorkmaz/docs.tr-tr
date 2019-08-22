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
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661230"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="b19f5-102">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="b19f5-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="b19f5-103">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b19f5-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="b19f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b19f5-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="b19f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b19f5-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="b19f5-106">'ndaki İncelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="b19f5-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="b19f5-107">dışı Nesnenin salt okunurdur bir kesimde olup olmadığını gösterir.`BOOL`</span><span class="sxs-lookup"><span data-stu-id="b19f5-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="b19f5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b19f5-108">Requirements</span></span>

<span data-ttu-id="b19f5-109">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="b19f5-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="b19f5-110">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b19f5-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b19f5-111">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b19f5-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b19f5-112">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19f5-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b19f5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b19f5-113">See also</span></span>

- [<span data-ttu-id="b19f5-114">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b19f5-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
