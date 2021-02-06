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
ms.openlocfilehash: 8ab942e6919f8029ef0d1c20336917622a1d22ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646536"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="62130-103">ICorProfilerInfo8:: ısfunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="62130-103">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="62130-104">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="62130-104">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="62130-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62130-105">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="62130-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62130-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="62130-107">\[içinde] `FunctionID` söz konusu işlevi tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="62130-107">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="62130-108">\[out] `BOOL` işlevin bir meta veri içermediğini belirten bir değer içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="62130-108">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="62130-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62130-109">Remarks</span></span>

<span data-ttu-id="62130-110">Bir işlev, meta veri yoksa dinamik olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="62130-110">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="62130-111">Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="62130-111">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="62130-112">Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="62130-112">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="62130-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62130-113">Requirements</span></span>

<span data-ttu-id="62130-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62130-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="62130-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="62130-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="62130-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62130-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="62130-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62130-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="62130-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62130-118">See also</span></span>

- [<span data-ttu-id="62130-119">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62130-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
