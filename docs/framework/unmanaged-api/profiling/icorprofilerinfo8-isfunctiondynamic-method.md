---
title: 'ICorProfilerInfo8:: ısfunctiondynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861742"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="161e0-102">ICorProfilerInfo8:: ısfunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="161e0-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="161e0-103">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="161e0-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="161e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="161e0-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="161e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="161e0-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="161e0-106">\[içinde, söz konusu işlevi tanımlayan `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="161e0-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="161e0-107">\[out] işlevin meta veri içermediğini belirten bir değer içeren bir `BOOL` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="161e0-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="161e0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="161e0-108">Remarks</span></span>

<span data-ttu-id="161e0-109">Bir işlev, meta veri yoksa dinamik olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="161e0-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="161e0-110">Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="161e0-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="161e0-111">Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="161e0-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="161e0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="161e0-112">Requirements</span></span>

<span data-ttu-id="161e0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="161e0-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="161e0-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="161e0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="161e0-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="161e0-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="161e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="161e0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="161e0-117">See also</span></span>

- [<span data-ttu-id="161e0-118">ICorProfilerInfo8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="161e0-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
