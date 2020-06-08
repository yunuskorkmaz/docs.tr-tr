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
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497367"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="30aec-102">ICorProfilerInfo2::GetArrayObjectInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="30aec-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="30aec-103">Bir dizi nesnesi hakkında ayrıntılı bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="30aec-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30aec-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="30aec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30aec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30aec-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="30aec-106">'ndaki Geçerli bir array nesnesinin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="30aec-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="30aec-107">'ndaki Dizinin derece (boyut sayısı).</span><span class="sxs-lookup"><span data-stu-id="30aec-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="30aec-108">dışı Her biri dizi boyutunun boyutunu temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="30aec-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="30aec-109">dışı Her biri dizi boyutunun alt sınırını temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="30aec-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="30aec-110">dışı Dizi için, C++ kuralına göre düzenlendiği ham arabelleğin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30aec-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30aec-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30aec-111">Remarks</span></span>  
 <span data-ttu-id="30aec-112">`pDimensionSizes`Ve `pDimensionLowerBounds` paralel dizilerdir, bu nedenle her dizide aynı dizinde bulunan öğeler aynı varlığın nitelikleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30aec-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30aec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30aec-113">Requirements</span></span>  
 <span data-ttu-id="30aec-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30aec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30aec-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="30aec-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30aec-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="30aec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30aec-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30aec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30aec-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30aec-118">See also</span></span>

- [<span data-ttu-id="30aec-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30aec-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="30aec-120">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30aec-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
