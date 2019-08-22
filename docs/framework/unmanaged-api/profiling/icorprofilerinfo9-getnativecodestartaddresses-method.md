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
ms.openlocfilehash: 80571933bc8d91c074dbee62aad50cece6277d51
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665503"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="0eeb5-102">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="0eeb5-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="0eeb5-103">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="0eeb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0eeb5-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a><span data-ttu-id="0eeb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0eeb5-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="0eeb5-106">'ndaki Yerel kod başlatma adresleri döndürülecek olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>

`reJitId` \
<span data-ttu-id="0eeb5-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-107">[in] The identity of the JIT-recompiled function.</span></span>

`cCodeStartAddresses` \
<span data-ttu-id="0eeb5-108">'ndaki `codeStartAddresses` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

`pcCodeStartAddresses` \
<span data-ttu-id="0eeb5-109">dışı Kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-109">[out] The number of available addresses.</span></span>

`codeStartAddresses` \
<span data-ttu-id="0eeb5-110">dışı Her birinin `UINT_PTR`, belirtilen işlev için yerel gövde başlangıç adresi olan dizisi.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="0eeb5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0eeb5-111">Remarks</span></span>

<span data-ttu-id="0eeb5-112">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="0eeb5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0eeb5-113">Requirements</span></span>

<span data-ttu-id="0eeb5-114">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="0eeb5-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="0eeb5-115">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0eeb5-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0eeb5-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0eeb5-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0eeb5-117">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eeb5-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0eeb5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0eeb5-118">See also</span></span>

- [<span data-ttu-id="0eeb5-119">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="0eeb5-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
