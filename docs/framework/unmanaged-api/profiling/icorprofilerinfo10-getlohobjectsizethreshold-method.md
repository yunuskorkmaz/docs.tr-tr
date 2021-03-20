---
description: ': ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerInfo10:: GetLOHObjectSizeThreshold'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7dca887f6d0ff5f9360b0edaa1568bc4b1bb42ac
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759774"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="45505-103">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="45505-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="45505-104">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="45505-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="45505-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45505-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="45505-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45505-106">Parameters</span></span>

<span data-ttu-id="45505-107">`pThreshold` dışı Bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="45505-107">`pThreshold` [out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="45505-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45505-108">Remarks</span></span>

<span data-ttu-id="45505-109">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="45505-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="45505-110">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="45505-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="45505-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45505-111">Requirements</span></span>

<span data-ttu-id="45505-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="45505-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="45505-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="45505-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="45505-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="45505-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="45505-115">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45505-115">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="45505-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45505-116">See also</span></span>

- [<span data-ttu-id="45505-117">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45505-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
