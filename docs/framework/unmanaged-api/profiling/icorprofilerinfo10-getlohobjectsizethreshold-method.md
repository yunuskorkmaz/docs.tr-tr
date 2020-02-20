---
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
ms.openlocfilehash: 7a0f6f6bea5bc919ebfe9c9acc3b02a31eaa7cd0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452220"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="bfa08-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfa08-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="bfa08-103">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bfa08-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfa08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfa08-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="bfa08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfa08-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="bfa08-106">\[out] bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="bfa08-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfa08-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfa08-107">Remarks</span></span>

<span data-ttu-id="bfa08-108">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="bfa08-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="bfa08-109">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir `pThreshold`, etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="bfa08-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfa08-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfa08-110">Requirements</span></span>

<span data-ttu-id="bfa08-111">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="bfa08-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="bfa08-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bfa08-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="bfa08-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bfa08-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bfa08-114">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa08-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bfa08-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfa08-115">See also</span></span>

- [<span data-ttu-id="bfa08-116">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfa08-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
