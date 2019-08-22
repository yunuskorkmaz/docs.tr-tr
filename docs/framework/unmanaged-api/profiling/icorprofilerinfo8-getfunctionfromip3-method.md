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
ms.openlocfilehash: 7b0d8033a5ea3b98623b9be384788ef7fc15bf04
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665630"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="64979-102">ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="64979-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="64979-103">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="64979-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="64979-104">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64979-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="64979-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64979-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

#### <a name="parameters"></a><span data-ttu-id="64979-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64979-106">Parameters</span></span>

`ip` \
<span data-ttu-id="64979-107">'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="64979-107">[in] The instruction pointer in managed code.</span></span>

`pFunctionId` \
<span data-ttu-id="64979-108">dışı İşlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="64979-108">[out] The function ID.</span></span>

`pReJitId` \
<span data-ttu-id="64979-109">dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="64979-109">[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="64979-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64979-110">Remarks</span></span>

<span data-ttu-id="64979-111">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64979-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="64979-112">Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="64979-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="64979-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64979-113">Requirements</span></span>

<span data-ttu-id="64979-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64979-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="64979-115">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="64979-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="64979-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64979-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="64979-117">**.NET Framework sürümleri:** [! [NET_CURRENT_V472PLUS](../../../../includes/net-current-v472plus.md) Ekle</span><span class="sxs-lookup"><span data-stu-id="64979-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="64979-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64979-118">See also</span></span>

- [<span data-ttu-id="64979-119">ICorProfilerInfo8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="64979-119">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
