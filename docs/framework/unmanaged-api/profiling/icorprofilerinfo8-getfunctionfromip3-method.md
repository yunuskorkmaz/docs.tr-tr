---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868336"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="d246e-102">ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="d246e-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="d246e-103">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="d246e-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="d246e-104">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d246e-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="d246e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d246e-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="d246e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d246e-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="d246e-107">\[, Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d246e-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="d246e-108">\[out] işlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d246e-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="d246e-109">\[out] işlevin JıT-yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="d246e-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="d246e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d246e-110">Remarks</span></span>

<span data-ttu-id="d246e-111">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d246e-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="d246e-112">Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d246e-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="d246e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d246e-113">Requirements</span></span>

<span data-ttu-id="d246e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d246e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="d246e-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d246e-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d246e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d246e-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d246e-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d246e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d246e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d246e-118">See also</span></span>

- [<span data-ttu-id="d246e-119">ICorProfilerInfo8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d246e-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
