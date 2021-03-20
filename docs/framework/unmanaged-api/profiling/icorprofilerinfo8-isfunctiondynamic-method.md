---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo8:: ısfunctiondynamic yöntemi'
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
ms.openlocfilehash: 139edeed3e078668974382f1719c8e03f83e2a09
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759084"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="871b4-103">ICorProfilerInfo8:: ısfunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="871b4-103">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="871b4-104">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="871b4-104">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="871b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="871b4-105">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="871b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="871b4-106">Parameters</span></span>

<span data-ttu-id="871b4-107">`functionId` 'ndaki  `FunctionID` Bu işlev, söz konusu işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="871b4-107">`functionId` [in]  The `FunctionID` that identifies the function in question.</span></span>

<span data-ttu-id="871b4-108">`isDynamic` dışı İşlevin bir işaretçisi, `BOOL` işlevinin meta veri içermediğini belirten bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="871b4-108">`isDynamic` [out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="871b4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="871b4-109">Remarks</span></span>

<span data-ttu-id="871b4-110">Bir işlev, meta veri yoksa dinamik olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="871b4-110">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="871b4-111">Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="871b4-111">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="871b4-112">Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="871b4-112">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="871b4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="871b4-113">Requirements</span></span>

<span data-ttu-id="871b4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="871b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="871b4-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="871b4-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="871b4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="871b4-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="871b4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="871b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="871b4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="871b4-118">See also</span></span>

- [<span data-ttu-id="871b4-119">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="871b4-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
