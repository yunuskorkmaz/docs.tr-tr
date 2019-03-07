---
title: ICorProfilerInfo2::GetArrayObjectInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fe86fbe7ee51e5f53eeea74d7d5a56046de5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484400"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="f1d7c-102">ICorProfilerInfo2::GetArrayObjectInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="f1d7c-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="f1d7c-103">Bir dizi nesnesi hakkında ayrıntılı bilgiler alır.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1d7c-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1d7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1d7c-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f1d7c-106">[in] Geçerli dizi nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="f1d7c-107">[in] Boyut (boyut sayısı) dizisi.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="f1d7c-108">[out] Her bir dizinin boyutu boyutunu gösteren tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="f1d7c-109">[out] Tamsayı içeren bir dizi, her alt temsil eden bir dizinin boyutu bağlı.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="f1d7c-110">[out] C++ kuralına göre düzenlendiğini dizisi için ham arabelleği adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1d7c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1d7c-111">Remarks</span></span>  
 <span data-ttu-id="f1d7c-112">`pDimensionSizes` Ve `pDimensionLowerBounds` aynı dizinde her dizi konumunda bulunan öğeleri aynı varlık özelliklerini şekilde paralel, dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1d7c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1d7c-113">Requirements</span></span>  
 <span data-ttu-id="f1d7c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1d7c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1d7c-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1d7c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1d7c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1d7c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1d7c-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1d7c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d7c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1d7c-118">See also</span></span>
- [<span data-ttu-id="f1d7c-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1d7c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f1d7c-120">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1d7c-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
