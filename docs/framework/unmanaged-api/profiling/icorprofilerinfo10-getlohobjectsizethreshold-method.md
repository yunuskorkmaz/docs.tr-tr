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
ms.openlocfilehash: 665a08ae226f04d5282b9584932078736751d5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737317"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="dcfc3-103">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcfc3-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="dcfc3-104">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="dcfc3-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcfc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcfc3-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="dcfc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcfc3-106">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="dcfc3-107">\[out] bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="dcfc3-107">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcfc3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcfc3-108">Remarks</span></span>

<span data-ttu-id="dcfc3-109">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="dcfc3-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="dcfc3-110">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="dcfc3-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcfc3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcfc3-111">Requirements</span></span>

<span data-ttu-id="dcfc3-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="dcfc3-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="dcfc3-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dcfc3-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dcfc3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dcfc3-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="dcfc3-115">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcfc3-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dcfc3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcfc3-116">See also</span></span>

- [<span data-ttu-id="dcfc3-117">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcfc3-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
