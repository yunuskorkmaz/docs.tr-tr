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
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868284"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="dd780-102">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd780-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="dd780-103">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="dd780-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd780-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd780-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="dd780-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd780-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="dd780-106">\[içinde] yerel kod başlatma adresleri döndürülecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dd780-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="dd780-107">\[içinde] JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="dd780-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="dd780-108">\[içinde] `codeStartAddresses` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="dd780-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="dd780-109">\[out] kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="dd780-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="dd780-110">\[out] her biri, belirtilen işlev için yerel bir gövde için başlangıç adresi olan bir `UINT_PTR`dizisi.</span><span class="sxs-lookup"><span data-stu-id="dd780-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd780-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd780-111">Remarks</span></span>

<span data-ttu-id="dd780-112">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd780-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd780-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd780-113">Requirements</span></span>

<span data-ttu-id="dd780-114">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="dd780-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="dd780-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dd780-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dd780-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dd780-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="dd780-117">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd780-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dd780-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd780-118">See also</span></span>

- [<span data-ttu-id="dd780-119">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd780-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
