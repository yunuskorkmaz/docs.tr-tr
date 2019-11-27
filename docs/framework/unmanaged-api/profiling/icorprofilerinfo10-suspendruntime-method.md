---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5104c779f99ef9f26a9eccc00008ded62336d8e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426964"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="8d69c-102">ICorProfilerInfo10:: SuspendRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d69c-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="8d69c-103">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="8d69c-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d69c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d69c-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="8d69c-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d69c-105">Requirements</span></span>

<span data-ttu-id="8d69c-106">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="8d69c-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="8d69c-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d69c-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="8d69c-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8d69c-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8d69c-109">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d69c-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8d69c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d69c-110">See also</span></span>

- [<span data-ttu-id="8d69c-111">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d69c-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
