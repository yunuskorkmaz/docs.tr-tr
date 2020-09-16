---
title: 'ICorProfilerInfo9:: Getnativecodestartaadresler'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ca1643dfa980fa647164accf6432082428124acb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541245"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="94176-102">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="94176-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="94176-103">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="94176-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="94176-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="94176-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="94176-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94176-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="94176-106">\[' de] yerel kod başlatma adresleri döndürülecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="94176-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="94176-107">\[içinde] JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="94176-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="94176-108">\[' de] dizinin en büyük boyutu `codeStartAddresses` .</span><span class="sxs-lookup"><span data-stu-id="94176-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="94176-109">\[out] kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="94176-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="94176-110">\[out] `UINT_PTR` her biri, belirtilen işlev için yerel gövde başlangıç adresidir.</span><span class="sxs-lookup"><span data-stu-id="94176-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="94176-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94176-111">Remarks</span></span>

<span data-ttu-id="94176-112">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="94176-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="94176-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94176-113">Requirements</span></span>

<span data-ttu-id="94176-114">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="94176-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="94176-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="94176-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="94176-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="94176-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="94176-117">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94176-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="94176-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94176-118">See also</span></span>

- [<span data-ttu-id="94176-119">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94176-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
