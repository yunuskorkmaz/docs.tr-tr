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
ms.openlocfilehash: 97b127c9a6aac0a0fefe25faf294791dcd2c8e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436040"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="f03ff-102">ICorProfilerInfo2::GetArrayObjectInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="f03ff-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="f03ff-103">Bir dizi nesnesi hakkında ayrıntılı bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="f03ff-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f03ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f03ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f03ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f03ff-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f03ff-106">'ndaki Geçerli bir array nesnesinin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f03ff-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="f03ff-107">'ndaki Dizinin derece (boyut sayısı).</span><span class="sxs-lookup"><span data-stu-id="f03ff-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="f03ff-108">dışı Her biri dizi boyutunun boyutunu temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="f03ff-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="f03ff-109">dışı Her biri dizi boyutunun alt sınırını temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="f03ff-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="f03ff-110">dışı Dizi için, C++ kurala göre düzenlendiği ham arabelleğin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f03ff-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f03ff-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f03ff-111">Remarks</span></span>  
 <span data-ttu-id="f03ff-112">`pDimensionSizes` ve `pDimensionLowerBounds` paralel dizilerdir, bu nedenle her dizide aynı dizinde bulunan öğeler aynı varlığın niteliklerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f03ff-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f03ff-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f03ff-113">Requirements</span></span>  
 <span data-ttu-id="f03ff-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f03ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f03ff-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f03ff-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f03ff-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f03ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f03ff-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f03ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03ff-118">See also</span></span>

- [<span data-ttu-id="f03ff-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f03ff-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f03ff-120">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f03ff-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
