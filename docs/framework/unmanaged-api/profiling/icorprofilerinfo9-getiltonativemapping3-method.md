---
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
ms.openlocfilehash: 22fe5608b0a3f86baf80abb3810a512077954ac3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449757"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="663f2-102">ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="663f2-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="663f2-103">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="663f2-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="663f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="663f2-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="663f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="663f2-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="663f2-106">\[, yerel bir işlevin başlangıcına yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="663f2-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="663f2-107">\[içinde] `map` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="663f2-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="663f2-108">\[out] kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="663f2-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="663f2-109">\[out] her biri, uzaklıkları belirten [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıların bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="663f2-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="663f2-110">`GetILToNativeMapping3` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="663f2-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="663f2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="663f2-111">Remarks</span></span>

<span data-ttu-id="663f2-112">Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="663f2-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="663f2-113">[ICorProfilerInfo9:: Getnativecodestartaaddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="663f2-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="663f2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="663f2-114">Requirements</span></span>

<span data-ttu-id="663f2-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="663f2-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="663f2-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="663f2-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="663f2-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="663f2-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="663f2-118">**.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="663f2-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="663f2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663f2-119">See also</span></span>

- [<span data-ttu-id="663f2-120">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="663f2-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
