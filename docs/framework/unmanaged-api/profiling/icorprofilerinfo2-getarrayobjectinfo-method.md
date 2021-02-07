---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetArrayObjectInfo yöntemi'
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
ms.openlocfilehash: 1427ad696f73d90a2a07698c71456571fb14ee70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760543"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="8b467-103">ICorProfilerInfo2::GetArrayObjectInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="8b467-103">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>

<span data-ttu-id="8b467-104">Bir dizi nesnesi hakkında ayrıntılı bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="8b467-104">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b467-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b467-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b467-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b467-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="8b467-107">'ndaki Geçerli bir array nesnesinin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8b467-107">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="8b467-108">'ndaki Dizinin derece (boyut sayısı).</span><span class="sxs-lookup"><span data-stu-id="8b467-108">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="8b467-109">dışı Her biri dizi boyutunun boyutunu temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="8b467-109">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="8b467-110">dışı Her biri dizi boyutunun alt sınırını temsil eden tamsayılar içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="8b467-110">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="8b467-111">dışı Dizi için, C++ kuralına göre düzenlendiği ham arabelleğin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b467-111">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b467-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b467-112">Remarks</span></span>  

 <span data-ttu-id="8b467-113">`pDimensionSizes`Ve `pDimensionLowerBounds` paralel dizilerdir, bu nedenle her dizide aynı dizinde bulunan öğeler aynı varlığın nitelikleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b467-113">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b467-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b467-114">Requirements</span></span>  

 <span data-ttu-id="8b467-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b467-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b467-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8b467-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b467-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b467-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b467-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b467-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b467-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b467-119">See also</span></span>

- [<span data-ttu-id="8b467-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b467-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8b467-121">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b467-121">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
