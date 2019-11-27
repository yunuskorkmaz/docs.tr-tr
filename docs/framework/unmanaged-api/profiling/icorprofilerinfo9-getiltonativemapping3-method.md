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
ms.openlocfilehash: 1a5a259e6604d906e55166b3fcb770bc37d346c5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444726"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="1a0e9-102">ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a0e9-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="1a0e9-103">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a0e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a0e9-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a><span data-ttu-id="1a0e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a0e9-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="1a0e9-106">'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-106">[in] A pointer to the start of a native function.</span></span>

`cMap` \
<span data-ttu-id="1a0e9-107">'ndaki `map` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-107">[in] The maximum size of the `map` array.</span></span>

`pcMap` \
<span data-ttu-id="1a0e9-108">dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

`map` \
<span data-ttu-id="1a0e9-109">dışı Her biri uzaklıkları belirten [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="1a0e9-110">`GetILToNativeMapping3` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a0e9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a0e9-111">Remarks</span></span>

<span data-ttu-id="1a0e9-112">Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="1a0e9-113">[ICorProfilerInfo9:: Getnativecodestartaaddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a0e9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a0e9-114">Requirements</span></span>

<span data-ttu-id="1a0e9-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1a0e9-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="1a0e9-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1a0e9-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1a0e9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a0e9-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1a0e9-118">**.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0e9-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1a0e9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a0e9-119">See also</span></span>

- [<span data-ttu-id="1a0e9-120">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a0e9-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
