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
ms.openlocfilehash: 865545e2352209447b3942da3a62f3733c165b35
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759332"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="e12bc-103">ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="e12bc-103">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="e12bc-104">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e12bc-104">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e12bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e12bc-105">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="e12bc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e12bc-106">Parameters</span></span>

<span data-ttu-id="e12bc-107">`pNativeCodeStartAddress` 'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e12bc-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="e12bc-108">`cMap` 'ndaki Dizinin en büyük boyutu `map` .</span><span class="sxs-lookup"><span data-stu-id="e12bc-108">`cMap` [in] The maximum size of the `map` array.</span></span>

<span data-ttu-id="e12bc-109">`pcMap` dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="e12bc-109">`pcMap` [out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

<span data-ttu-id="e12bc-110">`map` dışı Her biri uzaklıkları belirten [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="e12bc-110">`map` [out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="e12bc-111">`GetILToNativeMapping3`Yöntem döndüğünde, `map` yapıların bazılarını veya tümünü içerir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="e12bc-111">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="e12bc-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e12bc-112">Remarks</span></span>

<span data-ttu-id="e12bc-113">Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e12bc-113">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="e12bc-114">[ICorProfilerInfo9:: Getnativecodestartaaddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e12bc-114">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="e12bc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e12bc-115">Requirements</span></span>

<span data-ttu-id="e12bc-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e12bc-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="e12bc-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e12bc-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e12bc-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e12bc-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e12bc-119">**.NET Framework sürümleri:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12bc-119">**.NET Framework Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e12bc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e12bc-120">See also</span></span>

- [<span data-ttu-id="e12bc-121">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e12bc-121">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
