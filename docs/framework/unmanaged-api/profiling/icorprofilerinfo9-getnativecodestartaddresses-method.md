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
ms.openlocfilehash: 062aebf6d5bed208ea71b215bd9f857b82483673
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759058"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="d7b01-103">ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7b01-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="d7b01-104">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d7b01-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7b01-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7b01-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="d7b01-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7b01-106">Parameters</span></span>

<span data-ttu-id="d7b01-107">`functionId` 'ndaki Yerel kod başlatma adresleri döndürülecek olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d7b01-107">`functionId` [in] The ID of the function whose native code start addresses should be returned.</span></span>

<span data-ttu-id="d7b01-108">`reJitId` 'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="d7b01-108">`reJitId` [in] The identity of the JIT-recompiled function.</span></span>

<span data-ttu-id="d7b01-109">`cCodeStartAddresses` 'ndaki Dizinin en büyük boyutu `codeStartAddresses` .</span><span class="sxs-lookup"><span data-stu-id="d7b01-109">`cCodeStartAddresses` [in] The maximum size of the `codeStartAddresses` array.</span></span>

<span data-ttu-id="d7b01-110">`pcCodeStartAddresses` dışı Kullanılabilir adreslerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="d7b01-110">`pcCodeStartAddresses` [out] The number of available addresses.</span></span>

<span data-ttu-id="d7b01-111">`codeStartAddresses` dışı `UINT_PTR`Her birinin, belirtilen işlev için yerel gövde başlangıç adresi olan dizisi.</span><span class="sxs-lookup"><span data-stu-id="d7b01-111">`codeStartAddresses` [out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7b01-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7b01-112">Remarks</span></span>

<span data-ttu-id="d7b01-113">Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7b01-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7b01-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7b01-114">Requirements</span></span>

<span data-ttu-id="d7b01-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d7b01-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="d7b01-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d7b01-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d7b01-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d7b01-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d7b01-118">**.NET sürümleri:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7b01-118">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d7b01-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7b01-119">See also</span></span>

- [<span data-ttu-id="d7b01-120">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7b01-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
