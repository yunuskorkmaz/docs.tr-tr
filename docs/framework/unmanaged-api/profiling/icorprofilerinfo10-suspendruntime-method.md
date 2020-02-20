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
ms.openlocfilehash: 8d00718579f44a164cd83e2b05d41f70f1c65785
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452155"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="1ba0b-102">ICorProfilerInfo10:: SuspendRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ba0b-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="1ba0b-103">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ba0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba0b-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="1ba0b-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ba0b-105">Requirements</span></span>

<span data-ttu-id="1ba0b-106">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1ba0b-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="1ba0b-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1ba0b-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1ba0b-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ba0b-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1ba0b-109">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba0b-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ba0b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-110">See also</span></span>

- [<span data-ttu-id="1ba0b-111">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ba0b-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
