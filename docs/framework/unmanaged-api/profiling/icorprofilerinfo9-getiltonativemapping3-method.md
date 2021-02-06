---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi'
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 867375d57f9d166ed08bf68ada81fb5cdbb8afe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646523"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="fd7f2-103">ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd7f2-103">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="fd7f2-104">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-104">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd7f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd7f2-105">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="fd7f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd7f2-106">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="fd7f2-107">\[' de] yerel bir işlevin başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-107">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="fd7f2-108">\[' de] dizinin en büyük boyutu `map` .</span><span class="sxs-lookup"><span data-stu-id="fd7f2-108">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="fd7f2-109">\[out] kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-109">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="fd7f2-110">\[out] her biri, uzaklıkları belirten [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıların bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-110">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="fd7f2-111">`GetILToNativeMapping3`Yöntem döndüğünde, `map` yapıların bazılarını veya tümünü içerir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="fd7f2-111">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd7f2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd7f2-112">Remarks</span></span>

<span data-ttu-id="fd7f2-113">Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-113">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="fd7f2-114">[ICorProfilerInfo9:: Getnativecodestartaaddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-114">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd7f2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd7f2-115">Requirements</span></span>

<span data-ttu-id="fd7f2-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="fd7f2-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="fd7f2-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fd7f2-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="fd7f2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd7f2-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fd7f2-119">**.NET Framework sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd7f2-119">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fd7f2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd7f2-120">See also</span></span>

- [<span data-ttu-id="fd7f2-121">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd7f2-121">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
