---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi'
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
ms.openlocfilehash: 1ca686cef4a45ebb9e05190fa790ed5300c0d816
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646497"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="a7d12-103">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7d12-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="a7d12-104">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a7d12-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7d12-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7d12-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="a7d12-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7d12-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="a7d12-107">\[' de] yerel kod başlatma adresleri döndürülecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a7d12-107">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="a7d12-108">\[içinde] JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="a7d12-108">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="a7d12-109">\[' de] dizinin en büyük boyutu `codeStartAddresses` .</span><span class="sxs-lookup"><span data-stu-id="a7d12-109">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="a7d12-110">\[out] kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a7d12-110">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="a7d12-111">\[out] `UINT_PTR` her biri, belirtilen işlev için yerel gövde başlangıç adresidir.</span><span class="sxs-lookup"><span data-stu-id="a7d12-111">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7d12-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7d12-112">Remarks</span></span>

<span data-ttu-id="a7d12-113">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7d12-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7d12-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7d12-114">Requirements</span></span>

<span data-ttu-id="a7d12-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a7d12-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="a7d12-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7d12-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a7d12-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7d12-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a7d12-118">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d12-118">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d12-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7d12-119">See also</span></span>

- [<span data-ttu-id="a7d12-120">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7d12-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
