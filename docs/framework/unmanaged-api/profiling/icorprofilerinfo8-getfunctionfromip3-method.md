---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi'
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
ms.openlocfilehash: 3ce0a0964e26254ab09e515826b6bceb657e07bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783839"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="14f5f-103">ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="14f5f-103">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="14f5f-104">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="14f5f-104">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="14f5f-105">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="14f5f-105">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="14f5f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14f5f-106">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="14f5f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14f5f-107">Parameters</span></span>

- `ip`

  <span data-ttu-id="14f5f-108">\[' de] Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="14f5f-108">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="14f5f-109">\[out] işlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="14f5f-109">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="14f5f-110">\[out] işlevin JıT-yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="14f5f-110">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="14f5f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14f5f-111">Remarks</span></span>

<span data-ttu-id="14f5f-112">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="14f5f-112">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="14f5f-113">Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="14f5f-113">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="14f5f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14f5f-114">Requirements</span></span>

<span data-ttu-id="14f5f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f5f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="14f5f-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="14f5f-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="14f5f-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14f5f-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="14f5f-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14f5f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="14f5f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14f5f-119">See also</span></span>

- [<span data-ttu-id="14f5f-120">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14f5f-120">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
