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
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495131"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="60a33-102">ICorProfilerInfo8:: ısfunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="60a33-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="60a33-103">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="60a33-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="60a33-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="60a33-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="60a33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60a33-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="60a33-106">\[içinde] `FunctionID` söz konusu işlevi tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="60a33-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="60a33-107">\[out] `BOOL` işlevin bir meta veri içermediğini belirten bir değer içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="60a33-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="60a33-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60a33-108">Remarks</span></span>

<span data-ttu-id="60a33-109">Bir işlev, meta veri yoksa dinamik olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="60a33-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="60a33-110">Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="60a33-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="60a33-111">Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="60a33-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="60a33-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60a33-112">Requirements</span></span>

<span data-ttu-id="60a33-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a33-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="60a33-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="60a33-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="60a33-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60a33-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="60a33-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60a33-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="60a33-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60a33-117">See also</span></span>

- [<span data-ttu-id="60a33-118">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60a33-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
