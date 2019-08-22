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
ms.openlocfilehash: 74300a12d000565a63cd7ea862c759d47b87bbe1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665691"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="ae89a-102">ICorProfilerInfo10:: SuspendRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae89a-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="ae89a-103">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="ae89a-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae89a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae89a-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="ae89a-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae89a-105">Requirements</span></span>

<span data-ttu-id="ae89a-106">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="ae89a-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="ae89a-107">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ae89a-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ae89a-108">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae89a-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ae89a-109">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae89a-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ae89a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae89a-110">See also</span></span>

- [<span data-ttu-id="ae89a-111">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae89a-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
