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
ms.openlocfilehash: 1b753350f45f722d60099b17cfdd48bfd06e411a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759110"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="c2ce3-103">ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2ce3-103">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="c2ce3-104">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-104">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="c2ce3-105">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-105">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2ce3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2ce3-106">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="c2ce3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2ce3-107">Parameters</span></span>

<span data-ttu-id="c2ce3-108">`ip` 'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-108">`ip` [in] The instruction pointer in managed code.</span></span>

<span data-ttu-id="c2ce3-109">`pFunctionId` dışı İşlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-109">`pFunctionId` [out] The function ID.</span></span>

<span data-ttu-id="c2ce3-110">`pReJitId` dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-110">`pReJitId` [out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2ce3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2ce3-111">Remarks</span></span>

<span data-ttu-id="c2ce3-112">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-112">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="c2ce3-113">Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-113">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2ce3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2ce3-114">Requirements</span></span>

<span data-ttu-id="c2ce3-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ce3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c2ce3-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2ce3-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c2ce3-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c2ce3-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c2ce3-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ce3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c2ce3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2ce3-119">See also</span></span>

- [<span data-ttu-id="c2ce3-120">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2ce3-120">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
