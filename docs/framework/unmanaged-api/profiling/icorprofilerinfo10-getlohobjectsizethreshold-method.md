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
ms.openlocfilehash: 96c502dba5b2807f9cd9c3c5cceb6b3b9985a406
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106962"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="93d65-103">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="93d65-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="93d65-104">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="93d65-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="93d65-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93d65-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="93d65-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93d65-106">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="93d65-107">\[out] bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="93d65-107">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="93d65-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93d65-108">Remarks</span></span>

<span data-ttu-id="93d65-109">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="93d65-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="93d65-110">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="93d65-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="93d65-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93d65-111">Requirements</span></span>

<span data-ttu-id="93d65-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="93d65-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="93d65-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93d65-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="93d65-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="93d65-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="93d65-115">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d65-115">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="93d65-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93d65-116">See also</span></span>

- [<span data-ttu-id="93d65-117">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93d65-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
