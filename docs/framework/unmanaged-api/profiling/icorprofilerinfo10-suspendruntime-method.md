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
ms.openlocfilehash: a4c875f6aae996271dee9ac193768ef6981efc19
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863042"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="2a3f4-102">ICorProfilerInfo10:: SuspendRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a3f4-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="2a3f4-103">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="2a3f4-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a3f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a3f4-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="2a3f4-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a3f4-105">Requirements</span></span>

<span data-ttu-id="2a3f4-106">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="2a3f4-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="2a3f4-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a3f4-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2a3f4-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a3f4-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2a3f4-109">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a3f4-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2a3f4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a3f4-110">See also</span></span>

- [<span data-ttu-id="2a3f4-111">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a3f4-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
