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
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543952"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="53322-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="53322-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="53322-103">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="53322-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="53322-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="53322-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="53322-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53322-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="53322-106">\[out] bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="53322-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="53322-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53322-107">Remarks</span></span>

<span data-ttu-id="53322-108">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="53322-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="53322-109">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="53322-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="53322-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53322-110">Requirements</span></span>

<span data-ttu-id="53322-111">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="53322-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="53322-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53322-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="53322-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="53322-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="53322-114">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53322-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="53322-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53322-115">See also</span></span>

- [<span data-ttu-id="53322-116">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53322-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
