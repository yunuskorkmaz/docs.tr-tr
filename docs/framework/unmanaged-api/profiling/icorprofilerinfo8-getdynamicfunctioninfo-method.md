---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi'
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
ms.openlocfilehash: 48c8dbe20ccafb3fb23e9e289f728d5e3370613a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646588"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="26017-103">ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="26017-103">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="26017-104">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="26017-104">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="26017-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26017-105">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="26017-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26017-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="26017-107">\[' de] bilgi alınacak işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="26017-107">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="26017-108">\[' de] işlevin üst sınıfının tanımlandığı modülün bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="26017-108">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="26017-109">\[out] işlev için imzaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26017-109">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="26017-110">\[out] işlev imzası için bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26017-110">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="26017-111">\[' de] dizinin en büyük boyutu `wszName` .</span><span class="sxs-lookup"><span data-stu-id="26017-111">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="26017-112">\[out] dizideki karakterlerin sayısı `wszName` .</span><span class="sxs-lookup"><span data-stu-id="26017-112">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="26017-113">\[out] bir dizi varsa `WCHAR` işlevin adıdır.</span><span class="sxs-lookup"><span data-stu-id="26017-113">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="26017-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26017-114">Remarks</span></span>

<span data-ttu-id="26017-115">Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="26017-115">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="26017-116">Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="26017-116">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="26017-117">Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26017-117">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="26017-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26017-118">Requirements</span></span>

<span data-ttu-id="26017-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26017-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="26017-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26017-120">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="26017-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26017-121">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="26017-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26017-122">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="26017-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26017-123">See also</span></span>

- [<span data-ttu-id="26017-124">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26017-124">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
