---
title: 'ICorProfilerInfo8:: Getdynamicfunctionınfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495326"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="b2ebe-102">ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ebe-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="b2ebe-103">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2ebe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2ebe-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="b2ebe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2ebe-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b2ebe-106">\[' de] bilgi alınacak işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-106">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="b2ebe-107">\[' de] işlevin üst sınıfının tanımlandığı modülün bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-107">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="b2ebe-108">\[out] işlev için imzaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-108">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="b2ebe-109">\[out] işlev imzası için bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-109">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="b2ebe-110">\[' de] dizinin en büyük boyutu `wszName` .</span><span class="sxs-lookup"><span data-stu-id="b2ebe-110">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="b2ebe-111">\[out] dizideki karakterlerin sayısı `wszName` .</span><span class="sxs-lookup"><span data-stu-id="b2ebe-111">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="b2ebe-112">\[out] bir dizi varsa `WCHAR` işlevin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-112">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2ebe-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2ebe-113">Remarks</span></span>

<span data-ttu-id="b2ebe-114">Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="b2ebe-115">Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="b2ebe-116">Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2ebe-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2ebe-117">Requirements</span></span>

<span data-ttu-id="b2ebe-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ebe-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b2ebe-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b2ebe-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b2ebe-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2ebe-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b2ebe-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ebe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b2ebe-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ebe-122">See also</span></span>

- [<span data-ttu-id="b2ebe-123">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2ebe-123">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
