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
ms.openlocfilehash: b38bd7a4f440edba0a7156176f223ba38c9807cf
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759123"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="6860a-103">ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="6860a-103">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="6860a-104">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="6860a-104">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="6860a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6860a-105">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="6860a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6860a-106">Parameters</span></span>

<span data-ttu-id="6860a-107">`functionId` 'ndaki Bilgi alınacak işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6860a-107">`functionId` [in] The ID of the function for which to retrieve information.</span></span>

<span data-ttu-id="6860a-108">`moduleId` 'ndaki İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6860a-108">`moduleId` [in] A pointer to the module in which the function's parent class is defined.</span></span>

<span data-ttu-id="6860a-109">`ppvSig` dışı İşlev için imzaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6860a-109">`ppvSig` [out] A pointer to the signature for the function.</span></span>

<span data-ttu-id="6860a-110">`pbSig` dışı İşlev imzası için bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6860a-110">`pbSig` [out] A pointer to the count of bytes for the function signature.</span></span>

<span data-ttu-id="6860a-111">`cchName` 'ndaki Dizinin en büyük boyutu `wszName` .</span><span class="sxs-lookup"><span data-stu-id="6860a-111">`cchName` [in] The maximum size of the `wszName` array.</span></span>

<span data-ttu-id="6860a-112">`pcchName` dışı Dizideki karakterlerin sayısı `wszName` .</span><span class="sxs-lookup"><span data-stu-id="6860a-112">`pcchName` [out] The number of characters in the `wszName` array.</span></span>

<span data-ttu-id="6860a-113">`wszName` dışı Bir dizi, varsa `WCHAR` işlevin adıdır.</span><span class="sxs-lookup"><span data-stu-id="6860a-113">`wszName` [out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="6860a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6860a-114">Remarks</span></span>

<span data-ttu-id="6860a-115">Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="6860a-115">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="6860a-116">Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6860a-116">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="6860a-117">Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6860a-117">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="6860a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6860a-118">Requirements</span></span>

<span data-ttu-id="6860a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6860a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6860a-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6860a-120">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="6860a-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6860a-121">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6860a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6860a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6860a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6860a-123">See also</span></span>

- [<span data-ttu-id="6860a-124">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6860a-124">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
