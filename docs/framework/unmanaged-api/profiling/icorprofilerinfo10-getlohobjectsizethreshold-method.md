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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661235"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="a3c92-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3c92-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="a3c92-103">Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a3c92-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3c92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3c92-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a><span data-ttu-id="a3c92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3c92-105">Parameters</span></span>

`pThreshold` \
<span data-ttu-id="a3c92-106">dışı Bayt cinsinden büyük nesne yığın eşiği.</span><span class="sxs-lookup"><span data-stu-id="a3c92-106">[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3c92-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3c92-107">Remarks</span></span>

<span data-ttu-id="a3c92-108">Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3c92-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="a3c92-109">.NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.</span><span class="sxs-lookup"><span data-stu-id="a3c92-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3c92-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3c92-110">Requirements</span></span>

<span data-ttu-id="a3c92-111">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="a3c92-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="a3c92-112">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3c92-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a3c92-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3c92-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a3c92-114">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c92-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a3c92-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3c92-115">See also</span></span>

- [<span data-ttu-id="a3c92-116">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3c92-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
