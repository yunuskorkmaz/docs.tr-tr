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
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973707"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="a8350-102">ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8350-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>
  
 <span data-ttu-id="a8350-103">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="a8350-103">Retrieves information about dynamic methods.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="a8350-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8350-104">Syntax</span></span>  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8350-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8350-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a8350-106">'ndaki Bilgi alınacak işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a8350-106">[in] The ID of the function for which to retrieve information.</span></span>  

 `moduleId`  
 <span data-ttu-id="a8350-107">'ndaki İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8350-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="a8350-108">dışı İşlev için imzaya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8350-108">[out] A pointer to the signature for the function.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="a8350-109">dışı İşlev imzası için bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8350-109">[out] A pointer to the count of bytes for the function signature.</span></span>
  
 `cchName`  
 <span data-ttu-id="a8350-110">'ndaki `wszName` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="a8350-110">[in] The maximum size of the `wszName` array.</span></span>
  
 `pcchName`  
 <span data-ttu-id="a8350-111">dışı `wszName` Dizideki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a8350-111">[out] The number of characters in the `wszName` array.</span></span>

 `wszName` \
 <span data-ttu-id="a8350-112">dışı Bir dizi `WCHAR` , varsa işlevin adıdır.</span><span class="sxs-lookup"><span data-stu-id="a8350-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a8350-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8350-113">Remarks</span></span>  
 <span data-ttu-id="a8350-114">Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="a8350-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="a8350-115">Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8350-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

 <span data-ttu-id="a8350-116">Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8350-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>  
  

## <a name="requirements"></a><span data-ttu-id="a8350-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8350-117">Requirements</span></span>  
 <span data-ttu-id="a8350-118">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8350-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8350-119">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8350-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8350-120">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8350-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8350-121">**.NET Framework sürümleri:** [! [NET_CURRENT_V472PLUS](../../../../includes/net-current-v472plus.md) Ekle</span><span class="sxs-lookup"><span data-stu-id="a8350-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8350-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8350-122">See also</span></span>
- [<span data-ttu-id="a8350-123">ICorProfilerInfo8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8350-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

